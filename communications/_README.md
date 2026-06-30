# Communications with Piergiorgio (PJ)

The asynchronous channel between you and Piergiorgio. Each message is a file in this folder,
exchanged with `git push` / `git pull`. It is managed with the `/message-to-pj` and
`/message-from-pj` commands — normally you don't need to touch the files by hand.

## Format of a message

File name: `<YYYY-MM-DD>-<direction>-<slug>.md` — e.g. `2026-06-30-from-pj-welcome.md`.

Each file starts with a small YAML block (the frontmatter, between two `---` lines).
Ready-to-copy example:

```yaml
---
direction: from-pj
status: unread
date: 2026-06-30
type: question
reply_to: 2026-06-29-to-pj-export-question.md
---
```

Below the block is the message text, in free markdown.

### The fields

| Field | Required | Values | Meaning |
|---|---|---|---|
| `direction` | yes | `to-pj` \| `from-pj` | `to-pj` = from you to Piergiorgio; `from-pj` = from Piergiorgio to you. These tokens are **fixed**, they are not translated. |
| `status` | yes | `unread` \| `read` \| `answered` | read / reply status (see below). |
| `date` | yes | ISO date `YYYY-MM-DD` | date of the message, e.g. `2026-06-30`. |
| `type` | no | `question` | present **only** if the message is waiting for a reply; otherwise omitted. |
| `reply_to` | no | name of a file | the file this message replies to; present **only** in replies. |

## Statuses

- `unread` — just arrived, not yet read by the recipient.
- `read` — read by the recipient.
- `answered` — it was a question (`type: question`) and the reply has been written; the reply
  file links to it via `reply_to`.

### Who changes the statuses

For the status transition each message is "owned" by the side that receives it:

- **`from-pj` messages** (from Piergiorgio to you): you handle them with `/message-from-pj`.
  The command moves them from `unread` to `read`; if it is a question and you write the reply,
  the question moves to `answered`.
- **`to-pj` messages** (from you to Piergiorgio): **Piergiorgio transitions them from his
  side** — he reads them in geoDesktop and moves them to `read`. If one of your `to-pj`
  messages was a question (`type: question`), it moves back to `answered` when
  `/message-from-pj` receives Piergiorgio's reply: the command recognizes the `reply_to`
  pointing to your question and marks it `answered`.

## `_needs.md`

The `_needs.md` file collects the needs that emerge while you work: things you would like to
do that the agent can't cover yet. Normally it is **the agent** that notes them there
automatically (it is a rule in `CLAUDE.md`); you can still add some by hand whenever you want.
Piergiorgio reads them and prepares targeted updates for you.
