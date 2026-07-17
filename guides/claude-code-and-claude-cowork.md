# Using Claude Code and Claude Cowork on the same folder

Your neoDesktop is a folder of plain-text files on your computer. Claude Code (the terminal) and Claude Cowork (the Desktop app, with Projects) are two different ways of working on that folder, but only if **both of them actually point to the same folder on disk**. If they don't, one of them ends up working blind on files it never sees.

## The problem people run into

If you open Claude Cowork, create a Project, and **attach files** (PDFs, documents) directly in chat, those files stay inside the Project, not on your disk. They're context for that one conversation, not real files inside your neoDesktop folder. Open a terminal in the same folder afterward and run Claude Code, and it won't find them: Code only reads what's physically on disk.

## How to connect them properly

1. **Start from the folder, not the chat.** Create (or open) your neoDesktop folder on disk, e.g. `~/neodesktop` or your project folder.
2. **Open a terminal in that folder** and run `claude` (Claude Code). From here on, this is the folder you'll share with Cowork.
3. **Put files inside the folder**, not in chat. A PDF, a document, an image: drag them into the folder with Finder or File Explorer, don't upload them as a chat attachment.
4. **In Claude Cowork, attach the folder as a local workspace**, not as individual files. That's the option that gives Cowork real filesystem access to the folder, not just the text of an uploaded file.
5. From that point on, Code and Cowork read and write the **same files**. Edit a document in Finder, or have either tool update it: the other one sees it.

## What stays separate

One thing never gets shared between Code and Cowork: **chat history**. They're two separate conversations, each with its own memory. Whatever one of them "knows" from a conversation doesn't carry over to the other automatically: it only carries over if you write it down in a file inside the folder. If you want something available to both, the right place isn't the chat: it's a file in your neoDesktop.

It's, at bottom, the same principle as always: your neoDesktop is the folder, not the conversation. Any agent that reads it, whether a terminal or a desktop app, sees the same knowledge, because it lives in the files, not in a chat that disappears.
