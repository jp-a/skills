# Metadata and Structure Reference

This document provides detailed specifications for organizing YouTube channel captures in the Obsidian vault.

## Directory Structure

```
Library/KM/1. Capture/YouTube/
├── channels.md                           # Master registry of tracked channels
└── Channels/
    └── @ChannelHandle/
        ├── index.md                      # Channel-specific tracking file
        └── YYYY-MM-DD - Video Title.md   # Individual video captures
```

## Master Channel Registry

**Location:** `Library/KM/1. Capture/YouTube/channels.md`

**Purpose:** Central registry of all tracked YouTube channels for systematic knowledge capture.

**Structure:**
- Table format with columns: Channel Handle, Channel Name, Focus Area, Status, Last Checked, Videos Processed
- Sorted by channel handle alphabetically
- Links to individual channel directories

## Channel Index File

**Location:** `Library/KM/1. Capture/YouTube/Channels/@ChannelHandle/index.md`

**Purpose:** Track all videos processed from a specific channel with chronological order.

**Structure:**
- Channel metadata (name, URL, author handle, focus area)
- Statistics (total videos processed, last checked date)
- Chronological table of processed videos with: Date Published, Video Title, Processing Date, Status

## Video Note Metadata

Each video note must include the following metadata fields:

### Required Fields

- **video_url**: Full YouTube URL to the video
- **channel_handle**: Channel handle (e.g., @NateBJones)
- **channel_name**: Full channel name
- **video_title**: Full title of the video
- **publish_date**: Date the video was published (YYYY-MM-DD format)
- **extraction_date**: Date the transcript was extracted (YYYY-MM-DD format)
- **duration**: Video duration (if available)
- **status**: Processing status (captured, reviewed, curated, synthesized)

### Metadata Format

Use YAML frontmatter at the top of each video note:

```yaml
---
video_url: https://www.youtube.com/watch?v=VIDEO_ID
channel_handle: @ChannelHandle
channel_name: Channel Name
video_title: Video Title
publish_date: YYYY-MM-DD
extraction_date: YYYY-MM-DD
duration: HH:MM:SS
status: captured
---
```

## Content Structure for Video Notes

### 1. Video Overview
Brief 2-3 sentence summary of the video's purpose and content.

### 2. Key Themes
Identify 3-5 main themes or topics covered in the video:
- Theme 1
- Theme 2
- Theme 3

### 3. Main Takeaways
List the most important insights, lessons, or information from the video:
1. First major takeaway with brief explanation
2. Second major takeaway with brief explanation
3. Continue as needed

### 4. Notable Quotes & Examples
Capture direct quotes or specific examples that illustrate key points:
- "Quote from the video" - Context or explanation
- Example: Specific case study or scenario mentioned

### 5. Links & References
Any resources, websites, or materials mentioned in the video.

## File Naming Conventions

### Video Notes
Format: `YYYY-MM-DD - Video Title.md`
- Use publish date, not extraction date
- Sanitize video title (remove special characters: / \ : * ? " < > |)
- Limit filename to reasonable length (truncate long titles)

### Channel Directories
Format: `@ChannelHandle`
- Use exact channel handle with @ prefix
- Preserve capitalization as used by the channel

## Processing Status Values

- **captured**: Transcript extracted, structured content created
- **reviewed**: User has reviewed the captured content
- **curated**: Content has been curated (future skill)
- **synthesized**: Content has been synthesized with other knowledge (future skill)
