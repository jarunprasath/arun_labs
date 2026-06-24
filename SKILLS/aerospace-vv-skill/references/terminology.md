# Terminology, Citation Rules & Common Mistakes

## The Golden Rules — Apply in Every Response

These rules were established through repeated review of Arun's preferred standards-compliant language. Apply without exception.

---

## CORRECT vs FORBIDDEN Terminology

### Software Assurance Levels

| CORRECT | FORBIDDEN | Standard Basis |
|---------|-----------|---------------|
| "software Level A" | "DAL A software" | DO-178C §2.2 uses "Level" not "DAL" |
| "software Level B" | "Level B DAL" | same |
| "Level A objectives" | "DAL objectives" | DO-178C Table A-1 heading |
| "software Level A system" | "DAL A project" | consistent with §2.2 |

**Why it matters:** DO-178C §2.2 defines "software level" — the term DAL appears in DO-178C but as a general concept from ARP4754A. Saying "DAL A software" conflates the ARP4754A allocation with the DO-178C assignment. In a DER review or SOI audit, imprecise use of level terminology signals shallow standards familiarity.

### FDAL vs IDAL vs DAL

| Term | Correct context | Standard |
|------|----------------|---------|
| FDAL | Functional Development Assurance Level — assigned to an aircraft **function** | ARP4754A §5.1.1 |
| IDAL | Item Development Assurance Level — assigned to a **system item** (LRU, SW, HW) | ARP4754A §5.1.2 |
| DAL | Development Assurance Level — generic term, or used in DO-178C/DO-254 directly | DO-178C §2.2, DO-254 |

**NEVER say:** "The FDAL of the software is A" — software has an IDAL (which maps to DO-178C software level).  
**CORRECT:** "The function has FDAL A; the software item implementing it was allocated IDAL A, which maps to DO-178C Level A."

### Process Terminology

| CORRECT | FORBIDDEN | Standard Basis |
|---------|-----------|---------------|
| "transition criteria" | "exit criteria" | DO-178C §4.1 — standard uses transition criteria |
| "verification objectives" | "test objectives" | DO-178C §6 — verification includes reviews, analysis, and tests |
| "structural coverage" | "code coverage" | DO-178C §6.4.4 — code coverage is informal, non-standard |
| "problem report" | "bug", "defect", "issue", "ticket" | DO-178C §8, §11.5 |
| "Software Accomplishment Summary (SAS)" | "compliance report", "closure report" | DO-178C §11.20 |
| "Plan for Software Aspects of Certification (PSAC)" | "certification plan" | DO-178C §11.1 |
| "independence" | "separation of duties" | DO-178C §2.5 — uses "independence" specifically |
| "derived requirements" | "additional requirements", "implicit requirements" | DO-178C §5.1.1.d |
| "deactivated code" | "conditional code", "ifdef'd code" | DO-178C §2.4 — specific defined term |

---

## Citation Format Rules

### Format
`Standard §Section[.Subsection] [Table X] [Objective N]`

### Examples by standard

**DO-178C:**
- `DO-178C §6.4.4.2.c` — MC/DC requirement
- `DO-178C §2.5` — independence definition
- `DO-178C §11.1` — PSAC
- `DO-178C Table A-4, Objective 5` — specific verification objective
- `DO-178C §6.3.1` — review of high-level requirements

**ARP4754A:**
- `ARP4754A §5.1.1` — FDAL assignment
- `ARP4754A §5.1.2` — IDAL assignment
- `ARP4754A §5.2` — PSSA process
- `ARP4754A Table 3` — FDAL to IDAL mapping with independence

**DO-254:**
- `DO-254 §5.2.1` — hardware requirements process
- `DO-254 §6.2` — elemental analysis
- `DO-254 §10.1` — PHAC

**DO-160G:**
- `DO-160G §4` — temperature/altitude
- `DO-160G §22` — lightning induced transients
- `DO-160G §8` — vibration

**DO-326A:**
- `DO-326A §4` — airworthiness security process overview
- `DO-326A §5` — threat condition assessment

**ECSS:**
- `ECSS-E-ST-10-02C §5.3` — verification process
- `ECSS-E-ST-10-03C §4.2` — test requirements

### Rule: Every substantive technical claim requires a citation
If you state a fact about a standard's requirement, cite it. If you cannot cite it, qualify: "I believe this is in §X — confirm before using in interview."

