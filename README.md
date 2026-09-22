# IBM i Skills Hub

A static GitHub Pages catalog for skills used in native IBM i shops. The six starter cards are **ideas**, not finished skills.

## Publish

1. Create a public GitHub repository, for example `ibmi-skills-hub`.
2. Upload the contents of this folder to the repository root, including `.github`.
3. In repository **Settings → Pages**, choose **Deploy from a branch**, then `main` and `/ (root)`; save.
4. Open `https://YOUR-USERNAME.github.io/ibmi-skills-hub/`. Replace the username and repository name with your own.

The **Propose a skill** button opens this repository's GitHub issue form once the site is on a standard GitHub project Pages address. Proposers need a GitHub account. For a custom domain, set the link in `index.html` explicitly.

## Publish an approved skill

1. Review the submission for accuracy, safety, license, and native IBM i relevance. Remove private details.
2. Add `skills/<slug>/SKILL.md` with YAML `name` and `description` followed by instructions.
3. In `skills.json`, set its card's `path` to `skills/<slug>/SKILL.md`, or add a new card with `name`, `category`, `summary`, and `path`.
4. Commit to `main`; GitHub Pages updates from that branch.

GitHub Pages serves static files. Public visitors cannot write directly to `skills.json`; submissions become issues and you publish approved entries through a commit. No account credentials are stored in the site.

Suggested commit message: `Create IBM i skills catalog for GitHub Pages`
