# 🛒 Shopping List Skills

**Plan, review, and fill a grocery list on your own terms.** This repository contains four reusable [Agent Skills](https://agentskills.io), including skills for K‑Ruoka lists and S-kaupat carts. Your needs and constraints guide the work: the tools do not assume what your shopping list should look like.

> [!IMPORTANT]
> Allergies, prohibited products, and ingredients the user avoids are hard constraints. If a product's suitability cannot be verified, the skill says to leave it out.

## Contents

- [Skills](#-skills)
- [First time using Codex](#-first-time-using-codex)
- [Install](#-install)
- [Examples](#-examples)
- [Budget and prices](#-budget-and-prices)
- [Browser access and responsibilities](#-browser-access-and-responsibilities)
- [Privacy](#-privacy)
- [License](#-license)

## 🧰 Skills

| Skill | Use it when | What it does |
| --- | --- | --- |
| [`plan-shopping-list`](.agents/skills/plan-shopping-list/SKILL.md) | You want to build a new list | Plans meals and a shopping list from your needs, budget, preferences, and constraints. |
| [`analyze-shopping-list`](.agents/skills/analyze-shopping-list/SKILL.md) | You already have a list | Describes or reviews the list from the perspective you request, such as quantities, prices, or product groups. |
| [`fill-k-ruoka-list`](.agents/skills/fill-k-ruoka-list/SKILL.md) | You want to copy a reviewed list to K‑Ruoka | Finds products for a K-Market, K-Supermarket, or K-Citymarket store selected in K‑Ruoka and adds them to your list, if your AI tool supports browser control and you can edit it. |
| [`fill-s-kaupat-cart`](.agents/skills/fill-s-kaupat-cart/SKILL.md) | You want to build an S-kaupat cart | Adds clearly matched products from a reviewed list to your cart for a store and fulfillment option you chose. It stops before reserving a time, ordering, or paying. |

Use the skills independently. A typical flow is planning → review or analysis → optional transfer to a store. Filling a K‑Ruoka list and building an S-kaupat cart are separate actions and each requires its own request.

## 🧑‍💻 First time using Codex

You do not need to install the skills separately to try them in Codex:

1. Download this repository from GitHub with **Code → Download ZIP**, then extract the archive. Alternatively, clone the repository with Git.
2. In Codex, open the extracted `shopping-list-skills` folder as your project. Open the repository root—the folder containing this `README.md` and the `.agents/` directory.
3. Start a chat in that project. Codex discovers project skills in `.agents/skills/` automatically.
4. Ask naturally, or call a skill by name. For example:

   ```text
   $plan-shopping-list
   Plan two days of meals for two people. My budget is €50. I have rice at home.
   ```

   Other available skills are `$analyze-shopping-list`, `$fill-k-ruoka-list`, and `$fill-s-kaupat-cart`.

The skills are instructions Codex can follow; they do not provide browser access or log you in to a store. Filling a K‑Ruoka list or building an S-kaupat cart requires browser/computer control in your Codex setup and a signed-in account. For K‑Ruoka, you also need edit access to the target list. Review the products before asking Codex to fill a website list or cart.

## 🚀 Install

The skill instructions are platform-independent, but installation paths and invocation methods vary by AI tool.

| AI tool | Skill directory in this repository |
| --- | --- |
| Codex | `.agents/skills/` |
| GitHub Copilot | `.agents/skills/` |
| Claude Code | `.claude/skills/` |
| Other tools | Check the tool's own documentation |

Codex and GitHub Copilot can use this repository's `.agents/skills/` directory. For Claude Code, copy the skill directories to `.claude/skills/`. The Agent Skills format does not guarantee that every tool supports browser control or the same capabilities.

See the [usage guide](docs/USAGE.md) and [GitHub publishing guide](docs/PUBLISHING.md) for details.

### Install with the skills CLI

After publishing this repository on GitHub, install its skills into Claude Code or another supported agent with Vercel's [`skills` CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add OWNER/REPO --agent claude-code
```

Replace `OWNER/REPO` with the GitHub user or organization and repository name. The CLI finds the repository's skills and lets you choose which ones to install. Change `claude-code` to the identifier of another supported agent as needed.

## 💬 Examples

### Plan a list

Tell the skill about meals, household size, budget, food you already have, preferences, and hard constraints. For example:

> Plan meals for two for three days. My budget is at most €60. Use the potatoes and beans I already have. No ready-made meals. Avoid peanuts.

### Analyze a list

Say what you want to find out. The analysis skill does not assume the list should be judged or changed:

> Group this list by product category and estimate the cost of the packages I need to buy. Do not suggest changes.

### Fill a K‑Ruoka list

Review the plan first. Then separately ask the skill to fill the correct shared list:

> Add this reviewed list to my shared K‑Ruoka shopping list. Follow the budget and product preferences I gave you. Skip unclear products and tell me what you added. Do not move anything to the cart.

### Fill an S-kaupat cart

Review the plan first, then separately ask the skill to add clear product matches to your cart:

> Add this reviewed list to my S-kaupat cart for pickup at my chosen Prisma store. Skip unclear products or substitutions and tell me what you added. Do not change the pickup time, place an order, or pay.

Invocation varies by platform. For example, Codex can use `$plan-shopping-list`, `$analyze-shopping-list`, `$fill-k-ruoka-list`, and `$fill-s-kaupat-cart`; Claude Code can use the corresponding `/skill-name` commands.

## 💶 Budget and prices

- Say whether your budget is a **target** or a **hard limit**.
- Estimate the cost of the packages to buy. This differs from the calculated value of only the ingredient amounts used in recipes.
- Where possible, show the unit price (such as €/kg) alongside package price and package size. Unit price alone does not tell you which purchase costs less today.
- State the store and the date of price information when known. Mark member prices, discounts, and missing prices; never invent prices.
- For comparisons, name the stores you want considered and your preferred way to shop (in-store, pickup, or delivery). The first store named is the default primary store; other stores are comparison candidates. The skills do not assume a larger store is preferable or split a basket automatically.
- Package size should reflect the planned need. A lower unit price does not by itself justify buying a larger pack: consider the full checkout price and likely leftover, and do not assume extra food will be used, shared, or gifted.
- Include pickup, delivery, or travel costs only when they are visible or you provide them. Nearby-store comparisons need an area or postal code from you; vehicle access is optional and is never inferred.
- If the budget is exceeded, report the difference instead of silently changing products. Do not violate allergies, prohibitions, or exact product requirements to save money.

## 🖥️ Browser access and responsibilities

Filling a K‑Ruoka list or building an S-kaupat cart requires browser or computer control in the AI tool you choose. You must be signed in to the relevant service; for K‑Ruoka, you also need permission to edit the specific list. A skill file does not grant these permissions.

The K‑Ruoka skill adds products to a shopping list. The S-kaupat skill adds products to a cart. Neither skill reserves a pickup/delivery time, places an order, or pays. Review the products and changes on the store website.

You choose and configure your AI platform. You are responsible for its settings, permissions, privacy, and terms of use. Skills provide instructions, not a guarantee that every platform will behave the same way.

## 🔒 Privacy

Do not publish shopping-list links or contents, credentials, allergies, dietary restrictions, or personal preferences in this repository. The [`preferences.md` profile template](.agents/skills/plan-shopping-list/references/preferences.md) is blank: keep personal information local and out of version control.

## 📄 License

This repository is licensed under the [MIT License](LICENSE). The Agent Skills format does not require a specific license.

## ⚠️ Limitations

- Product prices, discounts, and availability change.
- The selected store can affect the available products and prices.
- Store comparisons may be incomplete when a store's assortment, fulfillment fees, or travel costs are not visible.
- Skills are instructions for AI tools, not a store product database or official integration.
- Test changes in your own AI environment before filling a long shopping list.
