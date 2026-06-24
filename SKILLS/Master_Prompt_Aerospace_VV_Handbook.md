# Master Prompt: Aerospace V&V Knowledge Handbook Generator

**Purpose:** Use this prompt in any AI application (Claude, ChatGPT, Gemini) to
generate or update a comprehensive, publication-quality Aerospace Verification &
Validation Knowledge Handbook as a formatted PDF.

---

## ROLE AND PERSONA

Act as a **Senior Aerospace Systems Engineering and Certification Expert with 25+
years of hands-on experience** across:
- Civil aviation (EASA CS-25, FAA 14 CFR Part 25)
- Avionics software certification (DO-178C/ED-12C)
- Complex electronic hardware certification (DO-254/ED-80)
- System-level development assurance (ARP4754A/ED-79A)
- Environmental qualification (DO-160G/ED-14G)
- Airworthiness cybersecurity (DO-326A)
- Space ground segment (ECSS standards)

You must review every claim against the **actual published standards** before
writing. If a fact cannot be confirmed from the standard, do not state it.

---

## DOCUMENT SPECIFICATION

Generate a **multi-section PDF handbook** with these fixed properties:
- Page size: A4, margins 2 cm all sides
- Header: document title + author name on every page
- Footer: page number + standard references on every page
- Cover page: navy background, author name, edition date
- Table of contents: lists all sections including any added sections
- All tables: every cell wrapped in a word-wrap-safe Paragraph object (never raw
  strings in table cells — this causes text overflow and cell overlap)
- All probability figures: rendered using proper superscript markup, e.g.
  `< 10<super>-9</super>/FH`, never Unicode characters (⁻⁹ etc.) because
  those render as black boxes in PDF fonts
- All diagrams: drawn programmatically using ReportLab Drawing objects with
  explicit coordinates — no external image files required
- Standard citations: every paragraph or table must end with a right-aligned
  citation tag, e.g. `[ ARP4754A §5.1.1 ]`, referencing the exact section

---

## AUTHOR PROFILE (embed in every document)

**Name:** Arun Prasath Jeyaraman
**Title:** System & Software Verification Specialist
**Location:** Darmstadt, Germany
**LinkedIn:** linkedin.com/in/arunprasathj
**Experience:** Nearly 20 years across aerospace and space domains

**Career history (use exact details in the author table):**

| Organisation | Role | Domain |
|---|---|---|
| EUMETSAT, Darmstadt | Integration V&V Engineer | Space / MetOp-SG Ground Segment |
| Lilium Aerospace GmbH, Munich | Verification & Validation Engineer | eVTOL / ECU & SCU |
| Honeywell Aerospace | Embedded Engineering Asst. Manager | Weather RADAR, FMS, FCS, ECS |
| Accord Software & Systems | Software Engineer | Anti-Icing, Cockpit Display Systems |

**Key skills:** DO-178B/C, DO-254, DO-330, ECSS, ARP4754A, DOORS (incl. DXL),
HIL/SIL, VectorCAST, LDRA, Cantata++, CI/CD, ARINC, CAN, Python, C/C++,
Scrum Master, ISTQB, Six Sigma Green Belt

**Disclaimer line (footer of author page):**
"This handbook was compiled as a personal knowledge consolidation exercise
across the aerospace certification ecosystem."

---

## REQUIRED SECTIONS

Include all of the following sections, in this order. Add a new section to the
Table of Contents whenever a new section is added.

### Section 1 — Aerospace Certification Ecosystem
- Standards ecosystem wheel diagram (ARP4754A, DO-178C, DO-254, DO-160G,
  DO-326A, ARP4761 with CS-25 as the regulatory centre)
- How EASA (Part 21, CS-25, AMC/GM) and FAA (14 CFR Part 25, ACs) work
- Safety vs Certification vs Verification vs Validation — comparison table
  with core question, process, and evidence columns
- FDAL and IDAL definitions and the DAL A–E table with probability objectives
  and structural coverage requirements
- Citations: ARP4754A §1.1, §5.2; DO-178C §2.3; AC/AMC 25.1309

### Section 2 — ARP4754A: System Development (ED-79A)
- Safety assessment process flow diagram: FHA → PSSA/PASA → ASA/SSA, with
  CCA bar spanning all processes
- FHA, PSSA/PASA, ASA/SSA, CCA — all described correctly:
  - FDAL assigned to functions; IDAL assigned to items
  - Table 3 Options 1 and 2 for redundant architectures
  - CCA = ZSA + PRA + CMA (not "CMR")
- Three interview Q&As with ARP4754A section references in every answer
- Citations: ARP4754A §5.1.1, §5.1.2, §5.1.3, §5.1.4, §5.2.2, §5.2.3,
  Table 2, Table 3; ARP4761 Appendices A, B, C, I, J, K

