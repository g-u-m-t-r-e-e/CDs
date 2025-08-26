# Critical Analysis of Company Dossier Prompts
*Analysis Date: 2025-08-25*
*Analyst: AI Implementation Strategy Review*

## Executive Summary

Your prompt engineering shows sophisticated understanding of institutional investment requirements. The dual-agent approach (creation + audit) is innovative and addresses the core LLM reliability challenge. However, biotech's inherent complexity requires additional frameworks for endpoint variability, platform technologies, and regulatory nuance.

**Overall Grade: B+ (Strong foundation, needs biotech-specific enhancements)**

---

## PART 1: STRENGTHS ANALYSIS

### 1.1 Exceptional Elements

#### **Citation Rigor** ⭐⭐⭐⭐⭐
Your requirement for inline citations with primary source validation is institutional-grade. The "UNKNOWN—PRIMARY REQUIRED" fallback prevents dangerous hallucinations.

```
STRENGTH: Forces transparency when data unavailable
IMPACT: Builds trust with investment committee
```

#### **Two-Phase Quality Control** ⭐⭐⭐⭐⭐
The biotech-investment-dossier → biotech-dossier-qc-auditor workflow mimics real analyst teams (junior analyst → senior review). This catches both creation errors and verification gaps.

#### **Source Hierarchy** ⭐⭐⭐⭐⭐
```
SEC > ClinicalTrials.gov > FDA > Company IR > News
```
This prioritization is exactly right for biotech investment analysis.

#### **Structural Standardization** ⭐⭐⭐⭐
The v2.2 specification ensures consistency across companies, enabling rapid comparative analysis.

### 1.2 Strong Technical Decisions

1. **ULTRATHINK Integration**: Multi-phase reasoning reduces single-pass errors
2. **WebSearch Requirements**: 15-30 searches enforce comprehensive coverage
3. **Date Formatting Discipline**: ISO standard prevents ambiguity
4. **Financial Unit Consistency**: M/B notation aligns with industry standards
5. **12-Month Horizons**: Practical for investment decisions

---

## PART 2: CRITICAL WEAKNESSES & SOLUTIONS

### 2.1 Biotech-Specific Gaps

#### **PROBLEM 1: Endpoint Heterogeneity**
Biotech trials use vastly different endpoints (OS, PFS, ORR, biomarkers, symptom scores). Your current framework treats all equally.

**SOLUTION - Endpoint Hierarchy Framework:**
```markdown
PRIMARY ENDPOINTS BY INDICATION:
Oncology:
- Registrational: OS > PFS > ORR (with DOR)
- Early stage: ORR, disease control rate
- Citation must include: HR, CI, p-value, median follow-up

Rare Disease:
- Functional: 6MWT, FVC, motor scores
- Biomarker: enzyme levels, substrate reduction
- Citation must include: baseline, % change, clinical meaningfulness

CNS:
- Cognitive: ADAS-Cog, CDR-SB, MMSE
- Psychiatric: PANSS, MADRS, HAM-D
- Citation must include: MCID, effect size, NNT
```

#### **PROBLEM 2: Platform vs Single-Asset Companies**
Platform companies (like Moderna, BioNTech) need different analysis than single-asset biotechs.

**SOLUTION - Company Type Classifier:**
```markdown
IF platform_company:
  - Add "Platform Technology" section before Pipeline
  - Include: validation studies, partnership deals, manufacturing capacity
  - Expand competitive analysis to platform level
ELSE:
  - Deep dive on single asset
  - Include backup compounds if available
  - Focus on market exclusivity period
```

#### **PROBLEM 3: Combination Therapy Complexity**
Many biotech drugs are tested/approved as combinations, complicating efficacy attribution.

**SOLUTION - Combo Therapy Framework:**
```markdown
For combination trials:
- Clearly state: [Drug] + [Partner Drug/SOC]
- Include monotherapy data if available
- Contribution analysis: synergy vs additive
- Commercial rights: who owns what percentage
- Pricing implications: combined vs separate
```

### 2.2 Financial Analysis Gaps

#### **PROBLEM 4: No Valuation Guidance**
Dossiers lack systematic valuation approach for different development stages.

**SOLUTION - Stage-Adjusted Valuation Framework:**
```markdown
Phase 1: Focus on platform validation, partnership potential
Phase 2: PoC value, competitive positioning
Phase 3: DCF with probability-adjusted scenarios
Commercial: Revenue multiples, market share trajectory
```

#### **PROBLEM 5: Limited Risk Quantification**
Bull/bear points are qualitative; investors need quantified risks.

