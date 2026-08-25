# Maria's Story: Why Medicaid CIN Belongs in Every Data Feed

## Our Goal

Convince stakeholders that adding Medicaid CIN to health data feeds (labs, clinical documents, surveillance reports) is worth the effort. We do this through Maria — a single fictional person whose records fragment across three systems because CIN is missing from two of them. The story is simple, visual, and hard to argue with.

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

Three different VeratoLinkIDs. Three different addresses. Three different MRNs. One name change. Zero CIN in the feeds that matter.

---

## Story Arc

### Scene 1: Maria signs up for Medicaid (2019)
She lives with her parents in Albany. Gets CIN A123B456. Clean record. One person.

### Scene 2: Maria tests HIV-positive (2020)
She moved to Utica. The HIV lab result flows through HealthiX but **does not include CIN**. Different address + different MRN = the MPI can't link it. New VeratoLinkID created. Now she's two people.

### Scene 3: Maria is pregnant (2023)
She moved to Whitesborough and changed her name to Rodriguez. Her PCP sends a CCD through HixNY but **does not include CIN**. New name + new address + new MRN = the MPI can't link it. Third VeratoLinkID created. Now she's three people.

### Scene 4: The system fails Maria
Medicaid has a program for pregnant HIV-positive members. It queries: "Who is enrolled, HIV-positive, AND pregnant?" Maria should appear. She doesn't. Three records, three identities, zero overlap. No outreach fires.

### Scene 5: How CIN fixes it
Replay the same story, but this time CIN A123B456 is in every feed. The MPI matches on CIN — deterministic, instant, no scoring needed. One VeratoLinkID. One Maria. Outreach fires. She gets help.

---

## What We're Selling

**The ask:** Include Medicaid CIN in every health data feed that might contain a Medicaid member.

**Why it works:**
- CIN is permanent — assigned once, never changes
- CIN is deterministic — it matches or it doesn't, no probabilistic scoring
- CIN is already known — providers verify eligibility (which returns CIN) before billing
- CIN cuts through all the noise: name changes, address changes, provider changes, MRN changes

**What it enables:**
- Programs find the people they're designed to help
- Care coordination starts on time, not months late (or never)
- The MPI links records it otherwise can't
- Vulnerable populations become visible instead of fragmented

---

## Goals / To-Do

1. ~~Write Maria's demographics for each scene~~ ✓
2. ~~Write each scene as a standalone file~~ ✓
3. Build a simple visual/presentation that walks through the 5 scenes
4. Show the side-by-side: "without CIN" vs "with CIN"
5. Quantify the gap — how many Medicaid members could be affected?
6. Identify which feeds should carry CIN first (highest impact)
7. Draft the actual ask / proposal for stakeholders

---

## Story Scenes (files)

| File | Scene | Purpose |
|------|-------|---------|
| Maria-SignupForMedicaid.md | Medicaid Enrollment | Establish Maria, assign CIN |
| maria-HIVPositives.md | HIV Diagnosis | Feed without CIN → new VeratoLinkID |
| maria-pregnancy.md | Pregnancy | Feed without CIN + name change → third VeratoLinkID |
| mpi-failure.md | The Problem | Three identities, one real person, zero linkage |
| resolution-with-cin.md | The Solution | CIN in every feed → instant match → outreach fires |