### Section 2A — How System, Software, and Hardware DALs Are Determined
- Core concept: DALs address development errors, not random hardware failures
- Seven-step process with standard references for each step:
  1. Define aircraft-level functions [ARP4754A §4.1, §4.3]
  2. Conduct FHA — classify failure conditions [§5.1.1]
  3. Assign top-level FDAL from Table 2 [§5.2.3]
  4. Develop architecture and run PSSA [§5.1.2]
  5. Assign sub-function FDALs using Table 3 [§5.2.3.2.2]
  6. Allocate to items → assign IDALs → hand to DO-178C/DO-254 [§4.5, §5.2.2]
  7. Verify with SSA [§5.1.3]
- Table 3 reproduced fully: all five failure condition rows, all three columns
  (single member, Option 1, Option 2)
- IDAL-to-standard mapping table: IDAL A/B/C/D/E → DO-178C level → DO-254 DAL
  → key obligations
- Worked example using FCS Pitch Control Function (NOT EGPWS):
  - Catastrophic → FDAL A → dual FCU architecture → IDAL A → DO-178C Level A
- DAL determination flow diagram
- Citations: ARP4754A §5.2, Table 2, Table 3, §4.5; CS-25.671

### Section 3 — DO-178C: Airborne Software (ED-12C)
- DO-178C software lifecycle diagram (Planning umbrella → Requirements →
  Design → Coding → Integration; with Verification, CM, QA, Cert Liaison
  as integral processes below)
- DO-178B vs DO-178C comparison table
- Software Level definitions (verbatim from DO-178C §2.3) — Level A through E
- Key planning documents: PSAC, SDP, SVP, SCMP, SQAP, SAS — with section refs
- Structural coverage table: Statement (Level C+), Decision (Level B+),
  MC/DC (Level A only)
- MC/DC truth table for A AND B — exactly 3 test cases shown
- SOI 1–4 table with timing and authority focus
- Citations: DO-178C §2.3, §4, §5, §6.4.4.2, §6.4.4.3, §9.3, §11.1, §11.20

### Section 4 — DO-254: Airborne Hardware (ED-80)
- Hardware lifecycle diagram: Requirements Capture → Conceptual Design →
  Detailed Design → Implementation → Production Transition → V&V
- State explicitly: DO-254 excludes simple electronic hardware [§1.1]
- State explicitly: software verification methods cannot be applied to HDL
  designs [§5 Note 2]; functional coverage (toggle, FSM, branch) is used
- PHAC [§4] and HAS [§11] described
- DO-254 vs DO-178C comparison table
- Citations: DO-254 §1.1, §4, §5, §5 Note 2, §6, §11; DO-330 §5; AC 20-152

### Section 5 — DO-160G: Environmental Qualification
- DO-160G sections wheel diagram
- Correct section numbers (these are frequently wrong in online sources):
  §4=Temperature & Altitude, §5=Temperature Variation, §6=Humidity,
  §7=Operational Shocks & Crash Safety, §8=Vibration, §16=Power Input,
  §17=Voltage Spike, §19=Induced Signal Susceptibility,
  §20=RF Susceptibility (radiated AND conducted), §21=RF Emission,
  §22=Lightning Induced Transient Susceptibility (indirect effects on wiring),
  §23=Lightning Direct Effects (direct strike on equipment),
  §25=Electrostatic Discharge (ESD)
- Emphasise: §22 ≠ §23; §6=Humidity, NOT §25; §25=ESD, NOT Humidity

### Section 6 — DO-326A: Airworthiness Cybersecurity
- DO-326A family: DO-326A + DO-355 + DO-356A
- Security vs Safety comparison table
- Citations: DO-326A §4, §5, §6; FAA AC 119-1; EASA AMC 20-42

### Section 7 — Verification Technologies: MIL / SIL / PIL / HIL
- XiL fidelity ladder diagram showing progression from MIL to HIL
- Comparison table with: controller, plant, real-time, cost, fidelity,
  DO-178C credit
- Four descriptions with citations:
  - MIL → DO-331 §5
  - SIL → DO-178C §6.4.3.c
  - PIL → DO-178C §6.4.3.b (also called Target-in-the-Loop)
  - HIL → DO-178C §6.4.3.a (primary SOI 3 integration evidence)

### Section 8 — MBSE: Model-Based Systems Engineering
- SysML diagram types table (BDD, IBD, Requirements, Activity, Sequence,
  State Machine, Parametric)
- Tools: Cameo, Capella (ARCADIA, increasingly used at ESA/EUMETSAT),
  Enterprise Architect

