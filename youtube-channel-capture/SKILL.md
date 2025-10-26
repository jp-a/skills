---
name: youtube-channel-capture
description: Systematically capture and structure YouTube video content from tracked channels using transcript extraction. Use this skill when the user requests processing YouTube videos (specific URLs or latest from a channel), checking what videos have been captured, or managing their YouTube channel registry. Stores organized notes in Obsidian vault under Library/KM/1. Capture/YouTube/ with channel tracking and metadata.
---

# YouTube Channel Capture

## Overview

This skill enables systematic capture and organization of YouTube video content for knowledge management. Extract transcripts from videos, structure key insights and takeaways, and maintain organized tracking of processed videos across multiple YouTube channels. The skill focuses solely on the capture phase—curation and synthesis are handled by separate skills.

## When to Use This Skill

Use this skill when the user:
- Provides a YouTube video URL to process and capture
- Asks to check latest videos from a tracked channel
- Requests to see which videos have been processed from a channel
- Wants to add a new channel to their tracking registry
- Asks about their YouTube knowledge capture system

**Do NOT use this skill for:**
- Video curation or content synthesis (separate skills)
- Playing or downloading videos
- Commenting on or interacting with YouTube

## Prerequisites

**Required MCP Tools:**
- `mcp__MCP_DOCKER__get_transcript` - Extract video transcripts
- `mcp__MCP_DOCKER__get_video_info` - Retrieve video metadata

**Required Obsidian MCP Tools:**
- `mcp__MCP_DOCKER__obsidian_get_file_contents` - Read existing files
- `mcp__MCP_DOCKER__obsidian_append_content` - Create/append to files
- Alternatively, use standard Read/Write tools if Obsidian MCP unavailable

**Base Directory:**
All content must be stored in: `Library/KM/1. Capture/YouTube/`

## Workflow Decision Tree

When the skill is triggered, determine the appropriate workflow:

1. **User provides a specific video URL** → Workflow: Process Single Video
2. **User asks for latest videos from a channel** → Workflow: Check Latest Videos
3. **User asks what's been captured** → Workflow: Review Tracking
4. **User wants to add a new channel** → Workflow: Initialize New Channel

## Workflow: Process Single Video

Use this workflow when the user provides a specific YouTube video URL.

### Step 1: Extract Video Information

Use `mcp__MCP_DOCKER__get_video_info` to retrieve:
- Video title
- Channel name and handle
- Publish date
- Duration

### Step 2: Check if Already Processed

1. Check if channel directory exists: `Library/KM/1. Capture/YouTube/Channels/@{ChannelHandle}/`
2. If channel directory exists, read the `index.md` file
3. Check if the video URL is already in the processed videos table
4. If already processed, inform the user and ask if they want to re-process

### Step 3: Extract Transcript

Use `mcp__MCP_DOCKER__get_transcript` to get the full video transcript.

**Handling Long Transcripts:**
- If the transcript is very long (>50k characters), use `next_cursor` to paginate
- Combine all pages into a complete transcript before analysis

### Step 4: Analyze and Structure Content

Analyze the transcript to create structured content:

1. **Video Overview** (2-3 sentences)
   - Summarize the video's main purpose and focus
   - Keep it concise but informative

2. **Key Themes** (3-5 themes)
   - Identify the main topics or themes covered
   - Format as bullet list with brief descriptions

3. **Main Takeaways** (numbered list)
   - Extract the most important insights, lessons, or information
   - Provide detailed explanations for each takeaway
   - Aim for 3-7 takeaways depending on content richness

4. **Notable Quotes & Examples**
   - Pull direct quotes that illustrate key points
   - Include specific examples, case studies, or scenarios mentioned
   - Provide context for why each quote/example is significant

5. **Links & References**
   - Extract any resources, websites, or materials mentioned
   - Format as markdown links with brief descriptions

### Step 5: Create Video Note File

**File Location:** `Library/KM/1. Capture/YouTube/Channels/@{ChannelHandle}/YYYY-MM-DD - Video Title.md`

**Filename Rules:**
- Use publish date (YYYY-MM-DD format), not extraction date
- Sanitize video title by removing special characters: / \ : * ? " < > |
- Truncate very long titles to keep filename reasonable (<100 characters)

**File Content:**
Use the template from `assets/video_note_template.md` and populate all fields:
- YAML frontmatter with complete metadata
- All structured content sections from Step 4
- Ensure all placeholders ({VIDEO_URL}, {CHANNEL_HANDLE}, etc.) are replaced

### Step 6: Update Channel Index

**File Location:** `Library/KM/1. Capture/YouTube/Channels/@{ChannelHandle}/index.md`

1. If the file doesn't exist, create it using `assets/channel_index_template.md`
2. Add a new row to the "Processed Videos" table:
   - Publish Date: YYYY-MM-DD
   - Video Title: Link to the video note file
   - Processing Date: Today's date
   - Status: captured
3. Update statistics:
   - Increment total videos processed count
   - Update last checked date
4. Sort table in reverse chronological order (newest first)

### Step 7: Update Master Channel Registry

**File Location:** `Library/KM/1. Capture/YouTube/channels.md`

1. If the file doesn't exist, create it using `assets/channel_registry_template.md`
2. If the channel is not in the registry, add a new row
3. Update the channel's row:
   - Increment videos processed count
   - Update last checked date
   - Ensure status is "Active"

