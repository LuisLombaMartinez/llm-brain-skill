---
name: llm-brain
description: Use ONLY when the user explicitly says "my brain" (or "mi cerebro", or names llm-brain), e.g. 'save to my brain', 'what's in my brain about X', 'set up my brain'. Never trigger on the words idea, project, note, tool or thought alone.
---

# llm-brain

The user's **brain** is a private GitHub repo of Markdown files holding their ideas, projects, thoughts, tools and notes. Claude saves to it and reads from it from any chat (phone, desktop, Claude Code), so things captured in one place can be picked up in another.

## Configuration

**Brain repo:** `<owner>/<repo>`

If the line above still says `<owner>/<repo>`, ask the user for their brain repo (`owner/name`) and use what they say. Then tell them to put it on that line of their copy of this skill so they aren't asked again.

## When to use this skill

Only when the user explicitly refers to **"my brain"** (or "mi cerebro", or `llm-brain`). For example:

- "Save this to my brain" / "add to my brain as a thought"
- "Make a note in my brain about this MCP I saw"
- "Write up what we decided and put it in my brain"
- "What's in my brain about X?" / "which tools in my brain haven't I tried?"
- "Review the ideas in my brain"
- "Set up my brain" (first time, on an empty repo)

If the user says "idea", "project", "note", "tool" or "save this" **without** mentioning their brain, this skill does not apply. Don't use it, and don't offer to save anything.

## 1. Get the brain

1. If a clone already exists and `git rev-parse HEAD` works there, run `git pull --rebase` and use it.
2. Otherwise, attach the brain repo with the add-repo tool (access `push`). Then clone it exactly as that tool's result says, and register the clone if it asks you to.
3. If the repo is **empty**, or the user asked to set it up, go to *Setting up a new brain* below.
4. **Read the brain's `GLOSSARY.md` and `CLAUDE.md` before doing anything else.** They are the source of truth for the types, folders, frontmatter, file names and commit style. Each brain can extend or change its own glossary, so never assume the defaults.

## 2. The glossary rule

Every brain has a `GLOSSARY.md`. It defines the **types** of things that can be saved (by default: idea, project, thought, tool, note), each with exactly one folder. It also defines the action words (write-up, next steps, promote, try, archive, review) and lists words to avoid.

- Use the glossary's words in files, commit messages and replies. Never use the ones it says to avoid.
- The type is decided by **what** is being saved, not the verb the user uses: "make a note of this MCP" is a tool if the glossary has a tool type.
- **Not sure which type?** Ask in one short question ("Idea or thought?"). If the user isn't around, use the glossary's fallback type (by default, idea) and say so.
- **Fits no type at all?** Ask whether to add a new type, then follow "Adding a new type" in the glossary. Don't invent a type or a folder on the spot.

## 3. Do the work

- **Search first.** Grep titles, tags and content. Update an existing file (append a dated section and bump `updated`) rather than creating a duplicate.
- Follow the brain's `CLAUDE.md` for frontmatter, file names and section layout.
- **Quick captures** stay tiny: the user's words, a title and tags. No padding or invented details.
- **Write-ups** of a conversation are written for the user reading them weeks later without the chat.
- **Lookups** answer from the files and name the paths used. Don't write anything unless asked.
- Write in the language the user used.
- Never store secrets, passwords, API keys or other people's private data.

## 4. Commit and push

Commit straight to `main`, with the user as the author (their name, and the email from the session's account context if there is one). Use the message format from the brain's `CLAUDE.md`, plus any attribution lines the session requires. Push. If the push is rejected, `git pull --rebase` and push once more.

Reply in one or two lines with the type and path, e.g. "Saved as a tool (MCP, to-try) in `tools/github-mcp.md`." Don't repeat the note back.

## Setting up a new brain

1. Find the starter brain. It's the `template/` folder next to this `SKILL.md`. If that folder isn't available (for example, the skill was installed as a single file), clone `https://github.com/LuisLombaMartinez/llm-brain-skill` and use `llm-brain/template/` from there.
2. Copy everything in `template/` into the root of the empty brain repo, `.gitkeep` files included.
3. In `README.md`, `CLAUDE.md` and `GLOSSARY.md`, replace `{{OWNER}}` with the user's first name.
4. Commit (`init: brain from llm-brain-skill template`) and push.
5. Tell the user in two or three lines what the types are, and that they can change the glossary any time by asking.

## If the brain can't be reached

If this session can't attach or clone repos, or the push keeps failing, give the user the finished Markdown (frontmatter included) and its intended path, and say plainly that it wasn't saved yet.
