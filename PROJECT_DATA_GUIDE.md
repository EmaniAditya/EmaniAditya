# Project Data Fetching Guide

This guide explains how to manage project data for your portfolio websites that use dynamic fetching from this GitHub README.md file.

## Overview

Both the [Shreejee Automobiles](https://shreejeeautomobiles.com/developer) and [Capital Diesels](https://capitaldiesels.com/developer) websites are configured to dynamically fetch project data from this repository's README.md file. This approach centralizes your project information in one place and makes updates easier.

## How It Works

1. The websites look for a specific JSON section in this README.md file
2. The section is marked with `PROJECT-DATA-START` and `PROJECT-DATA-END` tags
3. The JSON is parsed and displayed on the developer page of each site
4. If fetching fails, fallback projects are displayed

## JSON Format

Your project data should follow this structure:

```json
[
  {
    "title": "Project Name",
    "description": {
      "en": "Project description in English"
    },
    "url": "https://project-url.com",
    "techs": ["Technology1", "Technology2", "Framework", "Language"]
  },
  {
    "title": "Another Project",
    "description": {
      "en": "Another project description"
    },
    "url": "https://another-project.com",
    "techs": ["React", "Node.js", "TypeScript"]
  }
]
```

## Adding or Updating Projects

1. Edit this README.md file
2. Locate the section between `PROJECT-DATA-START` and `PROJECT-DATA-END`
3. Update the JSON array with your project information
4. Ensure the JSON is valid (you can use [JSONLint](https://jsonlint.com/) to validate)
5. Commit and push your changes

## Example

```markdown
... other README content ...

PROJECT-DATA-START
[
  {
    "title": "Premove",
    "description": {
      "en": "Fleet management SaaS across web, Android & iOS"
    },
    "url": "https://premove.app",
    "techs": ["React", "Node.js", "React Native"]
  },
  {
    "title": "Capital Diesels",
    "description": {
      "en": "Modern website for Authorized Bosch Diesel Service center in Raipur"
    },
    "url": "https://capitaldiesels.com",
    "techs": ["React", "Tailwind CSS"]
  },
  {
    "title": "Shreejee Automobiles",
    "description": {
      "en": "Official website for TATA Authorized Service Station in Raipur"
    },
    "url": "https://shreejeeautomobiles.com",
    "techs": ["React", "TypeScript", "Framer Motion", "Tailwind CSS"]
  }
]
PROJECT-DATA-END

... other README content ...
```

## Implementation Details

Both websites use these key elements in their implementation:

1. A fetch request to `https://raw.githubusercontent.com/EmaniAditya/EmaniAditya/main/README.md`
2. A regex pattern to extract the JSON data: `/PROJECT-DATA-START\s*\n([\s\S]*?)\s*PROJECT-DATA-END/m`
3. JSON parsing of the extracted content
4. Fallback data in case of fetch failure or parsing errors

## Troubleshooting

If your projects aren't showing up correctly:

1. Verify that your JSON is valid
2. Check that the `PROJECT-DATA-START` and `PROJECT-DATA-END` markers are present and correctly spelled
3. Ensure there's no extra whitespace or characters before or after the markers
4. Check the browser console for any error messages
5. Remember that GitHub raw content can be cached, so changes might not be immediately visible

## Future Enhancements

Consider these potential improvements:

1. Move to a dedicated JSON file in this repository instead of embedding in README
2. Create a simple GitHub Pages API endpoint for more structured data
3. Add more metadata fields like project dates, screenshots, or detailed descriptions
