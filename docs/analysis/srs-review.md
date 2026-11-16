# Analyst review of the SRS

Reviewed against the Week 4 handout (outline in section 7 of the notes, and the group assignment).

## Checklist

| Required | Found | Result |
| --- | --- | --- |
| Outline: introduction, overall description, FR, NFR, use cases, priorities, out of scope | All seven sections present | OK |
| At least 12 functional requirements with IDs | 14 (FR-01 to FR-14) | OK |
| At least 5 non-functional requirements with IDs | 6 (NFR-01 to NFR-06) | OK |
| Every requirement testable | Each one names a value or a visible result | OK |
| Stakeholder table | 5 stakeholders with their interest | OK |
| Use case diagram in `docs/diagrams/usecases.drawio.svg` | Was at the repository root under another name | Corrected |
| Three full use case descriptions | UC-03, UC-04, UC-06, each with flows and the requirements covered | OK |
| MoSCoW table | Present | OK |
| SRS at `docs/srs.md` | Was at `src/srs.md` | Corrected |
| User stories with two Given/When/Then each | Were missing | Added in `docs/user-stories.md` |

## Corrections made on this branch
1. Moved the SRS to `docs/srs.md` and the diagram to `docs/diagrams/usecases.drawio.svg`, the paths the handout asks for.
2. The use case section held a text placeholder where the diagram should be. It now shows the diagram.
3. The document said the group has five members. The group has ten.
4. Removed a `.DS_Store` file that was committed by mistake.

## Points for the analysis lead to decide
1. FR-03 (restock) and FR-04 (low-stock list) are marked Should. The notes say "products, sales and stock are Must". Without restock the stock can only go down, so FR-03 looks like a Must.
2. FR-09 asks for "total profit". Profit needs the buying price at the time of each sale. If the buying price changes at a restock, which price is used? This should be stated.
3. FR-06 says "show a receipt" but nothing says what is on it. One line listing its contents would make it testable.
4. FR-13 has no rule for a wrong password (how many tries, what message). US-07 proposes a message.
5. No requirement says what happens to a sale recorded while the phone has no connection. The assumptions say the stall has mobile data, so this may be out of scope, but it should be written in section 7.
6. The use cases are numbered UC-03, UC-04 and UC-06. A short list of all ten use cases with their IDs would let a reader see where these three sit.
