# Arun's CV Profile & Career Summary

## Personal
- Based: Darmstadt, Germany
- Certifications: ISTQB (certified tester), Scrum Master
- Languages: English (professional), Tamil (native), German (basic/developing)
- Publications: "Aerospace Systems V&V Knowledge Handbook" (in development — PDF/ebook, Gumroad + Amazon KDP)
- LinkedIn: Active presence
- YouTube: "My Travel Notes" channel

---

## Career Timeline

### EUMETSAT — Darmstadt, Germany (Current)
**Role:** Systems and Software Verification Specialist / IVV Engineer / Test Conductor  
**Programme:** MetOp-SG / EPS-SG PDAP (Programme Data Access and Processing)  
**Domain:** Satellite ground segment IVV  
**Standards:** ECSS (ECSS-E-ST-10-02C, ECSS-E-ST-10-03C, ECSS-Q-ST-80)

**Key responsibilities:**
- Test Conductor for PDAP IVV campaigns — planning, execution, evidence management
- Multi-facility coordination (MME_DIS, SIPF, EDL, VAL_UMARF, SATELLITE, TERRESTRIAL)
- Test incident management per ECSS problem report process
- V&V reporting to programme management
- Tooling development: Python scripts, shell automation, HTML dashboards for timeliness/completeness monitoring

**Notable achievements:**
- Built `Timeliness_Completeness_Summary.py` — live HTML dashboard (port 8082) for PDAP product monitoring across 7 facilities, with DOY selector, JSON caching, Excel reporting
- Built `edl_timeliness_analyzer.py` — EDL log analysis with dual format support and 30-min SLA alerting
- Smart search shell scripting (`smart_search.sh`) for automated PDAP log analysis
- Python-based Excel reporting pipeline for completeness charts
- Automated reporting reduced daily effort from ~2h to ~15min

---

### Lilium — Munich area, Germany
**Role:** Verification Engineer — Electric Propulsion Systems  
**Domain:** eVTOL (Electric Vertical Take-Off and Landing) propulsion  
**Standards:** DO-178C, ARP4754A, CS-23/CS-25 applicable parts

**Key responsibilities:**
- ECU (Electronic Control Unit) and SCU (System Control Unit) verification
- DO-178C software V&V for novel distributed propulsion control architecture
- 36-motor CAN-bus distributed controller integration test planning
- Requirements traceability in DOORS
- Coordination with systems team for derived requirements feedback (ARP4754A §5.3.2)

**Notable challenges:**
- Novel architecture not covered by conventional avionics V&V playbooks
- Distributed propulsion control (36 motors, CAN arbitration) presented unique timing failure modes
- Bridging DO-178C methodology to non-traditional eVTOL certification basis

---

### Honeywell — (India / various, ~10+ years)
**Role:** Avionics Systems V&V Engineer / Senior Verification Engineer  
**Domain:** Avionics systems (cockpit, navigation, environmental control)  
**Standards:** DO-178C (Levels A, B, C), DO-160G, ARP4754A, ARINC 429, CAN

**Products worked on:**
- EGPWS (Enhanced Ground Proximity Warning System)
- Weather Radar systems
- ECS (Environmental Control System) controllers
- FMS (Flight Management System) modules

**Key responsibilities:**
- Software V&V per DO-178C — requirements, design, code review; test case development
- Structural coverage analysis — statement, decision, MC/DC using VectorCAST
- Unit testing using LDRA Testbed and Cantata++
- HIL (Hardware-in-the-Loop) integration testing using dSPACE
- ARINC 429 interface testing
- DOORS requirements management and DXL scripting for automation
- Participation in SOI audits (1–4) with DER/certification authority
- Problem report lifecycle management

**Notable achievements:**
- DXL automation script reducing traceability update effort from 3 weeks to 4 days
- Structural coverage gap resolution achieving 100% decision/MC/DC before SOI-3
- HIL fault injection test discovering Level C safety-significant defect pre-integration
- DER audit preparation — 0 open findings at multiple SOI-3 audits

---

