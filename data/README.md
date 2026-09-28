# Myntra E-Commerce Business Analysis

**Tools:** Excel (Pivot Tables, VLOOKUP, filtering, aggregation, dashboards)
**Dataset:** Raw Myntra product listings — 146,438 products, 3,194 brands, 341 categories
**Type:** Self-directed — raw data only, no brief or question handed to me

## Why I did this

I started with a raw export of Myntra's product catalog and nothing else — no
business question, no stakeholder, no "here's what to find." The point of the
exercise was to practice what an analyst actually does before any analysis
begins: decide what's worth asking, and why it would matter to a business
running this catalog.

I settled on three questions a commercial or category team at Myntra would
plausibly care about:

1. **Where is the money concentrated?** — which brands and categories actually
   drive revenue, versus which just take up shelf space.
2. **Is pricing and discounting consistent, or all over the place?** — are
   some brands discounting so heavily it looks unsustainable, while others
   barely move?
3. **Does customer rating behavior track with revenue, or are high performers
   and high revenue different things?**

## Approach

- Cleaned and structured the raw export (146,438 rows) in Excel: standardized
  price fields, computed a `discount_percent` and a `revenue` proxy
  (`rating_count × discounted_price`) per product, and rolled products up to
  brand and category level.
- Built Pivot Tables to summarize by brand: average rating, average discount
  %, total revenue, units sold (`sum of rating_count`), and marked vs.
  discounted price totals.
- Built a second set of pivots at the category level to compare product count
  against revenue share, to separate "many products" from "many sales."
- Built two dashboards (brand-level and product-level) on top of the pivots
  so the findings could be skimmed rather than dug for.
- Used VLOOKUP to reconcile brand/category tags against the main listing
  table where naming was inconsistent between sheets.

## What I found

**Catalog scale**
- 146,438 products across 3,194 brands and 341 categories
- Price range: ₹49 (cheapest listing) to ₹45,900 (most expensive)
- Average listed price: ₹1,533

**Revenue is heavily brand-concentrated**
Ranking all 3,194 brands by modeled revenue, the top six alone are:

| Rank | Brand | Revenue |
|---|---|---|
| 1 | Roadster | ₹1.35B |
| 2 | HRX by Hrithik Roshan | ₹474M |
| 3 | SASSAFRAS | ₹433M |
| 4 | Philips | ₹361M |
| 5 | HIGHLANDER | ₹332M |
| 6 | Maybelline | ₹326M |

Roadster alone outsold the next-best brand by roughly 3×. For a catalog with
over 3,000 brands, that's a strong signal that commercial attention (stock
depth, promotional slots, negotiating leverage) is not evenly distributed and
probably shouldn't be — a handful of brands are doing most of the work.

**Discounting varies widely and doesn't map cleanly to performance**
Brand-level discount percentages ranged from 0% to over 80% in the sample I
inspected closely, with no obvious relationship between discount depth and
either rating or revenue — some heavily-discounted brands still moved very
little volume, which suggests discounting alone isn't what's driving the
top performers.

**Rating and revenue are not the same axis**
Several brands with strong average ratings (4.5+) had negligible revenue,
and some of the highest-revenue brands had middling ratings — a reminder
that "customers who bought it liked it" and "lots of customers bought it"
are two different questions, and a pricing or promotion team should look at
both, not assume one implies the other.

## Why this matters for a business

This is the kind of analysis that would inform:
- **Assortment decisions** — which brands/categories deserve more shelf
  space, promotional inventory, or negotiating priority
- **Pricing and discount policy** — whether current discount levels are
  actually correlated with what sells, or just eating margin
- **Vendor prioritization** — which brand relationships are worth protecting
  or renegotiating first

## Notes on the data

This is a self-scoped exercise, not client work — the Myntra dataset is a
publicly available scraped product listing used for practice, and the
findings are illustrative rather than commercially verified.