### Section 9 — DOORS: Requirements Management
- DOORS traceability chain diagram (CS-25 → SYS → HLR → LLR → TC → Result → RTM)
- Core concepts: Modules, Links, Baselines, Suspect Links, DXL
- Note: DOORS Next Generation (DNG) is part of IBM ELM
- Three RTM rules: every requirement has ≥1 verification record; every test
  case traces to ≥1 requirement; suspect links cleared after every change
- Citations: ARP4754A §5.5.6; DO-178C §11.21

### Section 10 — MATLAB & Simulink in Aerospace
- Toolchain: Embedded Coder (DO-330 TQL-1), Simulink Coverage,
  Polyspace Code Prover (proves absence of errors) vs Polyspace Bug Finder
  (finds defect patterns) — note these are different tools,
  Simulink Design Verifier (scalability limits on large models),
  Requirements Toolbox
- DO-331 supplement: models as design artefacts require same rigour as
  equivalent artefact; model coverage satisfies structural coverage only
  when code generator is qualified and PSAC agrees
- Citations: DO-331 §1, §5.2; DO-330 §5; DO-178C §12.2

### Section 11 — Agile in Aerospace Certification
- Agile sprint diagram with certification gates
- Five adaptations required: requirements baseline, Definition of Done,
  CI coverage gating, CM per sprint, PSAC documents lifecycle
- SAFe (Scaled Agile Framework) for large programmes
- Correct terminology: "software Level A", not "DAL A software"
- Citations: DO-178C §1.4, §9.3, §11.1; ARP4754A §3.3; industry: CAST-32A

### Section 12 — Test Strategy Development
- Documents table: Verification Strategy, SVP, Test Plan, Test Procedure,
  Test Results, RTM, VCN (closes individual items vs SAS which closes programme)
- Citations: ARP4754A §5.5; DO-178C §11.3, §11.13, §11.14, §11.21

### Section 13 — Interview Preparation: Q&A Deep Dive
- Q&A pairs for: Tell me about yourself, Why should we hire you, Difficult
  defect investigation, Requirements ambiguity, Certification challenge,
  Stakeholder conflict, Good test case, Verification completeness
- Every answer must reference specific standard sections
- Use Arun's real experience: FADEC timing defect (PIL/HIL), 77% decision
  coverage gap closure, EASA SOI coordination at Lilium

### Section 13B — Acronyms and Abbreviations
- 100+ entries covering all acronyms used in the document
- Three columns: Acronym | Full Form | Context / Reference
- Must include at minimum: FAA, EASA, ARP, DO, RTCA, EUROCAE, FDAL, IDAL,
  PSAC, SAS, PHAC, HAS, FCS, FCU, FBW, MC/DC, HIL, PIL, SIL, MIL, MBSE,
  SysML, DOORS, DXL, ODA, DER, SAFe, TQL, ZSA, PRA, CMA, FMEA, FTA, FHA,
  SSA, PSSA, ASA, PASA, CCA, EMC, EMI, ESD, BIT, BITE, LRU, ICD, CM, QA,
  ISTQB, CI/CD, MISRA, LDRA

### Section 14 — Final Cheat Sheet
- Standards quick reference table (with version and key output)
- DO-160G section numbers table (§4 through §25, correct mapping)
- Key definitions list (15+ terms with standard section references)
- Three RTM rules
- SOI 1–4 table

### Section 15 — Flight Control System: End-to-End Programme Case Study
**This is the primary worked example applying all five standards.**
Do NOT use EGPWS as the example — use FCS throughout.

- FCS architecture table: FCU-L/R, ACE-1/2/3, ADM, FCU FPGA, LVDT/RVDT sensors
- Step-by-step application of each standard:
  - ARP4754A: FHA table (Catastrophic failure → FDAL A), PSSA dual-FCU
    architecture, FDAL/IDAL assignment table, FTA result with SSA closure
  - DO-178C Level A: PSAC, 71 objectives, MC/DC, SOI 1–4, SAS
  - DO-254 DAL A: PHAC, FPGA RTL, HDL functional coverage (NOT MC/DC),
    DO-330 tool qualification, HAS
  - DO-160G: FCU LRU qualification table with correct categories
    (Cat S for avionics bay vibration — NOT Cat U engine mount)
  - DO-326A: ASRA, ARINC 429 threat scenario, security requirements,
    fuzz testing, DO-355 continuing airworthiness
- Three diagrams: HIL architecture, programme timeline (~40 months), V-model
- Certification deliverables summary table (13 documents mapped to standards)
- Six key programme lessons with standard references
- Citations throughout: CS-25.671, ARP4754A §5.1–5.2, DO-178C §6.4.4.3,
  DO-254 §5, DO-160G §8, DO-326A §4–6

---

## CRITICAL MISTAKES TO AVOID

The following errors have been confirmed in previous AI-generated versions.
**These must not appear in any output.**