### Step 8: Confirm Completion

Inform the user:
- Video title and channel processed
- File location where the note was saved
- Link to view the note in Obsidian (if applicable)
- Brief summary of what was captured (number of takeaways, themes identified)

## Workflow: Check Latest Videos

Use this workflow when the user asks to check latest videos from a tracked channel.

### Step 1: Verify Channel in Registry

1. Read `Library/KM/1. Capture/YouTube/channels.md`
2. Confirm the requested channel exists in the registry
3. If not found, ask user if they want to add it

### Step 2: Get Channel's Latest Videos

**Note:** The MCP tools provided (`get_video_info`, `get_transcript`) work on individual videos, not channel listings. Therefore:

1. Inform the user that you need video URLs to process
2. Ask the user to provide:
   - Specific video URLs from the channel they want to process, OR
   - Visit the channel page and share recent video URLs

**Alternative Approach:**
If the user has been manually tracking videos, check the channel's `index.md` to see what's already been processed and ask which new videos to add.

### Step 3: Process Each New Video

For each video URL provided:
1. Check if already in the channel index
2. If new, follow "Workflow: Process Single Video" (Steps 1-7)
3. Process videos sequentially, not in parallel, to avoid overwhelming the transcript service

### Step 4: Summary Report

After processing all videos, provide a summary:
- Number of new videos processed
- Number of videos already in the system
- Updated statistics from the channel index

## Workflow: Review Tracking

Use this workflow when the user wants to see what's been captured.

### Step 1: Determine Scope

Ask the user what they want to review:
- All channels (master registry)
- Specific channel (channel index)
- Recent captures across all channels

### Step 2: Read Relevant Files

**For All Channels:**
- Read `Library/KM/1. Capture/YouTube/channels.md`
- Present the table showing all tracked channels and statistics

**For Specific Channel:**
- Read `Library/KM/1. Capture/YouTube/Channels/@{ChannelHandle}/index.md`
- Present the processed videos table with links

**For Recent Captures:**
- Use `mcp__MCP_DOCKER__obsidian_get_recent_changes` with path filter for YouTube directory
- Show recently modified video notes

### Step 3: Present Information

Format the information clearly:
- Use tables for structured data
- Include relevant statistics
- Provide file links for easy navigation
- Highlight any gaps or channels that haven't been checked recently

## Workflow: Initialize New Channel

Use this workflow when adding a new channel to the tracking system.

### Step 1: Gather Channel Information

Ask the user for:
- Channel handle (e.g., @NateBJones)
- Channel name (e.g., "AI News & Strategy Daily | Nate B Jones")
- Focus area (e.g., "AI News & Strategy", "Technology", "Leadership")

Alternatively, if the user provides a video URL from a new channel, extract this information from the video metadata.

### Step 2: Create Channel Directory

Create directory: `Library/KM/1. Capture/YouTube/Channels/@{ChannelHandle}/`

### Step 3: Create Channel Index

Create `index.md` using the template from `assets/channel_index_template.md`:
- Populate all channel metadata fields
- Set initial statistics (0 videos processed)
- Create empty processed videos table

### Step 4: Add to Master Registry

Update `Library/KM/1. Capture/YouTube/channels.md`:
- Add new row for the channel
- Status: "Active"
- Videos Processed: 0
- Last Checked: Today's date

### Step 5: Confirm and Next Steps

Inform the user:
- Channel successfully added to tracking system
- Directory structure created
- Ask if they want to process any videos from this channel now

## File Organization Reference

All files follow the structure defined in `references/metadata_and_structure.md`. Key points:

**Directory Hierarchy:**
```
Library/KM/1. Capture/YouTube/
├── channels.md                           # Master registry
└── Channels/
    └── @ChannelHandle/
        ├── index.md                      # Channel tracking
        └── YYYY-MM-DD - Video Title.md   # Video notes
```

**Templates Available:**
- `assets/channel_registry_template.md` - Master registry format
- `assets/channel_index_template.md` - Channel tracking format
- `assets/video_note_template.md` - Individual video note format

**Metadata Standards:**
- All dates in YYYY-MM-DD format
- Video status: captured, reviewed, curated, synthesized
- Channel status: Active, Paused, Inactive
- Always include complete YAML frontmatter in video notes

## Best Practices

1. **Always check before processing** - Avoid duplicate captures by checking the channel index first

2. **Maintain consistent metadata** - Use exact formats specified in `references/metadata_and_structure.md`

3. **Handle errors gracefully** - If transcript extraction fails, inform the user and skip to next video

4. **Preserve chronological order** - Always sort processed videos by publish date (newest first)

5. **Be thorough in analysis** - Don't rush the content structuring; quality over speed

6. **Update all tracking files** - Every video capture should update: video note, channel index, AND master registry

7. **Use templates consistently** - Always base new files on the provided templates to maintain structure

## Resources

### references/
- `metadata_and_structure.md` - Detailed specifications for all file formats, metadata fields, and content structure

### assets/
- `channel_registry_template.md` - Template for the master channel registry
- `channel_index_template.md` - Template for individual channel tracking files
- `video_note_template.md` - Template for individual video capture notes

### scripts/
No scripts required for this skill. All operations use MCP tools or standard file operations.
