# Shopping list output format

Return a list that is easy to use in a store on a phone. Group products under a few familiar store departments. Each line should include:

- the product or ingredient name;
- the quantity or package count with units;
- the meal name only when it prevents confusion;
- a flexible-choice note when alternatives are acceptable.

After the list, state assumptions, estimated quantities, budget estimate, and unresolved questions. If the budget is tight, separate essential and optional products. Do not add store product codes or exact brands during planning unless the user asks for them.

When prices are available, show at least the estimated total for the packages to buy. For relevant comparisons, include unit price, package price, and package size. Explain that the calculated value of ingredients used is not the same as the full package cost paid at checkout. State the price source, date, store, and uncertainty. Do not give a precise total when some prices are missing; show a partial total or range and list the missing prices.

Example:

```text
Fruit and vegetables
- Bananas, 6
- Carrots, about 500 g

Dry goods
- Rolled oats, 1 package
- Kidney beans, 2 cans

Assumption: list covers five weekday meals for two people.
Flexible choice: frozen spinach can replace fresh spinach.
```
