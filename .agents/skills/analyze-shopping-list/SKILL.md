---
name: analyze-shopping-list
description: Analyze a grocery or shopping list from the user's chosen perspective, such as contents, prices, package sizes, or their own preferences. Use when the user asks to describe, review, or compare an existing list.
metadata:
  short-description: Analyze a shopping list from the user's perspective
---

# Analyze a shopping list

Describe or review the user's list from the perspective they request. By default, a list is not good, bad, healthy, expensive, balanced, or incomplete. Do not decide what it should become.

If the user does not specify a perspective, briefly ask what they want to find out. If the request is clear enough, answer without unnecessary questions. You may offer neutral options such as product groups, quantities, prices, unit prices, domestic origin, brands, frozen foods, ready-to-use foods, duplicates, or the user's own goals, but do not choose one for them.

## Neutral analysis

- Separate directly observable details, calculations, interpretations, and uncertainties.
- Say what information supports each claim. Do not invent prices, package sizes, origin, ingredients, or product details.
- For budget or price requests, distinguish the user's budget target from a hard limit. Estimate the cost of packages to buy; if prices are missing, explain what cannot be calculated.
- When available, show unit price alongside package price and package size. Unit prices are comparable only when product type, unit, and comparison basis (for example, drained weight) match.
- Separate the estimated checkout total from the calculated value of ingredients used. State the price source, store, date, and whether prices include membership discounts or offers.
- If the budget is exceeded or cannot be verified, say so directly. Do not suggest savings unless requested; if they are requested, keep allergies and other hard constraints in force.
- Use the user's own criteria and constraints. Do not replace them with a generic view of what is a better choice.
- Do not label products or the user's choices with value judgments such as "bad", "unhealthy", or "unnecessary" unless the user requests that assessment and defines its criteria.
- If the requested metric is ambiguous, state your definition or ask a question when the choice would materially change the conclusion.
- Suggest changes only when the user asks for recommendations. Tie them to the user's goals and explain relevant trade-offs.
- Do not modify a store shopping list, cart, or user profile during analysis. That requires a separate request and the appropriate skill.
- If the user asks you to analyze past purchases from store receipts, such as electronic receipts in a store account, use only the receipts they point to or ask you to open, and take only the details the analysis needs. Receipt prices are historical: label them with the purchase date. Do not copy receipt contents into a repository or saved profile.

## Hard food and allergy constraints

User-reported allergies, prohibited products or ingredients, and other hard constraints remain in effect throughout analysis. Do not recommend a product that conflicts with them or treat a restriction as a preference to weigh against something else. If the requested analysis requires checking a product's suitability, do not infer safety from incomplete information. State what information is missing; an unclear product is not confirmed suitable.

If a list item appears to conflict with a known allergy or prohibition, point out the conflict neutrally. Do not assess the product as safe or unsafe unless reliable ingredient information is available. Do not remove or change a list item without a separate user request.

## Response format

Shape the response to the request. Usually:

1. state the analysis perspective;
2. present findings and calculations clearly;
3. mark uncertain or missing information;
4. give recommendations only when requested, tied to the user's stated goals.

Read [references/analysis-guidelines.md](references/analysis-guidelines.md) for examples and general checks.
