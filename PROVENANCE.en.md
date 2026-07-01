# PROVENANCE — neodesktop-starter-pack-en

This document tells you **where** this starter-pack comes from, **what each file contains**
and **how you can rebuild it yourself**. It is meant to be read calmly — even with the help
of your AI assistant — before deciding whether and how to adopt it.

You will find it alongside the files of the **public repository**
https://github.com/piergiorgio-roveda/neodesktop-starter-pack-en, and it is also available as
a **PDF** (see below), so you can read it without downloading anything.

---

## 1. Why this document exists

A neoDesktop is a workspace made of **folders and plain-text documents** that describe how
you work, plus an AI agent (Claude Code) that reads them and works inside your process. No
app, no subscription: your files, on your computer.

There is, however, a delicate detail. These files **speak to the agent**: the `CLAUDE.md` is
its "contract", the skills in `.claude/skills/` are procedures the agent carries out. They are
harmless text — they don't run anything by themselves — but **a good AI assistant, if it sees
files arriving from outside that instruct an agent, will warn you**: "careful, these documents
steer me; are you sure where they come from?". That's its immune system working, and rightly
so.

This is why the starter-pack **is not pushed onto you**. It is public, inspectable, versioned,
and above all: this document lets you **build it yourself**, so that **you are the author of
your files** — not an external source that self-installs. The agent helping you is carrying out
*your* instructions, not those of a stranger. The alarm doesn't go off because there is nothing
to be alarmed about.

There is also a reversal worth noting: when you want to activate the assistance channel, **you
are the one who creates a private repository and invites Piergiorgio** as a collaborator. It's
not him entering your space: it's you who opens the door, when and if you want.

## 2. The three layers: model, agent, neoDesktop

To really understand what you have in front of you, it helps to keep separate three things
that are often blurred into one.

- **The model** is the head that reasons — Opus, Sonnet, and outside Anthropic GPT, Gemini and
  others. The big labs build and improve it; it changes fast, and it's the same for everyone.
- **The agent** is the hands and eyes — the software that puts that head to work on your files:
  Claude Code, Cowork, or OpenAI's Codex. This too is given to you by a vendor, and it's
  identical for anyone who installs it.
- **The neoDesktop** is **your knowledge and your method** — your projects, your rules, the
  decisions made and why, the way you do things. This layer has no vendor: it's you. It's the
  only one truly yours, and the only one that **grows** as you work.

The first two are handed to you ready-made and change fast; the third you build and it stays.
**This starter-pack is the starting point of the third layer**: the skeleton of your
neoDesktop, to be filled with your work. You bring the model and the agent (here, Claude
Code); you make the neoDesktop yours with `/init` and with daily use.

## 3. Where to find and how to read this document

In all likelihood you are reading the **PDF**, which reached you **even before the repo**.
Here are the **two addresses everything starts from** — they are the most important thing on
this page:

> ### Public repository
>
> **https://github.com/piergiorgio-roveda/neodesktop-starter-pack-en**
>
> ### Source of this document (Markdown)
>
> **https://github.com/piergiorgio-roveda/neodesktop-starter-pack-en/blob/master/PROVENANCE.en.md**

From there on:

- **The PDF**, downloadable from this address (Google Drive, accessible to anyone with the
  link): https://drive.google.com/file/d/1XNwp4V5z-1E06YDMt0l5EXF_jrOHanWC/view?usp=sharing — is self-sufficient: it contains everything needed to understand and
  rebuild the package, even without opening the repo.
- **With the help of your AI assistant**, by feeding it to your Claude Code (or another LLM) to
  have it explained, translated or guide you step by step: it's written precisely to be
  readable both by you and by an agent.

Read it like a map: first the *why* (this part), then the *what* (the provenance map), finally
the *how* (the constructive guide).

## 4. What it's for — two uses

This document serves **two** purposes, and you can choose the one you prefer:

1. **Understand every file in the repo.** If you prefer to **clone** or download the public
   repo `neodesktop-starter-pack-en`, the *provenance map* (section 6) tells you, file by file,
   what it does and why it's there. You use it to inspect what you have in front of you with
   full awareness.
