# Using the skills

## Install from GitHub

Once this repository is published on GitHub, install its skills into a supported agent with Vercel's `skills` CLI:

```sh
npx skills add OWNER/REPO --agent claude-code
```

Replace `OWNER/REPO` with the GitHub user or organization and repository name. The command discovers the skills and asks which ones to install. Change `claude-code` to the identifier for your agent. Invoke the installed skill using your platform's method.

## Analyze an existing list

Start `analyze-shopping-list` and say what you want to learn. It does not assume the list needs to be changed or judged by generic criteria.

Examples:

- "Group this list by product category. Do not judge it or suggest changes."
- "Compare the unit prices of these products using the prices and package sizes provided."
- "Review this list against my budget and brand preferences, and suggest savings without changing exact products or allergy restrictions."

If you do not specify a perspective, the skill asks what you want to find out or offers neutral analysis options.

## 1. Plan and review a list

Start `plan-shopping-list` using the method provided by your AI tool. Tell it the time period, household size, meals or goals, budget (target or hard limit), items already at home, preferences, and constraints. For a store-specific price estimate, name the store or stores and say whether you prefer in-store shopping, pickup, or delivery. When you name several stores, the first is treated as primary and the others as comparison candidates unless you say they are equal alternatives or choose a different primary store. Nearby-store comparisons use an area or postal code you provide; vehicle access is optional.

Review quantities, suggested products, substitutions, and budget assumptions before transferring the list to a store service.

A budget estimate uses the prices of the packages you need to buy, not just the portion used in meals. When prices are available, compare package price and size as well as unit prices for comparable products. Prefer package amounts that reasonably meet the planned need and avoid unnecessary surplus; a lower unit price alone does not justify a larger pack. Missing prices are reported, not guessed. A store comparison uses the same basket where possible, keeps unavailable items visible, and does not split the basket across stores unless you ask it to consider that option.

## 2. Transfer the list to a store

Start `transfer-shopping-list` in your AI tool. Name the store and choose a destination:

- **Price check** — prices and availability for the list at one store, returned in the chat. Nothing is saved to your account. This is the only option for Lidl, whose website has no shopping lists or online orders.
- **Shopping list** — products are added to a saved list in your K‑Ruoka or S-kaupat account. The skill records each product's price as it adds it, so the finished list is also your price check. A list is reusable and commits to nothing, so it is the suggested choice if you are unsure. Once it is ready, decide whether to shop in the store or ask for the list to be moved to the cart for pickup or delivery.
- **Cart** — products are added to your K‑Ruoka or S-kaupat cart for a store and pickup or delivery.

If you do not name a destination, the skill asks. It never chooses the cart on its own.

Provide the reviewed list, the store or stores you want used, and for a shopping list the correct list or its link. Add your priorities for brands, domestic origin, fresh or frozen, preparation level, and package size, and say whether substitutions are allowed. If the site has a different store selected, the skill asks you to confirm before relying on that store. It skips unclear products and reports them at the end.

Examples:

> Add the reviewed list below to my shared K‑Ruoka shopping list. Prefer K-Menu or Pirkka and domestic origin if the price difference is no more than 20%. Frozen vegetables are fine. Do not replace products I named precisely. Skip unclear matches and tell me what you could not add.

> Add the reviewed list below to my S-kaupat cart for pickup at my chosen Prisma store. Skip unclear products or substitutions and tell me what you added.

> Price-check the list below at my chosen Lidl store. Show offers separately from regular prices, with their validity dates.

Include the reviewed list after your request.

If an S-kaupat or K‑Ruoka pickup or delivery time is missing or has expired, the skill stops and tells you. Choose or renew it yourself, then ask the skill to continue.

## Browser access and responsibilities

Transferring a list requires browser or computer control in the AI tool you choose. For a shopping list or cart, you also need a signed-in account that can edit that list or cart. Without these, the skill cannot make the requested changes; a price check may still work if the store shows prices without signing in.

The skill instructions do not grant access to a browser or account. You are responsible for your chosen platform's tools, settings, privacy, and terms. Review product choices and confirm on the site that changes appear on the correct list or cart.

Product search may show a different store's assortment from the one selected for the shopping list or cart. Before making changes, the skill checks the destination, intended store, edit access, and current items. A site-selected branch does not mean you chose it. The skill stops if the correct list or edit access is unclear. It does not infer your precise location or access to a car, and it does not split a basket between stores unless you ask for that comparison.

## Scope of changes

The skills prepare; you commit. `transfer-shopping-list` adds products only to the destination you name, or only reads prices in a price check. No skill in this repository reserves or changes a pickup or delivery time, places an order, or pays — not even when asked, because those steps belong on the store's own checkout page where you see the final total and terms. Choosing products, building a cart, or having a time slot selected does not authorize an order.

## Final report

At the end, the skill reports:

- the store and destination: the list's name, the cart and its pickup or delivery method, or a price check;
- the products added or priced, with quantities;
- skipped and unavailable products, with reasons;
- the estimated product total shown by the site, marking offers, member prices, and missing prices;
- for a list or cart, whether the additions were saved and verified;
- that no time slot was reserved, no order was placed, and nothing was paid; for a shopping list, also that nothing was moved to the cart.

## Testing

`transfer-shopping-list` includes scenario tests in its `evals/` folder. They describe situations on store websites — a pre-selected store, an expired pickup time, an unverifiable allergen, instructions hidden in page text — and check the skill's response without a store account. With Claude Code, run `claude plugin eval . --allow-tools Write,Edit,Bash` in the skill's directory. These are real, billed model runs.

## Personal information

Do not add shared-list links, receipts, credentials, allergies, preferences, or shopping-list contents to a public repository. Keep them local.
