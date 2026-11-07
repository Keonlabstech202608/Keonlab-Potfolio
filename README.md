# Keonlabs Tech Portfolio

A responsive static portfolio for Keon Edgar. The published page reads its editable content from `content/portfolio.json`. The root `.pages.yml` file configures the separate Pages CMS editor. There is no site-side admin login, database, or backend.

## Preview locally

Because the page fetches its JSON content file, open the project through a local static-file server rather than double-clicking `index.html`. For example, use VS Code Live Server from this folder.

## Publish on GitHub Pages

Create a GitHub repository and put the project files at its root: `index.html`, `.pages.yml`, `content/portfolio.json`, `README.md`, `SECURITY.md`, and `.gitignore`. Keep repository write access limited to your own GitHub account.

On GitHub, open **Settings → Pages** and choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then save. When deployment completes, open the site URL and verify the portfolio. Enable **Enforce HTTPS** under the same Pages settings when it is available. Changes to the repository branch are published by GitHub Pages; content edits update `content/portfolio.json`.

GitHub Pages on GitHub Free requires a public source repository. On eligible paid plans, a private source repository may be used, but the published site is still publicly accessible. In either case, repository files and website content should be treated as public. See [GitHub's Pages plan and repository requirements](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site).

## Edit the live portfolio

1. Go to [Pages CMS](https://app.pagescms.org/) and sign in with your GitHub account.
2. Install the Pages CMS GitHub App for the account that owns this repository. Grant access only to this portfolio repository if GitHub offers a repository-selection choice.
3. Open the repository in Pages CMS. It reads `.pages.yml` and shows the structured **Portfolio content** editor.
4. Edit profile, projects, skills, services, education, contact details, and visual theme. Save the changes. Pages CMS writes repository changes; GitHub Pages then publishes the updated JSON and site.

Only grant repository write access to people you trust to change the published portfolio. Do not invite additional CMS collaborators unless you intend them to be able to edit the content. Pages CMS is a separate hosted service; its sign-in and GitHub authorization are not provided by this website.

## Content, images, and contact details

Anything in `content/portfolio.json` is delivered to every visitor and is public. The profile and project image fields accept HTTPS URLs or safe relative paths. Uploaded images can be stored in `assets/media` through the CMS media library; use a relative path such as `assets/media/example.jpg` in an image URL field. Never place passwords, API keys, private CVs, or other secrets in the content file.

The contact form endpoint is intentionally blank. If you connect a form provider, use its public HTTPS endpoint and configure spam controls and privacy information with that provider. Do not put provider credentials in the page or JSON file.

## Security notes

See [SECURITY.md](SECURITY.md) for the static-site threat model and publishing safeguards. GitHub Pages does not run the authenticated editor; the editor is at Pages CMS and uses GitHub repository permissions. The website itself is public.
