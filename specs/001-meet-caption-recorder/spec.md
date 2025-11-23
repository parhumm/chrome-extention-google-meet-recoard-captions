# Feature Specification: Google Meet Caption Recorder

**Feature Branch**: `001-meet-caption-recorder`
**Created**: 2025-11-23
**Status**: Draft
**Input**: User description: "Define a Chrome extension for Google Meet that, while captions are enabled, captures each speaker's lines in order and, when stopped, downloads a Markdown file with meeting title, local date, duration, and transcript grouped by speaker. Everything must stay local (no cloud, no accounts). easy-to-easy, easy-to-implemnt. not complicated."

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Start Recording and Download Transcript (Priority: P1)

A user joins a Google Meet meeting with captions enabled and wants to capture the conversation for later reference. They start the recording, participate in the meeting, and when finished, download a formatted transcript as a Markdown file to their local computer.

**Why this priority**: This is the core value proposition - capturing and downloading meeting transcripts. Without this, the extension has no purpose.

**Independent Test**: Can be fully tested by joining a test Google Meet, enabling captions, starting the extension, speaking with at least one other person, stopping the recording, and verifying a Markdown file downloads with the correct meeting info and transcript.

**Acceptance Scenarios**:

1. **Given** a user is in a Google Meet session with captions enabled, **When** they click the extension's "Start Recording" button, **Then** the extension begins capturing caption text with speaker names in chronological order
2. **Given** the extension is actively recording captions, **When** the user clicks "Stop Recording", **Then** a Markdown file is automatically downloaded to their default download folder
3. **Given** a recording has been stopped, **When** the user opens the downloaded Markdown file, **Then** they see the meeting title, date, duration, and transcript organized by speaker with timestamps

---

### User Story 2 - Visual Recording Status Indicator (Priority: P2)

A user wants to know at a glance whether the caption recording is active or not, so they don't accidentally miss capturing important parts of the meeting or waste time recording when they don't need to.

**Why this priority**: Provides essential user feedback and prevents user errors, but the core functionality (P1) must work first.

**Independent Test**: Can be tested by starting/stopping the recording and observing the visual indicator changes state appropriately without needing to wait for the download.

**Acceptance Scenarios**:

1. **Given** the user has not started recording, **When** they view the extension icon or popup, **Then** they see a clear "Ready to Record" or inactive state indicator
2. **Given** recording is active, **When** the user views the extension, **Then** they see a visual indicator (e.g., red dot, "Recording" text, or active state) showing recording in progress
3. **Given** recording has stopped, **When** the download begins, **Then** the indicator returns to inactive state

---

### User Story 3 - Handle Meeting Without Captions (Priority: P3)

A user tries to start recording but captions are not enabled in the Google Meet session. The extension should provide clear guidance on what to do.

**Why this priority**: Important for user experience but not core functionality. Users can manually enable captions before starting.

**Independent Test**: Can be tested by attempting to record in a meeting without captions enabled and verifying appropriate user guidance is shown.

**Acceptance Scenarios**:

1. **Given** a user is in a Google Meet without captions enabled, **When** they attempt to start recording, **Then** they see a message instructing them to enable captions first
2. **Given** captions are enabled after the initial warning, **When** the user clicks "Start Recording" again, **Then** recording begins normally

---

### Edge Cases

- What happens when the user leaves the Google Meet page while recording is active?
- How does the system handle extremely long meetings (e.g., 4+ hours)?
- What happens if captions are disabled mid-recording?
- How does the extension behave if multiple Google Meet tabs are open?
- What happens if the speaker name is not detected (shows as "Unknown" in captions)?
- How does the system handle special characters or emojis in captions?
- What happens if the user closes the browser tab during recording?

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: System MUST capture caption text in real-time as it appears in Google Meet's caption display
- **FR-002**: System MUST record the speaker name associated with each caption line
- **FR-003**: System MUST maintain chronological order of all captured captions
- **FR-004**: System MUST track recording start time and end time to calculate total duration
- **FR-005**: System MUST extract or allow user to specify meeting title
- **FR-006**: System MUST generate a Markdown file containing meeting metadata (title, date, duration) and full transcript
- **FR-007**: System MUST group consecutive captions from the same speaker together in the transcript output
- **FR-008**: System MUST automatically trigger file download when user stops recording
- **FR-009**: System MUST store all data locally in browser memory (no external services, databases, or cloud storage)
- **FR-010**: System MUST provide start and stop recording controls accessible from the extension UI
- **FR-011**: System MUST indicate current recording status to the user
- **FR-012**: System MUST work only when Google Meet captions are enabled
- **FR-013**: System MUST clear recording data after successful download to avoid memory buildup

### Key Entities

- **Caption Entry**: Represents a single caption line with speaker name, text content, and timestamp
- **Recording Session**: Represents one complete recording with start time, end time, meeting title, and collection of caption entries
- **Transcript Output**: Represents the formatted Markdown document with metadata header and speaker-grouped transcript

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Users can start recording captions within 2 clicks from opening the extension
- **SC-002**: Transcript file downloads automatically within 2 seconds of clicking "Stop Recording"
- **SC-003**: Captured captions maintain 100% chronological accuracy compared to Google Meet's caption display order
- **SC-004**: Downloaded Markdown file is properly formatted and readable in any Markdown viewer without errors
- **SC-005**: Extension operates without requiring any user authentication, account creation, or internet connectivity beyond the Google Meet session itself
- **SC-006**: Users can successfully capture and download transcripts from meetings lasting up to 2 hours without performance degradation
