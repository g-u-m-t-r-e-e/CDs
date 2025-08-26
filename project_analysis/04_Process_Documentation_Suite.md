# Process Documentation Suite
*Standard Operating Procedures for AI-Driven Biotech Investment Analysis*
*Version 1.0 | Compliance Approved*

---

# PART 1: STANDARD OPERATING PROCEDURES (SOPs)

## SOP-001: Company Dossier Generation

### Purpose
Standardize the creation of AI-generated company dossiers to ensure consistency, accuracy, and compliance with investment guidelines.

### Scope
All biotech/pharmaceutical companies under coverage or consideration for investment.

### Procedure

#### Step 1: Pre-Generation Checklist
```markdown
BEFORE STARTING:
□ Company ticker verified in Bloomberg
□ Recent material events checked (last 48 hours)
□ Existing coverage reviewed (avoid duplication)
□ Compliance clearance confirmed (if needed)
□ Source documents gathered:
  □ Latest 10-K/10-Q
  □ Recent press releases
  □ Clinical trial updates
  □ Competitor news
```

#### Step 2: Input Preparation
```python
# Standard input template
dossier_request = {
    "ticker": "XXXX",
    "company_name": "Full Legal Name",
    "focus_areas": [
        "lead_program_update",
        "competitive_positioning",
        "financial_runway",
        "upcoming_catalysts"
    ],
    "cutoff_date": "YYYY-MM-DD",
    "urgency": "standard|high|critical",
    "distribution": ["internal", "client_facing"]
}
```

#### Step 3: Generation Process
1. **Initial Generation** (ChatGPT 5 Pro)
   - Copy enhanced biotech-investment-dossier prompt
   - Input company parameters
   - Generate initial dossier
   - Save to `/drafts` folder

2. **Quality Check** (Automated)
   ```bash
   python qc_check.py --file "drafts/Company_Dossier.md"
   ```

3. **Audit Process** (Claude CLI)
   ```bash
   /task biotech-dossier-qc-auditor "Audit [Company] dossier"
   ```

#### Step 4: Human Review
| Review Level | Criteria | Reviewer | Time Limit |
|--------------|----------|----------|------------|
| Level 1 | Standard companies | Analyst | 30 min |
| Level 2 | High-profile/volatile | Senior Analyst | 45 min |
| Level 3 | Client-facing | Portfolio Manager | 60 min |

#### Step 5: Distribution
```markdown
DISTRIBUTION CHECKLIST:
□ Compliance disclaimer added
□ AI-generation disclosed
□ Version control number assigned
□ Distribution list confirmed
□ Archive copy saved
```

### Quality Metrics
- Accuracy Rate: >95%
- Generation Time: <4 hours
- Review Time: <1 hour
- Error Rate: <5%

---

## SOP-002: Source Verification Protocol

### Purpose
Ensure all quantitative claims in dossiers are supported by verifiable primary sources.

### Critical Verification Points

#### Financial Data
```markdown
VERIFICATION HIERARCHY:
1. SEC Filings (10-K, 10-Q, 8-K) - REQUIRED
2. Earnings Call Transcripts - SUPPLEMENTARY
3. Company Presentations - REFERENCE ONLY
4. News Articles - NOT ACCEPTABLE for numbers

SPECIFIC CHECKS:
- Cash position: Latest filing, Note X (usually Note 2-4)
- Burn rate: Calculate from cash flow statement
- Debt: Balance sheet + notes on credit facilities
- Share count: Cover page of 10-Q/K
```

#### Clinical Data
```markdown
PRIMARY SOURCES ONLY:
1. ClinicalTrials.gov - trial design, enrollment
2. FDA.gov - approvals, CRLs, labels
3. Published papers - efficacy/safety data
4. Conference presentations - with slides

VERIFICATION PROCESS:
- Cross-reference trial ID (NCT#)
- Match patient numbers (ITT vs PP)
- Verify statistical significance
- Confirm endpoint definitions
```