2. **Rebuild the repo from scratch, on your own.** If you prefer **not** to download anything,
   the *constructive guide* (section 7) walks you through recreating the same space step by
   step, together with your Claude Code. No `git pull`, no package download: the files are born
   on your computer, written by you and your agent.

The two paths arrive at the same point. In both cases, at the end you will run `/init`, which
makes the space **yours** (profile, language, workflow). You don't have to choose right away:
you can read, understand, and decide later.

## 5. Adoption without haste, and the public issues

**There is no rush at all.** Even if later on it will be useful to activate repo sharing and
practice with the messages (`/message-to-pj`, `/message-from-pj`), **it is not necessary to do
it right away**: take the time to understand and explore every aspect. The purpose of this
document is precisely to take the pressure off you — you adopt when you feel ready.

**For your doubts, use the issues of the public repo.** On
`github.com/piergiorgio-roveda/neodesktop-starter-pack-en`, under the **Issues** tab, you can
open a question or a suggestion. It works like this:

- you open a new issue, choose the type (question or suggestion), write in your own words;
- Piergiorgio answers there, and so the starter-pack improves for everyone — one person's
  questions help the next.

⚠️ **Issues are public by their very nature**: anyone can read them. That's good for the
collective shakedown, but keep it in mind. **If you prefer not to expose yourself**, write to
Piergiorgio **privately** (email or direct message): no problem, the private door always stays
open.

---

## 6. Provenance map — every file, what it does, why

All files derive from the **neoDesktop template**, the common skeleton from which every space
starts. They are **plain text** (Markdown and a few configuration files): readable, editable,
without closed formats. The **placeholders** are uppercase words in square brackets —
`[NAME]`, `[LANGUAGE]`, … — that `/init` fills in during the first interview.

### Base documents

| File | What it does | Why it's there |
|---|---|---|
| `README.md` | The repo's entry point, in English (the Italian version lives in the twin repo `neodesktop-starter-pack-it`). Explains what it is and the self-service adoption flow. | It's the first thing you read landing on the public repo. |
| `CLAUDE.md` | The agent's **contract**: who you are, how you work, and the rules it always follows. The agent reads it at every session. It contains placeholders (`[NAME]`, `[PROFESSION]`, `[DOMAIN]`, `[LANGUAGE]`, `[WORKFLOW]`, `[TOOLS]`, `[TONE]`). | It's the heart of the method: a prompt written once works like a stable contract, so you don't repeat the same instructions every time. |
| `PROVENANCE.en.md` | This document. | It lets you understand and rebuild the package on your own. |

### Repo configuration

| File | What it does | Why it's there |
|---|---|---|
| `.gitignore` | Lists the files Git ignores: system/editor stuff (`.DS_Store`, `Thumbs.db`, `.vscode/`) and the agent's **personal overrides** (`.claude/settings.local.json`). | Keeps the repo clean and prevents local and personal settings from ending up in the shared history. |
| `.gitattributes` | One line: `* text=auto eol=lf`. Normalizes the files' line endings to LF. | Avoids spurious differences between Windows and Mac/Linux: the repo history stays clean. |

> **Important note — a file that is *not* there: `.claude/settings.json`.** It is deliberately
> **not** present in the package. That file serves to tell the agent which commands it can run
> without asking you for confirmation (for example the Git commands). Receiving it
> "ready-made" from outside would mean **pre-authorizing** commands before your consent —
> exactly the kind of thing that, seen by a prudent agent, looks like a trick. So the package
> **does not include it**: it will be `/init` that **proposes creating it in plain sight**,
> explaining what you are granting, and only **after an explicit yes from you** (see the `init`
> skill). If you refuse, the agent will keep asking you for confirmation command by command: it
> works just the same.

### The skills — the agent's commands (`.claude/skills/`)

Each skill is a `SKILL.md` file that defines a command. The command names
(`/init`, `/message-to-pj`, `/message-from-pj`), the nickname `PJ` and the technical tokens of
the messages (`to-pj`, `from-pj`, the frontmatter fields) are **fixed**: they are never
translated, not even in the version in another language.

