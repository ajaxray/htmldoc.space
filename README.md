# htmldoc.space

Share one HTML or Markdown file as an unlisted link that lives 30 days. Ask your AI agent, or run one command. No deploy, no repo, no drag-and-drop.

## Ask your agent

Install the skill once, then say "share this report" in Claude Code, Codex, Pi, or [any agent that supports skills](https://www.skills.sh/agent). The agent runs the CLI and hands you the link. It never sees your key.

```sh
npx skills add ajaxray/htmldoc-skill
```

Then ask your agent in plain words: **"share this report"**, **"publish process.html with htmldoc"**, or **"make this plan shareable"**. It replies with the link and the expiry date.

![Claude Code answering "share the report.html" with a link](demo/agent.gif)

## Or run one command

No install needed. stdout is only the URL, so it pipes.

```sh
npx -y htmldoc-cli report.html
# https://p.htmldoc.space/NO8JWj8cd57m
```

![npx htmldoc-cli report.html prints a share link](demo/cli.gif)

Both links above are real pages, shared with the tool while recording: [the agent's](https://p.htmldoc.space/SQBQdOCsiEhS) and [the CLI's](https://p.htmldoc.space/NO8JWj8cd57m). Open one.

## Links

- Sign in and get a key: [htmldoc.space](https://htmldoc.space/?utm_source=github)
- Docs: [htmldoc.space/docs](https://htmldoc.space/docs?utm_source=github)
- CLI: [`htmldoc-cli` on npm](https://www.npmjs.com/package/htmldoc-cli), source [ajaxray/htmldoc-cli](https://github.com/ajaxray/htmldoc-cli)
- Agent skill: [ajaxray/htmldoc-skill](https://github.com/ajaxray/htmldoc-skill) on [skills.sh](https://skills.sh)

## This repo has no code

It is the public home of the product: the [roadmap](ROADMAP.md), the [changelog](CHANGELOG.md), demo assets, and the issue tracker. The service itself is closed source and runs on one small server, by one person.

## Where to report what

| You want to | Go to |
|---|---|
| Ask for a feature, vote on the roadmap, report the site being down or wrong | [Issues here](https://github.com/ajaxray/htmldoc.space/issues) |
| Report a bug in the `htmldoc` command | [htmldoc-cli issues](https://github.com/ajaxray/htmldoc-cli/issues) |
| Report the agent skill misbehaving | [htmldoc-skill issues](https://github.com/ajaxray/htmldoc-skill/issues) |
| Report a page that should not be online | The **Report** link in the badge on that page, or [htmldoc.space/report](https://htmldoc.space/report) |
| Anything private | [htmldoc.space/contact](https://htmldoc.space/contact) |

## Roadmap

Every planned item is an issue labelled [`roadmap`](https://github.com/ajaxray/htmldoc.space/issues?q=is%3Aissue+is%3Aopen+label%3Aroadmap+sort%3Areactions-%2B1-desc). React with 👍 on the ones you want; that list is sorted by votes and it is what gets built next. Nothing on it is promised.

## Facts worth knowing

One file per link. HTML is served byte for byte; Markdown is rendered server-side. Caps: 2 MB HTML, 512 KB Markdown, 100 live pages per account. Links expire after 30 days; re-sharing with `--update` keeps the URL and resets the clock. Every page carries a small badge with a Report link and nothing else. No analytics or ads on pages. GitHub sign-in, one API key per account. Free.