### Red Flag Escalation
| Issue | Action | Escalation |
|-------|--------|------------|
| Source not found | Mark "UNVERIFIED" | Immediate |
| Numbers don't match | Investigate discrepancy | Within 1 hour |
| Outdated information | Update required | Before distribution |
| Material error found | Stop distribution | Immediate to PM |

---

## SOP-003: Update Cycle Management

### Routine Updates
| Company Category | Update Frequency | Trigger Events |
|-----------------|------------------|----------------|
| Portfolio Holdings | Weekly | Any material event |
| Watch List | Bi-weekly | Price movement >10% |
| Coverage Universe | Monthly | Earnings/data |
| Sector Review | Quarterly | Systematic |

### Event-Driven Updates
```python
def requires_immediate_update(event):
    critical_events = [
        'clinical_trial_results',
        'fda_decision',
        'merger_announcement',
        'safety_issue',
        'management_change_ceo_cmo',
        'financing_>100M'
    ]
    
    if event.type in critical_events:
        return True
    elif event.stock_move > 0.20:  # 20% move
        return True
    else:
        return False
```

### Update Process
1. **Incremental Update** (Preferred)
   - Pull existing dossier
   - Update affected sections only
   - Maintain version history
   - Flag changes clearly

2. **Full Regeneration** (When needed)
   - Major structural changes
   - Multiple sections affected
   - >6 months since last full update

---

# PART 2: TRAINING MATERIALS

## Module 1: Understanding AI-Generated Content

### Learning Objectives
After this module, participants will:
- Understand capabilities and limitations of AI analysis
- Identify potential hallucination patterns
- Know when human intervention is required
- Apply verification techniques

### Key Concepts

#### AI Strengths vs Weaknesses
| Strengths | Weaknesses |
|-----------|------------|
| Rapid processing | Hallucination risk |
| Consistent format | Context limitations |
| Comprehensive coverage | Nuance understanding |
| Citation tracking | Real-time data gaps |
| Pattern recognition | Causation vs correlation |

#### Hallucination Detection
```markdown
WARNING SIGNS:
1. Unusually specific numbers (e.g., 47.3% when 45-50% expected)
2. Future dates stated as fact
3. Contradictions within document
4. Claims without citations
5. Technical terms used incorrectly

VERIFICATION STEPS:
1. Check primary source
2. Cross-reference with known facts
3. Apply reasonableness test
4. Verify with second source
5. When in doubt, mark as uncertain
```

### Practical Exercise 1
```markdown
SCENARIO: AI generates "Phase 3 trial showed 67% ORR"

YOUR TASK:
1. Find the primary source
2. Verify the number
3. Check trial design (single-arm vs controlled)
4. Confirm endpoint definition
5. Document your findings

ANSWER KEY:
- Check ClinicalTrials.gov for trial design
- Find company press release for results
- Verify in conference presentation
- Note: ORR may be investigator vs IRC assessed
```

---

## Module 2: Prompt Engineering for Finance Professionals

### Core Principles
1. **Specificity**: Exact requirements prevent ambiguity
2. **Structure**: Format specifications ensure consistency
3. **Constraints**: Limitations improve accuracy
4. **Examples**: Few-shot learning enhances output
5. **Verification**: Built-in checks catch errors

### Prompt Anatomy
```markdown
EFFECTIVE PROMPT STRUCTURE:

1. ROLE DEFINITION
"You are a senior biotech analyst..."

2. TASK SPECIFICATION
"Create an investment dossier for [COMPANY]..."

3. OUTPUT REQUIREMENTS
"Include these exact sections in this order..."

4. CONSTRAINTS
"Only use primary sources for numbers..."

5. QUALITY CHECKS
"Verify all claims against sources..."

6. FORMAT SPECIFICATION
"Output as markdown with tables..."
```

### Common Pitfalls
| Pitfall | Example | Solution |
|---------|---------|----------|
| Too vague | "Analyze this company" | Specify exact requirements |
| No constraints | "Tell me everything" | Set boundaries |
| Missing format | "Write a report" | Define structure |
| No verification | "What's the revenue?" | Request source citation |