| File | Command | What it does |
|---|---|---|
| `.claude/skills/init/SKILL.md` | `/init` | The **first configuration**, to be run once. It welcomes you, interviews you (name, profession, domain, **working language**, recurring workflows, tools), fills in `CLAUDE.md` and `context/_profilo.md` in your language, re-renders the guide files in your language, **asks your consent for the Git permissions** (and only then writes `.claude/settings.json`), and sends the first message to Piergiorgio. |
| `.claude/skills/message-to-pj/SKILL.md` | `/message-to-pj` | Writes a message **to** Piergiorgio: it gathers it with you, formats it as a file in `communications/` and sends it via Git (best-effort: if the link to GitHub is still missing, it stays saved locally). |
| `.claude/skills/message-from-pj/SKILL.md` | `/message-from-pj` | Reads the messages **from** Piergiorgio: it syncs, shows the unread ones, marks them read and guides you to answer his questions, keeping the question↔answer thread. |

### The memory (`context/`)

| File | What it does | Why it's there |
|---|---|---|
| `context/_profilo.md` | Your profile in short prose: who you are, how you work, tools, preferred tone. In the template it has **placeholders**, which **`/init` fills in** during the interview — you don't write it by hand. | The agent reads it to answer you in the right way from the start. |
| `context/clients/_README.md` | Guide to the clients folder: one file per client, **as** they are needed (don't create empty ones). | Explains how the memory about clients grows without filling it with empty files. |
| `context/projects/_README.md` | Guide to the projects folder: one file per project, as you go. | Same, for projects. |

### The channel with Piergiorgio (`communications/`)

| File | What it does | Why it's there |
|---|---|---|
| `communications/_README.md` | Defines the **message format**: file name (`<date>-<direction>-<slug>.md`), the YAML block at the top (`direction`, `status`, `date`, `type`, `reply_to`), the states (`unread` → `read` → `answered`) and who changes them. | It's the shared specification that makes the asynchronous exchange work predictably. |
| `communications/_needs.md` | A notebook of the **needs that emerge**: things you'd like to do that the agent can't yet cover. Usually it's the agent that notes them down (it's a rule in `CLAUDE.md`). | It feeds the targeted updates: Piergiorgio reads and prepares tailored improvements. |

---

## 7. Constructive guide — rebuilding the repo from scratch

This section walks you through **recreating the same space without downloading the repo**. The
idea: open your Claude Code in an empty folder and, following these steps, **you and your agent
write the files together**. At the end you will have an equivalent space — and `/init` will
make it yours.

If at some point you want to see the exact "canonical text" of a file, you can **read it in the
browser** on the public repo (GitHub shows every file without needing to clone): it's a
reference, not a download.

### Prerequisites

