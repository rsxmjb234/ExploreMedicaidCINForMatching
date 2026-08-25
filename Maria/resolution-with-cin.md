# Scene 5: How CIN Solves This Instantly

## The Replay

Same Maria. Same moves. Same name change. But this time, every data feed includes her Medicaid CIN.

## The Feeds — Now With CIN

| VeratoLinkID | Source | Name | City | CIN | Key Fact |
|---|---|---|---|---|---|
| 124252... | Medicaid MEF | Maria Alvarez | Albany | **A123B456** | Active member |
| 124252... | HealthiX \| Lab1 | Maria Alvarez | Utica | **A123B456** | HIV-positive |
| 124252... | HixNY \| PCP (CCD) | Maria Rodriguez | Whitesborough | **A123B456** | Pregnant |

## What Happens Now

1. HIV feed arrives with CIN A123B456.
2. MPI matches on CIN — **instant deterministic link** to VeratoLinkID 124252...
3. No ambiguity. No scoring. No threshold. One field, one match.

4. Pregnancy feed arrives with CIN A123B456.
5. Same CIN, same person — **instant link again**.

**Result: One VeratoLinkID. Three facts. Linked immediately.**

## The Outcome for Maria

The outreach program queries: "Show me members who are Medicaid-enrolled AND HIV-positive AND pregnant."

**Maria appears.**

| Field | Value |
|-------|-------|
| Name | Maria Alvarez / Rodriguez |
| CIN | A123B456 |
| VeratoLinkID | 124252... |
| Medicaid | Active (since 1/1/2019) |
| HIV Status | Positive (1/1/2020) |
| Pregnancy | Confirmed (1/1/2023) |
| Eligible Programs | Prenatal HIV Care Coordination |

Within days:
- A care coordinator contacts Maria
- She is connected to a prenatal HIV specialist
- Antiretroviral therapy is optimized for pregnancy
- A delivery plan is created to minimize transmission risk
- Post-delivery infant testing is scheduled

Maria and her baby get the support they need.

## Why CIN Works Where the MPI Alone Fails

| What Changed | Broke the MPI? | CIN Still Links? |
|---|---|---|
| Address: Albany → Utica → Whitesborough | Yes | **Yes** |
| Last name: Alvarez → Rodriguez | Yes | **Yes** |
| MRN: 1234 → 34432432 → 2132 | Yes | **Yes** |
| Provider system: MEF → Lab1 → PCP | Yes | **Yes** |

CIN is **deterministic**. It doesn't score. It doesn't estimate. It matches or it doesn't. And it's assigned once, for life.

## The Ask

Include CIN in every data feed that touches Medicaid members:

| Feed | Currently Has CIN? | Should Have CIN? |
|------|---------------------|-------------------|
| Medicaid MEF | Yes | Yes |
| HealthiX Lab feeds | **No** | **Yes** |
| HixNY PCP (CCD) feeds | **No** | **Yes** |
| HIV Surveillance | **No** | **Yes** |
| Immunization Registry | No | Yes |
| Hospital Discharge (SPARCS) | No | Yes |

The technical lift is small. Providers already verify Medicaid eligibility (which returns CIN) before billing. The CIN is known at the point of care. It just isn't flowing into the data feeds.

## One Field. One Link. One Maria.
