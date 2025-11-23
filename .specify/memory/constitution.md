<!--
================================================================================
SYNC IMPACT REPORT - Constitution v1.0.0
================================================================================

VERSION CHANGE:
  - Previous: NONE (initial creation)
  - Current: 1.0.0
  - Bump Type: INITIAL RATIFICATION
  - Rationale: First version of project constitution establishing core principles
    for Chrome Extension - Google Meet Caption Recording project

PRINCIPLES ADDED (5 total):
  1. I. Local-First & Privacy-Focused
     - Mandates all data stays local, no cloud services, no accounts
     - Ensures user privacy and data ownership

  2. II. Meeting-Focused Capture
     - Defines caption capture requirements from Google Meet CC
     - Specifies speaker attribution and chronological ordering

  3. III. Automatic & User-Friendly Output
     - Requires automatic Markdown download on stop
     - Defines required metadata (title, date, duration, transcript)

  4. IV. Minimal & Reliable
     - Enforces simplicity and single responsibility
     - Prioritizes reliability for real workshop use cases

  5. V. Chrome Extension Standards
     - Mandates Manifest V3 compliance
     - Requires minimal permissions and Chrome Web Store policy adherence

SECTIONS ADDED:
  - Technical Constraints: Manifest V3, permissions, storage, DOM observation,
    dependencies, file generation requirements
  - User Experience Requirements: Zero configuration, visual feedback, instant
    download, readable format, error handling
  - Governance: Amendment process, versioning policy, compliance requirements

MODIFIED PRINCIPLES: N/A (initial creation)
REMOVED SECTIONS: N/A (initial creation)

TEMPLATE CONSISTENCY VALIDATION:
  ✅ plan-template.md - Constitution Check gate verified (line 30-34)
     - Gate placeholder aligns with constitution-driven validation
     - Complexity Tracking section supports violation justification (line 99-105)

  ✅ spec-template.md - No constitution references required
     - Technology-agnostic requirements focus maintained
     - User story prioritization compatible with principle validation

  ✅ tasks-template.md - No constitution references required
     - User story organization supports independent testing per principles
     - Phase structure compatible with constitution validation gates

  ✅ agent-file-template.md - No updates required
     - Template designed for technology extraction, not governance

  ✅ checklist-template.md - No updates required
     - Quality validation framework is constitution-agnostic

PLACEHOLDERS REMAINING: NONE
  - All 17 placeholders filled with concrete values
  - No deferred fields or TODO items

FOLLOW-UP TASKS:
  - None required
  - Constitution ready for use in /speckit.specify workflow
  - Next step: Create feature specifications using /speckit.specify

GOVERNANCE METADATA:
  - Version: 1.0.0
  - Ratified: 2025-11-23
  - Last Amended: 2025-11-23
  - Amendment Process: Defined in Governance section
  - Versioning: Semantic versioning (MAJOR.MINOR.PATCH)

COMMIT RECOMMENDATION:
  docs: ratify constitution v1.0.0 (initial principles for Google Meet caption recording)

================================================================================
-->

# Chrome Extension - Google Meet Caption Recording Constitution

## Core Principles

### I. Local-First & Privacy-Focused

All captured data MUST remain on the user's local machine. The extension MUST NOT:

- Send data to cloud services or external servers
- Require user accounts or authentication
- Include tracking, analytics, or telemetry of any kind

Users maintain complete control and ownership of their meeting transcripts. Privacy is non-negotiable.

**Rationale**: Workshop users need assurance that sensitive meeting content stays private and under their control.

### II. Meeting-Focused Capture

The extension MUST capture live captions from Google Meet when closed captions (CC) are enabled. Capture requirements:

- Listen to on-screen caption elements in the DOM
- Extract speaker names and their dialogue in chronological order
- Track meeting duration from recording start to stop
- Operate ONLY during active recording (no background processing)

**Rationale**: Accurate, speaker-attributed transcripts require precise capture of Google Meet's caption rendering.

### III. Automatic & User-Friendly Output

Upon stopping recording, the extension MUST automatically download a formatted Markdown file containing:

- Meeting name/title
- Local date and time
- Total duration (start to stop time)
- Complete transcript grouped by speaker (e.g., "Parhum: Hello Everyone / Shirin: Hi Parhum / Hojjat: Heloooo")

No manual export steps or configuration dialogs are allowed.

**Rationale**: Workshop participants need instant, readable transcripts without friction or technical barriers.

### IV. Minimal & Reliable

The extension MUST prioritize simplicity and reliability:

- Single responsibility: capture and export captions only
- No feature creep or "nice-to-have" additions
- Designed for real-world workshop use cases
- Favor proven, simple solutions over complex architectures

**Rationale**: Real workshop scenarios demand tools that work consistently without complexity or failure modes.

### V. Chrome Extension Standards

The extension MUST adhere to Chrome Web Store and Manifest V3 requirements:

- Follow Manifest V3 specification
- Request minimal permissions (only Google Meet page access)
- Avoid external dependencies where possible
- Comply with Chrome Web Store policies and guidelines

**Rationale**: Ensures long-term viability, security, and distribution through official channels.

## Technical Constraints

The following technical constraints are binding:

- **Manifest Version**: Must use Manifest V3 (current Chrome extension standard)
- **Permissions**: Content scripts limited to Google Meet domains (`meet.google.com`)
- **Storage**: Use Chrome's local storage APIs (no IndexedDB unless required for scale)
- **DOM Observation**: Use MutationObserver for caption element detection
- **Dependencies**: Zero external API calls; minimize npm packages
- **File Generation**: Use Blob and download APIs for Markdown export

## User Experience Requirements

The following UX requirements are non-negotiable:

- **Zero Configuration**: Extension works immediately after installation
- **Visual Feedback**: Clear recording status indicator in Meet interface
- **Instant Download**: Transcript downloads automatically when recording stops
- **Readable Format**: Markdown output must be human-readable without processing
- **Error Handling**: Graceful degradation if captions unavailable or Meet UI changes

## Governance

This constitution supersedes all feature requests, architectural preferences, and implementation shortcuts.

**Amendment Process**:

- Proposed changes must document impact on existing features
- Require validation against current specifications and plans
- Version bump according to semantic versioning rules

**Versioning Policy**:

- MAJOR: Backward-incompatible changes to core principles
- MINOR: New principles added or existing principles expanded
- PATCH: Clarifications, wording fixes, non-semantic refinements

**Compliance**:

- All features MUST pass Constitution Check during planning phase
- Pull requests MUST reference relevant principles
- Testing MUST validate principle adherence (e.g., verify no network calls for Principle I)

**Version**: 1.0.0 | **Ratified**: 2025-11-23 | **Last Amended**: 2025-11-23