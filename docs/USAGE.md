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

Start `plan-shopping-list` using the method provided by your AI tool. Tell it the time period, household size, meals or goals, budget (target or hard limit), items already at home, preferences, and constraints. If you want a store-specific price estimate, name the store or branch.

Review quantities, suggested products, substitutions, and budget assumptions before transferring the list to a store service.

A budget estimate uses the prices of the packages you need to buy, not just the portion used in meals. When prices are available, compare package price and size as well as unit prices for comparable products. Missing prices are reported, not guessed.

## 2. Fill a K‑Ruoka list

Start `fill-k-ruoka-list` in your AI tool. Provide the reviewed list, the correct shared K‑Ruoka list or its link, the selected store if known, and your priorities for brands, domestic origin, fresh or frozen, preparation level, and package size. Say whether substitutions are allowed. The skill skips unclear products and reports them at the end.

Example:

> Add the reviewed list below to my shared K‑Ruoka shopping list. Prefer K-Menu or Pirkka and domestic origin if the price difference is no more than 20%. Frozen vegetables are fine. Do not replace products I named precisely. Skip unclear matches and tell me what you could not add. Do not move anything to the cart.

Include the reviewed list after your request.

## Browser access and responsibilities

Filling a K‑Ruoka list requires browser or computer control in the AI tool you choose. You must sign in with your own account and confirm that you can edit the shared list. Without these conditions, the skill cannot fill the list.

The skill instructions do not grant access to a browser or account. You are responsible for your chosen platform's tools, settings, privacy, and terms. Review product choices and confirm on the site that changes appear on the correct list.

Product search may show a different store's assortment from the one selected for the shopping list. Before making changes, check the list name, store, edit access, and current items. Stop if the correct list or edit access is unclear.

## Scope of changes

This skill only adds products to the requested shopping list. Moving items to a cart, placing an order, paying, selecting delivery, and changing list-sharing settings are separate actions and are not included.

## Final report

At the end, report:

- the number and names or categories of products added;
- skipped products and the reasons;
- the selected store and unavailable products;
- the amount shown by the site, if reliable;
- whether the additions were saved to the list;
- that no cart or order was created.

## Personal information

Do not add shared-list links, credentials, allergies, preferences, or shopping-list contents to a public repository. Keep them local.
