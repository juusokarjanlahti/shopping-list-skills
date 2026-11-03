# Preferences and constraints

Use a short user profile only when the user has provided the information or asked to save it. Do not infer private preferences from browsing, past purchases, or a single shopping list. Keep allergies and prohibitions separate from preferences. `allergies`, `never_buy`, and prohibited ingredients are always hard exclusions.

Suggested profile fields:

```yaml
household_size: null
planning_horizon_days: null
budget_amount: null
budget_currency: EUR
budget_type: target # target or hard_limit; ask if needed
price_estimate_store: null
preferred_stores: []
store_comparison_mode: null # primary_plus_alternatives or equal_candidates
preferred_fulfillment: null # in_store, pickup, or delivery
vehicle_access: null # record only when the user states it
dietary_rules: []
allergies: []
never_buy: []
exact_products: []
preferred_brands: []
preferred_origin: []
prefer_frozen: null
convenience_level: null # basic, mixed, or ready-to-use
pantry_items: []
avoid_food_waste: true
```

Interpret the fields as follows:

- `allergies`, `never_buy`, prohibited ingredients, and explicit dietary restrictions are hard exclusions. Never score, relax, or override them because of price, discounts, availability, convenience, or a shopping-list request.
- Never suggest, select, add, or substitute a product that contains a user-reported allergen or prohibited ingredient.
- If ingredient, allergen, or cross-contamination information is missing or unclear, exclude the product and explain why. Do not claim it is safe or ask the user to accept a risky product.
- A one-time shopping request does not cancel a persistent allergy or prohibition. If a list item conflicts with the profile, skip it and report the conflict.
- `exact_products` means the specified product, brand, or form must be preserved. Do not silently substitute it.
- Brand, domestic origin, frozen/fresh, and convenience are preferences unless the user says "only", "must be", or similar. Report material trade-offs without claiming a preference was met when it was not.
- `budget_amount` is a target unless the user defines it as a hard limit (`budget_type: hard_limit`). If the plan exceeds a target, state the estimated difference and offer changes. For a hard limit, do not present an over-budget list as fitting the budget. Never silently break dietary restrictions, exact product requirements, or other hard constraints to meet the amount.
- `price_estimate_store` identifies the store or branch when the user wants a store-specific estimate. Prices and availability can vary by store, date, member pricing, and discounts; report the source and date when available.
- `preferred_stores` records stores the user names for a request. If multiple stores are listed without further direction, the first is primary and the rest are comparison candidates; do not assume the biggest store is primary. `store_comparison_mode` records whether the user wants a primary store compared with alternatives or regards all named stores as equal candidates. Do not assume they want the basket split across stores.
- `preferred_fulfillment` records the user's stated preference for in-store shopping, pickup, or delivery. Include fees and minimums only when shown or supplied. `vehicle_access` is optional context the user may provide for nearby-store comparisons; never infer it from location, browser state, or other data.
- `prefer_frozen` and `convenience_level` describe shopping preferences. Frozen food may reduce waste and prep; fresh food may suit a recipe better. Ready-to-use products may cost more, so compare the full package price too.
- `avoid_food_waste` guides package-size choices. Prefer the smallest package or number of packages that reasonably meets the planned need. Do not assume future use, sharing, or gifting to justify a larger package. If the user gives a meal-planning horizon, use it; otherwise ask only when likely surplus materially changes the choice.
- Confirm `pantry_items` with the user. Do not treat an old list as current without checking.

Ask whether the user wants a profile saved if persistence would materially help. Do not create or write a profile file automatically. If a profile exists in the local workspace, respect its scope and do not copy personal information into a public repository.