**SOLUTION - Risk Scoring Matrix:**
```markdown
Each risk gets scored 1-5:
- Probability (1=unlikely, 5=highly likely)
- Impact (1=minimal, 5=company-ending)
- Timeframe (1=>2 years, 5=<6 months)
Total Risk Score = Probability × Impact × (6-Timeframe)
```

### 2.3 Regulatory Complexity

#### **PROBLEM 6: Regulatory Pathway Nuance**
Not all FDA approvals are equal (full vs accelerated, orphan designation, breakthrough therapy).

**SOLUTION - Regulatory Status Classifier:**
```markdown
For each program, specify:
- Pathway: 505(b)(1) new drug / 505(b)(2) / Biosimilar / BLA
- Designations: Orphan / Breakthrough / Fast Track / Priority Review
- Approval type sought: Full / Accelerated (with confirmatory trial status)
- Geographic strategy: US first / Parallel US-EU / Asia inclusion
```

### 2.4 Competitive Intelligence Weaknesses

#### **PROBLEM 7: Static Competitor Analysis**
Current prompt captures current state but misses competitive dynamics.

**SOLUTION - Dynamic Competitive Framework:**
```markdown
For each competitor:
- Current: phase, efficacy, safety
- Timeline: expected approval, launch timing
- Differentiation: efficacy delta, dosing advantage, safety profile
- Commercial: pricing strategy, payer coverage
- Future threats: next-gen programs, biosimilar risk
```

---

## PART 3: IMPLEMENTATION IMPROVEMENTS

### 3.1 Enhanced biotech-investment-dossier Prompt Additions

Add these sections to your biotech-investment-dossier prompt:

```markdown
## BIOTECH-SPECIFIC REQUIREMENTS

### Clinical Trial Intelligence
- For pivotal trials: enrollment rate, site distribution, protocol amendments
- Statistical design: superiority/non-inferiority, sample size, power
- DMC recommendations if public
- Crossover allowance and impact on OS

### Manufacturing & Supply Chain
- Drug substance: in-house vs CMO
- Commercial readiness: capacity, tech transfer status
- Supply agreements: exclusive vs multi-source
- For biologics: comparability studies, facility inspections

### Intellectual Property Assessment
- Composition of matter patents: expiry dates by geography
- Method patents: manufacturing, formulation, combination
- Data exclusivity periods: NCE, orphan, pediatric
- Biosimilar/generic threat timeline

### Payer & Market Access
- Anticipated pricing: US list price, EU reference pricing
- Reimbursement strategy: buy-and-bill vs specialty pharmacy
- ICER assessment status
- Competitive contracting dynamics
```

### 3.2 Enhanced biotech-dossier-qc-auditor Prompt Additions

Strengthen your audit agent with:

```markdown
## BIOTECH-SPECIFIC AUDIT CHECKS

### Clinical Data Verification
- Verify primary endpoint definition matches trial protocol
- Cross-check safety data with FDA adverse event database
- Confirm patient numbers: ITT vs PP vs safety population
- Validate statistical significance: one-sided vs two-sided p-values

### Regulatory Timeline Validation
- PDUFA dates: verify against FDA calendar
- Advisory committee: check if scheduled/required
- Manufacturing inspections: PAI status
- Label negotiations: any restrictions likely?

### Financial Sustainability Check
- Cash runway vs next catalyst
- Dilution risk score: warrant overhang, ATM remaining
- Partnership dependencies: milestone triggers, royalty stacking
- Going concern warnings in filings
```

---

## PART 4: CHATGPT 5 PRO ADAPTATION CHALLENGES

### 4.1 Key Differences to Address

1. **No WebSearch**: GPT-5 Pro lacks real-time search
   - Solution: Pre-fetch source documents
   - Create source packages by company

2. **Token Limitations**: GPT may have different limits than Claude
   - Solution: Modular prompts (financial, clinical, competitive)
   - Chain outputs programmatically

3. **Citation Handling**: GPT processes citations differently
   - Solution: Explicit citation format training
   - Few-shot examples mandatory

4. **Consistency**: GPT more prone to format drift
   - Solution: Stronger structural enforcement
   - Regular calibration checks

### 4.2 Migration Strategy

```python
# Pseudo-code for GPT-5 Pro adaptation
def adapt_prompt_for_gpt5(original_prompt):
    gpt5_prompt = original_prompt
    gpt5_prompt = add_explicit_examples(gpt5_prompt, n=3)
    gpt5_prompt = strengthen_format_requirements(gpt5_prompt)
    gpt5_prompt = add_verification_loops(gpt5_prompt)
    gpt5_prompt = chunk_for_token_limits(gpt5_prompt)
    return gpt5_prompt
```

