# Scene 4: The MPI Can't Find Maria

## The Problem

Medicaid wants to reach Maria with targeted services for pregnant women who are HIV-positive. This is a real program — coordinated prenatal care, antiretroviral support, prevention of mother-to-child transmission.

But the MPI sees fragmented records:

| VeratoLinkID | Source | Name | City | Key Fact | CIN |
|---|---|---|---|---|---|
| 124252... | Medicaid MEF | Maria Alvarez | Albany | Active Medicaid member | A123B456 |
| 23456... | HealthiX \| Lab1 | Maria Alvarez | Utica | HIV-positive | *missing* |
| 78910... | HixNY \| PCP (CCD) | Maria Rodriguez | Whitesborough | Pregnant | *missing* |

## Why the MPI Fails

All three records have **different VeratoLinkIDs** — the MPI sees them as three separate people:

1. **124252... → 23456...** failed to link because: address changed (Albany → Utica), different MRN (1234 vs 34432432), no CIN in the HIV feed
2. **124252... → 78910...** failed to link because: last name changed (Alvarez → Rodriguez), address changed (Albany → Whitesborough), different MRN (1234 vs 2132), no CIN in the PCP feed
3. **23456... → 78910...** failed to link because: last name changed, different address, different MRN, no CIN in either feed

## The Consequence

The outreach program queries: "Show me members who are Medicaid-enrolled AND HIV-positive AND pregnant."

- VeratoLinkID 124252... shows Medicaid member — but no HIV or pregnancy
- VeratoLinkID 23456... shows HIV-positive — but no Medicaid or pregnancy
- VeratoLinkID 78910... shows pregnant — but no Medicaid or HIV

**Maria is not identified. No outreach is triggered. No care coordination begins.**

She navigates a high-risk pregnancy with HIV without the support that Medicaid designed specifically for her situation.

## This Is Not a Technology Failure

The MPI is working correctly given its inputs. It cannot reliably link records when:
- Addresses have no overlap (Albany → Utica → Whitesborough)
- Names change (Alvarez → Rodriguez)
- Different provider MRNs across systems
- No persistent identifier (CIN) connects the records

The failure is in the data feeds. They carry everything *except* the one identifier designed to stay constant.
