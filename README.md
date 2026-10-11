# llm-brain skill 🧠

A Claude skill that turns a private GitHub repo into your **brain**: a place to save ideas, projects, thoughts, tools and notes from any Claude chat (phone, desktop, Claude Code) and pick them up later from any other.

You're walking and get an idea? Tell Claude on your phone *"save to my brain: …"*. Weeks later in Claude Code: *"what's in my brain about that idea?"*

The skill only runs when you say **"my brain"**, so talking about ideas or projects in other chats doesn't set it off.

## Why "llm-brain"?

I'm [Luis Lomba Martínez](https://github.com/LuisLombaMartinez), and I built this for myself. I kept getting ideas while walking, or making decisions in a chat with Claude on my phone, and then losing them. I wanted one place to drop everything and pick it up later from anywhere, including Claude Code.

The name has two meanings. **LLM** is my initials, so it's my brain. It's also a brain written together with a **large language model**. My own brain lives in a private repo with the same name. This repo shares the method behind it, so you can grow your own brain: call it whatever you like, the skill works the same.

## What's in here

```
llm-brain/
  SKILL.md        The skill: when to run, how to read and write the brain, how to commit
  template/       Starter brain, copied into your repo on first setup
    GLOSSARY.md   The vocabulary: types (idea, project, thought, tool, note), action words, words to avoid
    CLAUDE.md     Writing rules: frontmatter, file names, commit messages
    README.md
    ideas/ projects/ thoughts/ tools/ notes/
```

Your brain repo holds your data. This repo only holds the method. Your brain's own `GLOSSARY.md` always wins over the template, so you can add types or rename things without touching the skill.

## Setup

1. **Create an empty private repo** on GitHub for your brain (e.g. `my-brain`).
2. **Install the skill:**
   - **Claude app:** download the `llm-brain/` folder, zip it, and add it as a skill in Claude's settings.
   - **Claude Code:** copy the `llm-brain/` folder to `~/.claude/skills/llm-brain/`.
3. **Set your repo:** in your copy of `SKILL.md`, replace `<owner>/<repo>` on the *Brain repo* line with your repo. If you skip this, Claude asks the first time.
4. In a Claude chat with GitHub access, say **"set up my brain"**. Claude copies the template into your repo and commits it.

## Using it

- "Save to my brain: an app that …"
- "Add this to my brain as a thought: …"
- "Make a note in my brain about this MCP: <link>"
- "Write up what we decided and save it to my brain"
- "What's in my brain about X?"
- "Review the ideas in my brain" / "which tools in my brain haven't I tried?"

## Requirements

Claude needs to be able to attach, clone and push to your GitHub repo from the chat (for example, a Claude session with GitHub connected, or Claude Code with git access). Where it can't, it gives you the finished note and its path so you can commit it yourself.
