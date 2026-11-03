# S-kaupat (s-kaupat.fi)

Stores: Prisma, S-market, Sale, and Alepa stores in the S-kaupat online service.

| Destination | Supported | Notes |
| --- | --- | --- |
| Price check | Yes | Prices, offers, and availability depend on the selected store. |
| Shopping list | Yes | Saved lists are in the user's profile. Moving list items to the cart is a separate destination. |
| Cart | Yes | The cart belongs to the selected store and fulfillment method (pickup or delivery). |
| Time slot, order, payment | Out of scope | S-kaupat supports online orders, but this skill never reserves a time, orders, or pays. |

## Site notes

- A pickup or delivery time is its own reservation, separate from the cart. It can be missing or expire while you work. If the site asks you to choose or renew a time, stop and tell the user; choosing it is their step.
- A store, fulfillment method, or time slot already shown on the site is not proof the user chose it. Confirm the store and method the user named.
- After each addition, check the cart's product line and quantity before the next one. The cart view can lag behind an add action, and repeating the action can add the product twice.
- Some fresh goods are sold by the piece with an estimated price. Report the estimate and say the final amount may vary.

## If the site differs

These notes reflect the site as tested in November 2026. If the site behaves differently, follow what you see, tell the user about the difference, and stop before any step that goes beyond the requested destination.
