# Privacy & Data Handling

## Overview

The **design-intelligence** bundle processes design-related data to support creative workflows, trend awareness, and aesthetic reasoning. All user data and collected information is stored locally on the user's machine. No data is transmitted to the bundle maintainers.

## What Data Is Collected

### Design Trend Data

- **Content**: RSS feed metadata including titles, URLs, descriptions, and publication dates from [Awwwards](https://www.awwwards.com/), [Siteinspire](https://www.siteinspire.com/), and [The FWA](https://thefwa.com/).
- **Storage**: Stored locally in the `archive/` directory, which is gitignored and never committed to version control.
- **Source**: Publicly available RSS feeds — the intended syndication format provided by these sites.
- **Method**: Standard HTTP GET requests to public RSS endpoints. No automated scraping, headless browsers, or DOM extraction is used.

### User Design Preferences (Taste Profiles)

- **Content**: Aesthetic preferences such as typography, color, spacing, and motion choices, along with confidence levels (Low/Medium/High) derived from observed patterns during design conversations.
- **Storage**: `~/.amplifier/design-preferences.md` (global profile) and `.design/preferences.md` (per-project profile).
- **Opt-in**: Taste profiles are only created when users explicitly confirm a preference proposal. Preferences are never inferred or stored silently.
- **Disclosure**: At session start, users are informed that design preferences may be tracked during the conversation.
- **Opt-out**: Set `taste_tracking: false` in the bundle configuration to disable all preference observation entirely.

### Design Specifications

- **Content**: Project-specific design specs, aesthetic guides, and wireframes created as part of the normal design workflow.
- **Storage**: Stored in the `.design/` directory within the user's project.
- **Visibility**: All generated specifications are visible to the user and managed as standard project files.

### Knowledge Base

- **Content**: The `context/observed-expression/` directory contains shared design knowledge — curated observations about design patterns, aesthetic techniques, and creative expression.
- **Contributions**: Users may be asked to contribute observations to this shared resource. Contributions always require explicit consent.
- **Transparency**: Because contributions are made to a shared, git-tracked resource, users are informed of this before confirming any addition.

## External Services

### Vision AI (Optional, User-Initiated)

When users request visual analysis of screenshots or design assets, images may be sent to one of the following providers:

| Provider | Model | Role |
|---|---|---|
| Google | Gemini Flash | Primary |
| Anthropic | Claude | Fallback |
| OpenAI | GPT-4 Vision | Fallback |

- API keys are provided by the user via environment variables. This bundle does not include or manage API credentials.
- No images are sent without explicit user initiation.
- Refer to each provider's privacy policy for details on how they handle data submitted through their APIs:
  - [Google AI Privacy](https://ai.google.dev/terms)
  - [Anthropic Privacy Policy](https://www.anthropic.com/privacy)
  - [OpenAI Privacy Policy](https://openai.com/policies/privacy-policy)

### RSS Feeds

- Standard HTTP GET requests to public RSS endpoints.
- No authentication is required or used.
- No user data is sent to these services.

## Data Retention

| Data Type | Retention | Location |
|---|---|---|
| Archive data | Stored locally indefinitely by default | `archive/` |
| Taste profiles | Persist until manually deleted by the user | `~/.amplifier/design-preferences.md`, `.design/preferences.md` |
| Design specs | Part of the user's project, managed by the user | `.design/` |

## User Controls

Users have full control over all stored data:

- **Disable preference tracking**: Set `taste_tracking: false` in the bundle configuration.
- **Remove global taste profile**: Delete `~/.amplifier/design-preferences.md`.
- **Remove project taste profile**: Delete `.design/preferences.md`.
- **Remove all collected trend data**: Delete the `archive/` directory.

## No Telemetry

This bundle does not collect telemetry, usage analytics, or any data transmitted to the bundle maintainers. All processing occurs locally within the user's environment.
