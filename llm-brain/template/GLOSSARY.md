# Glossary

These are the words for what lives in the brain. Use them exactly, in notes, file names, commit messages and when talking to {{OWNER}}. If something doesn't fit any of them, ask {{OWNER}} whether it needs a new entry (see "Adding a new type"). Don't invent a word on the spot.

## Things you can save (types)

Each type has exactly one folder. **Fallback type: idea.** Use it when the type is unclear and {{OWNER}} can't be asked. The type is decided by **what** is being saved, not by the verb {{OWNER}} uses: "make a note of this MCP" is a **tool**, not a note.

| Type | Folder | What it is | Not to be confused with |
|---|---|---|---|
| **Idea** | `ideas/` | Something to come back to that isn't being worked on yet: a possible project, a "what if", something to try building. One file per idea. | A project. An idea becomes a project only when {{OWNER}} says so (see *Promote*). |
| **Project** | `projects/<slug>/` | Something {{OWNER}} has decided to build or do. It has its own folder: `README.md` is the main page (what, why, status, next steps), and more files can be added as it grows. | An idea, which is not committed to yet. |
| **Thought** | `thoughts/` | A personal reflection, opinion or journal-style entry. | A note, which is factual reference. |
| **Tool** | `tools/` | An existing thing made by someone else that {{OWNER}} wants to try or keeps using: a Claude skill, an MCP server, a plugin, an app, a library. One file per tool. Set `kind:` to `skill`, `mcp`, `plugin`, `app` or `library`. | An idea (something {{OWNER}} might build themselves) and a note (knowledge, not a thing to try). |
| **Note** | `notes/` | Reference knowledge on a topic: how something works, a how-to or technique {{OWNER}} learned, a summary of an article, useful links. | A thought (personal opinion) or a tool (a specific thing to try). |

### What a tool file contains
- **Source:** where {{OWNER}} saw it (link, post, person).
- **What it does:** one or two lines.
- **Why it caught my eye:** in {{OWNER}}'s own words.
- **Verdict:** filled in after trying it, covering what worked, what didn't, and whether it stays.

## Words for actions and formats

| Word | Meaning |
|---|---|
| **Brain** | This repo (`llm-brain`) as a whole. "Save to my brain" means write here. |
| **Write-up** | A summary of a conversation: Context, Decisions, Next steps. It's a format, not a type. It goes inside the project it's about, or becomes an idea if there is no project yet. |
| **Next steps** | The checklist at the end of a project or write-up. Use this phrase rather than tasks, to-dos or action items. |
| **Promote** | Turn an idea into a project. Move it to `projects/<slug>/README.md` and delete it from `ideas/`. Only when {{OWNER}} asks. |
| **Try** | Test a tool. Afterwards set its status to `tried`, then `adopted` or `dropped`, and fill in the verdict. |
| **Archive** | Retire something without deleting it: set `status: archived`. |
| **Review** | Go through `ideas/` (or the `to-try` tools) with {{OWNER}} to decide what to promote, try, merge or archive. |

## Words to avoid

| Avoid | Use instead | Why |
|---|---|---|
| inbox | ideas | There is no separate inbox. Unsorted captures are ideas. |
| memory, memories | brain, note | "Memory" is Claude's own memory feature, which is separate from this. |
| doc, document, page, file (as a type) | the type name (idea, note...) | Too vague. |
| task, to-do, action item | next steps | One word for one concept. |
| skill (as a type), resource, bookmark | tool (with `kind: skill` etc.) | All "things to try" are tools; the kind tells them apart. |
| journal, diary, reflection | thought | One word for one concept. |

## Adding a new type

When {{OWNER}} wants to save something that fits none of the types (for example *book*, *recipe*, *contact*), ask them whether to add a new type. If they say yes:

1. Add a row to the types table above with the type, folder, definition and "not to be confused with".
2. Create the folder with a `.gitkeep` file.
3. Add it to the layout in `CLAUDE.md` and `README.md`.
