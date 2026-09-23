# Changelog

What shipped, newest first. Three moving parts: the **service** (htmldoc.space and the `p.` viewer), the **CLI** (`htmldoc-cli` on npm), and the **skill** (`ajaxray/htmldoc-skill` on skills.sh).

## 2026-09-24: pinned pages

- Service: pin a page from the dashboard and it stops expiring. A pinned page is never purged and keeps its link. Five pins per account; unpin and the usual 30 days start again from that moment. Pinning an expired page that is still inside its 7-day grace window brings it back. Pinned pages still count toward the 100 live pages.
- Service: `--update` on a pinned page keeps the pin. The API page list adds `pinned`, and a pinned page has no expiry (`expires_at: null`). Pinning is dashboard-only; there is no CLI or API way to pin.
- CLI 0.2.1: `htmldoc list` shows `pinned` in the EXPIRES column, and the line after an upload says `expires: never (pinned)`.
- Docs, landing page, and `llms.txt` describe pinning.

## 2026-09-18: sign in without copying a key

- CLI 0.2.0: `htmldoc login` prints an approval link and a code and opens it in your browser. Sign in with GitHub, check the code, click Approve; the command waits for the click, stores the key, and says who you are. `login --no-wait` and `login --wait` split that in two for agents, which have no terminal. `login --paste` keeps the old copy-the-key way.
- Skill: when the CLI has no key, the agent runs the approval flow itself, relays the link and code word for word, waits for your click, then finishes the share. It never sees the key.
- Service: the approval page at `/connect/<code>`, with GitHub sign-in handing you back to it, and the pairing endpoints behind it. An account is created on first sign-in. Disclosed in the terms and described in `llms.txt`.
- Landing, docs, and dashboard describe both sign-in paths.

## 2026-09-12

- Service: link previews. Every page carries a description, canonical URL, Open Graph and Twitter card, with a 1200×630 image.
- Service: `/robots.txt`, `/sitemap.xml`, and `/llms.txt`. Shared pages stay disallowed and `noindex`.
- Service: guests reading the landing page or docs get no session cookie and cause no database write.
- Service: the landing page counts visits per day and referring source, with no per-visitor data. Disclosed in the terms. Shared pages are not counted.
- Docs: an Examples section with six live pages, a "Why HTML, and what to ask for" section, and a Feedback section pointing at this repo.
- Hero pill reads "unlisted links · free · agent-ready".

## 2026-09-11

- Service: the viewer answers conditional requests with an ETag, so a reopened page that has not changed costs a 304 instead of a re-download.
- Service: page tables on the dashboard and admin panel render as cards on small screens.
- Service: landing and docs say the skill works with any agent that supports skills, not only Claude Code.
- CLI 0.1.2: README leads with a 15-second demo GIF and a three-line pitch; documents the agents the skill supports.
- Skill: README shows the agent demo GIF.

## 2026-09-09: v1 is public

**Service**

- Landing page and `/docs`.
- GitHub sign-in. One API key per account; reveal it or regenerate it from the dashboard.
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