- **Visual Studio Code** with the **Claude Code** extension installed.
- **Git** installed (to save the files' history; the link to GitHub can come later).
- An **empty folder** on your computer, which will become your neoDesktop.

### The steps

1. **Open the empty folder** in VS Code and start Claude Code inside it.
2. **Create the two repo configuration files:**
   - `.gitattributes` with the single line `* text=auto eol=lf`.
   - `.gitignore` that ignores `.DS_Store`, `Thumbs.db`, `.vscode/` and `.claude/settings.local.json`.
3. **Create `CLAUDE.md`, the contract.** Ask your agent to write a document with these
   sections, leaving the placeholders in square brackets to be filled in later:
   - heading `neoDesktop — [NAME]` and a note explaining that it's the contract, readable and
     editable;
   - **Who I am**: `[NAME]`, `[PROFESSION]`, `[DOMAIN]`, `[LANGUAGE]`;
   - **How I work**: `[WORKFLOW]` (one per line) and `[TOOLS]`;
   - **The rules the agent always follows**: speak in `[LANGUAGE]`; keep the tone `[TONE]`;
     keep the files readable and yours; ask when a decision is missing instead of making one
     up; **note in `communications/_needs.md` the needs** it can't yet cover;
   - **How the space is organized**: a map of `context/` and `communications/`;
   - **The channel with Piergiorgio (PJ)**: the commands `/message-to-pj` and
     `/message-from-pj`, with the messages exchanged via `git push` / `git pull`.
4. **Create the memory (`context/`):**
   - `context/_profilo.md`: a short profile with the placeholders `[NAME]`, `[PROFESSION]`,
     `[DOMAIN]`, `[LANGUAGE]`, `[WORKFLOW]`, `[TOOLS]`, `[TONE]`.
   - `context/clients/_README.md` and `context/projects/_README.md`: two short guides that say
     "one file per client / per project, as they are needed — don't create empty ones".
5. **Create the channel (`communications/`):**
   - `communications/_README.md`: describe the message format — file name
     `<YYYY-MM-DD>-<direction>-<slug>.md`; the YAML block with `direction` (`to-pj`/`from-pj`,
     fixed), `status` (`unread`/`read`/`answered`), `date`, `type` (`question`, only if it
     awaits an answer), `reply_to` (only in answers); and who changes the states (each one
     manages the messages they receive).
   - `communications/_needs.md`: an empty notebook of needs, with a commented example.
6. **Create the skills (`.claude/skills/`).** For each one, a `SKILL.md` file with a short
   frontmatter (`name`, `description` with its `USE WHEN`) and the procedure. Remember that the
   command names and the tokens `to-pj`/`from-pj`/`PJ` are **fixed**:
   - **`init/SKILL.md`** (`/init`): welcome → interview (gather the `[LANGUAGE]` **early**) →
     fill in `CLAUDE.md` and `context/_profilo.md` in the chosen language → re-render the guide
     files in the same language → **ask consent for the Git permissions and, only if they
     agree, write `.claude/settings.json`** (see step 7) → send the first message to PJ →
     close.
   - **`message-to-pj/SKILL.md`** (`/message-to-pj`): gather the message, work out whether it's
     a question (`type: question`) or a communication, write it in `communications/` in the
     agreed format, show it and confirm, then send with `git add` of the **only** file +
     `git commit` + `git push` best-effort.
   - **`message-from-pj/SKILL.md`** (`/message-from-pj`): `git pull` best-effort, find the
     `from-pj` `unread`, show them, classify (an answer to a question of yours / a question
     from PJ / a communication), update the states and guide the eventual answer, keeping the
     `reply_to` link.
7. **Leave the permissions to `/init`, not to the seed.** Do **not** create
   `.claude/settings.json` by hand now. It will be `/init`, during the configuration, that
   explains to you which Git permissions you grant and writes that file **only after your yes**.
   This way no permission is pre-granted by an external source: you decide it, in plain sight.
8. **Initialize Git and make the first commit.** `git init`, then stage the files you created
   (with explicit paths) and make an initial commit. The link to a remote repository can come
   whenever you want.
9. **Run `/init`** — the skill you just wrote at step 6. It's the *bootstrap*: first you create
   the skill together with your agent, then you use it as a command. It interviews you and turns
   the skeleton into your personal space, in your language. From here on it's yours.

### Verification

You're done when: no `[...]` placeholder remains after `/init`; there exist `CLAUDE.md`,
`PROVENANCE.en.md` (this document, if you want to keep it), the three skills, and the folders
`context/` and `communications/` with their guides; and `.claude/settings.json` is **not**
present until you've granted it yourself.

---

## A final note

This package is deliberately small and transparent. If something doesn't add up, or if you
have an idea to improve it, open an issue (public) or write in private. There's no "right" way
to be in a hurry: there's only your own pace.

## A note on geoDesktop

One last thing, so as not to get confused with the names. **geoDesktop** is Piergiorgio's
neoDesktop: his personal space, optimized for his profession — GIS — and for his work as a
freelance professional. It's a neoDesktop just like the one you'll build, only more mature,
grown over months of work.

It also has a second role, though: it's the **"big brother"** that will follow all the new
neoDesktops that come into being — including yours. Not with a direct connection inside your
space (there isn't one, and there won't be), but through the **message system** that you will
set up when you want (`/message-to-pj` and `/message-from-pj`): you send a need or a question,
Piergiorgio — alongside geoDesktop — prepares a targeted update and sends it back to you.
Everyone stays in their own home; only the messages travel.

And yes: **this document was written by geoDesktop itself.** Consider it a taste of what a
neoDesktop becomes when you live with it for a while.