---

## PART 5: CRITICAL SUCCESS FACTORS

### 5.1 What Will Determine Success

1. **Source Data Quality** (40% of success)
   - Pre-curated document libraries
   - API access to primary databases
   - Real-time filing alerts

2. **Prompt Evolution** (30% of success)
   - Weekly refinement based on outputs
   - Error pattern analysis
   - Feedback loop from investment team

3. **Human-in-the-Loop** (20% of success)
   - Expert review before distribution
   - Rapid correction mechanism
   - Institutional knowledge capture

4. **Tool Integration** (10% of success)
   - CRM integration for coverage tracking
   - Portfolio management system links
   - Compliance audit trail

### 5.2 Risk Factors

**HIGH RISK**: Hallucinated clinical data → investment loss
- Mitigation: Mandatory human verification of all efficacy claims

**MEDIUM RISK**: Missed competitive threats → poor positioning
- Mitigation: Systematic competitor monitoring system

**LOW RISK**: Format inconsistencies → reduced usability
- Mitigation: Automated format validation

---

## PART 6: SPECIFIC PROMPT IMPROVEMENTS

### 6.1 biotech-investment-dossier Enhancements

```markdown
# Add after line 89 (Competitive Landscape)
- Patent & Exclusivity: composition of matter expiry, orphan exclusivity, data exclusivity periods [#]
- Manufacturing: in-house vs CMO, capacity for commercial launch, supply chain risks [#]
- Regulatory Strategy: filing timeline, approval pathway (full/accelerated), post-marketing requirements [#]
```

### 6.2 biotech-dossier-qc-auditor Enhancements

```markdown
# Add after line 108 (Sell-Side Pulse check)
H) Patent & Regulatory Verification
- Cross-check patent expiries with USPTO/EPO databases
- Verify regulatory designations against FDA database
- Confirm data exclusivity calculations

I) Trial Design Appropriateness
- Verify primary endpoint matches indication standards
- Check statistical power for commercial viability
- Assess control arm selection (placebo vs active)
```

---

## PART 7: RECOMMENDATIONS

### Immediate Actions (Week 1)
1. Add endpoint standardization framework to prompts
2. Create biotech metric glossary for team training
3. Implement platform vs single-asset classifier
4. Test enhanced prompts with 3 diverse companies

### Short-term (Month 1)
1. Build source document repository
2. Develop ChatGPT 5 Pro parallel prompts
3. Create validation checklist for human reviewers
4. Establish error tracking system

### Medium-term (Quarter 1)
1. API integrations with primary databases
2. Automated competitive monitoring
3. ML-based hallucination detection
4. ROI measurement framework

### Long-term (Year 1)
1. Full automation of standard coverage
2. Predictive analytics integration
3. Natural language querying of dossier database
4. Real-time alert system for material changes

---

## APPENDIX A: Biotech Complexity Examples

### Example 1: CAR-T Therapy Challenges
- Manufacturing is patient-specific
- Efficacy: ORR vs durability of response
- Safety: CRS, ICANS grading systems
- Commercial: slot availability, vein-to-vein time
- Competition: allogeneic vs autologous

### Example 2: Gene Therapy Nuances
- One-time treatment pricing models
- Durability uncertainty
- Manufacturing capacity constraints
- Payer outcomes-based agreements
- Redosing possibilities

### Example 3: Biosimilar Complications
- Interchangeability designation importance
- Formulary positioning vs reference product
- Manufacturing cost advantages
- Patent dance outcomes
- Emerging market opportunities

---

## APPENDIX B: Success Metrics

### Quantitative KPIs
- Time to dossier: <4 hours → <30 minutes
- Error rate: <5% factual errors
- Coverage expansion: 20 → 100+ companies
- Update frequency: Quarterly → Monthly → Real-time

### Qualitative KPIs
- Investment team confidence score
- Regulatory filing citation rate
- Client feedback ratings
- Competitive intelligence value

---

## CONCLUSION

Your prompt engineering foundation is strong, particularly in citation rigor and quality control architecture. The primary enhancement opportunity lies in biotech-specific frameworks that handle the sector's inherent complexity. The dual-agent approach is innovative and scalable.

Focus immediate efforts on:
1. Endpoint standardization
2. Platform classification
3. ChatGPT 5 Pro adaptation
4. Source repository building

With these enhancements, your system can become the industry standard for AI-driven biotech investment analysis.

---

*End of Critical Analysis Document*
*Next: Implementation Roadmap*