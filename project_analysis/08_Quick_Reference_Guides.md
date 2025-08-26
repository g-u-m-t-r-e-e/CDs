# Quick Reference Guides for AI-Powered Company Dossiers
## Biotech Portfolio Management Implementation

---

## 1. DAILY WORKFLOW CHECKLIST

### Morning Routine (15 minutes)
- [ ] Check overnight FDA approvals/CRLs
- [ ] Review clinical trial updates (clinicaltrials.gov)
- [ ] Scan biotech news for portfolio companies
- [ ] Queue priority dossier updates

### Dossier Creation Process
```bash
# Step 1: Generate dossier
/task biotech-investment-dossier "Create dossier for [TICKER]"

# Step 2: Audit dossier
/task biotech-dossier-qc-auditor "Audit the [TICKER] dossier"

# Step 3: Review & file
Move from drafts/ to dossiers/ after validation
```

### Weekly Review (Fridays)
- [ ] Update 5 highest-conviction dossiers
- [ ] Audit 3 random dossiers for quality
- [ ] Generate portfolio overview report
- [ ] Document key learnings/improvements

---

## 2. PROMPT ENGINEERING CHEAT SHEET

### Core Structure Template
```
[CONTEXT] + [SPECIFIC TASK] + [CONSTRAINTS] + [OUTPUT FORMAT]
```

### Biotech-Specific Modifiers
```
"focusing on [PRIMARY/SECONDARY] endpoints"
"including comparator analysis against SOC"
"with emphasis on [DISEASE AREA] regulatory pathway"
"considering [COMBO/MONO] therapy dynamics"
```

### Source Hierarchy Commands
```
PRIMARY: "verify via SEC filings"
SECONDARY: "cross-reference ClinicalTrials.gov"
TERTIARY: "confirm through company IR"
FALLBACK: "mark as UNKNOWN—PRIMARY REQUIRED"
```

---

## 3. CLINICAL TRIAL ASSESSMENT MATRIX

| Trial Phase | Key Questions | Red Flags | Green Flags |
|------------|---------------|-----------|-------------|
| **Phase 1** | Safety profile? Dose finding? | SAEs >20%, Narrow therapeutic window | Clean safety, Linear PK |
| **Phase 2** | Efficacy signal? Patient selection? | p>0.05, High dropout | p<0.01, Biomarker enrichment |
| **Phase 3** | Powering? Endpoints? | Interim futility, Site issues | Over-enrollment, FDA SPA |
| **Pivotal** | Regulatory path? Competition? | CRL history, Crowded market | Fast Track, First-in-class |

---

## 4. VALUATION QUICK CALCULATOR

### rNPV Formula Components
```
rNPV = Σ[(Revenue × Probability) / (1+r)^t] - Development Costs

Where:
- Revenue = Peak Sales × Market Share × Duration
- Probability = Phase Success Rate × Regulatory Approval Rate
- r = Discount Rate (10-15% typical)
- t = Time to Revenue
```

### Success Rate Benchmarks
- Phase 1→2: 65%
- Phase 2→3: 35%
- Phase 3→Approval: 60%
- Approval→Launch: 90%

### Quick Multiples
- Platform companies: 3-5x forward revenue
- Single-asset: Risk-adjusted NPV
- Commercial: 2-4x current revenue + pipeline value

---

## 5. COMPETITIVE INTELLIGENCE SHORTCUTS

### Market Position Assessment (30 seconds)
1. **Leader**: >40% market share, premium pricing
2. **Challenger**: 15-40% share, differentiated positioning
3. **Niche**: <15% share, specific indication focus
4. **Disruptor**: New MOA, paradigm shift potential

### Threat Level Classification
- **CRITICAL**: Competing Phase 3, same indication, superior efficacy
- **HIGH**: Phase 2 competitor, better safety profile
- **MEDIUM**: Different MOA, same patient population
- **LOW**: Early stage, different indication

---

## 6. ERROR PREVENTION CHECKLIST

