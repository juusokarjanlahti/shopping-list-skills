# Changelog

Notable changes to this repository. Versions follow [Semantic Versioning](https://semver.org/). While the version is 0.x, skill names and structure may still change between releases.

## [0.1.0] - 2026-11-03

First tagged release.

### Skills

- `plan-shopping-list` plans meals and a shopping list from your needs, budget, preferences, and hard constraints.
- `analyze-shopping-list` describes or reviews an existing list from the perspective you choose.
- `transfer-shopping-list` takes a reviewed list to a store: a price check, a saved shopping list, or the online cart.
  - K‑Ruoka (K-Market, K-Supermarket, K-Citymarket): price check, shopping list, cart.
  - S-kaupat (Prisma, S-market, Sale, Alepa): price check, shopping list, cart.
  - Lidl: price check with store-specific offers.

### Principles

- **The skills prepare; you commit.** No skill reserves a pickup or delivery time, places an order, or pays.
- Allergies, prohibited products, and ingredients you avoid are hard constraints. Unverifiable products are left out.
- Building a shopping list is also its price check. Questions are asked once, before the first change; unresolved product choices are reported at the end.
- Generic items get an ordinary everyday version, and the final report says what was chosen so you can swap it.
- Package size follows the planned need rather than the lowest unit price. Store and location are never inferred.

### Changed

- `fill-k-ruoka-list` and `fill-s-kaupat-cart` are replaced by `transfer-shopping-list`. If you installed either one, remove it and install `transfer-shopping-list`.

### Testing

- `transfer-shopping-list` includes nine scenario tests in `evals/` that run without a store account. Before this release all nine passed (29 checks). The first run showed agents asking about product variants the user never mentioned and planning to skip ordinary items like milk; after the fix, the three cases where this was clearest were re-run and passed, and two checks now guard against it.
