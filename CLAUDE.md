# Company Dossier Creation & QC Audit Workflow

## Quick Commands

### IMPORTANT: Agent System Names
⚠️ **Note**: The agents are registered in Claude's system as:
- **Dossier Creation**: Use `biotech-investment-dossier`
- **QC Audit**: Use `biotech-dossier-qc-auditor`

### IMPORTANT: Always Include ULTRATHINK and WebSearch
When invoking these agents, explicitly request ULTRATHINK reasoning and WebSearch:

### Create a new dossier
```bash
# Basic usage - creates investment-grade dossier for any biotech ticker
/task biotech-investment-dossier "Using ULTRATHINK reasoning and WebSearch, create a comprehensive dossier for [TICKER]"

# Examples
/task biotech-investment-dossier "Using ULTRATHINK reasoning and WebSearch, create a comprehensive dossier for MRNA"
/task biotech-investment-dossier "Using ULTRATHINK reasoning and WebSearch, create a comprehensive dossier for GILD"
/task biotech-investment-dossier "Using ULTRATHINK reasoning and WebSearch, create a comprehensive dossier for VRTX"
```

### Audit an existing dossier
```bash
# QC audit for compliance and accuracy
/task biotech-dossier-qc-auditor "Using ULTRATHINK reasoning and WebSearch validation, review the [COMPANY] dossier in /dossiers folder for compliance and accuracy"

# Example
/task biotech-dossier-qc-auditor "Using ULTRATHINK reasoning and WebSearch validation, review the Moderna dossier in /dossiers folder for compliance and accuracy"
```

### Full workflow (create + audit)
```bash
# Create and immediately audit
1. /task biotech-investment-dossier "Using ULTRATHINK reasoning and WebSearch, create a comprehensive dossier for [TICKER]"
2. Wait for completion
3. /task biotech-dossier-qc-auditor "Using ULTRATHINK reasoning and WebSearch validation, review the newly created dossier for [COMPANY]"
```

## Directory Structure

```
Company_Dossiers/
├── CLAUDE.md           # This file - workflow instructions
├── dossiers/          # Completed, QC-approved dossiers
├── drafts/            # Work-in-progress dossiers
├── audit-reports/     # QC audit results and recommendations
└── sources/           # Cached primary sources and references
```

## Agent Capabilities

### biotech-investment-dossier
- **System Name**: biotech-investment-dossier
- **Config File**: `.claude/agents/biotech-investment-dossier.md`
- **Purpose**: Creates comprehensive investment-grade company dossiers
- **Required**: Use ULTRATHINK reasoning and WebSearch for all dossiers
- **Compliance**: Follows Company Dossier v2.2 specifications exactly
- **Key Features**:
  - Retrieves and cites primary sources (SEC filings, ClinicalTrials.gov, press releases)
  - Structures output with all required sections
  - Formats dates as YYYY-MM-DD
  - Uses M/B for financial units
  - Marks missing primary data as "UNKNOWN—PRIMARY REQUIRED"

### biotech-dossier-qc-auditor
- **System Name**: biotech-dossier-qc-auditor
- **Config File**: `.claude/agents/biotech-dossier-qc-auditor.md`
- **Purpose**: Performs quality control auditing on dossiers
- **Required**: Use ULTRATHINK reasoning and WebSearch for validation
- **Validation Checks**:
  - Structural compliance with v2.2 format
  - Primary source verification for all quantitative claims
  - Citation format and completeness
  - Date consistency and formatting
  - Required section presence
  - Table structure integrity

## ULTRATHINK & WebSearch Instructions for Agents

### When Using biotech-investment-dossier:
The agent should apply ULTRATHINK reasoning with these phases:
1. **Information Gathering**: Use WebSearch to find primary sources
2. **Deep Analysis**: Apply pattern recognition and cross-validation
3. **Synthesis**: Create investment thesis with bull/bear tension
4. **Verification**: Cross-check all quantitative claims

### When Using biotech-dossier-qc-auditor:
The agent should apply ULTRATHINK verification with:
1. **Structural Analysis**: Verify all sections present and ordered
2. **WebSearch Validation**: Independently verify each claim
3. **Contradiction Resolution**: Identify and resolve conflicts
4. **Quality Assessment**: Determine pass/fail with specific issues

### Required WebSearch Patterns
Both agents should use targeted searches like:
```
# Financial verification
"[TICKER] cash equivalents Q2 2024 10-Q"
"[COMPANY] burn rate operating expenses quarterly"

# Clinical validation  
"[DRUG] primary endpoint phase 3 results"
"site:clinicaltrials.gov [COMPANY] recruiting"

# Competitive intelligence
"[INDICATION] market size 2024 forecast"
"[COMPETITOR] vs [COMPANY] efficacy comparison"
```

### Key Requirements:
- **15-30 WebSearches minimum** per dossier/audit
- **Source Priority**: SEC > Clinical Registries > Company Direct > News
- **3+ search variations** for critical facts
- **Always verify dates** and financial figures
- **Cross-reference** multiple sources for accuracy

