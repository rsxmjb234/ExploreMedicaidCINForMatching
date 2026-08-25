# Maria's Story: Why Medicaid CIN Belongs in Every Data Feed

## Project Goal

Convince stakeholders that adding Medicaid CIN to health data feeds is worth the effort. We do this through:
1. **Maria's Story** — a person whose records fragment because CIN is missing
2. **The Duplicate CIN Story** — showing that CIN errors don't break matching (addresses the counterargument)
3. **The Ask** — the technical plan for getting CIN into each QE's data flow

---

## The Story in One Sentence

Maria is a Medicaid member who is HIV-positive and pregnant, but no system can see all three facts are about the same person — because the feeds that carry her HIV result and pregnancy don't include her CIN.

---

## Maria's Data Across Time

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

Three different VeratoLinkIDs. Three different addresses. Three different MRNs. One name change (marriage). Zero CIN in the feeds that matter.

---

## Maria's Life Journey (for narrative context)

- **Jan 2019** — Maria is 21, living with her parents in Albany. Mom helps her sign up for Medicaid. Assigned CIN A123B456.
- **Jan 2020** — Maria moves to her first apartment in Utica (~90 miles away). Fresh start. Tests HIV-positive at a local clinic.
- **Jan 2023** — Maria has married Carlos Rodriguez. They move to Whitesborough (near Utica) to be closer to his family. Her PCP confirms she's pregnant.

---

## Story Arc (as built in index.html)

### The site opens with Maria as a person
- SVG portrait
- She's excited (pregnant) and concerned (HIV)
- She's on Medicaid — and Medicaid wants to help her with specific programs
- But the system can't find her

### The MPI sees 3 strangers
- Three identity cards with hover tooltips showing full demographics
- Each card has a different VeratoLinkID
- Hover reveals field-by-field data (green = match, red = mismatch/missing)
- Callout explains why matching fails

### Maria falls through the cracks
- The outreach query can't find her across the three identities
- No care coordination begins

### CIN fixes it (timeline)
- Maria's life journey told as a vertical timeline (2019 → 2020 → 2023)
- Each milestone shows full demographics with CIN in green
- CIN links all records instantly across 4 years, 3 cities, and a name change

---

## Story 2: Duplicate CIN (Tom Jones)

Addresses the counterargument: "won't errors create false links?"

- Tom Jones (DOB 11/3/1955, Male, Buffalo) gets same CIN as Maria through data entry error
- MPI compares: 1 field matches (CIN), 7 fields don't
- Score is extremely low — records are never linked
- Analogy: two NY residents share the same DOB all the time; the MPI handles it
- Conclusion: a missing CIN is dangerous (missed matches). A duplicate CIN is a non-event.

---

## Story 3: The Ask (roughed out)

Three technical paths depending on the QE:

| QE | Path | What to do |
|---|---|---|
| Bronx RHIO | Add to file | Modify the demographic feed file submitted to statewide MPI |
| HealthiX & HixNY | Add to API | Include CIN in the custom API that syncs with statewide Verato |
| Everyone else | Local Verato | Get CIN into local Verato; flows via Verato-to-Verato sync |

Sources of CIN: Medicaid MEF (already there), lab feeds, PCP/CCD feeds, ADT/hospital feeds, immunization registry.

**Status: Roughed out, needs technical detail.**

---

## What's Done

- [x] Maria's demographics defined (real NY addresses, local flavor)
- [x] Each scene written as standalone markdown file
- [x] index.html site with 3 stories on home page
- [x] Story 1: Maria narrative with hover tooltips and life timeline
- [x] Story 2: Tom Jones duplicate CIN counterargument
- [x] Story 3: The Ask roughed out (3 QE paths)
- [x] Steering files in .kiro/steering/ for Kiro guidance

## What's Next

- [ ] Flesh out "The Ask" with technical specs per QE
- [ ] Detail the Verato-to-Verato sync mechanism
- [ ] Detail the HealthiX/HixNY custom API modification
- [ ] Quantify the gap (how many Medicaid members affected?)
- [ ] Identify highest-impact feeds to target first
- [ ] Add more stories / populations
- [ ] Polish visual design

---

## How to Reproduce This Project

If starting from scratch with another AI:

1. Create `index.html` — a self-contained static site (no dependencies) hosted on AWS Amplify
2. Use the demographic data in this file (Maria's 3 scenes + Tom Jones) as the source of truth
3. The site tells 3 stories from a landing page: Maria, Duplicate CIN, The Ask
4. Maria's story starts with HER (emotions, situation) before showing data
5. Identity cards have hover tooltips with full demographics (color-coded: green=match, red=mismatch)
6. The solution section is a life-journey TIMELINE (not just a table) — show time passing, life changing
7. The audience understands MPI matching — speak to that expertise via the hover details
8. Keep it one HTML file, inline CSS/JS, no build step
9. All markdown files in `Maria/` folder document the data and narrative for reference

---

## Story Scenes (files)

| File | Scene | Purpose |
|------|-------|---------|
| Maria-SignupForMedicaid.md | Medicaid Enrollment | Establish Maria, assign CIN |
| maria-HIVPositives.md | HIV Diagnosis | Feed without CIN, new VeratoLinkID |
| maria-pregnancy.md | Pregnancy | Feed without CIN, name change, third VeratoLinkID |
| mpi-failure.md | The Problem | Three identities, one person, zero linkage |
| resolution-with-cin.md | The Solution | CIN in every feed = instant match |
| tom.md | Duplicate CIN | Same CIN, different person — MPI handles it correctly |
