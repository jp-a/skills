# Topic Taxonomy & Organization Guidelines

This document provides guidelines for organizing curated content into coherent topic areas.

## Principles of Topic Organization

### 1. User-Centric Organization

**Primary Question:** "If I wanted to find X, where would I look?"

Organize by:
- **Problem space** (not technology): "AI Writing" not "GPT-4 Text Generation"
- **Use case** (not method): "Job Market Strategy" not "Resume Optimization"
- **Domain** (when clear): "Security", "Education", "Healthcare"
- **Capability** (not tool): "Prompt Engineering" not "ChatGPT Tips"

### 2. Granularity Sweet Spot

**Too Broad:**
- "AI" - Everything fits, nothing is findable
- Indicators: >20 sources, disparate subtopics, hard to summarize

**Too Narrow:**
- "ChatGPT-4 Prompt Engineering for Python Code" - Too specific, won't accumulate content
- Indicators: <2 sources, likely won't grow, could be subsection

**Just Right:**
- "Prompt Engineering" - Clear scope, room to grow, distinct from related topics
- Indicators: 3-15 sources, coherent theme, can summarize in 2-3 sentences

### 3. Coherence Over Convenience

Prefer topics that:
- Share underlying principles or frameworks
- Address related problems or use cases
- Build on each other conceptually

Avoid topics that:
- Group by arbitrary criteria (e.g., "Tuesday's Captures")
- Mix unrelated domains (e.g., "AI and Cooking")
- Are purely temporal or source-based

---

## Topic Lifecycle

### Creating New Topics

**When to Create:**
1. **Critical Mass:** 2-3 captured items address the same domain/problem
2. **Distinct Identity:** Can't fit naturally into existing topics
3. **Growth Potential:** Likely to accumulate more content over time
4. **Clear Scope:** Can define in 2-3 sentences what belongs

**Creation Process:**
1. Choose clear, descriptive name (see naming conventions below)
2. Create topic directory and `_index.md`
3. Add initial content to Principles and/or Examples
4. Update cross-references if related to existing topics
5. Add to curation registry topic distribution

**Starting Template:**
```
Topics/{TopicName}/
├── _index.md          # Start here
├── Principles.md      # Add as insights accumulate
└── Examples.md        # Add when you have concrete cases
```

### Growing Topics

**As topics accumulate 5+ sources:**
- Refine organization within Principles.md and Examples.md
- Add subsections if needed
- Strengthen cross-references
- Update topic overview to reflect growing understanding

**As topics accumulate 10+ sources:**
- Consider if sub-topics are emerging
- May need to split (see below)
- Definitely strengthen cross-references
- May warrant synthesis document

### Merging Topics

**When to Merge:**
- Heavy content overlap (>50% of sources contribute to both)
- Difficult to distinguish boundaries
- Better served as subsections of single topic
- Users confused about where to look

**Merge Process:**
1. Choose primary topic (usually broader or more sources)
2. Move content from secondary topic
3. Create subsections if needed
4. Update all cross-references
5. Create redirect note in old topic location
6. Update curation registry

### Splitting Topics

**When to Split:**
- Topic becomes too broad (>15-20 sources)
- Clear sub-themes emerge with distinct principles
- Different use cases that don't benefit from combination
- Navigation becomes difficult

**Split Process:**
1. Identify natural divisions (usually by sub-theme or use case)
2. Create new topic directories
3. Redistribute content
4. Create clear cross-references between new topics
5. Update parent topic overview to reference child topics
6. Consider keeping high-level overview in original topic
7. Update curation registry

---

## Naming Conventions

### Format Rules

**Use Kebab-Case:**
- ✅ `AI-Writing`
- ✅ `Claude-Skills`
- ✅ `Job-Market-Strategy`
- ❌ `ai_writing` (underscores)
- ❌ `AIWriting` (PascalCase)
- ❌ `ai writing` (spaces)

**Be Specific But Not Too Narrow:**
- ✅ `Prompt-Engineering` (clear, broad enough)
- ✅ `AI-Agent-Architecture` (specific domain)
- ❌ `AI` (too broad)
- ❌ `GPT-4-Prompt-Engineering-for-Marketing-Copy` (too narrow)

**Use Domain/Problem Language:**
- ✅ `Business-Writing` (problem space)
- ✅ `Security-Testing` (domain + activity)
- ❌ `LLM-Text-Generation` (technology focus)
- ❌ `Tuesday-Topics` (arbitrary grouping)

**Prefer Nouns and Noun Phrases:**
- ✅ `Job-Market-Strategy`
- ✅ `Memory-Engineering`
- ❌ `How-To-Find-Jobs` (too procedural)
- ❌ `Thinking-About-Memory` (too vague)

### Common Topic Patterns

**Skill/Practice Topics:**
- Pattern: `{Skill-Name}`
- Examples: `Prompt-Engineering`, `AI-Writing`, `Code-Review`