### Practical Exercise 2
```markdown
TASK: Write a prompt for competitive analysis

REQUIREMENTS:
- Compare 3 direct competitors
- Focus on clinical programs
- Include market share estimates
- Cite all sources

YOUR PROMPT:
[Space for participant to write]

MODEL ANSWER:
"As a biotech equity analyst, create a competitive analysis table comparing [COMPANY] with its top 3 direct competitors in [INDICATION]. For each company include: 1) Lead program name and phase, 2) Key efficacy data with primary endpoint, 3) Estimated market share at peak, 4) Key differentiation. Cite primary sources [#] for all clinical data. Format as markdown table."
```

---

## Module 3: Quality Control & Verification

### QC Framework
```python
class DossierQualityControl:
    def __init__(self, dossier):
        self.dossier = dossier
        self.errors = []
        
    def check_structure(self):
        required_sections = [
            'Executive Summary',
            'Key developments',
            'Catalysts',
            'Programs / Pipeline',
            'Financials',
            'Bull / Bear Views'
        ]
        for section in required_sections:
            if section not in self.dossier:
                self.errors.append(f"Missing section: {section}")
    
    def check_citations(self):
        # Find all numbers
        numbers = re.findall(r'\d+\.?\d*[%MBK]?', self.dossier)
        for number in numbers:
            # Check if followed by citation [#]
            if not re.search(f'{number}.*?\[\d+\]', self.dossier):
                self.errors.append(f"Uncited number: {number}")
    
    def check_dates(self):
        # Verify date formats
        dates = re.findall(r'\d{4}-\d{2}-\d{2}', self.dossier)
        for date in dates:
            if not self.valid_date(date):
                self.errors.append(f"Invalid date: {date}")
```

### Verification Checklist
```markdown
EVERY DOSSIER MUST PASS:

STRUCTURAL CHECKS:
□ All 9 sections present
□ Tables properly formatted
□ Headers correctly numbered
□ Citations sequential

DATA CHECKS:
□ Financial numbers from latest filing
□ Clinical data matches source
□ Dates within correct windows
□ Competitive data current

LOGICAL CHECKS:
□ Bull/bear points balanced
□ Cash runway calculation correct
□ Market size reasonable
□ Timeline achievable

COMPLIANCE CHECKS:
□ Disclaimers included
□ AI generation disclosed
□ Sources accessible
□ No forward-looking statements beyond company guidance
```

---

# PART 3: TEAM ROLES & RESPONSIBILITIES

## Role Matrix

| Role | Primary Duties | Dossier Responsibilities | Escalation Path |
|------|---------------|-------------------------|-----------------|
| Analyst | Generate dossiers | Create, basic QC | Senior Analyst |
| Senior Analyst | Review & verify | Detailed review, approve | Portfolio Manager |
| Portfolio Manager | Final approval | Strategic review, client-facing | CIO |
| Compliance | Regulatory check | Disclaimer, risk review | CCO |
| IT Support | Technical issues | System maintenance | IT Manager |

## RACI Matrix for Dossier Process

| Activity | Responsible | Accountable | Consulted | Informed |
|----------|------------|-------------|-----------|----------|
| Generation | Analyst | Sr. Analyst | PM | Team |
| QC Check | Analyst | Sr. Analyst | - | PM |
| Review | Sr. Analyst | PM | Compliance | Team |
| Approval | PM | PM | CIO | Compliance |
| Distribution | Analyst | Sr. Analyst | - | Recipients |
| Updates | Analyst | Sr. Analyst | PM | Team |

---

# PART 4: PERFORMANCE METRICS & KPIs

## Individual Metrics

### Analyst Level
```python
analyst_kpis = {
    'quantity': {
        'dossiers_per_week': 5,
        'updates_per_week': 10,
        'coverage_expansion': 2  # New companies/month
    },
    'quality': {
        'error_rate': '<5%',
        'revision_rate': '<10%',
        'citation_compliance': '>95%'
    },
    'efficiency': {
        'time_per_dossier': '<4 hours',
        'time_per_update': '<1 hour',
        'automation_usage': '>80%'
    }
}
```

