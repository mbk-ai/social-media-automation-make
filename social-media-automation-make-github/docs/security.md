# Security Notes

This repository is intentionally safe for public GitHub showcasing.

## Removed from the exported Make.com scenario

- Make.com connection identifiers
- Google account email addresses
- Gmail recipient address
- Google Sheets spreadsheet identifier
- Facebook Page identifier
- Instagram account identifier
- Account-specific connection labels

## Before publishing your own screenshots

Inspect every screenshot for:

- API keys
- OAuth client secrets
- access tokens
- refresh tokens
- cookies
- private email addresses
- private spreadsheet URLs
- unpublished business information

Use GitHub Secrets or Make.com's built-in connection management for real credentials. Never place production credentials in the repository.
