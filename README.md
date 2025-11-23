# Chrome Extension - Google Meet Record Captions

A Chrome extension that records and captures captions from Google Meet sessions.

## Description

This extension allows users to capture and save captions/subtitles during Google Meet video conferences, making it easier to keep records of meetings and discussions.

## Features

- Record captions from Google Meet sessions
- Save captured captions for later review
- Easy-to-use interface

## Installation

1. Clone this repository
2. Open Chrome and navigate to `chrome://extensions/`
3. Enable "Developer mode"
4. Click "Load unpacked" and select the extension directory

## Usage

1. Join a Google Meet session
2. Enable captions in Google Meet
3. Use the extension to start recording captions
4. Stop recording when done
5. Access your saved captions

## Development

This project uses [Spec-Kit](https://github.com/github/spec-kit/) for spec-driven development.

### Development Workflow

This project follows a spec-driven development approach using slash commands:

#### Core Workflow (use in order):

1. `/speckit.constitution` - Establish project principles and development guidelines
2. `/speckit.specify` - Create detailed feature specifications
3. `/speckit.plan` - Create technical implementation plans
4. `/speckit.tasks` - Generate actionable task breakdowns
5. `/speckit.implement` - Execute the full feature build

#### Enhancement Commands (optional):

- `/speckit.clarify` - Ask structured questions to de-risk ambiguous areas (use before planning)
- `/speckit.analyze` - Check cross-artifact consistency and alignment (use after tasks, before implementation)
- `/speckit.checklist` - Generate quality checklists to validate requirements
- `/speckit.taskstoissues` - Convert tasks to GitHub issues

### Setup Spec-Kit

If you need to set up spec-kit:

```bash
# Install spec-kit
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git

# Initialize in project (already done for this project)
specify init --here --ai claude --force

# Verify installation
specify check
```

## License

TBD

## Author

parhumm
