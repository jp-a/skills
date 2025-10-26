# Git Workflow for Skills Repository

## Repository Setup

**Your Fork:** https://github.com/jp-a/skills
**Upstream:** https://github.com/anthropics/skills

## Remotes Configuration

```bash
origin    git@github.com:jp-a/skills.git (your fork)
upstream  https://github.com/anthropics/skills (anthropics original)
```

## Daily Workflow: Adding/Modifying Your Custom Skills

```bash
cd ~/.claude/skills

# Make changes to your skills
# ... edit files ...

# Stage and commit
git add .
git commit -m "Add new skill or update existing"

# Push to your fork
git push origin main
```

## Syncing from Upstream: Getting New Skills from Anthropics

When Anthropics adds new skills to their repository:

```bash
cd ~/.claude/skills

# Fetch latest from upstream
git fetch upstream

# Merge upstream changes into your main
git merge upstream/main

# Push merged changes to your fork
git push origin main
```

### If There Are Conflicts

If you've modified files that Anthropics also changed:

```bash
# After merge conflict appears
git status                    # See conflicted files
# Resolve conflicts in your editor
git add .                     # Stage resolved files
git commit -m "Merge upstream changes"
git push origin main
```

## Quick Reference Commands

```bash
# Check current status
git status

# See which remote you're tracking
git remote -v

# View recent commits
git log --oneline -10

# See what changed in last commit
git show

# Check if upstream has new changes
git fetch upstream
git log HEAD..upstream/main --oneline
```

## Your Custom Skills

Current custom skills in this repository:
- `content-curator` - Knowledge management curation skill (Step 2: Capture → Curate → Synthesize)
- `youtube-channel-capture` - Systematic YouTube video transcript capture and organization

## Best Practices

1. **Commit frequently** with clear messages
2. **Sync from upstream regularly** (weekly or monthly) to avoid large merge conflicts
3. **Test skills locally** before committing
4. **Keep custom skills in their own directories** to minimize conflicts
5. **Document your skills** with README.md files

## Troubleshooting

### Can't push to origin
```bash
# Make sure you're using SSH
git remote set-url origin git@github.com:jp-a/skills.git
```

### Need to see what's different from upstream
```bash
git fetch upstream
git diff upstream/main
```

### Want to undo last commit (not pushed)
```bash
git reset --soft HEAD~1   # Keeps changes
git reset --hard HEAD~1   # Discards changes (careful!)
```

## Initial Setup (Already Done)

For reference, here's what was configured:

```bash
cd ~/.claude/skills
git remote rename origin upstream
git remote add origin git@github.com:jp-a/skills.git
git push -u origin main
```