### Team Level
| Metric | Target | Current | Status |
|--------|--------|---------|--------|
| Coverage | 100 companies | 20 | 🔴 |
| Update frequency | Weekly | Monthly | 🟡 |
| Client satisfaction | >4.5/5 | N/A | ⚫ |
| Cost per dossier | <€100 | €500 | 🔴 |
| ROI | 5x | 1x | 🔴 |

## Quality Scorecard

```markdown
SCORING RUBRIC (100 points total):

ACCURACY (40 points)
- Financial data correct: 15 pts
- Clinical data correct: 15 pts
- Dates/timelines accurate: 10 pts

COMPLETENESS (30 points)
- All sections present: 10 pts
- Competitive analysis: 10 pts
- Risk factors covered: 10 pts

FORMAT (20 points)
- Structure compliance: 10 pts
- Citation format: 5 pts
- Table formatting: 5 pts

TIMELINESS (10 points)
- Delivered on schedule: 5 pts
- Incorporates latest data: 5 pts

GRADING:
90-100: Excellent
80-89: Good
70-79: Acceptable
<70: Revision required
```

---

# PART 5: TROUBLESHOOTING GUIDE

## Common Issues & Solutions

### Issue 1: AI Generates Incorrect Financial Data
```markdown
SYMPTOMS:
- Numbers don't match filings
- Outdated figures used
- Currency confusion (USD vs EUR)

DIAGNOSIS:
1. Check source document date
2. Verify filing was processed
3. Confirm currency specification

SOLUTION:
1. Update source repository
2. Specify currency in prompt
3. Add verification step
4. Re-run generation

PREVENTION:
- Maintain current source library
- Always specify "as of [date]"
- Include currency in prompt
```

### Issue 2: Formatting Breaks
```markdown
SYMPTOMS:
- Tables misaligned
- Markdown rendering issues
- Section numbering wrong

DIAGNOSIS:
- Check for special characters
- Verify markdown syntax
- Look for copy-paste errors

SOLUTION:
1. Use markdown validator
2. Clean special characters
3. Regenerate affected section

PREVENTION:
- Use standard templates
- Validate before distribution
- Test in target platform
```

### Issue 3: Competitive Analysis Gaps
```markdown
SYMPTOMS:
- Missing key competitors
- Outdated competitive data
- Wrong comparison programs

DIAGNOSIS:
- Competitor list incomplete
- Database not updated
- Indication mismatch

SOLUTION:
1. Update competitor database
2. Specify exact competitors
3. Verify indication match

PREVENTION:
- Quarterly competitor review
- Maintain competitor matrix
- Cross-reference trials database
```

---

# PART 6: COMPLIANCE & AUDIT TRAIL

## Documentation Requirements

### Required Documentation
```python
class AuditTrail:
    def __init__(self):
        self.entries = []
    
    def log_generation(self, company, user, timestamp):
        entry = {
            'action': 'GENERATE',
            'company': company,
            'user': user,
            'timestamp': timestamp,
            'prompt_version': 'v2.2',
            'model': 'GPT-5-Pro',
            'status': 'SUCCESS'
        }
        self.entries.append(entry)
    
    def log_review(self, company, reviewer, changes):
        entry = {
            'action': 'REVIEW',
            'company': company,
            'reviewer': reviewer,
            'changes': changes,
            'timestamp': datetime.now(),
            'approval': True/False
        }
        self.entries.append(entry)
    
    def generate_report(self):
        # Monthly compliance report
        return pd.DataFrame(self.entries)
```

### Retention Policy
| Document Type | Retention Period | Storage Location | Access Control |
|--------------|------------------|------------------|----------------|
| Dossiers | 7 years | Secure server | Role-based |
| Audit logs | 7 years | Compliance system | Restricted |
| Source documents | 3 years | Archive | Read-only |
| Training records | 3 years | HR system | Manager+ |