### Before Submitting Dossier
- [ ] All numbers traced to primary source?
- [ ] Trial identifiers (NCT#) verified?
- [ ] Market cap/financials <24 hours old?
- [ ] Competitor data current quarter?
- [ ] Risk factors updated?

### Common Pitfalls to Avoid
❌ Using press releases as primary source
❌ Mixing fiscal/calendar years
❌ Confusing interim/final data
❌ Missing combination therapy dynamics
❌ Ignoring manufacturing risks

---

## 7. CHATGPT 5 PRO QUICK COMMANDS

### Structured Prompts
```
/analyze_pipeline [TICKER] with focus on [PHASE]
/compare [DRUG1] vs [DRUG2] for [INDICATION]
/valuation [COMPANY] using [DCF/COMPS/PRECEDENT]
/regulatory_timeline [DRUG] considering [FDA/EMA]
```

### Token-Efficient Shortcuts
- Replace "Please analyze..." with "/analyze"
- Use abbreviations: OS→Overall Survival, PFS→Progression-Free Survival
- Batch queries: "Analyze MRTX, RVMD, CRSP pipelines"

---

## 8. EMERGENCY PROCEDURES

### When Dossier Generation Fails
1. Check WebSearch availability
2. Verify ticker symbol spelling
3. Try company name instead of ticker
4. Fallback to manual template completion

### Audit Failure Recovery
```bash
# Step 1: Identify failure point
grep "ERROR" audit-reports/[TICKER]_audit.md

# Step 2: Manual verification
- Check primary sources manually
- Document discrepancies
- Re-run with specific focus area
```

### Hallucination Detection
**Red Flags:**
- Oddly specific percentages (87.3%)
- Future dates for past events
- Mixing company data
- Non-existent trial numbers

**Verification Protocol:**
1. Stop immediately
2. Flag section for manual review
3. Verify with 2+ primary sources
4. Document in risk log

---

## 9. STAKEHOLDER COMMUNICATION TEMPLATES

### Investment Committee Brief
```markdown
## [TICKER] Investment Thesis Update
**Generated:** [DATE] | **Confidence:** [HIGH/MEDIUM/LOW]

### Key Changes Since Last Review
- [BULLET POINTS MAX 3]

### Catalyst Timeline
- [NEXT 3 CATALYSTS WITH DATES]

### Risk Update
- [PRIMARY RISK + MITIGATION]

### Recommendation
[MAINTAIN/INCREASE/DECREASE/EXIT] position
```

### Client Update Template
```markdown
Dear [CLIENT],

Quick update on [COMPANY]:
- [ONE LINE SUMMARY]
- Next catalyst: [EVENT] on [DATE]
- Our view: [BULLISH/NEUTRAL/BEARISH]

Full dossier available upon request.
```

---

## 10. OPTIMIZATION TIPS

### Speed Improvements
- Pre-cache common company data
- Use batch commands for portfolio updates
- Set up automated overnight runs
- Create templates for recurring analyses

### Quality Improvements
- Implement peer review rotation
- Track error rates by section
- A/B test prompt variations
- Document edge cases

### Cost Management
- Monitor token usage weekly
- Optimize prompt length
- Cache static data
- Batch similar requests

---

## 11. TROUBLESHOOTING MATRIX

| Problem | Likely Cause | Quick Fix | Long-term Solution |
|---------|-------------|-----------|-------------------|
| Slow generation | Large context | Reduce scope | Implement caching |
| Wrong data | Outdated source | Force refresh | API integration |
| Missing trials | NCT not indexed | Manual add | ClinicalTrials API |
| Valuation errors | Wrong assumptions | Check model | Standardize inputs |
| Compliance flag | Unapproved source | Primary only | Source whitelist |

---

## 12. REGULATORY CALENDAR TRACKING

### FDA Key Dates
- PDUFA: Prescription Drug User Fee Act deadline
- AdCom: Advisory Committee meeting (-6 weeks typical)
- Priority Review: 6 months (vs 10-12 standard)

### Quick Timeline Calculator
```
Submission → Approval:
- Priority: 6 months
- Standard: 10-12 months
- Breakthrough: 4-6 months

Clinical Hold → Resolution:
- Typical: 30 days
- Complex: 60-90 days
```

---

## APPENDIX: ESSENTIAL BOOKMARKS

### Primary Sources
- SEC EDGAR: https://www.sec.gov/edgar
- ClinicalTrials.gov: https://clinicaltrials.gov
- FDA Calendar: https://www.fda.gov/news-events
- EMA Updates: https://www.ema.europa.eu

### Market Intelligence
- Biomedtracker: [Subscription]
- Evaluate Pharma: [Subscription]
- GlobalData: [Subscription]
- Cortellis: [Subscription]

### Quick References
- FDA Guidance Docs: https://www.fda.gov/regulatory-information
- Biomarker Qualification: https://www.fda.gov/biomarker-qualification-program
- Breakthrough Designations: https://www.fda.gov/breakthrough-therapy

---

*Document Version: 1.0*
*Last Updated: Analysis Date*
*Next Review: Quarterly*

**Remember: Speed matters, but accuracy matters more. When in doubt, mark as "UNKNOWN—PRIMARY REQUIRED" rather than guess.**