---

## Common Interview Mistakes to Avoid

### Mistake 1: Conflating verification and testing
**Wrong:** "Verification is testing the software."  
**Correct:** "Verification per DO-178C §6 encompasses reviews, analyses, and tests. Testing (§6.4) is one part of verification; reviews (§6.3) and analysis are equally important and have their own objectives in Tables A-3, A-4, A-5."

### Mistake 2: Saying "we" in STAR stories
**Wrong:** "We found a coverage gap..."  
**Correct:** "I analysed the VectorCAST coverage report and identified..."

### Mistake 3: Using "exit criteria" for DO-178C phase transitions
**Wrong:** "The exit criteria for the coding phase are..."  
**Correct:** "The transition criteria (DO-178C §4.1) for moving from coding to verification include..."

### Mistake 4: Saying all structural coverage is required at all levels
**Wrong:** "DO-178C requires 100% MC/DC coverage."  
**Correct:** "MC/DC (DO-178C §6.4.4.2.c) is required at software Level A and Level B. At Level C, decision coverage (§6.4.4.2.b) is required. At Level D, structural coverage analysis is not required."

### Mistake 5: Confusing PSAC and SAS purpose
**Wrong:** "The SAS is submitted before development to agree the certification approach."  
**Correct:** "The PSAC (§11.1) is submitted to the authority before development begins — it is the agreement. The SAS (§11.20) is the final compliance summary submitted at certification closure, confirming all objectives have been met."

### Mistake 6: Tool qualification confusion
**Wrong:** "You always have to qualify your tools in DO-178C."  
**Correct:** "Tool qualification (DO-330) applies when a tool's output is used without manual verification. If the tool output is independently verified by other means, qualification may not be required. The need is assessed per DO-178C §12.2 based on the tool type (development vs verification) and the potential for undetected errors."

### Mistake 7: Independence = different company
**Wrong:** "Independence means using a separate test organisation."  
**Correct:** "Independence (DO-178C §2.5) means the reviewer did not develop the item being reviewed — it is a separation of responsibility within the programme, not necessarily a separate organisation. At Level A, testing requires an independent tester (§6.4.2 independence for test execution); at Level B, independence is required for reviews and analyses only."

---

## Industry Jargon vs Standards Terminology

| Informal (acceptable in conversation) | Formal (use in interview / documentation) |
|---------------------------------------|------------------------------------------|
| "box" | LRU (Line Replaceable Unit) |
| "code coverage" | structural coverage |
| "V&V" | verification and validation (or "verification" alone in DO-178C context) |
| "sign off" | close (problem report), approve (artifact) |
| "audit" | SOI (Stage of Involvement) in certification context |
| "DER sign-off" | DER approval / finding of compliance |
| "test plan" | Software Verification Plan (SVP, §11.3) |
| "bug" | problem report (PR) |
| "regression" | re-verification after change |
| "delta review" | impact analysis + change verification |
| "pass/fail" | test case result (pass = meets acceptance criteria) |

---

## ECSS ↔ DO-178C Bridging (for OHB / space interviews)

When talking to space companies, bridge ECSS experience to DO-178C vocabulary:

| ECSS Concept | DO-178C Equivalent | Notes |
|-------------|-------------------|-------|
| Verification Matrix | Requirements Traceability Matrix | ECSS ECSS-E-ST-10-02C §5.4 |
| Test Specification | Software Verification Cases & Procedures §11.13 | similar purpose |
| Non-Conformance Report (NCR) | Problem Report (PR) §11.5 | different threshold for raising |
| Review Item Discrepancy (RID) | Problem Report (review finding) | ECSS uses RID at reviews |
| RID dispositions (A/B/C/D) | Problem report resolution | ECSS categorises by dispositioner |
| Inspection | Review (DO-178C §6.3) | both involve independent checking |
| MRR / PDR / CDR / QR | SOI 1/2/3/4 (approximate mapping) | milestone = assurance gate |
| SVVP | SVP (Software Verification Plan) | same intent |
| DRD (Data Requirement Description) | DO-178C §11 lifecycle data items | list of required outputs |

**Key message for space company interviews:** "My EUMETSAT IVV background maps directly — ECSS verification philosophy (review-heavy, evidence-driven, milestone-gated) is structurally similar to DO-178C, with different terminology. I've bridged the two in practice and can operate in either framework."
