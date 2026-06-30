---
name: init
description: "First setup of the neoDesktop. USE WHEN: the user runs /init, or it is the first session and CLAUDE.md still contains placeholders [...]. Interviews the user, fills in CLAUDE.md and context/_profilo.md in the working language, prepares the space and sends the first message to Piergiorgio."
---

# /init — first setup of your neoDesktop

It is run **once**, at the beginning. It turns the skeleton (with the `[...]` placeholders)
into the user's personal neoDesktop, explaining each step as it goes. The user is at the
keyboard; you guide them.

## Principle

Don't download anything and don't do magic: **build and narrate**. Explain in plain words
what you are doing and why, one step at a time. The user is not necessarily technical.

## Working language

This is a multilingual space. The language is not decided in advance: you **collect** it in
the interview (the `[LANGUAGE]` field) and from that moment it governs everything.

- **Conduct the interview** in the language the user writes to you in; as soon as you have
  confirmed `[LANGUAGE]`, continue the whole interaction in that language.
- **Write all the files in `[LANGUAGE]`.** Both the ones you fill in (`CLAUDE.md`,
  `context/_profilo.md`, the first message to PJ), and the four **static guide files** that
  the template already ships written in English (`communications/_README.md`,
  `communications/_needs.md`, `context/clients/_README.md`, `context/projects/_README.md`):
  these must be **re-rendered** in the chosen language (steps 5 and 6). Don't leave prose in a
  language different from the chosen one.
- In `CLAUDE.md` you don't just replace the placeholders: **render the prose** (titles,
  section text, rules) in `[LANGUAGE]`. The **fixed tokens** stay unchanged and are never
  translated — the command slugs (`/init`, `/message-to-pj`, `/message-from-pj`), the
  `direction` values (`to-pj` / `from-pj`), the nickname `PJ`. Only the prose around them is
  localized (e.g. "the channel with Piergiorgio (PJ)").

## Procedure

0. **First setup or re-run?** Before anything else, check whether the template files —
   first of all `CLAUDE.md` — still contain `[...]` placeholders. If there **are** residual
   placeholders, it is the first setup: continue from step 1. If there are **no** more, the
   space is **already configured**: don't redo the init from scratch (see "After /init"),
   skip to the profile-update branch.
1. **Welcome.** In 2-3 sentences, explain what this space is: a folder + documents that
   describe how you work + an agent that reads them. No jargon.
2. **Interview.** One question at a time, calmly. Collect: name and how they prefer to be
   called; profession and domain; **working language** (`[LANGUAGE]` — ask for it early, so
   the rest of the interview and all the files respect it); 1-3 recurring workflows (what
   comes in, what goes out, where it slows down); tools they use today. If they have already
   answered these questions by email to Piergiorgio, start from those and only ask for
   confirmation.
3. **Fill in `CLAUDE.md`.** Replace every `[...]` placeholder with the answers and **render
   the prose in `[LANGUAGE]`** (see the "Working language" section). Show the result and ask
   for confirmation before saving. Check that no residual `[...]` remains.
4. **Fill in `context/_profilo.md`.** Write the profile in short prose, in `[LANGUAGE]`.
5. **Explain the memory, and re-render its guides.** Show `context/clients/` and
   `context/projects/`: this is where one file per client and per project will appear, over
   time. Don't create any now to no purpose. Translate into `[LANGUAGE]` the two static guide
   files `context/clients/_README.md` and `context/projects/_README.md` (they are in English
   in the template): render the prose, leave the file and folder names unchanged.
6. **Explain the channel with PJ, and re-render its guides.** Show `/message-to-pj` and
   `/message-from-pj` and what they are for. Translate into `[LANGUAGE]`
   `communications/_README.md` and `communications/_needs.md` (in English in the template):
   **render the prose but leave the fixed tokens unchanged** — the frontmatter field names
   (`direction`, `status`, `date`, `type`, `reply_to`), the values
   `to-pj`/`from-pj`/`unread`/`read`/`answered`, and the example YAML block. Only the
   surrounding text is translated.
7. **Permissions to save and sync — ask before granting.** The next step (the first message
   to PJ) uses Git to **save** your work and, if you want, **send** it to Piergiorgio. So that
   Claude doesn't have to stop and ask you for confirmation on every command, it can remember
   your consent to use Git in a small configuration file. **It does not create it secretly: it
   asks you now, in the open.** Proceed like this:
   - **Explain in plain words** what these permissions concern: *only* Git — the tool that
     keeps the history of your files and syncs them. Nothing else. In detail: saving a version
     (`git add`, `git commit`), sending and receiving updates (`git push`, `git pull`),
     consulting status and history (`git status`, `git log`).
   - **Ask for explicit consent** to grant these six permissions. **Don't write anything before
     their answer.**
   - **If they agree:** create the file `.claude/settings.json` with exactly this content,
     then confirm to them that it is done and that they can re-read it or change it whenever
     they want — it is a file as readable as all the others, nothing hidden:

     ```json
     {
       "permissions": {
         "allow": [
           "Bash(git add:*)",
           "Bash(git commit:*)",
           "Bash(git push:*)",
           "Bash(git pull:*)",
           "Bash(git status:*)",
           "Bash(git log:*)"
         ]
       }
     }
     ```

   - **If they refuse or are unsure:** that's fine, **don't get stuck**. Explain that they can
     grant them later — just re-run this step — and that in the meantime, at the next step,
     Claude will ask them for confirmation on every Git command (or they can save by hand).
     Continue anyway.
8. **First message to PJ.** Create a `to-pj` "setup complete" message, so that Piergiorgio
   knows you have started and prepares the first updates. Proceed like this:
   - **Create the file** in `communications/` with name `<YYYY-MM-DD>-to-pj-<slug>.md` (today's
     date in ISO `YYYY-MM-DD`; `<slug>` = short descriptive slug **in `[LANGUAGE]`**, e.g.
     `setup-complete` — it is prose, not a fixed token), following the schema in
     `communications/_README.md`. The frontmatter is:

     ```
     ---
     direction: to-pj
     status: unread
     date: <YYYY-MM-DD>
     ---
     ```

     No `type` field: it is not a question. Below the block, write in `[LANGUAGE]` a short
     summary of the profile (name, profession/domain, language, the recurring workflows
     collected) — just enough for PJ to get oriented.
   - **Send the message.** Add *only this file* to the stage (`git add` of the message path,
     not `git add -A`) and make a local commit with a descriptive message.
   - **Sync, best-effort.** Try `git push`. If it succeeds, the message has reached PJ. If it
     **fails** — typically because the repo does not yet have a remote configured (the normal
     case on the first run) — **degrade gracefully**: the local commit is made anyway, so
     explain to the user that the message is saved locally and that the sync with Piergiorgio
     will happen as soon as the remote is configured. It is not an error to fix: it is the
     expected state of the first run.
9. **Closing.** Say that everything is ready and that they can start using their Claude by
   asking questions about their work.

## After /init

This skill is no longer needed once the setup is complete. The concrete signal is the
**absence of `[...]` placeholders** in the template files (see step 0): if there are no more,
the space is already configured.

If the user re-runs `/init` on an already-configured space, **don't reset anything**.
Acknowledge it openly and instead propose to **update the profile**:

- ask what has changed (new domain, new workflows, different tools, language);
- rewrite **only the touched parts** of `CLAUDE.md` and re-fill `context/_profilo.md`,
  keeping `[LANGUAGE]` as the current working language;
- don't recreate the scaffolding files or overwrite the existing work. A new message to PJ
  here is optional: send it only if the update is substantial.
