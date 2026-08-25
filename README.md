# ExploreMedicaidCINForMatching

**The case for adding Medicaid CIN to every health data feed.**

URL: https://main.dxm8owlbnta6q.amplifyapp.com/

---

## What This Is

A narrative-driven site that argues for including Medicaid Client Identification Number (CIN) in as many health data feeds as possible. We use stories — visual, data-backed, and emotionally grounded — to explain why CIN matters and what happens without it.

The site is a static `index.html` hosted on AWS Amplify. It's self-contained with no external dependencies — all styling and interaction is inline.

---

## Current State

The site has **three stories** accessible from a home page:

### Story 1: Maria's Story
The main narrative. Maria is a Medicaid member who is HIV-positive and pregnant. Because CIN is missing from the HIV and pregnancy feeds, the MPI sees her as three unlinked people and Medicaid's outreach program can't find her.

### Story 2: What If the CIN Has a Mistake?
Addresses the counterargument: "won't duplicate CINs create false matches?" Shows Tom Jones getting the same CIN as Maria through a data entry error. The MPI correctly keeps them apart because all other demographics disagree. CIN is treated like DOB — it contributes to matching but doesn't override other evidence.

### Story 3: The Ask
Roughed-out plan for how to get CIN into the feeds. Three paths depending on the QE:
- **Bronx RHIO** — add CIN to the demographic file submitted to statewide MPI
- **HealthiX & HixNY** — add CIN to the custom API (Verato sync)
- **Everyone else** — get CIN into local Verato instance; it flows via Verato-to-Verato sync

---

## Maria's Demographics (the real data)

| | Scene 1: MEF | Scene 2: HIV Test | Scene 3: Pregnancy |
|---|---|---|---|
| **When** | 1/1/2019 | 1/1/2020 | 1/1/2023 |
| **Source** | Medicaid MEF | HealthiX \| Lab1 | HixNY \| PCP (CCD) |
| **VeratoLinkID** | 124252... | 23456... | 78910... |
| **MRN** | 1234 | 34432432 | 2132 |
| **First** | Maria | Maria | Maria |
| **Last** | Alvarez | Alvarez | Rodriguez |
| **DOB** | 6/26/1997 | 6/26/1997 | 6/26/1997 |
| **Address** | 300 State Street | 126 Cross Street | 15-1 Olena Dr |
| **City** | Albany | Utica | Whitesborough |
| **Zip** | 12210 | 3495 | 13492 |
| **CIN** | A123B456 | *missing* | *missing* |

Three different VeratoLinkIDs. Three different addresses. Three MRNs. One name change. No CIN in feeds 2 and 3.

### Tom Jones (Story 2 counterargument)

| Field | Value |
|-------|-------|
| When | 3/15/2022 |
| Source | HealthiX \| Lab1 |
| VeratoLinkID | 99887... |
| MRN | 7788543 |
| First | Tom |
| Last | Jones |
| DOB | 11/3/1955 |
| Address | 42 Main Street |
| City | Buffalo, NY 14201 |
| Gender | M |
| CIN | A123B456 (same as Maria — error) |

---

## File Structure

```
index.html                          <- The site (all three stories, self-contained)
README.md                           <- This file
Maria/
  story-outline.md                  <- Master narrative outline and goals
  Maria-SignupForMedicaid.md        <- Scene 1: Medicaid enrollment, Albany
  maria-HIVPositives.md             <- Scene 2: HIV diagnosis, Utica, no CIN
  maria-pregnancy.md                <- Scene 3: Pregnancy, Whitesborough, no CIN
  mpi-failure.md                    <- Scene 4: MPI can't link the 3 records
  resolution-with-cin.md            <- Scene 5: CIN fixes it
  tom.md                            <- Tom Jones duplicate CIN scenario
  Maria-SignupForMedicaid.bmp       <- Screenshot of original data
  maria-HIVPositives.bmp            <- Screenshot of original data
  maria-hivpositive.bmp             <- Screenshot of original data
guidance/                           <- Original prompts from friend (reference only)
.kiro/steering/                     <- Steering files (active, auto-included by Kiro)
```

---

## Design Decisions

- **Story-first**: Start with Maria as a person (excited, concerned) before showing data
- **Hover tooltips on identity cards**: Audience understands matching — they can see field-by-field why the MPI fails
- **Timeline in the solution**: Shows Maria's life journey (parents → first apartment → married) so time and life changes are felt
- **No external dependencies**: Single HTML file, inline CSS/JS, works on any host
- **Real NY locations**: Albany, Utica, Whitesborough — upstate geography that's realistic for moves

---

## What's Done

- [x] Maria's demographics defined (3 scenes with real addresses)
- [x] Each scene written as standalone markdown
- [x] index.html with all 3 stories
- [x] Hover tooltips with field-level demographic comparison
- [x] Life-journey timeline in the CIN solution section
- [x] Tom Jones duplicate-CIN counterargument
- [x] "The Ask" roughed out with 3 QE paths

## What's Next

- [ ] Flesh out "The Ask" with technical specs for each path
- [ ] Add detail on modifying QE feeds to include CIN
- [ ] Detail the Verato-to-Verato sync mechanism
- [ ] Detail the HealthiX/HixNY custom API modification
- [ ] Quantify the gap — how many Medicaid members could be affected?
- [ ] Identify highest-impact feeds to target first
- [ ] Polish visual design / add more interactivity
- [ ] Consider additional stories for other populations/conditions