### Accord Software & Systems — Bangalore, India
**Role:** Avionics Verification Engineer (early career)  
**Domain:** Avionics V&V services (customer programmes)  
**Standards:** DO-178C, DO-160G  
**Context:** Testing services company supporting avionics OEM programmes

---

## Toolchain Summary

| Category | Tools |
|----------|-------|
| Requirements management | DOORS, DXL scripting |
| Software unit test | VectorCAST, LDRA Testbed, Cantata++ |
| HIL test | dSPACE Hardware-in-the-Loop |
| Bus interfaces | ARINC 429, CAN |
| Scripting / automation | Python, Bash/Shell, DXL |
| Reporting | Python (ReportLab, openpyxl), HTML, Excel |
| Space IVV | ECSS test frameworks, internal EUMETSAT tooling |
| Version control | Basic git usage |
| Process | ISTQB, Scrum, DO-178C software planning |

---

## Competitive Differentiators

### 1. Cross-domain rarity
Avionics (DO-178C) → eVTOL (emerging) → Space (ECSS). Few candidates have operated at the intersection of all three civil aerospace domains. This provides perspective on how different safety cultures approach the same fundamental V&V challenges.

### 2. Both software and system level
DO-178C software-level depth AND ARP4754A system-level experience (FDAL/IDAL, FHA/PSSA/SSA). Many engineers are strong on one, not both.

### 3. Tool depth + automation mindset
Not just a tool user — a tool extender. DXL scripting, Python dashboards, shell automation. In V&V where manual effort is a bottleneck, automation capability is a genuine differentiator.

### 4. SOI audit experience
Actual DER-facing SOI-1 through SOI-4 experience at Honeywell. Many engineers have process knowledge but have never been in the room for an SOI.

### 5. Active publication
V&V Knowledge Handbook in progress — demonstrates mastery depth, professional commitment, ability to synthesise across standards.

---

## Gaps to Address Proactively

| Gap | How to address in interview |
|-----|---------------------------|
| German language (limited) | "Actively developing; professional English fluency is strong; available for German language training" |
| No direct flight controls Level A (Liebherr, Safran) | Redirect to EGPWS/FMS Level A/B and HIL fault injection rigour |
| Defence domain (Hensoldt) | "Adjacent; DO-178C rigor transfers; willing to develop MIL-STD familiarity" |
| MBSE / SysML (Airbus) | "Familiar with DOORS-based system modelling; developing MBSE awareness" |
| ATM specific (Frequentis) | "V&V process transfers directly; domain ramp-up similar to avionics→space transition I've made" |

---

## Interview Answer Frameworks

### "Walk me through your background"
*3-minute structure:*
1. "I've spent nearly 20 years in aerospace V&V across three domains — avionics at a Tier-1 OEM, eVTOL propulsion, and currently satellite ground segment IVV at a European space agency." (15 sec)
2. Avionics highlight: "At [Tier-1 OEM], I specialised in DO-178C software verification at Level A and B — EGPWS, FMS, ECS systems — using VectorCAST, LDRA, and dSPACE HIL, and participated in multiple DER SOI audits." (30 sec)
3. eVTOL: "I then moved to verify flight control software for a novel eVTOL propulsion system — 36 distributed motor controllers, which required adapting DO-178C methodology to a non-traditional architecture." (20 sec)
4. Space: "Currently, as Test Conductor on a MetOp-SG IVV programme, I plan and execute large-scale ECSS system verification campaigns and have built Python automation tools that reduced our reporting overhead significantly." (25 sec)
5. Close: "I'm now looking to bring this cross-domain depth to [Company] — particularly your [relevant product line]." (10 sec)

### "Why are you leaving EUMETSAT / why do you want to join us?"
*Framework:* "I value my current role and the ECSS IVV experience it has given me. I'm seeking a role that brings me back closer to DO-178C and ARP4754A — the standards framework I'm most deeply trained in — and [Company]'s [product/programme] is exactly that kind of challenge. The combination of your [domain] and my [relevant background] feels like a natural fit."
