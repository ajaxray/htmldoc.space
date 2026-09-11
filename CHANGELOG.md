# Changelog

What shipped, newest first. Three moving parts: the **service** (htmldoc.space and the `p.` viewer), the **CLI** (`htmldoc-cli` on npm), and the **skill** (`ajaxray/htmldoc-skill` on skills.sh).

## Unreleased

- Service: the landing page counts visits per day and referring source, with no per-visitor data, so a launch post can be traced to sign-ups. Disclosed in the terms. Shared pages are not counted.

## 2026-09-11

- Service: the viewer answers conditional requests with an ETag, so a reopened page that has not changed costs a 304 instead of a re-download.
- Service: page tables on the dashboard and admin panel render as cards on small screens.
- Service: landing and docs say the skill works with any agent that supports skills, not only Claude Code.
- CLI 0.1.2: README leads with a 15-second demo GIF and a three-line pitch; documents the agents the skill supports.
- Skill: README shows the agent demo GIF.

## 2026-09-09: v1 is public

**Service**

- Landing page and `/docs`.
- GitHub sign-in. One API key per account, shown once, regenerable from the dashboard.
- Dashboard: live pages with state and expiry, delete, and **+ New** to share a file from the browser by upload or paste, through the same validation and upload budget as the CLI.
- Viewer on `p.htmldoc.space`: HTML served byte for byte, Markdown rendered server-side, a small badge on every page with a **Report** link, no cookies, no analytics.
- Report form, public, with a lookup page for pasting a link. Reports are stored, then emailed to the operator within a rate limit.
- Admin panel at `/admin` for listed GitHub logins: stats, page and user lists, remove page, suspend user.
- `/terms` and `/contact`.
- Limits: 2 MB HTML, 512 KB Markdown, 100 live pages per account, 10 uploads a minute and 100 a day. 30-day expiry with a 7-day grace window, then the body is purged.

**CLI 0.1.0** (npm, 2026-09-08)

- `htmldoc <file>` uploads an `.html`, `.htm`, `.md`, or `.markdown` file and prints only the share URL on stdout; id and expiry go to stderr.
- `--update <id|url>` keeps the URL and resets the 30 days. `--json` prints id, URL, and expiry as one line.
- `htmldoc login` (hidden paste), `htmldoc list [--json]`, `htmldoc delete <id|url>`.
- Files are checked locally before any request: extension, size, non-empty, UTF-8.
- `HTMLDOC_API_KEY` for agents and CI. Zero dependencies, Node 22 or newer. MIT.

**Skill**

- `npx skills add ajaxray/htmldoc-skill`. Triggers on "share this doc", "share this plan", "publish this with htmldoc", and the like. Runs the CLI, never touches the key, replies with the link and expiry, and remembers the id for "share again".
