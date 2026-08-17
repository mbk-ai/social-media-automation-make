# Architecture

## High-Level Design

```text
                 ┌────────────────────┐
                 │    Google Sheets   │
                 │ Idea + Status      │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │    Make.com        │
                 │ Filter + Router    │
                 └───────┬─────┬──────┘
                         │     │
          Content Gen ───┘     └─── Publishing
                 │                     │
                 ▼                     ▼
        ┌─────────────────┐    ┌─────────────────┐
        │ OpenAI Text     │    │ Facebook        │
        │ Generation      │    │ Instagram       │
        └────────┬────────┘    │ LinkedIn        │
                 │              └─────────────────┘
                 ▼
        ┌─────────────────┐
        │ JSON Parser     │
        └────────┬────────┘
                 ▼
        ┌─────────────────┐
        │ Google Sheets   │
        │ Save copy       │
        └────────┬────────┘
                 ▼
        ┌─────────────────┐
        │ OpenAI Image    │
        └────────┬────────┘
                 ▼
        ┌─────────────────┐
        │ Approval Email  │
        └─────────────────┘
```

## Design Pattern

The scenario uses a **state-driven automation pattern**. Google Sheets stores the state of each content item, while Make.com performs the next action based on the status value.

This makes the workflow:

- easy to understand
- easy to monitor
- simple to restart
- suitable for human approval
- extensible to additional platforms
