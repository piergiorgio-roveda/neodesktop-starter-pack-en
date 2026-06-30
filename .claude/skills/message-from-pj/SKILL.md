---
name: message-from-pj
description: "Reads Piergiorgio's (PJ) messages and handles the replies. USE WHEN: the user runs /message-from-pj, or asks whether there is any news/messages from Piergiorgio. Syncs, shows the unread ones, marks them read and guides the reply to PJ's questions."
---

# /message-from-pj — reading Piergiorgio and replying

**Language.** These instructions are addressed to you, the agent. Show, summarize the messages
and talk with the user **in the language of their profile** (`[LANGUAGE]` in `CLAUDE.md` /
`context/_profilo.md`). What stays **fixed** in every language are the technical tokens: the
command slug and the `direction` values (`to-pj` / `from-pj`).

## Procedure

1. **Sync.** Try `git pull` **best-effort** to download any new messages from Piergiorgio. If
   the remote is missing (repo not yet connected to GitHub), **it is not an error**: continue
   by reading the `from-pj` files already present locally and warn that the sync with PJ will
   start when the remote is configured.
2. **Find the unread ones.** Look in `communications/` for files with `direction: from-pj` and
   `status: unread`. If there are none, say so and stop.
3. **Show.** Present each unread message in a readable way (date + content), in the language of
   the profile.
4. **Classify each message** into one of the three cases and handle it:
   - **(a) PJ's reply to one of your questions** — the `from-pj` has a `reply_to` field that
     points to one of your `to-pj` with `type: question`. It is PJ replying: mark the
     `from-pj` to `status: read` and bring the original `to-pj` (your question) to
     `status: answered`, closing the thread. Show the reply next to the question.
   - **(b) PJ's question** — the `from-pj` has `type: question`. Mark to `status: read`.
     Then **propose** to reply, but **don't force** the reply in the same run: if the user
     wants to reply now, go to step 5; if they prefer to postpone, leave the message at
     `read` — they will reply later by re-running the command, and the question stays
     recognizable as still open.
   - **(c) Simple communication** — no `type: question`. Mark to `status: read`, nothing else
     is needed.
5. **Composing the reply to a PJ question** (only if the user chooses to reply now —
   case (b)). Guide the user to compose the reply in the language of the profile. Create a new
   `to-pj` file (name `<YYYY-MM-DD>-to-pj-<slug>.md`) with frontmatter:
   - `direction: to-pj`
   - `status: unread`
   - `date:` today's date in ISO `YYYY-MM-DD`
   - `reply_to: <name-of-the-from-pj-question-file>`

   Then bring Piergiorgio's original message (the `from-pj` question) to `status: answered`.
6. **Send.** `git add` of the **modified or created files only** (explicit paths, never `-A`):
   the updated statuses and the reply, if any. `git commit` with a clear message. Then try
   `git push` **best-effort**: if it succeeds, confirm; if the remote is missing, the update
   stays valid locally and will reach PJ at the next sync — warn and continue without treating
   it as an error.

## Notes

- Don't write the `from-pj` messages yourself: Piergiorgio writes them from his side. You only
  change their `status` (`unread` → `read`, and `answered` when it is a question you have
  replied to).
- Keep the question↔reply link with `reply_to`, so the thread stays readable in both
  directions.
