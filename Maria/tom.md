# Tom Jones — Same CIN, Different Person

## The Scenario

What if a CIN has a mistake? What if two people end up with the same CIN in the system?

This is the "what about false matches?" question. Here's why it's not a real risk.

## Tom's Record

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
| City | Buffalo |
| State | NY |
| Zip | 14201 |
| Gender | M |
| CIN | A123B456 |

## Maria's Record (for comparison)

| Field | Value |
|-------|-------|
| When | 1/1/2019 |
| Source | Medicaid MEF |
| VeratoLinkID | 124252... |
| MRN | 1234 |
| First | Maria |
| Last | Alvarez |
| DOB | 6/26/1997 |
| Address | 300 State Street |
| City | Albany |
| State | NY |
| Zip | 12210 |
| Gender | F |
| CIN | A123B456 |

## Why This Doesn't Break Matching

The MPI doesn't match on CIN alone — just like it doesn't match on DOB alone or address alone. CIN is a **contributing field**, one signal among many.

When the MPI compares Tom's record to Maria's:

| Field | Tom | Maria | Match? |
|-------|-----|-------|--------|
| First | Tom | Maria | No |
| Last | Jones | Alvarez | No |
| DOB | 11/3/1955 | 6/26/1997 | No |
| Gender | M | F | No |
| Address | 42 Main St, Buffalo | 300 State St, Albany | No |
| CIN | A123B456 | A123B456 | Yes |

One field matches. Five fields don't. The MPI scoring algorithm produces a **very low score**. These records are never linked.

## The Analogy

Two NY residents can and do share the same date of birth. That doesn't make the MPI link them — because everything else is different. CIN works the same way. It contributes to the match score, but it doesn't override all other evidence.

A duplicate CIN is no more dangerous than a shared DOB. The MPI handles it the same way: consider all fields, score the pair, decide.

## The Difference

- **CIN missing** = the MPI loses its strongest signal and can't link records that belong together (Maria's problem)
- **CIN duplicated by mistake** = the MPI sees one matching field but all others disagree, so it correctly keeps them apart (Tom's non-problem)

The risk of NOT having CIN (missed matches for vulnerable people) far outweighs the risk of a duplicate CIN (which the MPI handles naturally).