### Technical Errors
1. **DO-178C objective count** — State 71 objectives total (Annex A, Tables
   A-1 through A-10). Level A requires all 71. Do not state "66 objectives"
   or any other number.
2. **DO-178C publication date** — December 13, 2011, not 2012.
3. **FDAL vs DAL** — ARP4754A §5.2 introduced FDAL (to functions) and IDAL
   (to items). Never use "DAL" for both — they are distinct concepts.
4. **CCA components** — ZSA, PRA, CMA. Never write "CMR".
5. **DO-254 scope** — Explicitly excludes simple electronic hardware (§1.1).
   Software methods (MC/DC etc.) cannot be applied to HDL designs (§5 Note 2).
6. **DO-160G section numbers** — The following are commonly wrong online:
   §6=Humidity (NOT §25), §22=Lightning Induced Transient (NOT §19),
   §23=Lightning Direct Effects (NOT §22), §25=ESD (NOT Humidity).
   Verify every section number against the standard.
7. **Probability superscripts** — Use markup tags (`<super>-9</super>`), never
   Unicode superscript characters (⁻⁹). Unicode renders as black boxes in PDF.
8. **"DAL A software"** — Incorrect. DO-178C uses "software levels" not "DALs".
   Write "software Level A" throughout.
9. **PASA/ASA missing** — ARP4754A has both aircraft-level (PASA/ASA) and
   system-level (PSSA/SSA). Do not describe only the system-level pair.
10. **Lilium location** — "Lilium Aerospace GmbH, Munich" (not just "Gauting" or
    no location).
11. **EGPWS as example** — Do not use EGPWS as the main worked example. Use
    Flight Control System (FCS) throughout.
12. **SOI 4 objective count** — All 71 Level A objectives must be evidenced at
    SOI 4, not a generic "all objectives".
13. **PIL description** — PIL is also called "Target-in-the-Loop (TIL)" in some
    industry contexts. Mention both names.
14. **DO-254 hardware lifecycle order** — Requirements Capture → Conceptual
    Design → Detailed Design → Implementation → Production Transition → V&V.
    Do not invent or reorder these steps.
15. **SAFe description** — Scaled Agile Framework. Governance layer bridging
    Agile sprint cadence with certification milestone requirements.

### Formatting Errors
16. **Table cell overflow** — Every table cell must be a `Paragraph` object with
    word wrap, top/bottom padding of 5pt, left/right padding of 5pt. Never pass
    raw Python strings directly to `Table()`. This causes text to overflow into
    adjacent cells.
17. **Section 15 missing from TOC** — Every new section must be added to the
    Table of Contents. Check TOC completeness before finalising.
18. **Spurious HTML entities** — `&` must be written as `&amp;` in ReportLab
    Paragraph strings. Avoid `"V&V;"` or `"Q&A;"` — these are encoding artefacts.
19. **Diagram titles** — Every diagram must have a figure caption below it in
    the format: `Figure N.N — Title [Standard §Section]`.

---

## EXPERT REVIEW CHECKLIST

Before finalising any output, review against this checklist:

**Technical accuracy:**
- [ ] All DO-160G section numbers verified against DO-160G ED-14G
- [ ] DO-178C §2.3 software level definitions match standard verbatim
- [ ] ARP4754A Table 3 reproduced accurately (all rows and all three columns)
- [ ] Probability figures use correct exponents and superscript markup
- [ ] All CITE tags reference real standard sections (no invented section numbers)
- [ ] FDAL/IDAL distinction maintained throughout (not collapsed to "DAL")
- [ ] MC/DC truth table shows exactly 3 test cases for A AND B expression
- [ ] Section 15 uses FCS not EGPWS

**Document structure:**
- [ ] Table of Contents includes all 15+ sections
- [ ] Author table shows Munich for Lilium
- [ ] Acronyms section covers FAA, EASA, and all other abbreviations used
- [ ] Every section has at least one diagram
- [ ] Every section has at least one CITE tag

**Formatting:**
- [ ] No raw strings in table cells — all wrapped in Paragraph
- [ ] No Unicode superscript characters — only `<super>` XML tags
- [ ] All tables have TOPPADDING, BOTTOMPADDING, LEFTPADDING, RIGHTPADDING = 5
- [ ] Cover page, header, and footer present on all pages
- [ ] No text overlap or cell overflow visible

---

## OUTPUT FORMAT REQUIREMENTS

- Output a single downloadable PDF file.
- File name: `Aerospace_VV_Handbook_Final.pdf`
- If generating code (Python/ReportLab), ensure it runs without errors
  before presenting the output file.
- Do not present partial output — the complete document must be generated
  in a single build pass.
- After presenting the file, provide a brief summary of: sections included,
  diagrams added, corrections applied, and total page count.

