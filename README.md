# Chrome Extension - Google Meet Caption Recorder

A lightweight Chrome extension that captures and records captions from Google Meet sessions in real-time, automatically saving transcripts every 30 seconds. Everything runs locally in your browser - no accounts, no cloud storage, no internet connection required beyond Google Meet itself.

## Description

This extension allows users to capture and save captions/subtitles during Google Meet video conferences, making it easier to keep records of meetings and discussions. The extension automatically downloads or updates a Markdown file every 30 seconds while recording is active, ensuring you never lose your meeting transcripts even if your browser crashes or the meeting disconnects unexpectedly.

## Features

- **Real-time Caption Capture**: Records captions as they appear in Google Meet, maintaining chronological order
- **Automatic Saves**: Downloads or updates transcript file every 30 seconds during recording
- **Speaker Identification**: Groups consecutive captions by speaker for easy reading
- **Rich Metadata**: Includes meeting title, date, duration, and formatted transcript in each file
- **Fully Local**: All data stays in your browser - no accounts, no cloud services, no external storage
- **Simple Controls**: Start and stop recording with clear visual status indicators
- **Markdown Output**: Generates clean, readable Markdown files with format `GoogleMeet_[MeetingTitle]_[Date]_[StartTime].md`

## Project Status

**Current Phase**: Specification Complete

This project is currently in the specification phase. The feature specification, including detailed requirements, user stories, and acceptance criteria, has been completed using Spec-Kit methodology. Implementation is planned to follow the spec-driven development workflow outlined below.

See [spec.md](specs/001-meet-caption-recorder/spec.md) for the complete feature specification.

## Installation

> Note: Extension implementation is pending. Installation instructions will be updated once the extension is built.

1. Clone this repository
2. Open Chrome and navigate to `chrome://extensions/`
3. Enable "Developer mode"
4. Click "Load unpacked" and select the extension directory

## Usage

1. Join a Google Meet session
2. **Enable captions** in Google Meet (required - click the "CC" button in the meeting controls)
3. Click the extension icon and click "Start Recording"
4. The extension will automatically save/update the transcript file every 30 seconds
5. Click "Stop Recording" when done - a final transcript will be saved automatically
6. Find your transcript files in your Downloads folder

### Output Format

Each transcript is saved as a Markdown file with the following structure:

```markdown
# Meeting Title
**Date**: YYYY-MM-DD
**Duration**: HH:MM:SS

## Transcript

**Speaker Name**
- Caption line 1
- Caption line 2

**Another Speaker**
- Caption line 1
```

### Important Notes

- Captions **must be enabled** in Google Meet for the extension to work
- If you navigate away from the Meet page, recording stops automatically and saves what was captured
- If auto-save fails (e.g., permission issues), the extension will retry every 30 seconds while keeping your data safe in memory
- If captions are disabled mid-recording, the extension pauses and prompts you to re-enable them

## Development

This project uses [Spec-Kit](https://github.com/github/spec-kit/) for spec-driven development with Claude AI. Follow these steps to get started:

### Getting Started

#### 1. Clone the Repository

```bash
git clone https://github.com/parhumm/chrome-extention-google-meet-recoard-captions.git
cd chrome-extention-google-meet-recoard-captions
```

#### 2. Stay Updated

Before starting work, always pull the latest changes:

```bash
git pull origin main
```

#### 3. Install Claude Code

Claude Code is an AI coding assistant that works with Spec-Kit.

- Download from: https://claude.com/claude-code
- Follow the installation instructions for your operating system
- Open Claude Code in this project directory

#### 4. Install Spec-Kit (One-Time Setup)

Spec-Kit helps manage feature specifications and development workflow:

```bash
# Install spec-kit using uv
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git

# Verify installation
specify check
```

> Note: This project is already initialized with Spec-Kit. You don't need to run `specify init` again.

### Spec-Kit Workflow

#### Command Order (Follow These Steps)

Use these commands in order when building a new feature:

1. **Define Principles** → `/speckit.constitution`
2. **Write Feature Spec** → `/speckit.specify`
3. **Create Implementation Plan** → `/speckit.plan`
4. **Break Down Tasks** → `/speckit.tasks`
5. **Build the Feature** → `/speckit.implement`

#### Example Workflow

Let's say you want to add a "dark mode" feature:

```bash
# In Claude Code, run these commands in order:

# Step 1: Create the feature specification
/speckit.specify

# Claude will ask: "What feature would you like to specify?"
# You respond: "Add a dark mode toggle to the extension popup that saves the user's preference"

# Step 2: Clarify ambiguous areas (optional but recommended)
/speckit.clarify

# Step 3: Create implementation plan
/speckit.plan

# Step 4: Generate task breakdown
/speckit.tasks

# Step 5: Build the feature
/speckit.implement
```

#### Optional Helper Commands

| Command | When to Use | Purpose |
|---------|------------|---------|
| `/speckit.clarify` | After `/speckit.specify` | Ask questions to clarify unclear requirements |
| `/speckit.checklist` | After `/speckit.specify` | Validate specification quality |
| `/speckit.analyze` | After `/speckit.tasks` | Check consistency across spec, plan, and tasks |
| `/speckit.taskstoissues` | After `/speckit.tasks` | Create GitHub issues from tasks |

### Slash Commands Reference

After running Spec-Kit's `specify init`, Claude Code has access to these commands:

| Command | Description | When to Use |
|---------|-------------|-------------|
| `/speckit.constitution` | Create/update project principles | Start of project or when changing development philosophy |
| `/speckit.specify` | Create feature specification | Beginning of any new feature |
| `/speckit.clarify` | Ask clarifying questions about spec | When requirements are ambiguous |
| `/speckit.plan` | Create technical implementation plan | After specification is complete |
| `/speckit.tasks` | Generate actionable task list | After planning is complete |
| `/speckit.implement` | Execute all tasks | When ready to build |
| `/speckit.checklist` | Generate quality checklist | To validate spec quality |
| `/speckit.analyze` | Check cross-artifact consistency | Before implementation starts |
| `/speckit.taskstoissues` | Convert tasks to GitHub issues | For team collaboration |

### Committing Your Changes

When you've completed work:

```bash
# Check what changed
git status

# Add your changes
git add .

# Commit with a descriptive message
git commit -m "feat: add dark mode toggle to extension popup"

# Push to GitHub
git push origin your-branch-name
```

#### Commit Message Format

Use these prefixes for clarity:
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `refactor:` - Code refactoring
- `test:` - Adding tests
- `chore:` - Maintenance tasks

## License

TBD

## Author

parhumm
