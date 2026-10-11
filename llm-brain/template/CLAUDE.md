# Brain

This is {{OWNER}}'s brain: a personal knowledge base of ideas, projects, thoughts, tools and notes. It's plain Markdown, versioned with git, and Claude reads and writes it from any surface (phone app, claude.ai, Claude Code) through the [llm-brain skill](https://github.com/LuisLombaMartinez/llm-brain-skill).

**Read [`GLOSSARY.md`](GLOSSARY.md) first.** It defines every type and action word. Use its words and avoid the ones it lists as confusing.

## Layout

```
ideas/              One file per idea (not yet a project).
projects/<slug>/    One folder per project. README.md is the main page; add more files as it grows.
thoughts/           Personal reflections.
tools/              Claude skills, MCPs, plugins, apps, libraries to try or in use. One file per tool.
notes/              Reference knowledge, including how-tos {{OWNER}} has learned.
GLOSSARY.md         The vocabulary. It is the source of truth for types.
```

## Rules for writing

1. **Every file starts with frontmatter:**

   ```yaml
   ---
   title: Short human title
   type: idea          # idea | project | thought | tool | note
   created: YYYY-MM-DD
   updated: YYYY-MM-DD
   tags: [tag-one, tag-two]
   status: open        # ideas/thoughts/notes: open | archived
                       # projects: active | paused | done | archived
                       # tools: to-try | tried | adopted | dropped
   source: phone-chat  # phone-chat | desktop-chat | claude-code | manual
   ---
   ```
   Tools also get `kind: skill | mcp | plugin | app | library` and `link:` (the URL, if there is one).
   Extra files inside a project folder use `type: project` too.

2. **File names:** lowercase-kebab-case, slugs in English.
   - `ideas/` and `thoughts/`: prefix the date, `YYYY-MM-DD-short-slug.md`.
   - `projects/`, `tools/`, `notes/`: no date, just a stable slug (`tools/github-mcp.md`).

3. **Search before creating.** If a related file exists, update it: append a dated section and bump `updated`. Don't create a duplicate.

4. **Write-ups** (summaries of a conversation) have three sections: **Context** (one or two lines), **Decisions** (bullets) and **Next steps** (a checklist). Put a write-up in the project it's about; if there is no project, make it an idea.

5. **Ideas** captured on the go can be tiny: title, a paragraph in {{OWNER}}'s own words, tags. Don't pad them or invent details.

6. **Tools** have the sections Source, What it does, Why it caught my eye, and Verdict (left empty until tried). Use the link {{OWNER}} gives. If you look up what a tool does, keep it to one or two lines.

7. **Language:** write in the language {{OWNER}} used. Slugs stay in English.

8. **Commit and push** after every change, straight to `main` (no branches or PRs). Message format: `add: ideas/YYYY-MM-DD-slug`, `update: projects/foo`, `promote: ideas/x -> projects/x`, `try: tools/z (adopted)`, `archive: notes/y`.

## Review

When {{OWNER}} asks to review their ideas or tools, go through `ideas/` or the `to-try` tools with them. For each one, suggest what to do (promote, try, merge, archive or leave). Only act on what they confirm.

## Never

- Never store secrets, passwords, API keys or other people's private data.
- Never delete anything unless asked. Archive instead. The one exception is promoting, where the idea file is moved, not lost.
