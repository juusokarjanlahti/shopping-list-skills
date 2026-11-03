# 🛒 Shopping List Skills

**Plan, review, and take a grocery list to the store on your own terms.** This repository contains three reusable [Agent Skills](https://agentskills.io): one plans a list, one analyzes it, and one takes a reviewed list to K‑Ruoka, S-kaupat, or Lidl. Your needs and constraints guide the work: the tools do not assume what your shopping list should look like.

> [!IMPORTANT]
> - **The skills prepare; you commit.** No skill reserves a pickup or delivery time, places an order, or pays. Those steps stay with you on the store's own checkout page.
> - Allergies, prohibited products, and ingredients you avoid are hard constraints. If a product's suitability cannot be verified, the skill leaves it out.

## Contents

- [Skills](#-skills)
- [Store support](#-store-support)
- [First time using Codex](#-first-time-using-codex)
- [Install](#-install)
- [Examples](#-examples)
- [Budget and prices](#-budget-and-prices)
- [Browser access and responsibilities](#-browser-access-and-responsibilities)
- [Testing](#-testing)
- [Privacy](#-privacy)
- [License](#-license)

## 🧰 Skills

| Skill | Use it when | What it does |
| --- | --- | --- |
| [`plan-shopping-list`](.agents/skills/plan-shopping-list/SKILL.md) | You want to build a new list | Plans meals and a shopping list from your needs, budget, preferences, and constraints. |
| [`analyze-shopping-list`](.agents/skills/analyze-shopping-list/SKILL.md) | You already have a list | Describes or reviews the list from the perspective you request, such as quantities, prices, or product groups. |
| [`transfer-shopping-list`](.agents/skills/transfer-shopping-list/SKILL.md) | You want to take a reviewed list to a store | Price-checks the list at a store you choose, or adds it to a saved shopping list or the online cart. You choose the destination. |

Use the skills independently. A typical flow is planning → review or analysis → optional transfer to a store. Transfer needs its own request, and you choose the destination: a price check, a saved shopping list, or the cart. If you are unsure, use a shopping list: it is reusable and commits to nothing.

Earlier versions had separate `fill-k-ruoka-list` and `fill-s-kaupat-cart` skills. Both are now part of `transfer-shopping-list`.

## 🏪 Store support

| Store | Price check | Shopping list | Cart | Order, time slot, payment |
| --- | --- | --- | --- | --- |
| K‑Ruoka (K-Market, K-Supermarket, K-Citymarket) | ✓ | ✓ | ✓ | Never by a skill |
| S-kaupat (Prisma, S-market, Sale, Alepa) | ✓ | ✓ | ✓ | Never by a skill |
| Lidl | ✓ store-specific offers | – | – | Not offered online |

Store notes live in [`transfer-shopping-list/references/stores/`](.agents/skills/transfer-shopping-list/references/stores/). They reflect the sites as tested in November 2026. To add a store, add one file there describing its destinations and site behaviour.

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

   The other available skills are `$analyze-shopping-list` and `$transfer-shopping-list`.

The skills are instructions Codex can follow; they do not provide browser access or log you in to a store. Transferring a list requires browser/computer control in your Codex setup. Adding to a shopping list or cart also requires a signed-in account with edit access to that list or cart. Review the products before asking Codex to transfer them.

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

### Transfer a list to a store

Review the plan first. Then ask separately, naming the store and the destination:

> Add this reviewed list to my shared K‑Ruoka shopping list. Follow the budget and product preferences I gave you. Skip unclear products and tell me what you added.

> Add this reviewed list to my S-kaupat cart for pickup at my chosen Prisma store. Skip unclear products or substitutions and tell me what you added.

> Price-check this list at my chosen Lidl store, including its current offers. I will shop in the store.

Invocation varies by platform. For example, Codex can use `$plan-shopping-list`, `$analyze-shopping-list`, and `$transfer-shopping-list`; Claude Code can use the corresponding `/skill-name` commands.

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

Transferring a list requires browser or computer control in the AI tool you choose. For a shopping list or cart, you must be signed in to the store's service and able to edit that list or cart. A skill file does not grant these permissions.

`transfer-shopping-list` adds products only to the destination you name. It does not move list items to the cart unless you ask for the cart, and it never reserves a pickup or delivery time, places an order, or pays. Review the products and changes on the store website.

You choose and configure your AI platform. You are responsible for its settings, permissions, privacy, and terms of use. Skills provide instructions, not a guarantee that every platform will behave the same way.

### Desktop and mobile

- Planning and analysis need only a chat, so they work on any device where your AI tool can load skills.
- Transferring a list needs a browser the AI can control, which usually runs on a computer, for example the built-in browser in the Claude desktop app. Some tools let you start or follow the task from your phone while the computer does the browsing. The computer must stay awake, online, and running that app.
- K‑Ruoka shopping lists also appear in the K‑Ruoka mobile app, so you can use them in the store.

## 🧪 Testing

`transfer-shopping-list` includes scenario tests in [`evals/`](.agents/skills/transfer-shopping-list/evals/). Each test describes a situation on a store website and checks the skill's response, so it runs without a store account or a real cart. With Claude Code, run them from the skill's directory:

```bash
claude plugin eval . --allow-tools Write,Edit,Bash
```

These are real, billed model runs.

## 🔒 Privacy

Do not publish shopping-list links or contents, receipts, credentials, allergies, dietary restrictions, or personal preferences in this repository. The [`preferences.md` profile template](.agents/skills/plan-shopping-list/references/preferences.md) is blank: keep personal information local and out of version control.

## 📄 License

This repository is licensed under the [MIT License](LICENSE). The Agent Skills format does not require a specific license.

## ⚠️ Limitations

- Product prices, discounts, and availability change.
- The selected store can affect the available products and prices.
- Store websites change; the store notes may fall behind them.
- Store comparisons may be incomplete when a store's assortment, fulfillment fees, or travel costs are not visible.
- Skills are instructions for AI tools, not a store product database or official integration.
- Test changes in your own AI environment before transferring a long shopping list.
