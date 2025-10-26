# Content Curator Skill

## Purpose

Systematically curates captured knowledge from `Library/KM/1. Capture` into organized, refined insights in `Library/KM/2. Curation`. This skill implements the second step of a three-part knowledge management process:

1. **Capture** - Gather raw information from various sources
2. **Curate** ← This skill - Organize and refine into reliable, usable knowledge
3. **Synthesis** - Create knowledge products and insights

## What This Skill Does

### Core Capabilities

- **Tracks Processing Status:** Maintains a registry of what's been curated and what's pending
- **Identifies Themes:** Recognizes patterns and topics across captured content
- **Organizes by Topic:** Creates coherent topic areas with principles, examples, and frameworks
- **Assesses Quality:** Evaluates content for depth, novelty, reliability, actionability, and coherence
- **Cross-References:** Connects related insights across different topics and sources
- **Maintains Traceability:** Always links curated insights back to source material

### Output Structure

Creates organized knowledge in `Library/KM/2. Curation/`:

```
2. Curation/
├── curation-registry.md              # Master tracking file
├── Topics/                           # Organized by theme
│   ├── {TopicName}/
│   │   ├── _index.md                # Topic overview
│   │   ├── Principles.md            # Core concepts and frameworks
│   │   └── Examples.md              # Real-world cases and anti-patterns
├── Sources/                          # Per-source curation notes
│   └── {SourceType}/{SourceName}/
│       └── curation-notes.md
└── Cross-References/                 # Connection maps
    └── theme-connections.md
```

## When to Use This Skill

✅ **Use when:**
- You want to curate new captured content
- You ask to organize or refine captured knowledge
- You request to identify themes or patterns
- You want to see what's new in Capture directory
- You ask about curated insights
- You need to cross-reference related content

❌ **Don't use when:**
- Initially capturing content (use capture skills)
- Creating final synthesis or knowledge products
- Just reading raw captured content

## Key Features

### 1. Incremental Processing

- **Only processes new content:** Tracks what's been curated via registry
- **No redundant work:** Skips already-curated items automatically
- **Efficient updates:** Add new captures without reprocessing everything

### 2. Quality Assessment

Evaluates content across five dimensions:
- **Depth:** Surface-level vs. deep analysis
- **Novelty:** Repeats known info vs. new perspectives
- **Reliability:** Sourced claims vs. opinions
- **Actionability:** Theoretical vs. practical guidance
- **Coherence:** Clear and consistent vs. contradictory

### 3. Systematic Organization

- **Topic-based structure:** Groups by theme, not source
- **Multiple perspectives:** Principles, examples, anti-patterns
- **Cross-referencing:** Connects related insights
- **Traceable:** Always links back to original source

### 4. Flexible Taxonomy

- **Evolves with content:** Create topics as themes emerge
- **Merge/split support:** Adapt organization as needed
- **Flat structure:** Easy navigation, simple cross-referencing
- **Clear guidelines:** Documented standards for consistency

## Quick Start

### First Time Use

1. **Claude will initialize the curation system:**
   - Creates `curation-registry.md`
   - Scans Capture directory
   - Reports what's available to curate

2. **Run first curation:**
   ```
   "Curate all new captured content"
   ```

3. **Review results:**
   ```
   "Show me curation status"
   ```

### Ongoing Use

**Curate new content:**
```
"Curate new captures"
"Curate content about [specific topic]"
```

**Check status:**
```
"What's been curated?"
"Show pending curation items"
"What topics do we have?"
```

**Explore curated knowledge:**
```
"Show me insights about [topic]"
"What are the cross-references between [topic A] and [topic B]?"
"What patterns have emerged?"
```

## Files and Templates

### Core Files

- **skill.md** - Complete workflow instructions for Claude
- **README.md** - This file (user documentation)

### Templates (assets/)

- `curation-registry-template.md` - Master tracking file
- `topic-index-template.md` - Topic overview structure
- `topic-principles-template.md` - Principles and frameworks
- `topic-examples-template.md` - Examples and case studies
- `source-curation-notes-template.md` - Per-source tracking
- `cross-references-template.md` - Connection mapping

