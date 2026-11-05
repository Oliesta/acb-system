# Worked Example: Village Stadium

This is the example from the original ACB idea, shown through the [spend ledger rules](../domains/spend/rules.md). All names and numbers are illustrative.

## The tender

A municipality awards R10,000,000 to a contractor to build a stadium in a village. The award is published, so the contract record exists from day one. The contractor opens a spend ledger.

## Budget lines

| # | Line item | Budget | Covers |
|---|-----------|--------|--------|
| 1 | Land and site preparation | R500,000 | Grading, excavation, levelling |
| 2 | Design and planning | R750,000 | Architects, engineers, permits, construction documents |
| 3 | Construction materials | R2,500,000 | Steel, concrete, masonry, roofing, insulation |
| 4 | Labour and subcontractors | R3,500,000 | Foundations, framing, roofing, electrical, plumbing, HVAC, finishing |
| 5 | Seating and fixtures | R1,250,000 | Seating, bleachers, scoreboards, sound, lighting |
| 6 | Safety and security | R250,000 | Fencing, gates, barriers, cameras, security staff |
| 7 | Concessions and restrooms | R500,000 | Concession stands, restrooms |
| 8 | Landscaping and site amenities | R250,000 | Sidewalks, parking, landscaping, irrigation |
| 9 | Equipment and furniture | R100,000 | Goal posts, furniture, loose equipment |
| 10 | Contingency | R500,000 | Unforeseen costs, change orders, insurance |
| | **Total** | **R10,000,000** | |

### Improvements over the original draft

- **No overlap (SPD-002).** The draft listed scoreboards, bleachers and seating under both line 5 and line 9. Overlapping lines are where money hides, because the same item can be charged twice. Here they sit only in line 5.
- **Land is usually not the contractor's cost.** In most public projects the municipality owns or buys the land before the tender, and design is often a separate professional services tender. If so, these lines belong on other contract records. Line 1 here covers site preparation only.
- **Contingency needs reasons (SPD-005).** Every Rand drawn from line 10 must say what it paid for.
- **Rand, not credits (SPD-003).** The draft used 10,000,000 credits. Using Rand directly is clearer and avoids any confusion with cryptocurrency.

## A purchase, step by step

1. The contractor orders 2,000 bags of cement from a building supplier.
2. They record a spend entry: line 3, R190,000 including VAT, payee "Example Building Supplies (Pty) Ltd", 2,000 bags at R95 each. The ledger issues **ACB-2026-STD01-000123**. Stage: Committed.
3. The supplier puts ACB-2026-STD01-000123 on their invoice.
4. The contractor pays and uploads the proof of payment. Stage: Paid. The line 3 balance drops to R2,310,000.
5. The supplier looks up the reference on the portal and confirms the amount. The entry is marked confirmed.
6. That night the entry is included in a batch anchored on-chain.

## How irregularities show up

| What happens | How it becomes visible | Flag |
|--------------|------------------------|------|
| The contractor records R190,000 but the real invoice was R90,000 | The supplier looks up the reference and disputes the amount | F13 |
| Entries go to a company registered last month | Payee registration date is checked | F03 |
| Cement costs R250 a bag | Unit price is compared with comparable purchases | F08 |
| R4,000,000 received, only R1,500,000 recorded | The unaccounted balance is shown on the contract page | F10 |
| 80% of the materials line is spent, but watchdogs see only foundations | Spend is compared with verified site observations | F14 |
| Payroll shows 60 workers, watchdogs count 15 on site on most days | Worker counts are compared with observations | F14 |
| A worker's payslip reference shows a lower amount than they were paid, or does not exist | The worker checks their own reference | F13 |

None of these flags blocks a payment. They make the problem public while the project is still running, so the community, journalists, the municipality's council and oversight bodies such as the SIU can act before the money is gone.
