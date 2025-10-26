# Content Curator

## Overview

This skill systematically curates captured knowledge from `Library/KM/1. Capture` into organized, refined insights in `Library/KM/2. Curation`. It tracks what's been processed, identifies themes and patterns, cross-references related content, and assesses quality to transform raw captures into reliable, usable knowledge assets.

## When to Use This Skill

Use this skill when the user:
- Wants to curate new captured content
- Asks to organize or refine captured knowledge
- Requests to identify themes or patterns across captures
- Wants to see what's new in the Capture directory
- Asks about curated insights or knowledge organization
- Needs to cross-reference related content

**Do NOT use this skill for:**
- Initial capture of content (use youtube-channel-capture or other capture skills)
- Final synthesis or knowledge products (that's step 3)
- Reading or searching uncurated content directly

## Prerequisites

**Required Directory Structure:**
- `Library/KM/1. Capture/` - Source content (already captured)
- `Library/KM/2. Curation/` - Destination for curated content
- Standard Read/Write/Edit tools

**Base Directories:**
- Capture: `Library/KM/1. Capture/`
- Curation: `Library/KM/2. Curation/`

## Workflow Decision Tree

When the skill is triggered, determine the appropriate workflow:

1. **User asks to curate new content** → Workflow: Curate New Captures
2. **User asks what's been curated** → Workflow: Review Curation Status
3. **User asks to curate specific topic/theme** → Workflow: Thematic Curation
4. **User asks to see curation registry** → Workflow: Show Processing Status

## Core Curation Process

### Curation Registry

**File:** `Library/KM/2. Curation/curation-registry.md`

This file tracks all captured content and its curation status:

```markdown
# Curation Registry

Last Updated: YYYY-MM-DD

## Processing Status

| Source Path | Source Type | Captured Date | Curated Date | Status | Curated Topics |
|-------------|-------------|---------------|--------------|--------|----------------|
| 1. Capture/YouTube/Channels/@NateBJones/2025-10-24... | YouTube Video | 2025-10-26 | 2025-10-26 | curated | AI Writing, Prompt Engineering |
| 1. Capture/YouTube/Channels/@NateBJones/2025-10-23... | YouTube Video | 2025-10-26 | - | pending | - |

## Statistics

- Total Captured Items: X
- Total Curated Items: X
- Pending Curation: X
- Last Curation Run: YYYY-MM-DD
```

### Curation Directory Structure

```
Library/KM/2. Curation/
├── curation-registry.md           # Master tracking file
├── Topics/                        # Organized by theme/topic
│   ├── AI-Writing/
│   │   ├── _index.md             # Topic overview and cross-references
│   │   ├── Principles.md         # Core principles and frameworks
│   │   └── Examples.md           # Concrete examples and case studies
│   ├── Claude-Skills/
│   │   ├── _index.md
│   │   ├── Building-Skills.md
│   │   └── Meta-Skills.md
│   ├── AI-Agents/
│   ├── AI-Tools/
│   └── Job-Market/
├── Sources/                       # Organized by source type
│   └── YouTube/
│       └── @NateBJones/
│           └── curation-notes.md  # Per-channel curation tracking
└── Cross-References/              # Connection maps
    └── theme-connections.md       # How topics relate to each other
```

## Workflow: Curate New Captures

Use this workflow when the user wants to curate new captured content.

### Step 1: Scan for New Content

1. Read the curation registry: `Library/KM/2. Curation/curation-registry.md`
2. If it doesn't exist, create it using the template above
3. Scan `Library/KM/1. Capture/` for all markdown files
4. Compare with registry to identify uncurated items (status: pending or not in registry)
5. Report to user: "Found X new items to curate"

### Step 2: Analyze Content for Curation

For each uncurated item:

1. **Read the full content** from the Capture directory
2. **Extract key elements:**
   - Core themes and topics (3-7 themes)
   - Unique insights not found elsewhere
   - Actionable principles or frameworks
   - Notable examples or case studies
   - Quality indicators (depth, novelty, reliability)
   - Cross-reference opportunities (mentions topics from other captures)

3. **Quality Assessment:**
   - Depth: Surface-level vs. deep analysis
   - Novelty: Repeats known info vs. new perspectives
   - Reliability: Sourced claims vs. opinions
   - Actionability: Theoretical vs. practical
   - Coherence: Clear vs. contradictory

### Step 3: Identify or Create Topic Areas

1. **Check existing topics** in `Library/KM/2. Curation/Topics/`
2. **Determine fit:**
   - Does content belong to existing topic(s)?
   - Does it warrant a new topic area?
   - Does it bridge multiple topics?
3. **Topic naming conventions:**
   - Use kebab-case: `AI-Writing`, `Claude-Skills`
   - Be specific but not too narrow
   - Aim for 5-15 major topic areas maximum

### Step 4: Create or Update Topic Files

For each relevant topic, update or create files in `Library/KM/2. Curation/Topics/{TopicName}/`:

**`_index.md`** - Topic Overview
```markdown
# {Topic Name}

## Overview
{2-3 sentence description of topic scope}

## Key Themes
- Theme 1
- Theme 2

## Core Insights
{High-level summary of curated insights}

## Sources
- [{Source Title}](../../Sources/{path}) - {One-line description}

## Related Topics
- [[Topics/{RelatedTopic}/_index|{RelatedTopic}]]

## Last Updated
YYYY-MM-DD
```

**`Principles.md`** - Core Principles & Frameworks
```markdown
# {Topic Name}: Principles & Frameworks

## Core Principles

### Principle 1: {Name}
**Source:** [{Source}](path)
**Insight:** {Detailed explanation}
**Key Quote:** "{Quote if applicable}"

### Principle 2: {Name}
...

## Frameworks

### {Framework Name}
**Source:** [{Source}](path)
**Description:** {How it works}
**Application:** {When/how to use}

## Contradictions & Tensions
{Note any conflicting viewpoints from different sources}
```

**`Examples.md`** - Concrete Examples & Case Studies
```markdown
# {Topic Name}: Examples & Case Studies

## Real-World Examples

### {Example Name}
**Source:** [{Source}](path)
**Context:** {Setup}
**Outcome:** {Result}
**Lesson:** {Takeaway}

## Anti-Patterns

### {Anti-Pattern Name}
**Source:** [{Source}](path)
**Description:** {What not to do}
**Why it fails:** {Explanation}
```

### Step 5: Update Cross-References

Update `Library/KM/2. Curation/Cross-References/theme-connections.md`:

```markdown
# Theme Connections

## Connection Map

### AI Writing ↔ Prompt Engineering
**Nature:** Direct dependency
**Insight:** Effective AI writing requires explicit prompt engineering principles
**Sources:** [{Source 1}](path), [{Source 2}](path)

### Claude Skills ↔ Meta-Skills
**Nature:** Hierarchical
**Insight:** Meta-skills enable building and managing other skills
**Sources:** [{Source}](path)

## Emerging Patterns

### Pattern: {Name}
**Appears in topics:** {Topic 1}, {Topic 2}, {Topic 3}
**Description:** {What the pattern is}
**Significance:** {Why it matters}
```

### Step 6: Create Source Curation Note

Create/update `Library/KM/2. Curation/Sources/{SourceType}/{SourceName}/curation-notes.md`:

```markdown
# Curation Notes: {Source Name}

## Source Overview
- **Type:** YouTube Channel / Article / Book / etc.
- **Focus:** {Primary focus area}
- **Curated Items:** {Count}

## Curation Quality Assessment
- **Depth:** High / Medium / Low
- **Novelty:** High / Medium / Low
- **Reliability:** High / Medium / Low
- **Consistency:** {Notes on coherence across items}

## Topics Contributed To
- [[Topics/AI-Writing/_index|AI Writing]] - {Brief note}
- [[Topics/Claude-Skills/_index|Claude Skills]] - {Brief note}

## Curation Log

### {Item Title}
- **Curated:** YYYY-MM-DD
- **Topics:** {Topic 1}, {Topic 2}
- **Key Contribution:** {What this added to the knowledge base}
- **Quality Notes:** {Any special observations}
```

### Step 7: Update Curation Registry

Update `Library/KM/2. Curation/curation-registry.md`:

1. Change status from "pending" to "curated"
2. Add curated date
3. List topics the content contributed to
4. Update statistics
5. Update last curation run date

### Step 8: Report Completion

Inform the user:
- Number of items curated
- Topics created or updated
- Notable insights or patterns discovered
- Next steps (e.g., "3 items remaining" or "All caught up!")

## Workflow: Review Curation Status

Use this workflow when the user wants to see what's been curated.

### Step 1: Read Curation Registry

Read `Library/KM/2. Curation/curation-registry.md`

### Step 2: Present Summary

Format clearly:
- Total items: captured vs. curated vs. pending
- Topics created: list with item counts
- Recent curation activity: last 5-10 items
- Pending items: what's left to process

### Step 3: Offer Actions

Suggest:
- "Would you like me to curate the pending items?"
- "Would you like to explore a specific topic?"
- "Would you like to see cross-references and patterns?"

## Workflow: Thematic Curation

Use this workflow when the user wants to curate content by specific theme.

### Step 1: Identify Relevant Captures

1. Scan all captured content (curated and uncurated)
2. Filter for items matching the theme
3. Present list to user

### Step 2: Deep Thematic Analysis

For theme-specific curation:
1. Read all relevant captures
2. Identify unique vs. repeated insights
3. Extract core principles specific to this theme
4. Note contradictions or evolving perspectives
5. Build comprehensive framework

### Step 3: Create Rich Topic Documentation

Go deeper than standard curation:
- More detailed principles
- More cross-referencing
- Synthesis of multiple sources
- Identification of gaps or questions

## Best Practices

### Quality Standards

**Depth Over Breadth:**
- Extract meaningful insights, not summaries
- Focus on "why" and "how," not just "what"
- Capture nuance and context

**Deduplication:**
- Don't repeat insights across topics
- Cross-reference instead of copying
- Note when multiple sources confirm same insight

**Traceability:**
- Always link back to source
- Include enough context to verify
- Preserve key quotes verbatim

**Coherence:**
- Organize logically within topics
- Use consistent structure across topics
- Make cross-references explicit

### Topic Management

**When to Create New Topic:**
- At least 2-3 sources contribute to it
- Distinct from existing topics
- Likely to grow with future captures

**When to Merge Topics:**
- Heavy overlap in content
- Difficult to distinguish boundaries
- Better served as subsections

**When to Split Topics:**
- Topic becomes too broad (>15 sources)
- Clear sub-themes emerge
- Easier navigation as separate topics

### Cross-Reference Standards

**Always Cross-Reference When:**
- One topic mentions another explicitly
- Same principle applies to multiple topics
- Example from one topic illustrates principle from another
- Source contributes to multiple topics

### Efficiency Tips

1. **Batch Processing:** Curate multiple related items together
2. **Template Reuse:** Copy structure from existing topic files
3. **Incremental Updates:** Add to existing files rather than recreating
4. **Pattern Recognition:** After 3-5 items, patterns become clear

## File Templates

See `assets/` directory for complete templates:
- `topic-index-template.md`
- `topic-principles-template.md`
- `topic-examples-template.md`
- `source-curation-notes-template.md`
- `curation-registry-template.md`
- `cross-references-template.md`

## Resources

### references/
- `curation-quality-standards.md` - Detailed quality assessment criteria
- `topic-taxonomy.md` - Guidelines for topic organization and naming

### assets/
- All file templates for curation outputs

### scripts/
- None required - all operations use standard tools

## Output Standards

### File Naming Conventions

- Topics: `Topics/{Kebab-Case-Name}/`
- Topic files: `_index.md`, `Principles.md`, `Examples.md`
- Source notes: `Sources/{SourceType}/{SourceName}/curation-notes.md`
- Cross-refs: `Cross-References/theme-connections.md`

### Markdown Standards

- Use `##` for main sections
- Use `###` for subsections
- Use bullet lists for enumerations
- Use numbered lists for sequences
- Use blockquotes (`>`) for quotes
- Use **bold** for emphasis, *italic* for terms
- Always include frontmatter where applicable

### Link Standards

- Use relative paths for internal links
- Use Obsidian wikilinks for cross-references: `[[path|display]]`
- Always include link text/context
- Verify links resolve correctly

## Error Handling

**If Curation Registry Doesn't Exist:**
- Create it from template
- Scan all Capture directory and mark all as "pending"

**If Topic Directory Doesn't Exist:**
- Create directory structure
- Create `_index.md` first
- Add other files as needed

**If Source Has No Metadata:**
- Extract what you can from content
- Use filename/path as fallback
- Note incomplete metadata in curation notes

**If Quality Is Low:**
- Still curate but note quality issues
- Consider separate "Low-Confidence" section
- Flag for user review

## Success Metrics

A successful curation creates:
- ✅ Clear, organized topic structure
- ✅ Traceable insights back to sources
- ✅ Cross-referenced related concepts
- ✅ Quality-assessed content
- ✅ Updated tracking registry
- ✅ Discoverable knowledge (easy to find what you need)
