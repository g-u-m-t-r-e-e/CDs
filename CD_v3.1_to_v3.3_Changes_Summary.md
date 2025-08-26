# Company Dossier v3.1 → v3.3 Changes Summary

## Overview
This document summarizes the key differences between Company Dossier prompt versions 3.1 and 3.3, based on audit feedback to improve accuracy and flexibility.

## Key Changes

### 1. Competitive Landscape (Section 4 - Programs/Pipeline)
**Issue:** Fixed limit of 3 competitors was too rigid - sometimes more are relevant, sometimes none exist.

**v3.1 (Old):**
- "for the top 3 competitors-assets each"

**v3.3 (New):**
- "Include only clinically/commercially relevant competitor-assets in the same indication/mechanism. Number may vary from 0 to multiple depending on the program."

**Impact:** Allows appropriate competitor coverage based on actual market landscape rather than forcing arbitrary number.

---

### 2. Cash Burn Reporting (Section 5 - Financials)
**Issue:** Generic "burn rate (per quarter)" caused calculation errors when companies report differently (quarterly, semi-annually, or annually).

**v3.1 (Old):**
- "Burn rate (per quarter)"

**v3.3 (New):**
- "Cash burn (latest reported period only - specify Q# YYYY, H# YYYY, or FY YYYY)"
- Added explicit note: "Report only the actual cash burn from the most recent reported period. Do not calculate averages. Specify the exact reporting period used."

**Impact:** Prevents incorrect averaging/calculations and ensures accurate reporting of actual cash burn figures.

---

### 3. Key Developments Chronological Order (Section 2)
**Issue:** No explicit ordering instruction led to inconsistent presentation.

**v3.1 (Old):**
- No ordering specification

**v3.3 (New):**
- Added "Listed in reverse chronological order (most recent first)" directly after section heading

**Impact:** Ensures consistent presentation with most relevant/recent developments appearing first.

---

## Version Reference Updates

### Header Changes
- **v3.1:** "Prompt: Company Dossier v. 3.0" (inconsistent versioning)
- **v3.3:** "Prompt: Company Dossier v. 3.3" (corrected)

### Section Numbering
- **v3.1:** Had duplicate "1)" for Executive Summary and Key developments
- **v3.3:** Corrected to proper sequential numbering (1, 2, 3...)

### Verification Checklist Updates
Added three new checklist items in v3.3:
- [ ] Competitive landscape includes only relevant competitors (may be 0 to multiple)
- [ ] Key developments in reverse chronological order  
- [ ] Cash burn from single reporting period only (not averaged)

---

## Summary of Benefits

1. **Greater Flexibility:** Competitive landscape now adapts to actual market conditions
2. **Improved Accuracy:** Cash burn reporting prevents calculation errors
3. **Better Organization:** Chronological ordering makes recent developments easier to find
4. **Consistency:** All version references now correctly show v3.3

## Implementation Notes

These changes address specific issues identified during QC audits of dossiers created with v3.1. The modifications maintain all other structural requirements while improving precision in these three critical areas.

---

*Document prepared: 2025-08-26*
*For: Company Dossier Project Team*