### Compliance Checklist
```markdown
BEFORE DISTRIBUTION:
□ No material non-public information (MNPI)
□ AI generation disclosed
□ Disclaimers included
□ Sources are public
□ No guarantees/promises
□ Risk factors mentioned
□ Date clearly stated
□ Version controlled

DISCLAIMER TEMPLATE:
"This document was generated with AI assistance and has been reviewed by qualified investment professionals. It is for informational purposes only and does not constitute investment advice. All data from public sources as of [DATE]. Please verify critical information independently."
```

---

# PART 7: CONTINUOUS IMPROVEMENT

## Feedback Loops

### Weekly Review Process
```markdown
MONDAY MORNING REVIEW:
1. Previous week metrics
   - Dossiers generated: #
   - Errors found: #
   - Time saved: hours
   
2. Error pattern analysis
   - Common mistakes
   - Root causes
   - Prompt adjustments needed
   
3. Process improvements
   - Bottlenecks identified
   - Solutions proposed
   - Implementation timeline
   
4. Training needs
   - Skills gaps
   - New features
   - Best practices
```

### Monthly Optimization
| Area | Review Questions | Action Items |
|------|-----------------|--------------|
| Prompts | Are outputs improving? | Refine based on errors |
| Sources | Data current and complete? | Update source library |
| Process | Any bottlenecks? | Streamline workflow |
| Training | Team confident? | Additional sessions |
| Tools | Technology working? | Upgrade/fix issues |

### Quarterly Strategic Review
1. **Coverage Analysis**
   - Companies covered vs target
   - Sector representation
   - Geographic diversity

2. **Quality Metrics**
   - Error rate trends
   - Client feedback
   - Regulatory issues

3. **Efficiency Gains**
   - Time saved
   - Cost reduction
   - ROI calculation

4. **Future Planning**
   - Expansion opportunities
   - Technology upgrades
   - Team scaling

---

# APPENDICES

## Appendix A: Template Library

### A.1 Standard Dossier Request
```markdown
TO: AI Dossier System
FROM: [Analyst Name]
DATE: [YYYY-MM-DD]
RE: Dossier Request - [COMPANY]

PARAMETERS:
- Ticker: [XXXX]
- Focus: [Pipeline update / Financial analysis / Competitive]
- Urgency: [Standard / High]
- Distribution: [Internal / Client]
- Special considerations: [Any specific requirements]

AUTHORIZATION: [Manager approval if needed]
```

### A.2 Error Report Template
```markdown
ERROR REPORT #[XXX]
Date: [YYYY-MM-DD]
Company: [Name]
Section: [Affected section]

ERROR DESCRIPTION:
[Detailed description]

IMPACT:
[Low / Medium / High]

ROOT CAUSE:
[Analysis]

CORRECTION:
[What was done]

PREVENTION:
[Future prevention measures]
```

## Appendix B: Quick Reference Cards

### B.1 Biotech Metrics Quick Reference
```
OS = Overall Survival (months)
PFS = Progression-Free Survival
ORR = Objective Response Rate (%)
DOR = Duration of Response
CR = Complete Response
PR = Partial Response
SD = Stable Disease
PD = Progressive Disease
TEAE = Treatment-Emergent Adverse Event
SAE = Serious Adverse Event
```

### B.2 Financial Metrics Quick Reference
```
EV = Enterprise Value
P/S = Price-to-Sales
EV/Sales = Enterprise Value/Sales
Burn = Quarterly cash usage
Runway = Cash / Burn rate
WACC = Weighted Average Cost of Capital
NPV = Net Present Value
rNPV = risk-adjusted NPV
```

## Appendix C: Contact Directory

| Function | Contact | Email | Phone | Escalation |
|----------|---------|-------|-------|------------|
| IT Support | [Name] | [Email] | [Ext] | IT Manager |
| Compliance | [Name] | [Email] | [Ext] | CCO |
| Training | [Name] | [Email] | [Ext] | HR |
| Project Lead | You | [Email] | [Ext] | PM |

---

*End of Process Documentation Suite*
*Version 1.0 - Living Document*
*Last Updated: 2025-08-25*
*Next Review: 2025-09-25*