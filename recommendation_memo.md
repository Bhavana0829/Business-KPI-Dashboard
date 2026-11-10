# Recommendation Memo – Reducing Subscriber Churn

**To:** Head of Customer Success  **Re:** Who to contact first, and what to change  **Data:** 15 customers (`cleaned_customer_churn.csv`)

## Decision
Focus retention effort on **month-to-month customers in their first 12 months**, and move every Medium/High-risk active customer onto an annual plan before they leave.

## What the data shows
| Finding | Evidence |
|---|---|
| Overall churn is high | 7 of 15 customers churned (**46.7%**); retention is 53.3% |
| Contract type is the clearest dividing line | Month-to-Month churn 7/7 (100%); One Year 0/4; Two Year 0/4 |
| Churn happens early | Churned customers averaged **7.0 months** tenure vs **29.1** for retained; see note below |
| Friction precedes churn | Churned customers raised **4.3** support tickets on average vs **1.0** for retained |
| Revenue impact | **$409.93 MRR lost** (32.3% of total MRR, ≈ $4,919/yr) |
| Revenue still exposed | **$99.98 MRR** (≈ $1,200/yr) belongs to 2 active customers scored Medium risk: CUST-1006 and CUST-1013 |
| Payment method | UPI 3/4 churned, Debit Card 2/2, Credit Card 2/6, Bank Transfer 0/3. Overlaps with contract type, so not treated as a separate driver |

Note on tenure: all 6 customers with 12 months or less tenure on a month-to-month plan churned (CUST-1001, 1003, 1005, 1007, 1010, 1014); the only other churner (CUST-1012) left at 14 months.

## Segments
| Segment | Customers | Churn | Action |
|---|---|---|---|
| A. Month-to-month, high friction (≥ 4 tickets) | 5 | 100% | Fix onboarding and support issues; proactive outreach after the 2nd ticket |
| B. Month-to-month, moderate friction | 2 | 100% | Offer a discount to move to a 1-year plan |
| C. One-year, building habit | 4 | 0% | Monitor; contact the 2 Medium-risk accounts before renewal |
| D. Two-year, loyal | 4 | 0% | Protect; low priority, highest revenue (avg $149.99/month) |

## Risk score (transparent, 0–10)
Contract (0–3) + tenure (0–3) + support tickets (0–3) + Basic plan (1). **High ≥ 7, Medium 4–6, Low ≤ 3.** Rules, edge-case tests and code are in `notebooks/segmentation_risk_model.ipynb`.
Result: 6/6 High churned, 1/3 Medium churned, 0/6 Low churned.

## Recommendations
1. **Annual-plan incentive at day 30–60** for month-to-month customers (e.g. first-month credit for switching). Target: Segments A and B.
2. **Support-ticket trigger:** a ticket count of 3 or more in the first 6 months opens a customer-success call within 48 hours.
3. **Call list now:** CUST-1006 and CUST-1013 (Medium, active, $49.99 each) – check renewal intent.
4. **Re-score monthly** and track High-band customers as the weekly retention KPI.

## Expected impact (illustrative, not a forecast)
If the incentive converts **half** of month-to-month customers who would otherwise churn into annual-plan customers, then on this sample ~3.5 of 7 churners are saved: roughly **$205 MRR (≈ $2,460/yr)** retained. This assumes annual-plan customers behave like today's annual customers, which is not tested.

## Limitations
* **n = 15.** Results are directional. One customer changes churn by 6.7 points.
* **In-sample validation only.** The score was designed from business logic, not fitted, but it was checked on the same 15 rows. Re-test on new customers.
* **Contract type and churn are perfectly aligned in this sample**, so contract effect cannot be separated from tenure, tickets or price. Longer contracts may also attract more committed customers (selection effect); the incentive may therefore save fewer customers than assumed.
* No dates, cancellation reasons, or usage data, so "why" is inferred, not observed.
* Medium band is the least reliable: it contained one miss (CUST-1012, 14 months, 3 tickets, churned).
