# Security and privacy notes

## How editing is protected

The public website has no administrator route, server-side login, database, or private browser configuration. Content editing happens separately at Pages CMS. Its hosted app signs you in with GitHub and writes changes to the selected repository using GitHub authorization. Keep repository write access limited to your own trusted accounts, install the Pages CMS GitHub App only on the portfolio repository when possible, and do not invite CMS collaborators unless they should be able to publish edits.

The Pages CMS configuration in `.pages.yml` is not a secret. It defines which content fields appear in the editor; it does not grant access by itself. GitHub repository permissions and the CMS's GitHub authorization protect repository changes. Pages CMS is a third-party hosted service, separate from GitHub Pages.

## What is public

GitHub Pages publishes a public site. Every visitor can download its HTML, JavaScript, CSS, images, and `content/portfolio.json`. Do not put passwords, API keys, confidential CV files, private contact-request records, or other secrets in the repository or page content. A public repository also exposes its source files. GitHub Free requires a public source repository for GitHub Pages; eligible paid plans can publish from a private repository, but the deployed website remains public.

Browser storage, hidden controls, JavaScript checks, and client-side access codes are not server-enforced access control. This release does not use the old browser-only editor or local browser state as its source of truth. CMS-managed `content/portfolio.json` is loaded as the public content. Do not use a client-side CV unlock flow to protect sensitive material.

## Safeguards in this release

- The old browser-only Studio/editor and owner-review controls are hidden and forced off in the public build.
- The content loader ignores prior browser-stored edits and old exported content snapshots, so repository CMS data remains authoritative.
- Restoring an old browser backup cannot enable owner mode in this release.
- Project/contact links reject unsafe schemes; form destinations must use HTTPS and cannot embed credentials.
- Dynamic image URLs allow HTTPS, supported image data URLs, or safe relative repository paths, so CMS media uploads can work under a GitHub Pages project URL.
- External links opened in new tabs use `noopener noreferrer`, and a strict-origin referrer policy is set.

These safeguards reduce accidental exposure and unsafe URL use. They do not turn the website into a private application.

## Publishing safely

Review portfolio text, claims, public email/phone details, contact URLs, project links, and image sources before saving a CMS change. Changes written to the configured GitHub Pages branch publish to the public site. If the wrong content is committed, revert that repository change and wait for Pages to deploy again.

The contact form is blank by default. Use a form provider intended for public client-side submissions, configure its spam protection and allowed domains there, and collect only necessary information. Never place API tokens or provider credentials in the HTML or JSON.

GitHub Pages does not let repository files set arbitrary HTTP response headers. For stronger headers such as a restrictive Content-Security-Policy, use a hosting layer that supports them and test the policy there. This page currently contains inline scripts and styles, so a strict policy requires refactoring those first. `frame-ancestors` must be delivered as an HTTP header rather than a CSP meta tag.