### Reference Docs (references/)

- `curation-quality-standards.md` - Quality assessment criteria
- `topic-taxonomy.md` - Organization guidelines

## Workflow Overview

### Standard Curation Flow

1. **Scan for New Content**
   - Check curation registry
   - Compare with Capture directory
   - Identify uncurated items

2. **Analyze Content**
   - Read full captured content
   - Extract key themes and insights
   - Assess quality across 5 dimensions
   - Identify cross-reference opportunities

3. **Organize by Topic**
   - Match to existing topics or create new
   - Extract principles and frameworks
   - Document examples and anti-patterns
   - Create/update topic files

4. **Cross-Reference**
   - Connect related topics
   - Identify emerging patterns
   - Note contradictions or tensions
   - Update connection map

5. **Track and Update**
   - Update curation registry
   - Create source curation notes
   - Update statistics
   - Report completion

## Quality Standards

### Content Tiers

**Tier 1 - Premium:** Deep extraction, featured in overviews
- High on 3+ quality dimensions
- Forms foundation for frameworks

**Tier 2 - Quality:** Standard curation
- High on 1-2 dimensions
- Extracts key insights with caveats

**Tier 3 - Supplementary:** Light curation
- Medium on most dimensions
- Unique contributions only

**Tier 4 - Low Value:** Minimal or skip
- Low on 3+ dimensions
- Only if fills specific gap

### Curation Principles

1. **Depth Over Breadth:** Extract meaningful insights, not summaries
2. **Deduplication:** Cross-reference instead of copying
3. **Traceability:** Always link back to source
4. **Coherence:** Logical organization and clear structure
5. **Efficiency:** Batch processing and template reuse

## Topic Management

### Creating Topics

**When to create:**
- 2-3 sources address same domain/problem
- Distinct from existing topics
- Likely to grow over time
- Clear, definable scope

**Naming conventions:**
- Use kebab-case: `AI-Writing`, `Claude-Skills`
- Be specific but not too narrow
- Use problem/domain language (not technology)

### Growing Topics

- **5+ sources:** Refine organization, strengthen cross-refs
- **10+ sources:** Consider sub-topics or splitting
- **15+ sources:** Likely needs splitting

### Merging/Splitting

- **Merge when:** Heavy overlap, hard to distinguish
- **Split when:** Too broad, clear sub-themes emerge

## Integration with Capture

Works with any Capture skill that:
- Stores content in `Library/KM/1. Capture/`
- Uses markdown files with frontmatter
- Includes structured sections (Overview, Key Themes, Main Takeaways, etc.)

Currently tested with:
- `youtube-channel-capture` skill

## Next Steps After Curation

Curated content serves as input for:
- **Synthesis (Step 3):** Creating knowledge products, insights reports, frameworks
- **Reference:** Quick lookup of organized insights
- **Learning:** Structured exploration of domains
- **Decision-making:** Evidence-based frameworks and principles

## Troubleshooting

**Registry doesn't exist:**
- Claude will create it automatically on first run

**Topics feel disorganized:**
- Review `topic-taxonomy.md` guidelines
- Consider merging overlapping topics
- May need to split broad topics

**Quality is inconsistent:**
- Review `curation-quality-standards.md`
- May need to recurate low-quality items
- Consider source-level quality assessment

**Cross-references are missing:**
- Run thematic curation to deepen connections
- Review cross-reference file for gaps
- Explicitly ask for pattern identification

## Maintenance

### Regular Activities

**After each capture session:**
```
"Curate new content"
```

**Weekly/monthly:**
```
"Show curation status"
"What patterns are emerging?"
```

**Quarterly:**
```
"Review topic organization"
"Identify merge or split candidates"
"Update cross-references"
```

## Version

- **Created:** 2025-10-26
- **Version:** 1.0
- **Compatible with:** Claude Code, Claude.ai (with file upload)

## Credits

Created for systematic knowledge management following Capture → Curate → Synthesize workflow.