**Domain Topics:**
- Pattern: `{Domain}` or `{Domain-Aspect}`
- Examples: `Security`, `Education-Technology`, `Healthcare-AI`

**Problem/Solution Topics:**
- Pattern: `{Problem-Area}` or `{Solution-Space}`
- Examples: `Job-Market-Strategy`, `Knowledge-Management`, `Team-Coordination`

**Tool/Technology Topics (Use Sparingly):**
- Pattern: `{Tool-Name}` (only if tool-specific knowledge)
- Examples: `Claude-Skills`, `MCP-Servers`
- Warning: Prefer problem-space naming when possible

**Architecture/Design Topics:**
- Pattern: `{System-Type}-Architecture` or `{Design-Pattern}`
- Examples: `AI-Agent-Architecture`, `Verification-Systems`, `Memory-Engineering`

---

## Topic Hierarchy

### Flat vs. Nested

**Default: Flat Structure**
```
Topics/
├── AI-Writing/
├── Prompt-Engineering/
├── Claude-Skills/
└── Security-Testing/
```

**Advantages:**
- Easier to navigate
- Simpler cross-referencing
- Less cognitive overhead
- Flexibility to reorganize

**When to Nest (Rare):**
Only when clear parent-child relationship AND child unlikely to be sought independently

```
Topics/
├── AI-Agents/
│   ├── _index.md
│   ├── Architecture/
│   ├── Memory/
│   └── Testing/
└── AI-Writing/
```

**Use nested only if:**
- Sub-topics are genuinely subordinate
- Users would naturally drill down (not search directly for subtopic)
- Benefits clarity more than flat structure

**Generally avoid nesting more than 2 levels deep**

### Cross-References Over Hierarchy

**Prefer:** Multiple flat topics with strong cross-references
**Over:** Deep hierarchy attempting to capture all relationships

Relationships between topics are rarely pure hierarchies - cross-references handle complexity better.

---

## Special Topic Categories

### Meta-Topics

**Purpose:** Topics about the knowledge management process itself

**Examples:**
- `Knowledge-Curation` - About curation practices
- `Synthesis-Methods` - About synthesis approaches

**Location:** Can be in main Topics/ or separate Meta/ directory

### Cross-Cutting Themes

**Challenge:** Some themes appear across many domains

**Examples:**
- "Memory" appears in AI-Agents, Knowledge-Management, System-Design
- "Verification" appears in Job-Market, Security, Quality-Assurance

**Solutions:**
1. **Create dedicated topic if substantial:** If 3+ sources focus primarily on this theme
2. **Document in Cross-References:** If it's truly cross-cutting
3. **Use as subsections:** Include in each relevant topic with cross-refs

### Emerging vs. Established Topics

**Emerging:**
- <5 sources
- Boundaries not yet clear
- May be speculative

**Mark as:** "(Emerging)" in index, note this in overview
**Watch for:** Growth, clarity, or need to merge/split

**Established:**
- 5+ sources
- Clear scope and boundaries
- Coherent principles

**These form** the stable backbone of your curation

---

## Topic Metadata

In each `_index.md`, include:

```markdown
---
topic_name: {Name}
created: {YYYY-MM-DD}
status: {emerging / established}
source_count: {X}
last_updated: {YYYY-MM-DD}
confidence: {high / medium / low}
---
```

**Status:**
- `emerging`: <5 sources, boundaries unclear
- `established`: 5+ sources, clear scope

**Confidence:**
- `high`: Multiple high-quality sources, coherent principles
- `medium`: Some high-quality sources, some gaps
- `low`: Limited sources or quality concerns

---

## Quality Checks for Topics

### Good Topic Indicators

✅ Can summarize scope in 2-3 sentences
✅ Clear what belongs vs. doesn't belong
✅ Contains coherent set of principles
✅ Sources reinforce each other
✅ Natural cross-references to related topics
✅ User would know to look here for this domain

### Poor Topic Indicators

❌ Hard to explain what's in it
❌ Arbitrary collection of sources
❌ No coherent principles emerge
❌ Sources don't relate to each other
❌ User wouldn't know where to find this
❌ Just a convenient dumping ground

---

## Migration and Maintenance

### Regular Review (Quarterly)

1. **Scan for merge candidates:**
   - Topics with <3 sources after 3+ months
   - Topics with >70% overlap

2. **Scan for split candidates:**
   - Topics with >15 sources
   - Topics with emergent clear sub-themes
   - Topics users struggle to navigate

3. **Update emerging status:**
   - Promote to established if warranted
   - Consider merging if not growing

4. **Review naming:**
   - Do names still make sense?
   - Better alternatives emerged?

### Documentation

Keep changelog in curation registry:
```markdown
## Topic Evolution

### 2025-10-26
- Created: AI-Writing, Claude-Skills, AI-Agents
- Merged: LLM-Prompting → Prompt-Engineering
- Split: AI-Tools → AI-Tool-Design + AI-Tool-Evaluation
```

This helps track thinking and makes it easier to maintain consistency.
