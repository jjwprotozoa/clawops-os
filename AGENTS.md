# ClawOps Agent Architecture

ClawOps is a controlled autonomous system.

Background automation MUST NOT use paid models.
Human-triggered sessions MAY escalate to paid models.

---

## Model Policy

### Tier 1 – Local (Default for automation)

Provider: Ollama

Use for:

- Scheduled content generation
- Blog drafting
- Social posts
- Summaries
- File diffs
- Health checks
- Heartbeats
- Log parsing
- Structured extraction

Never escalate automatically.

### Tier 2 – Haiku (Human-supervised work)

Provider: Anthropic Haiku

Use for:

- Interactive content refinement
- Planning
- Lightweight reasoning
- Controlled code edits
- Tactical decision support

Requires human presence.

### Tier 3 – Sonnet (Restricted)

Provider: Anthropic Sonnet

Use only for:

- Architecture decisions
- Security review
- Complex debugging
- High-stakes refactors
- Multi-project strategic reasoning

Explicit invocation required.

---

## Hard Rules

1. No scheduled workflow may call Tier 2 or Tier 3 models.
2. All automation must:
   - Enforce max calls per run
   - Enforce max runtime
   - Enforce max token limits
3. Any loop detection → immediate abort.
4. Human approval required before:
   - Publishing content
   - Deploying changes
   - Merging structural updates

---

## Continuous Improvement Loop

### Daily (Local Only)

- Summarize work into memory/YYYY-MM-DD.md
- Extract decisions
- Extract blockers
- Extract opportunities

### Weekly (Haiku Allowed)

- Evaluate output quality
- Propose prompt optimizations
- Suggest agent adjustments

### Strategic (Sonnet Optional)

- Redesign agent architecture
- Security audits
- Major system evolution

---

## Cost Protection

Paid models are never used:

- By cron
- By heartbeat
- By retry loops
- By unattended automation

If cost anomalies detected → pause automation.
