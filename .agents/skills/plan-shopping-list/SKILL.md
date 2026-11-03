---
name: plan-shopping-list
description: Plan a grocery shopping list around the user's meals, budget, needs, preferences, dietary rules, and pantry. Use when the user asks to build or plan a shopping list in any Agent Skills-compatible AI tool.
metadata:
  short-description: Plan a shopping list around the user's needs
---

# Plan a shopping list

Create a practical, reviewable list that fits the user's situation. Do not assume their diet, household size, budget, pantry contents, preferences, or allergies. Ask only about details that materially affect the list. If the user wants to move quickly, state your assumptions and draft the list.

Treat user-reported allergies, prohibited products, and ingredients to avoid as hard constraints. Never suggest, plan, or recommend a product that violates them because of price, availability, convenience, a recipe, or another preference. If ingredient or cross-contamination information is unclear, exclude the product and explain why. Do not claim that a product is safe without verifiable information.

## Workflow

1. Establish the scope: number of days or meals, household size, budget (target or hard limit), whether a price estimate is wanted, and whether the user wants only food or household essentials too. For store-specific prices, ask which store or stores the user wants considered and whether they prefer in-store shopping, pickup, or delivery. Ask about travel or vehicle constraints only when the user wants nearby-store comparisons.
2. Separate hard constraints (allergies, prohibited products, dietary rules, exact products) from preferences (for example domestic origin, organic, brand, price, frozen, or convenience).
3. Ask what food is already at home when that could prevent meaningful duplicate purchases. If pantry contents are unknown, do not claim an item is already there.
4. Draft the list with practical quantities. Combine ingredients used in multiple meals and remove duplicates.
5. Check that quantities, budget, meal plan, and constraints are consistent. State the source, date, store, uncertainty, and unresolved substitutions for any price estimate.
6. Return the list in familiar store categories that are easy to read on a phone, with quantities and clearly stated assumptions.

## Selection principles

- Allergies, user prohibitions, and ingredients to avoid are absolute exclusions. No price, discount, availability, or other goal can override them. If a requested item conflicts with a hard constraint, leave it out and report the conflict; do not add it.
- Other hard constraints are filters, not scores. Never ignore them to choose a cheaper product.
- A preference may guide choices without silently becoming a hard requirement. If meeting it materially affects cost, explain the trade-off when relevant.
- Distinguish a budget target from a hard spending limit. Do not assume a budget or promise that the list fits without price-based calculation.
- For a budget estimate, include the full prices of packages to buy, not just the calculated cost of the quantities used in recipes. Exclude ingredients the user already owns from the shopping total, but mention that they will be used.
- Use unit prices per kilogram, litre, or item only for comparable products. Show package price and size alongside the unit price because a cheaper unit price on a large package can still increase today's checkout total.
- Treat the requested quantity as the expected need, not a reason to exceed it for unit-price savings. Prefer the smallest available package or combination that reasonably meets an approximate quantity and avoids unnecessary surplus. Compare total package cost and likely leftover as well as unit price. Do not assume surplus will be used later, shared, or given away. If package options create a material cost or waste trade-off and the user's preference does not resolve it, show the options or ask.
- If the user names multiple stores, treat the first as the primary store and the others as comparison candidates unless the user says they are equal alternatives or marks another store as preferred. Compare the same basket at each store where possible; do not assume a larger store is better. Do not split the basket across stores unless the user asks to consider that and extra trip or fulfillment costs can be assessed.
- Include pickup, delivery, minimum-order, or travel costs in a store comparison only when they are visible or provided by the user. Keep unknown costs separate rather than estimating them. Do not infer vehicle access or precise location. Use an area or postal code the user provides; do not use device or account location without the user's explicit direction.
- If price or package information is missing, mark the item as unpriced or give a clearly bounded estimate; never invent prices. If the budget appears insufficient, state the difference and offer options based on the user's goals. Do not change hard constraints or exact product requirements to meet the budget.
- Keep the list practical: choose ingredients that work across meals, sensible package amounts, and products likely to be used before they spoil.
- Do not invent quantities when they materially affect price or safety. Ask or clearly label an estimate.
- Do not add products to a store website's shopping list; this skill plans the list. Use `fill-k-ruoka-list` only when the user asks to transfer the list to K‑Ruoka, and `fill-s-kaupat-cart` only when the user asks to build an S-kaupat cart.

Read [references/preferences.md](references/preferences.md) for profile fields and handling preferences. Read [references/list-format.md](references/list-format.md) for the output format.
