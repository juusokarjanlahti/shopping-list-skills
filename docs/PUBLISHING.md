# Publish the repository on GitHub

This folder can be reviewed locally before publishing.

1. Confirm the license: this repository uses the MIT License (`LICENSE`).
2. Create a new repository on GitHub and choose its visibility. Do not initialize it with another README; this folder already contains one.
3. Copy the repository's HTTPS or SSH URL.
4. Open a terminal in this folder and publish the files, for example:

   ```sh
   git init -b main
   git add README.md LICENSE .gitignore .agents docs
   git commit -m "Add grocery shopping list skills"
   git remote add origin <GitHub-repository-URL>
   git push -u origin main
   ```

If this folder is already a Git repository, skip `git init -b main`. Review `git status` before committing and make sure only files intended for public release are included.

Do not publish shopping-list links, allergies, dietary restrictions, credentials, preference profiles, or shopping-list contents. Keep these details local and out of Git.

You can install the repository's skills into multiple agents with Vercel's `skills` CLI, for example `npx skills add OWNER/REPO --agent claude-code`. To distribute through a Claude Code plugin marketplace, package the skills as a plugin and add a marketplace catalog; see [Claude Code's publishing guide](https://code.claude.com/docs/en/plugins/publish). Check each other platform's installation instructions. The platform's capabilities and the user's account permissions determine which actions are possible.
