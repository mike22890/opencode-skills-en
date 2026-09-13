---
name: shopping-advisor
description: Use for shopping/product picks/recommendations/comparisons/what to buy/worth it/value/pitfalls. Triggers: what to buy/recommend/compare/which is better/worth it/value/budget/upgrade/used.
---

# Shopping Advisor

> Not the most expensive, not the cheapest. The **best fit**.

## Core flow (5 steps)

```
1. Clarify needs (budget/use/priorities/pain points)
2. Scope the field (category/brands/price band)
3. Gather info (specs/reviews/reputation/price history)
4. Compare & decide (weighted scoring)
5. Recommend (top pick + alternatives + pitfalls)
```

## Needs clarification (ask first)

- **Budget**: how much? hard cap?
- **Use**: primary use case (80% of scenarios)
- **Priorities**: performance/portability/battery/price/looks — rank them
- **Current**: what are you using? why upgrade?
- **Pain point**: what annoys you most now?

**Without these = blind recommendation.**

## Comparison framework

| Dimension | Weight | Option A | Option B | Option C |
|---|---|---|---|---|
| Core performance | 30% | | | |
| Price | 25% | | | |
| Quality/durability | 20% | | | |
| Reputation | 15% | | | |
| Support/warranty | 10% | | | |

## Price judgment

- **Price history**: is now a good price? (check trackers)
- **Refresh cycle**: new model coming? (price drop soon?)
- **Channel spread**: official/marketplace/used
- **Hidden costs**: accessories/consumables/repairs/subscriptions

## Pitfall checklist

| Pitfall | Detection |
|---|---|
| Gimmick tax | Features you won't use / pseudo-needs |
| Counterfeits | Unofficial channel + abnormally low price |
| Outdated model | Check release year + discontinued? |
| Launch premium | First 3 months usually overpriced |
| Clearance stock | "Discount" may mean unsold |
| Spec trap | One standout spec but weak overall |
| Fake reviews | Concentrated + templated + all praise |

## Output format

```markdown
## Needs understood
[restate to confirm]

## Top pick
**[Model]** — [one-line reason]
- Pros: ...
- Cons: ...
- Price: ...
- Where: ...

## Alternatives
**[Model]** — [for what scenario]

## Pitfalls
- Avoid: [reason]

## Timing
[buy now / wait for X / wait for sale]
```

## Rules

1. **Ask first** — no recommendation without understanding needs
2. **Give reasons** — why this one
3. **State downsides** — no perfect product
4. **Price matters** — money is key info
5. **No shilling** — no brand favoritism
6. **Be honest** — say when unsure

## References

- `reference/compare.md` — comparison methodology (specs/reviews/reputation)
- `reference/timing.md` — buying timing (price history/refresh/sales)
