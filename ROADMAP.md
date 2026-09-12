# Roadmap

Ideas to weigh now that v1 is out. Nothing here is committed. The filter for every item: does it make a shared link more useful to the reader, or to the agent that published it, without turning htmldoc into a hosting product?

Positioning to keep: the publish step for agents and one-command sharing. Unlisted links, 30 days, one file, no install.

Each item is an issue. 👍 the ones you want; [this list](https://github.com/ajaxray/htmldoc.space/issues?q=is%3Aissue+is%3Aopen+label%3Aroadmap+sort%3Areactions-%2B1-desc) is sorted by votes.

## Agent-side value (the differentiator)

- **MCP server** ([#4](https://github.com/ajaxray/htmldoc.space/issues/4)). htmldoc as a tool in Claude Desktop, Cursor, and others without a skill install.
- **Comments on pages** ([#6](https://github.com/ajaxray/htmldoc.space/issues/6)). Lightweight threads the CLI can read back, so the agent can revise from feedback.
- **Diff link on update.** After `--update`, a second link showing what changed between versions.
- **Pull a page back down.** `htmldoc get <id>` returns the source so a new session can keep editing.

## Reader-side value

- **Visit counts** ([#2](https://github.com/ajaxray/htmldoc.space/issues/2)). Total and last-seen on the dashboard and in `list --json`. No per-visitor logging.
- **Choose the expiry** ([#3](https://github.com/ajaxray/htmldoc.space/issues/3)). `--expires 7d|30d|90d` within a cap.
- **Password on a page** ([#5](https://github.com/ajaxray/htmldoc.space/issues/5)). A step above "unlisted" for drafts shared with a client.
- **Editable slug** ([#7](https://github.com/ajaxray/htmldoc.space/issues/7)). `p.htmldoc.space/q3-report` instead of a random id; the id stays as an alias.

## Distribution and retention

- **Team spaces.** GitHub org login, shared page list, shared cap.
- **Custom viewer domain.** `docs.acme.com` as a CNAME to the viewer host.
- **Webhooks.** Post to Slack or a URL on publish and on report.
- **Public gallery, opt-in.** Off by default; owners can flag a page for a "made with agents" showcase.

## Operator side

- **Abuse signals in the admin panel.** Cheap heuristics that catch phishing before a report arrives.
- **Export and delete account** from the dashboard.

Items without an issue number are ideas; open an issue if you want one of them.

## Not planned

- **Multi-file bundles** ([#1](https://github.com/ajaxray/htmldoc.space/issues/1)). One file per link is the product; a directory with assets is a site. Ask your agent to inline CSS and images into one self-contained file.
