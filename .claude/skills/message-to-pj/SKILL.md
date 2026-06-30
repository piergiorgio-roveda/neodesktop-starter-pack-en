---
name: message-to-pj
description: "Writes an asynchronous message to Piergiorgio (PJ). USE WHEN: the user runs /message-to-pj, or says they want to write/ask Piergiorgio something. Collects the message interactively, formats it in communications/ and sends it via git."
---

# /message-to-pj — writing to Piergiorgio

Asynchronous channel toward Piergiorgio. The message becomes a file in `communications/`,
which he reads when he syncs the repo.

**Language.** These instructions are addressed to you, the agent. Talk with the user **in the
language of their profile** (`[LANGUAGE]` in `CLAUDE.md` / `context/_profilo.md`): questions,
confirmations and explanations go in that language. What stays **fixed** in every language are
the technical tokens — the command slug, the value `direction: to-pj` and the token `to-pj` in
the file name: they are not translated.

## Procedure

1. **Ask what they want to say.** If they haven't already written it, let them tell the
   message in their own words. Help them make it clear, without distorting it.
2. **Understand the type.** Is it a **question** (it expects a reply) or a **communication**
   (it just informs)? This decides whether the file carries the `type: question` field.
3. **Write the file.** In `communications/`, name `<YYYY-MM-DD>-to-pj-<slug>.md`, with the
   YAML block of the format defined in `communications/_README.md`:
   - `direction: to-pj`
   - `status: unread`
   - `date:` today's date in ISO `YYYY-MM-DD`
   - `type: question` **only** if it is a question (otherwise omit the field)

   Below the YAML block is the body of the message.
4. **Show and confirm.** Show the formatted message and ask for confirmation.
5. **Send.** `git add` of the **file you just wrote only** (explicit path, never `-A`), then
   `git commit` with a clear message. Then try `git push` **best-effort**:
   - if the push succeeds, confirm that the message has gone out;
   - if it fails because the remote is missing (the repo is not yet connected to GitHub),
     **it is not an error**: the local commit is valid and holds. Let the user know that the
     message is saved locally and will reach Piergiorgio as soon as the remote is configured
     and the sync starts.

   If the user is not familiar, explain in one line that you are "sending" the message.

## Notes

- One file = one message. Don't pile up multiple messages in the same file.
- **Statuses of a `to-pj`.** Once sent, the statuses of your `to-pj`
  (`unread` → `read`) are transitioned by **Piergiorgio from his side** when he reads it: don't
  touch them yourself. The only exception is closing the thread of a `to-pj` **question**:
  when PJ's reply arrives (a `from-pj` with `reply_to` to your `to-pj`), it is
  `/message-from-pj` that brings the original `to-pj` to `answered`.
- Don't touch the `from-pj` messages: those are handled with `/message-from-pj`.
