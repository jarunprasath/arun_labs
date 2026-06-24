# STAR Story Bank & Coaching Rules

## STAR Framework for Aerospace V&V Interviews

### Structure
- **S**ituation: 2 sentences — set the scene, the stakes, the domain context
- **T**ask: 1 sentence — your specific responsibility
- **A**ction: 3–5 bullet points — what YOU did (not the team), technically specific
- **R**esult: Quantified where possible — defects found, time saved, risk reduction, certification outcome

### Rules
1. **Never name the company** — use descriptive substitutes (see below)
2. **Use aerospace/DO terminology naturally** — show familiarity with the standard
3. **First person, not team** — "I identified", "I proposed", "I developed"
4. **Quantify** — "reduced regression time by 40%", "found 17 of 23 critical defects pre-integration", "0 findings at SOI-3"
5. **End with impact** — what changed because of your action

### Company Substitutes
| Real Company | Use Instead |
|-------------|-------------|
| Honeywell | "a Tier-1 avionics OEM" or "an avionics cockpit systems programme" |
| Lilium | "an eVTOL propulsion programme" or "a novel electric propulsion control system" |
| EUMETSAT | "a European space agency" or "a satellite ground segment IVV programme" |
| Accord Software | "an avionics V&V services company" |

---

## Story Bank

### Story 1 — DO-178C Level A/B Structural Coverage Gap (Honeywell context)

**Category:** Problem solving, attention to detail, verification rigour

**Situation:** During Level B verification of a flight management system module, structural coverage analysis using VectorCAST revealed 12% of decision branches in the navigation computation logic were not covered by the existing test suite.

**Task:** As verification engineer, I was responsible for achieving decision coverage compliance per DO-178C §6.4.4.2.b before the SOI-3 audit.

**Actions:**
- Analysed each uncovered branch using the LDRA Testbed report to classify as dead code, deactivated code, or test gap
- Found 4 branches were genuine test gaps — added additional test cases covering boundary conditions
- Identified 3 branches as compiler-generated defensive code — prepared justification per DO-178C §6.4.4.3 for DER review
- Coordinated with the software development team to confirm 2 branches as unreachable (dead code) and had them removed from the build
- Documented all findings and resolutions in the verification problem report system per §11.5

**Result:** Achieved 100% decision coverage compliance. 0 open findings at SOI-3 structural coverage review. The DER accepted the dead code justification without further query, setting a template reused across 3 subsequent LRUs on the same programme.

---

### Story 2 — DOORS/DXL Automation for Requirements Traceability (Honeywell context)

**Category:** Initiative, tooling, efficiency improvement

**Situation:** A mid-programme requirements update on an avionics cockpit systems project introduced 340 new or modified HLRs, requiring manual re-verification of traceability links to LLRs and test cases in DOORS — a process estimated at 3 weeks of manual effort.

**Task:** I was asked to assess whether the traceability update could be accelerated to meet the SOI-2 schedule.

**Actions:**
- Developed a DXL script that parsed the modified HLR attribute and automatically flagged all downstream LLRs and test cases requiring review
- Added link validity checking to identify broken traceability chains (orphaned requirements)
- Generated a structured report sorted by verification engineer, enabling parallel team assignment
- Validated the script output against 20 manually traced requirements before full rollout

**Result:** Reduced traceability update effort from 3 weeks to 4 days. Identified 23 orphaned test case links that would not have been caught before SOI-2. Script became part of the programme's standard CM toolkit.

---

### Story 3 — dSPACE HIL Integration Test Discovery (Honeywell context)

**Category:** Technical depth, system integration, V&V effectiveness

**Situation:** During integration testing of an environmental control system controller on a dSPACE HIL test bench, a fault injection test scenario revealed inconsistent response behaviour that did not match the LLR specification — the unit passed the normal range tests but failed only under a specific sensor fault combination.

**Task:** As the HIL test engineer, I was responsible for investigating, documenting, and driving resolution of the anomaly per the problem report process.

**Actions:**
- Reproduced the issue in 3 consecutive test runs to confirm it was deterministic, not a bench artefact
- Traced the fault to an incorrect priority assignment in the multi-sensor voting logic — a derived requirement (DO-178C §5.1.1.d) that had not been captured during design
- Raised a problem report per §8 and coordinated with the software design lead to update the LLR and regenerate code
- Re-ran the full fault injection matrix after the fix to verify no regression

**Result:** Resolved a Level C safety-significant defect before aircraft integration. The root cause analysis was used in a lessons-learned review that updated the sensor voting design guidance for subsequent LRU programmes.

---

### Story 4 — eVTOL ECU/SCU Verification Strategy (Lilium context)

**Category:** Adaptability, novel domain, applying DO-178C to non-traditional architecture

**Situation:** Joining an eVTOL propulsion programme, the existing V&V strategy was inherited from conventional avionics practice, but the propulsion controller architecture (36 motor controllers on distributed CAN) presented structural coverage challenges not covered by existing test procedures.

