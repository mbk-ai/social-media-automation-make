# AI Social Media Automation — Make.com

A portfolio-ready **Make.com social media automation** scenario that turns ideas stored in Google Sheets into platform-ready content, generates an image, requests approval, and publishes approved content to Facebook, Instagram, and LinkedIn.

> **Security:** This repository contains a sanitized showcase blueprint. Credentials, connection IDs, account identifiers, page IDs, spreadsheet IDs, and personal email addresses have been removed or replaced with placeholders.

## Workflow Overview

```text
Google Sheets
    │
    ├── status = "content generation"
    │       │
    │       ├── OpenAI → generate Facebook / Instagram / LinkedIn copy
    │       ├── Parse JSON
    │       ├── Google Sheets → save generated copy
    │       ├── OpenAI Image Generation → create 1024×1024 image
    │       ├── Google Sheets → save image URL + "generated" status
    │       └── Gmail → send approval notification
    │
    └── status = "ready to post"
            │
            ├── Facebook → publish post + image
            ├── Instagram → publish photo + caption
            ├── HTTP → download image
            ├── LinkedIn → publish image post
            └── Google Sheets → mark "posting complete"
```

## What This Project Demonstrates

- Business-process automation with Make.com
- AI-assisted social media content generation
- Structured JSON generation and parsing
- AI image generation
- Human-in-the-loop approval
- Google Sheets as a lightweight content management layer
- Multi-platform publishing
- Conditional routing based on content status
- Automated workflow status tracking
- Credential-safe portfolio packaging

## Technology Stack

| Component | Purpose |
|---|---|
| Make.com | Workflow orchestration |
| Google Sheets | Content queue and status tracking |
| OpenAI | Social copy + image generation |
| Gmail | Approval notification |
| Facebook Pages | Facebook publishing |
| Instagram Business | Instagram publishing |
| LinkedIn | LinkedIn image publishing |
| HTTP module | Image download before LinkedIn publishing |

## Scenario Structure

The supplied Make.com scenario contains a Google Sheets intake/filter step followed by a router with two business paths. The first path handles content generation and approval; the second handles publishing of rows marked as ready to post.

### Content Generation Path

1. Read/filter a Google Sheets row.
2. Check for the `content generation` status.
3. Send the idea to OpenAI.
4. Generate JSON containing:
   - Facebook copy
   - Instagram copy
   - LinkedIn copy
5. Parse the generated JSON.
6. Write the generated copy back to Google Sheets.
7. Generate a 1024×1024 image.
8. Store the image URL and update the row to `generated`.
9. Send an approval email.

### Publishing Path

1. Find the next row whose status is `ready to post`.
2. Publish to Facebook.
3. Publish to Instagram.
4. Download the image.
5. Publish the image to LinkedIn.
6. Update the spreadsheet to `posting complete`.

## Google Sheet Structure

The workflow uses these core columns:

- `Idea`
- `status`
- `Facebook post`
- `instagram post`
- `linkedin`
- `image`

Additional columns can be retained for future extensions.

## Status Lifecycle

```text
content generation
        ↓
     generated
        ↓
   ready to post
        ↓
posting complete
```

The status field acts as the workflow's control mechanism and makes the automation easy to operate without building a separate dashboard.

## Import / Setup

### 1. Import the blueprint

In Make.com:

1. Create a new scenario.
2. Import `workflow/make-scenario-sanitized.json`.
3. Reconnect every service when Make asks for missing connections.

### 2. Configure Google Sheets

Create a spreadsheet with the required columns shown above.

Replace:

- `YOUR_GOOGLE_SHEET_ID`

with your own spreadsheet during configuration.

### 3. Configure AI

Reconnect your OpenAI account in the OpenAI modules.

The source workflow uses OpenAI for:

- text generation
- image generation

### 4. Configure approval email

Reconnect Gmail and replace:

- `YOUR_EMAIL@example.com`

with your approval recipient.

### 5. Configure social accounts

Reconnect:

- Facebook Pages
- Instagram Business
- LinkedIn

Replace:

- `YOUR_FACEBOOK_PAGE_ID`
- `YOUR_INSTAGRAM_ACCOUNT_ID`

with the appropriate values when configuring the modules.

## Important Notes

- The sanitized blueprint is intended for **portfolio/showcase use**.
- It is not shipped with working credentials.
- You must reconnect services after import.
- Never commit API keys, OAuth tokens, cookies, access tokens, or private account IDs to GitHub.
- The image-generation module in the source scenario uses DALL·E 3. If your current Make/OpenAI integration offers a newer image model, you can substitute it during implementation.

## Screenshots

Place project screenshots in:

`/screenshots/`

Recommended screenshots:

1. Make.com scenario overview
2. Google Sheets content queue
3. AI-generated social copy
4. Generated image
5. Approval email
6. Published Facebook post
7. Published Instagram post
8. Published LinkedIn post

## Portfolio Value

This project demonstrates more than simple social posting. It shows how a business process can be converted into a controlled automation pipeline with AI generation, structured data, human approval, multi-channel distribution, and state management.

## Repository Structure

```text
social-media-automation-make/
├── README.md
├── LICENSE
├── .gitignore
├── workflow/
│   └── make-scenario-sanitized.json
├── screenshots/
│   └── README.md
├── docs/
│   ├── architecture.md
│   ├── setup-checklist.md
│   └── security.md
├── examples/
│   └── google-sheet-template.csv
└── config/
    └── environment.example
```

## Author

**Md. Motasim Bin Kamal**  
AI Automation Engineer | Make.com | n8n | AI Agents | Workflow Automation

This project is presented as a portfolio demonstration of AI-powered business automation.
