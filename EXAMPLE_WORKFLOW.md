# Example Workflow: Creating a Dossier for Vertex Pharmaceuticals (VRTX)

## Step 1: Create the Dossier

Run this command in Claude:
```
/task dosag "Using ULTRATHINK reasoning and WebSearch, create a comprehensive investment dossier for VRTX focusing on their cystic fibrosis franchise, pipeline expansion into pain and kidney disease, and recent Trikafta performance"
```

This will:
- Gather primary sources from SEC filings, clinical trials, FDA
- Structure the dossier per v2.2 specifications
- Include all required sections with proper citations
- Save to `drafts/Vertex Pharmaceuticals - Investment Dossier.md`

## Step 2: Run QC Audit

After creation, run:
```
/task audag "Using ULTRATHINK reasoning and WebSearch validation, perform comprehensive QC audit on the Vertex Pharmaceuticals dossier in drafts folder checking Company Dossier v2.2 compliance, verifying all primary source citations, and ensuring proper formatting"
```

The auditor will:
- Check structural compliance with v2.2
- Verify primary source accuracy
- Validate citation formatting
- Ensure date consistency
- Generate audit report in `audit-reports/`

## Step 3: Review and Finalize

1. Review the audit report for any issues
2. If PASSED: Move from `drafts/` to `dossiers/`
3. If FAILED: Fix identified issues and re-audit

## Expected Output Structure

The final dossier will include:

```markdown
# Vertex Pharmaceuticals - Investment Dossier

**Company**: Vertex Pharmaceuticals (VRTX)
**Date**: 2025-08-25
**Model**: Claude Opus 4.1
**Prompt**: Company Dossier v. 2.2

1) **Executive Summary**
- Leading CF therapy company with >90% market share
- Bull/bear: Franchise durability vs pipeline execution risk

2) **Key developments (last ~12M)**
| Date | Event | Interpretation |
|---|---|---|
| 2024-XX-XX | Trikafta sales update | Continued growth [1] |

3) **Catalysts (next ~12M)**
| Expected date | Event | Context & potential impact |
|---|---|---|
| Q4 2025 | VX-548 pain data | Key diversification (↑) [2] |

[... continues with all required sections ...]

**Sources**
[1] Vertex Q2 2024 10-Q, SEC.gov, URL, 2025-08-25
[2] ClinicalTrials.gov NCT#, URL, 2025-08-25
```

## Using the Helper Scripts

### Option 1: Individual Scripts
```batch
create-dossier.bat VRTX
audit-dossier.bat "Vertex Pharmaceuticals"
```

### Option 2: Full Workflow Script
```batch
full-workflow.bat VRTX "focusing on CF franchise and pipeline"
```

## Common QC Audit Findings

1. **Missing Primary Citations**: All numbers need [#] with primary source
2. **Date Format Issues**: Must be YYYY-MM-DD
3. **Table Structure**: Ensure proper markdown formatting
4. **Financial Units**: Use M/B consistently
5. **Unknown Data**: Mark as "UNKNOWN—PRIMARY REQUIRED"

## Success Criteria

✅ All sections present in correct order
✅ Every quantitative claim has primary citation
✅ Tables properly formatted
✅ Dates consistently formatted
✅ Sources list complete with URLs
✅ QC audit shows "PASSED"