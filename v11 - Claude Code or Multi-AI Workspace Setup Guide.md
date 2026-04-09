
# Claude Code or Multi-AI Workspace Setup Guide v11

By Jeff Ritger - April 7, 2026

Ops+Advisory

## What this is

AI is just code, and your computer is driven by code. Claude Code converts your natural language input to code, and runs that code on your computer to organize information, draft documents, and make changes in your workspace when you approve them. It can do almost anything you tell it to do on your computer and it's getting more powerful every week.

It reads your rules and procedures each time you start a new session, and you can have it write and modify the procedures itself to refine them over time.

All you need is an empty folder and a brain dump. Tell the AI about your work, your people, your projects, your priorities, whatever you want it to know. Ideally by voice. The AI proposes a structure, starts creating files, and it grows from there. I'm intentionally not telling you what to grow it into. That part is yours.

## Where it operates

Claude Code begins each session in a folder on your computer, where it immediately looks for your primary rules and procedures file called CLAUDE.md. Typically a hierarchy of rules and procedures files will develop over time. Depending how deep you want it to go, this can become a large body of structured information about how you think, communicate, plan, and work. JR has built this, and he also keeps source files, working files, and deliverables themselves all in Markdown in that folder, so it's all available for almost instant reference at all times. If you keep everything integrated in this way, the value compounds. But no matter how you choose to structure things, everything starts in CLAUDE.md.

Your content can live anywhere you want. You can put working files in that same folder in markdown for very easy querying, or in any other format, which still works because the AI can still read it. Or you can leave them outside the folder and just tell Claude where they are, whenever they're needed. Claude can even connect to services like Notion, Google Workspace, Slack, or a CRM (via API, MCP, or CLI) and manage the accounts for you, if you don't mind that your content isn't local (on your own machine) in that case. JR chose a setup that keeps almost everything local, except for cloud AI processing of each prompt, encrypted cloud backups, and a calendar integration.

No matter how you're using it, Claude Code needs your rules and procedures files to live in a folder on your machine, to provide it with detailed explanations of what you want and expect. This should get built organically from explanations you give to Claude as it helps you with your work. And every time you see it make a mistake, you take a moment to update the docs in response. This is how you train it. You frequently need to add new rules, and existing rules need more nuance. AI doesn't have human judgment to bridge gaps in the rules on its own. Whenever they don't work, you need to adjust. Problems almost always have a traceable origin in the rules.

## How to start