**Task:** I was tasked with reviewing and updating the verification strategy to ensure DO-178C compliance for the novel distributed propulsion control software.

**Actions:**
- Mapped the distributed controller architecture against DO-178C §6.4 to identify where integration-level testing was necessary vs unit test
- Identified 3 timing-dependent failure modes that could only be exposed at integration level (not unit test) due to CAN bus arbitration
- Proposed an augmented test suite including timing injection and bus load scenarios to supplement MC/DC unit coverage
- Coordinated with the systems team to ensure derived requirements from the distributed architecture were fed back into the PSSA per ARP4754A §5.3.2

**Result:** Verification strategy accepted by the DER at SOI-1 review. Identified 2 previously undetected timing race conditions during integration testing that were safety-significant.

---

### Story 5 — EUMETSAT ECSS IVV Test Execution and Reporting (EUMETSAT context)

**Category:** Process discipline, large-scale IVV, cross-domain leadership

**Situation:** As Test Conductor on a satellite ground segment IVV programme, I was responsible for planning and executing a series of system-level validation campaigns for PDAP data processing chains against ECSS-E-ST-10-03C test requirements.

**Task:** Coordinate test execution across 5 teams and 3 external facilities, ensuring test evidence met the IVV close-out criteria.

**Actions:**
- Developed a test execution schedule mapping to the IVV master test plan, coordinating dependencies across facilities
- Automated timeliness and completeness monitoring using Python scripts to detect processing delays before they became NCRs
- Maintained the test incident database, classifying and escalating anomalies per the ECSS problem report process
- Presented daily status to programme management, translating technical test results into risk-rated programme impact

**Result:** Completed the planned IVV campaign on schedule, with 94% of test procedures passing first time. 3 system anomalies discovered and resolved before formal review. Automation tooling reduced daily reporting effort from 2 hours to 15 minutes.

---

### Story 6 — VectorCAST Unit Test Suite Development (Honeywell context)

**Category:** Tool expertise, unit testing, DO-178C §6.4

**Situation:** Tasked with developing the unit test suite for a new navigation computation module being integrated into an avionics FMS at Level B.

**Task:** Achieve full statement and decision coverage, and achieve MC/DC compliance on all boolean expressions per DO-178C §6.4.4.2.c.

**Actions:**
- Analysed the source code to identify all decision points and boolean expressions requiring MC/DC test cases
- Developed test cases in VectorCAST using the MC/DC analysis feature to confirm independence of conditions
- Identified 2 instances of masking (short-circuit evaluation) and designed test cases specifically to unmask each condition
- Ran structural coverage report and achieved 100% statement, 100% decision, and 100% MC/DC coverage
- Peer-reviewed test cases with an independent verifier per §2.5 independence requirement at Level B

**Result:** Unit test suite accepted with zero findings at Level B review. Coverage report submitted as §11.13/11.14 evidence. The masking analysis approach was shared across the verification team as a practice guide.

---

## Behavioural Question Mapping

| Question | Best Story | Key STAR elements to emphasise |
|----------|-----------|-------------------------------|
| Tell me about a time you found a critical defect | Story 3 (HIL) | Technical investigation, PR process, safety significance |
| Describe an improvement you made to a process | Story 2 (DOORS/DXL) | Initiative, tooling, quantified time saving |
| How do you handle an unfamiliar technical domain? | Story 4 (eVTOL) | DO-178C mapping to novel architecture |
| Tell me about a complex stakeholder situation | Story 5 (EUMETSAT) | Multi-team coordination, technical communication |
| How do you ensure compliance under schedule pressure? | Story 1 (Coverage) | Systematic analysis, DER engagement, zero findings |
| Describe your approach to test strategy | Story 4 or 6 | Structured V&V, coverage targets, independence |

---

## Common Interview Behavioural Questions — Aerospace V&V

1. "Tell me about a time you identified a defect that others had missed."
2. "Describe a situation where you had to challenge a design decision from a V&V perspective."
3. "How have you managed a V&V activity under tight schedule pressure without compromising standards compliance?"
4. "Tell me about a time you worked with a certification authority or DER."
5. "Describe your approach to test case design for safety-critical software."
6. "Tell me about a time you had to learn a new domain or standard quickly."
7. "How do you ensure traceability from requirements to test evidence?"
8. "Describe a time when your testing found a system-level issue, not just a software bug."
9. "How have you used automation in V&V activities?"
10. "Tell me about a programme where you were involved from requirements through certification."

---

## STAR Coaching Rules (apply in every session)

1. If Arun gives a story without quantified results → ask: "Can you put a number on the outcome?"
2. If Arun uses "we" → redirect: "What specifically did YOU do?"
3. If Arun names the company → flag: "Remove the company name — use the substitute"
4. If the situation is too long → trim to 2 sentences maximum
5. If no standard is cited in a technical story → add one: "Which DO section/objective does this relate to?"
6. If the story doesn't match the company's domain → re-tailor the vocabulary
7. Always end coaching with: "Now say it again, in 90 seconds, without notes."
