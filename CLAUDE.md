# Company Dossier Creation Workflow

## 🚀 Automated Workflow Pipeline

### Complete Process: dosag → audag
The system uses a two-step automated workflow:

1. **dosag** creates the initial company dossier → saves to `drafts/`
2. **audag** audits the dossier → creates:
   - Audit report in `audit-reports/`
   - Corrected/audited dossier in `dossiers/`

### Quick Start Commands:
```bash
# Step 1: Create dossier (saves to drafts/)
/task dosag "Analyze CRNX"

# Step 2: Audit the dossier (creates audit report + final dossier)
/task audag "Read and audit drafts/Crinetics Pharmaceuticals - Investment Dossier.md"
```

## Available Agents

### Project-Specific Agents (v3.2):
- `dosag` - Creates comprehensive investment-grade biotech dossiers
- `audag` - QC auditor that validates and corrects dossiers

### System Agents (Fallback):
- `biogod` - Comprehensive biotech company analysis
- `bigo` - Biotech investment analysis with conviction scoring
- `compi` - Competitive intelligence for biotech products

## How to Use Working Agents

### Using biogod for Company Analysis:
```bash
/task biogod "Analyze [COMPANY] ([TICKER]) with focus on clinical pipeline, financials, competitive positioning, and investment thesis. Include ULTRATHINK reasoning and WebSearch for primary sources."

# Example:
/task biogod "Analyze Crinetics Pharmaceuticals (CRNX) with focus on paltusotine for acromegaly, atumelnant for CAH, financial runway, and competitive positioning versus Ascendis and Chiasma."
```

### Using bigo for Investment Analysis:
```bash
/task bigo "Create institutional-grade investment analysis for [TICKER] with conviction scoring"
```

### Using compi for Competitive Intelligence:
```bash
/task compi "Compare [DRUG1] vs [DRUG2] for [INDICATION] including efficacy, safety, and market positioning"
```

## Directory Structure & Workflow

```
Company_Dossiers/
├── CLAUDE.md              # This file - workflow instructions
├── .claude/           
│   └── agents/            # Project agents with v3.2 prompts
│       ├── dosag.md       # Dossier creator agent
│       └── audag.md       # QC auditor agent
├── prompts/               # Agent prompt specifications
│   ├── CD v3.2 C04.md     # Company Dossier v3.2 prompt
│   └── QC v3.2 C04.md     # QC Auditor v3.2 prompt
├── drafts/                # [STEP 1] dosag outputs here
├── audit-reports/         # [STEP 2a] audag audit reports here
├── dossiers/              # [STEP 2b] audag final dossiers here
└── sources/               # Cached primary sources

Workflow: drafts/ → audit → dossiers/
```

## Troubleshooting

### If agents don't show in /agents:
1. Check if agents appear with `/agents` command
2. Try restarting Claude Code
3. Use system agents (biogod, bigo, compi) instead
4. Report issue: https://github.com/anthropics/claude-code/issues

### Agent File Format:
```markdown
---
name: agent-name
description: When to use this agent
---

Agent instructions here...
```

## Company Dossier Requirements (v3.2)

### Required Sections:
1. Executive Summary
2. Key developments (last 12M) - table
3. Catalysts (next 12M) - table  
4. Programs / Pipeline - detailed bullets
5. Financials - with citations
6. Sell-Side Pulse
7. Bull / Bear Views - table
8. Investment View / Takeaways
9. Sources - numbered list

### Key Rules:
- 15-30 WebSearches minimum
- Every number needs [#] citation
- Dates as YYYY-MM-DD
- Financials as M/B (millions/billions)
- Mark unknowns as "UNKNOWN—PRIMARY REQUIRED"

## Quick Start for Crinetics Analysis

Since project agents may not work, use biogod:

```bash
/task biogod "Create comprehensive analysis of Crinetics Pharmaceuticals (CRNX) including:
- Paltusotine Phase 3 PATHFNDR studies for acromegaly
- Atumelnant Phase 2 for congenital adrenal hyperplasia  
- CRN04894 for hyperinsulinism
- Financial runway and burn rate
- Competitive analysis vs Ascendis (veldoreotide) and Chiasma (Mycapssa)
- Investment thesis with bull/bear cases
Use WebSearch for primary sources, include all citations"
```

This will generate a comprehensive analysis using the working biogod agent.