# Scene 2: Maria Tests HIV-Positive

Maria has moved out and is now living in Utica. She is diagnosed HIV-positive.

## Maria - in the HIV Positive Test

| Field | Value |
|-------|-------|
| When | 1/1/2020 |
| VeratoLinkID | 23456... |
| Source | HealthiX \| Lab1 |
| MRN | 34432432 |
| First | Maria |
| Last | Alvarez |
| DOB | 6/26/1997 |
| Address | 126 Cross Street |
| City | Utica |
| State | NY |
| Zip | 3495 |
| Gender | F |
| CIN | *(not included)* |

## What's Happening

Maria moved from Albany to Utica. She tests HIV-positive and the result flows through the HealthiX lab feed.

Notice what changed:
- **Address**: Albany → Utica (different city, ~90 miles away)
- **MRN**: 1234 → 34432432 (different provider, different MRN)
- **CIN**: A123B456 → **missing** (the feed doesn't carry it)

Because the address is completely different and there's no CIN to anchor the match, the MPI **cannot link this record** to the MEF record from Scene 1. It creates a new VeratoLinkID: **23456...**

Maria is now **two people** in the system:
- VeratoLinkID 124252... — Maria Alvarez, Albany, Medicaid member
- VeratoLinkID 23456... — Maria Alvarez, Utica, HIV-positive

They are not linked.
