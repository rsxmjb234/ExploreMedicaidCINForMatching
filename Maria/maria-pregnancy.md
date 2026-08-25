# Scene 3: Maria Is Pregnant

Maria has moved again and changed her last name. A pregnancy is confirmed via her PCP.

## Maria - Pregnant

| Field | Value |
|-------|-------|
| When | 1/1/2023 |
| VeratoLinkID | 78910... |
| Source | HixNY \| PCP (CCD) |
| MRN | 2132 |
| First | Maria |
| Last | Rodriguez |
| DOB | 6/26/1997 |
| Address | 15-1 Olena Dr |
| City | Whitesborough |
| State | NY |
| Zip | 13492 |
| Gender | F |
| CIN | *(not included)* |

## What's Happening

Maria has moved again — this time to Whitesborough (near Utica). She also changed her last name from Alvarez to Rodriguez (likely married).

Notice what changed from Scene 1:
- **Last name**: Alvarez → Rodriguez
- **Address**: Albany → Whitesborough
- **MRN**: 1234 → 2132 (new provider)
- **CIN**: A123B456 → **missing** (the feed doesn't carry it)

The MPI assigns a **third** VeratoLinkID: **78910...** — because the name changed (Alvarez → Rodriguez) and the address is different again. It cannot confidently link this to either previous record without CIN.

Maria is now **three people** in the system:
- VeratoLinkID 124252... — Maria Alvarez, Albany, Medicaid member
- VeratoLinkID 23456... — Maria Alvarez, Utica, HIV-positive
- VeratoLinkID 78910... — Maria Rodriguez, Whitesborough, pregnant

None of them are linked. **The system cannot see that the Medicaid member, the HIV-positive patient, and the pregnant woman are all the same Maria.**