## Primary Source Requirements

### Must Have Primary Citations
- [ ] Financial metrics (cash, burn rate, debt)
- [ ] Clinical trial results (endpoints, p-values, safety data)
- [ ] Pipeline stage and study design
- [ ] Regulatory milestone dates
- [ ] Recent capital raises and deal terms
- [ ] Key development dates (last 12 months)
- [ ] Upcoming catalyst dates (next 12 months)

### Acceptable Primary Sources
1. **SEC Filings**: 10-K, 10-Q, 8-K, S-1, proxies
2. **Clinical Data**: ClinicalTrials.gov, FDA.gov, company presentations
3. **Press Releases**: Company IR site, BusinessWire, PR Newswire
4. **Conferences**: Transcripts from investor conferences
5. **Regulatory**: FDA approvals, CRL letters, PDUFA dates

### Secondary Sources (supplementary only)
- Sell-side research (for consensus PT only)
- News articles (for context, not primary facts)
- Third-party databases (cross-reference only)

## Output Format Validation Checklist

### Document Header
- [ ] Company name and ticker
- [ ] Date in YYYY-MM-DD format
- [ ] Model name specified
- [ ] Prompt version: Company Dossier v. 2.2

### Required Sections (exact order)
1. [ ] Executive Summary
2. [ ] Key developments (last ~12M) - table format
3. [ ] Catalysts (next ~12M) - table format
4. [ ] Programs / Pipeline - detailed bullets per program
5. [ ] Financials - with citations
6. [ ] Sell-Side Pulse
7. [ ] Bull / Bear Views - table format
8. [ ] Investment View / Takeaways
9. [ ] Sources - numbered list with URLs

### Citation Requirements
- [ ] Every quantitative claim has [#] citation
- [ ] Primary sources listed before secondary
- [ ] Citations include title, publisher, URL, access date
- [ ] Citation numbers are sequential and unique

## Common Issues & Troubleshooting

### Issue: Missing primary source data
**Solution**: Mark as "UNKNOWN—PRIMARY REQUIRED" rather than inferring

### Issue: Inconsistent date formats
**Solution**: Always use YYYY-MM-DD for specific dates, or YYYY-MM/YYYY/Q# YYYY for catalysts

### Issue: Table formatting breaks
**Solution**: Ensure proper markdown table syntax with | separators and header row

### Issue: Citation mismatch
**Solution**: Verify citation numbers in text match Sources section exactly

### Issue: Financial units inconsistent
**Solution**: Always use M for millions, B for billions (not MM or Bn)

## Example Workflow

```bash
# 1. Create dossier for Moderna (with ULTRATHINK and WebSearch)
/task biotech-investment-dossier "Using ULTRATHINK reasoning and WebSearch, create a comprehensive dossier for MRNA focusing on their mRNA platform, COVID franchise, and pipeline programs including INT, RSV, and oncology"

# 2. Save to drafts folder initially
# Agent will create: drafts/Moderna - Investment Dossier.md

# 3. Run QC audit (with ULTRATHINK and WebSearch validation)
/task biotech-dossier-qc-auditor "Using ULTRATHINK reasoning and WebSearch validation, perform comprehensive QC audit on drafts/Moderna - Investment Dossier.md checking v2.2 compliance, primary source accuracy, and formatting"

# 4. Review audit report
# Check: audit-reports/Moderna - QC Audit Report.md

# 5. If audit passes, move to final folder
# Move: drafts/Moderna - Investment Dossier.md → dossiers/Moderna - Investment Dossier.md

# 6. If audit fails, address issues and re-audit
# Fix issues identified in audit report, then repeat step 3
```

## Best Practices

1. **Always audit before publishing**: Never skip the QC audit step
2. **Use specific prompts**: Include focus areas in your agent prompts
3. **Verify primary sources**: Spot-check critical numbers against sources
4. **Maintain consistency**: Use the same format for all dossiers
5. **Update regularly**: Refresh dossiers quarterly or after major events
6. **Archive versions**: Keep historical versions for comparison

## Quick Reference - Company Dossier v2.2 Rules

- **Structure**: Must follow exact headings and table formats
- **Citations**: Inline bracketed [#] markers for every claim
- **Primary evidence**: Required for all hard numbers
- **Unknown data**: Mark as "UNKNOWN—PRIMARY REQUIRED"
- **Date formats**: YYYY-MM-DD (events), YYYY-MM/Q#/H# (catalysts)
- **Financial units**: M = Million, B = Billion
- **Time horizons**: Key developments = last 12M, Catalysts = next 12M
- **File naming**: `{Company Name} - Investment Dossier.md`

## Contact & Support

For issues with:
- Agent functionality: Check agent descriptions with `/agents`
- Workflow problems: Review this CLAUDE.md file
- Format compliance: Refer to Company Dossier v2.2 specification
- QC failures: Check audit reports in `/audit-reports`