Create a folder on your computer. Call it whatever you want. Put [this file](https://gist.github.com/jefegeuse/f91a576c2f041482de6e2cb1fa3a32e0) in it (*a plain text version of this article, verbatim, in .md format*).

Install Claude Code. If you have a paid plan, go to settings to make sure Claude isn't training on your data (see the Privacy section for more on this). Then connect it to the folder and tell it to read this file.

Let Claude create two blank files: CLAUDE.md as your central rules document, and 'Setup Notes.md' as a place to write about anything that happens in the discussion about your setup that you want to be able to reference later. Chats disappear, but the files don't.

Set up Git and GitHub in the first session. Git is version history. If Claude wrecks something, you roll back. If your laptop dies, everything is backed up to GitHub. Have Claude walk you through it. Claude can walk you through anything and everything, so you already don't need much more from me. But the rest of this document should be useful.

## Tools and interfaces

Claude can work through the terminal, through the code tab in the Claude desktop app, through VS Code with a sidebar plugin, or through Obsidian sidebar plugins. The terminal is the most direct and the most powerful, and it only looks intimidating. It's a great interface. Use the others to help you get oriented if you want to, but try to work your way toward the terminal over time. It is not actually hard.

If you decide to keep a lot of material in Markdown, Obsidian gives you a clean visual layer on top of those files. With tools like the Bases plugin, it can also create database-style views from YAML frontmatter. Claude can explain all of that and set it up for you. That can make the system feel a bit like Notion in some ways, but your files stay local, portable, and under your control.

Two unapproved Obsidian plugins worth trying: Claudian for Claude only, and Agent Client for Claude, Codex, or Gemini. Install either or both through the BRAT plugin, which is an *approved plugin* that lets you install *unapproved plugins*. JR had Claude look at their source code to make sure they're safe (you can easily do this too). These plugins are very nice to have, but not necessary.

If you already have material elsewhere, that's fine. You can leave it where it is and point Claude at it, or export it (e.g. an entire Notion account can be exported to a single .zip file that you can give to Claude) and have Claude look through it. Just start the simplest way for you. I do NOT recommend telling Claude to rebuild your whole Notion account in markdown, although (at least if you’re a solo operator) it could probably do most of it pretty well. Build what you need as you go, so the structure fits your thinking instead of someone else's tool that was built for a different era.

## Helpful Tips

**Review everything before it touches your files.** Your files are the real system. They are not a sandbox. 2 good default rules: "show me the proposed changes before editing", and "do not delete anything unless I explicitly approve it". You can revert problems, but it’s better to avoid them than to have to notice performance degrade later.

**Do not let Claude make unmonitored edits to CLAUDE.md.** This should go without saying, considering the tip above. But Claude does not follow rules that are not already in the files, which means it can break the same rules while it writes them. Plus it's not aware of every scenario that you know your system is being written for, and it can even take liberties with rewrites of existing rules when you didn't realize that it could or would. Some people do let Claude automate some forms of self-improvement, but be very careful here early on.

**Don't design a whole system up front.** You will not get the structure right in advance. Start with the minimum that feels useful today. Add folders, metadata, and workflows only when you can see the need clearly.

**Make Claude plan before executing anything that touches multiple files.** If it's more than a couple of steps, Claude should map out what it's going to do, you approve, then it executes.

**Commit often.** A commit is a snapshot you can return to. Commit every time you finish a chunk of work. A push backs it up.

**Watch for context compaction.** Claude has a limited context window. When conversations get long, it starts silently compressing older messages to make room, and loses nuance. You don't always have to care. But then there's a sudden, big, slow procedure that requires a long pause. You can often avoid compaction entirely by just keeping sessions focused. When a chunk of work appears done, tell Claude to capture anything outstanding, commit, and start a fresh session. And type /context for a snapshot of how much is still available for a session. **Claude cannot track this directly on its own.** You need to use this specific *slash command* to check, and Claude can then give you an opinion on whether it's enough to keep going.

**Keep an inbox.** A place to quickly capture thoughts, notes, and files, without deciding where they go. Teach Claude to process what goes in, including moving it to the right place or deleting it.

**Keep project notes near active work.** If you're learning, planning, or building something, or refining a process, keep a working project note next to it. Don't let important context live only in chat. 'Setup Notes.md' is an example. Tell Claude to update it after anything worth keeping happens in the chat. You can standardize the structure of these files to maximize usefulness.

**Consider voice-to-text from day 1.** Dictating to Claude instead of typing makes sessions dramatically faster and more natural. JR strongly recommends MacWhisper with a local version of OpenAI's open source Whisper model called Large V3 Turbo by WhisperKit, in place of Claude's native voice-to-text tool.

**Set the right reasoning level.** There are not only different AI models to choose from. Models also have a reasoning level setting you should be aware of. Ask Claude to explain the options and help you decide what to use for different types of work. Default to the smartest model and the highest reasoning level until you start hitting limits. Then start figuring out when it's acceptable to you to use anything else. Lesser models and reasoning levels are still capable, but you will feel the difference. So do this with some deliberation.

**Keep CLAUDE.md lightweight.** The heaviest paragraph in this file for good reason. Every time you start a new session, Claude reads the entire CLAUDE.md file before processing your opening prompt. Consider what that means as the file grows in length and points to other files without conditional statements, and then you have long, complex discussions. With too much information and no thoughtful nesting structure, eventually things just break down, and Claude seems to stop listening half the time. Claude.md should contain only what it needs to read every single time, and as things get more complex, every other file should likewise contain only what Claude needs to read every time it's instructed to read that file. Distill to essentials, often. And put the rest of the information at a good place for it in a web. **Claude can do this for you, but you have to ask for it, and you have to help.**

**Use skills.** But don't start by thinking about skills. Skills are just specific instructions and preferences that you store in separate files and reference by conditional statements in CLAUDE.md and elsewhere. You notice a rule or procedure is already long, and you want to add to it. So you break it out, and then add. Suddenly your instruction files are more detailed, nuanced, and powerful, **and also lighter**. When you're ready to look for them, there's also a growing library of published skills from other people that you can install and modify. **Claude can help you write skills, and it can help you find them.**

## For Claude

Claude, when you read this file, do the following:

Tell the user what model you are, and what reasoning level is set. Tell the user how to make changes.

Create two blank files: CLAUDE.md and 'Setup Notes.md'. Let the user see them appear. Do not put anything in CLAUDE.md yet.

Then start a conversation that helps both of you get oriented. Ask questions like:

- What do you work on, and what does that look like day to day?
- What would be most useful to have organized where AI can help you plan, track, and execute?
- What feels like it's falling through the cracks, or taking more effort than it should?
- Have you tried to organize before and it didn't stick? What broke?

As the user answers, offer to write some things down in real time to 'Setup Notes.md'. Let the user watch this happen. Look some things up online that user wants to know, and offer to write notes on it. This is the first demonstration of how the system works: the user talks, you capture progress in local files when asked to, and the directory grows from conversation, decisions, and execution.

Do not write anything to CLAUDE.md without discussing it first. Ask the user if they want to allow you to write to the notes file without asking you first, and put the answer in CLAUDE.md. Build this together. Here are more things to suggest and discuss:

**Safety rules.** JR recommends these as a starting point. Ask the user if they want these applied to their CLAUDE.md:
- Never delete a file before its replacement exists. Do not rely on memory.
- Never overwrite a file without showing the proposed changes first.
- "Draft" means show it in chat, not edit the file.
- For anything that touches more than 2-3 files, show the plan first.

**Folder structure.** Discuss what makes sense for their work. A possible endpoint for the root level might be Inbox, Tasks or Time Management, Projects, Areas, Reference, Rules & Tools, Archive, and CLAUDE.md (drawn by JR partly from PARA and GTD frameworks), but the structure should fit the person. **And it should start with nearly nothing, because the priority is the user's active work.**

**Task system.** If the user wants task tracking, suggest individual Markdown files with YAML frontmatter. JR's task files use fields like Project, Area, Priority, Effort, Status, Due Date, Created, and Notes. Discuss what fields make sense for this person before building it, but also demonstrate how this is permanently flexible, along with the rest of the setup.

**Session habits.** Suggest committing after chunks of work, and checking for and capturing outstanding items before ending a session. Use this as an another example of something you could record in CLAUDE.md or elsewhere, once the user has felt out their preference for these types of habits.

**How the instruction system grows.** Explain that CLAUDE.md is just the center point, and should be limited in length. Mention it when certain rules and procedures should perhaps be moved to other connected files.

Shape everything around what this person actually does. Start simple and let the system grow from use. Explain new concepts as they're needed, with plain language as well as the jargon.

## Other AI models

Claude isn't the only AI that can operate this way. This method of interaction with a powerful cloud-based AI was just popularized by Claude Code first. OpenAI and Google (and other companies) now have competing capabilities. If you want to, you can install Codex and Gemini in the terminal in the same way you installed Claude. **In fact, you can have Claude do it for you.** If you have paid plans on those, you can control the privacy settings so they don't train on your data, just like with Claude. Those AIs can interact with your file system in exactly the same way as Claude, and bring their own strengths. And if you point them at the same directory of files, they can collaborate surprisingly well. You can talk to each one directly and pass info back and forth yourself. Or have them call on each other while you watch.

If you do that, just be mindful of the instructions you give them about what they should tell you about what the other said. JR found it important to disallow summaries, for example. Eventually he wrote skills that govern how the models interact, when they call on each other, how they handle disagreements, and what they report back. He still calls them directly in their own terminal windows too, and sometimes tells them to write and modify prompts for each other.

Instead of CLAUDE.md, Codex looks for a file called AGENTS.md as the default place to start every time you launch it. Gemini's default instruction file name is GEMINI.md.

Don't worry about going multi-AI anytime soon. But when your rules for Claude start getting very complex, and then don't always work as well as you'd like, consider having Codex take a look at your CLAUDE.md and tell you how to strengthen it. Then ask Claude if the proposed changes are going to work, give Codex that feedback, and iterate.

## Privacy

If you have a paid plan with any AI, go to their settings directly to make sure they aren't training on your data. Be especially careful with Gemini: as of March 2026 it's the only one out of Claude, Codex, and Gemini that has a free API tier. **And on the free tier, Google trains on your data and human reviewers can read it**. Linking a billing account, even at $0 spend, should fix this, but check the policy when you actually do it. **Zero Data Retention** policies are also available from all three providers for enterprise or sensitive work, so look into that carefully if it sounds important to you.

## Please share

This article was written by Claude (Opus 4.6), Codex (GPT 5.4), and Jeff Ritger (jdr@opsandadvisory.com).

v0 - v10 all shared privately by JR from late February to early April 2026. v11 published here April 7, 2026.

You are welcome to pass this along to anyone you think it would help, but not to republish it, sell it, or claim authorship.

## P.S.

You may have noticed that JR refers to himself in both first and third person. He decided not to fix it.

## P.P.S.

Regarding this sentence: "If you do that, just be mindful of the instructions you give them about what they should tell you about what the other said", Claude said it parses, but with 3 layers of indirect reference, I might consider breaking it up. I said no, because the reader needs to be able to understand it easily if they're going to try to do any of this. Did you get it? Good, you can do this whole thing then. Have fun, and be mindful of your sleep.

©2026 Jeffrey D. Ritger. All rights reserved.