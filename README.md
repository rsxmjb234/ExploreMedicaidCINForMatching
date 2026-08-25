# ExploreMedicaidCINForMatching

**The case for adding Medicaid CIN to every health data feed.**

URL: https://main.dxm8owlbnta6q.amplifyapp.com/

---

## What This Is

A narrative-driven argument for including Medicaid Client Identification Number (CIN) in as many health data feeds as possible — HIV surveillance, clinical labs, immunization registries, hospital discharges, and more.

We tell this story through **Maria**, a fictional Medicaid member whose records become fragmented across systems because the feeds that carry her health events don't include her CIN.

---

## The Problem

When a Medicaid member moves and changes providers, probabilistic matching (MPI) struggles to link their records. Without a persistent identifier, the same person becomes multiple unlinked records. Targeted programs — the ones designed to help the most vulnerable people — can't find them.

## The Solution

CIN is permanent, unique, and already known at the point of care. If data feeds include it, the MPI matches deterministically. No scoring. No ambiguity. One person, always.

---

## Maria's Story

| Scene | File | What Happens |
|-------|------|--------------|
| 1. Signup | [Maria-SignupForMedicaid.md](Maria/Maria-SignupForMedicaid.md) | Maria enrolls in Medicaid, is assigned CIN AB12345C |
| 2. HIV Diagnosis | [maria-HIVPositives.md](Maria/maria-HIVPositives.md) | Maria has moved to Queens; HIV feed arrives without CIN |
| 3. Pregnancy | [maria-pregnancy.md](Maria/maria-pregnancy.md) | Maria has moved to Brooklyn; lab feed arrives without CIN |
| 4. MPI Failure | [mpi-failure.md](Maria/mpi-failure.md) | The system sees 3 unlinked people; outreach doesn't fire |
| 5. The Fix | [resolution-with-cin.md](Maria/resolution-with-cin.md) | With CIN in each feed, Maria is one person instantly |

**Full outline:** [story-outline.md](Maria/story-outline.md)

---

## The Ask

Add Medicaid CIN to every data feed that might contain a Medicaid member. One field. One link. One Maria.
