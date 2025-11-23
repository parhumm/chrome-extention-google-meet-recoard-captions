# Feature Specification: Google Meet Caption Recorder

**Feature Branch**: `001-meet-caption-recorder`
**Created**: 2025-11-23
**Status**: Draft
**Input**: User description: "Define a Chrome extension for Google Meet that, while captions are enabled, captures each speaker's lines in order and, when stopped, downloads a Markdown file with meeting title, local date, duration, and transcript grouped by speaker. Everything must stay local (no cloud, no accounts). easy-to-easy, easy-to-implemnt. not complicated."

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Start Recording and Auto-Save Transcript (Priority: P1)

A user joins a Google Meet meeting with captions enabled and wants to capture the conversation for later reference. They start the recording, and the extension automatically downloads or updates the transcript file every 30 seconds during the meeting. The user can stop recording at any time, and the final transcript is saved.

**Why this priority**: This is the core value proposition - capturing and continuously saving meeting transcripts. Without this, the extension has no purpose. Auto-save ensures no data loss if the browser crashes or meeting disconnects.

**Independent Test**: Can be fully tested by joining a test Google Meet, enabling captions, starting the extension, speaking with at least one other person, waiting at least 30 seconds to verify automatic download, and confirming the file updates with new captions.

**Acceptance Scenarios**:

1. **Given** a user is in a Google Meet session with captions enabled, **When** they click the extension's "Start Recording" button, **Then** the extension begins capturing caption text with speaker names in chronological order
2. **Given** the extension is actively recording captions, **When** 30 seconds elapse since the last save, **Then** a Markdown file is automatically downloaded or updated with the current transcript
3. **Given** the transcript file has been auto-saved at least once, **When** new captions are captured and another 30 seconds pass, **Then** the same file is updated with the complete transcript including new content
4. **Given** recording is active, **When** the user clicks "Stop Recording", **Then** a final transcript file is saved with all captured content
5. **Given** a recording has been saved, **When** the user opens the downloaded Markdown file, **Then** they see the meeting title, date, duration, and transcript organized by speaker with timestamps

---

### User Story 2 - Visual Recording Status Indicator (Priority: P2)

A user wants to know at a glance whether the caption recording is active or not, and when auto-saves are occurring, so they don't accidentally miss capturing important parts of the meeting or waste time recording when they don't need to.

**Why this priority**: Provides essential user feedback and prevents user errors, but the core functionality (P1) must work first.

**Independent Test**: Can be tested by starting/stopping the recording and observing the visual indicator changes state appropriately, including brief feedback during auto-save events.

**Acceptance Scenarios**:

1. **Given** the user has not started recording, **When** they view the extension icon or popup, **Then** they see a clear "Ready to Record" or inactive state indicator
2. **Given** recording is active, **When** the user views the extension, **Then** they see a visual indicator (e.g., red dot, "Recording" text, or active state) showing recording in progress
3. **Given** recording is active and an auto-save occurs, **When** the file is being saved, **Then** the user sees brief feedback (e.g., "Saving..." or save icon) that disappears after save completes
4. **Given** recording has stopped, **When** the final download completes, **Then** the indicator returns to inactive state

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
- What happens if the user stops recording before the first 30-second auto-save occurs?
- How does the system handle file download failures or permission issues during auto-save?
- What happens if new captions arrive during the auto-save process?

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: System MUST capture caption text in real-time as it appears in Google Meet's caption display
- **FR-002**: System MUST record the speaker name associated with each caption line
- **FR-003**: System MUST maintain chronological order of all captured captions
- **FR-004**: System MUST track recording start time and end time to calculate total duration
- **FR-005**: System MUST extract or allow user to specify meeting title
- **FR-006**: System MUST generate a Markdown file containing meeting metadata (title, date, duration) and full transcript
- **FR-007**: System MUST group consecutive captions from the same speaker together in the transcript output
- **FR-008**: System MUST automatically download or update the transcript file every 30 seconds while recording is active
- **FR-009**: System MUST automatically trigger a final transcript file download when user stops recording
- **FR-010**: System MUST store all data locally in browser memory (no external services, databases, or cloud storage)
- **FR-011**: System MUST provide start and stop recording controls accessible from the extension UI
- **FR-012**: System MUST indicate current recording status to the user
- **FR-013**: System MUST work only when Google Meet captions are enabled
- **FR-014**: System MUST use consistent filename for auto-save updates to avoid creating multiple files for the same meeting
- **FR-015**: System MUST clear recording data after user stops recording and final transcript is saved to avoid memory buildup

### Key Entities

- **Caption Entry**: Represents a single caption line with speaker name, text content, and timestamp
- **Recording Session**: Represents one complete recording with start time, end time, meeting title, and collection of caption entries
- **Transcript Output**: Represents the formatted Markdown document with metadata header and speaker-grouped transcript

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Users can start recording captions within 2 clicks from opening the extension
- **SC-002**: Transcript file is automatically saved or updated every 30 seconds (±5 seconds) during active recording
- **SC-003**: Final transcript file downloads automatically within 2 seconds of clicking "Stop Recording"
- **SC-004**: Captured captions maintain 100% chronological accuracy compared to Google Meet's caption display order
- **SC-005**: Downloaded Markdown file is properly formatted and readable in any Markdown viewer without errors
- **SC-006**: Extension operates without requiring any user authentication, account creation, or internet connectivity beyond the Google Meet session itself
- **SC-007**: Users can successfully capture and download transcripts from meetings lasting up to 2 hours without performance degradation
- **SC-008**: Auto-save updates use the same filename, preventing duplicate files for a single meeting
