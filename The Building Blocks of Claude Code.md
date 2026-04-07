# The Building Blocks of Claude Code

*For business leaders, product managers, and anyone curious about how Anthropic's AI assistant actually works.*

---

## Table of Contents

- [What Is Claude Code?](#what-is-claude-code)
- [How Can You Use Claude Code?](#how-can-you-use-claude-code)
- [1. The Brain: The Claude AI Model](#1-the-brain-the-claude-ai-model)
- [2. The Conversation Loop: How Claude Code "Thinks"](#2-the-conversation-loop-how-claude-code-thinks)
- [3. The Toolbox: What Claude Code Can Actually Do](#3-the-toolbox-what-claude-code-can-actually-do)
- [4. The Commands: Your Reusable Shortcuts](#4-the-commands-your-reusable-shortcuts)
- [5. Skills: The Smarter, Self-Activating Successor](#5-skills-the-smarter-self-activating-successor)
- [6. Subagents: Your Custom Specialist Team](#6-subagents-your-custom-specialist-team)
- [7. Memory: The Kitchen's Logbook](#7-memory-the-kitchens-logbook)
- [8. MCP Servers: The Kitchen's Supply Chain](#8-mcp-servers-the-kitchens-supply-chain)
- [9. Hooks: The Kitchen's Safety Interlocks and House Rules](#9-hooks-the-kitchens-safety-interlocks-and-house-rules)
- [10. Plugins: The Boxed Meal Kit](#10-plugins-the-boxed-meal-kit)
- [11. CLAUDE.md: The Kitchen's House Manual](#11-claudemd-the-kitchens-house-manual)
- [12. The Safety System: Asking Before Acting](#12-the-safety-system-asking-before-acting)
- [14. Best Practices](#14-best-practices-httpscodeClaudecomdocsenbest-practices)
- [How It All Fits Together](#how-it-all-fits-together)
- [Why This Matters](#why-this-matters)

---

## What Is Claude Code?

Imagine you hired a very talented entry-level employee who never sleeps, reads incredibly fast, and can work on your entire project at once. That is essentially what Claude Code is: an AI-powered assistant built by Anthropic that can read, write, and manage files -- code, documents, data, reports, and much more -- by working directly on your computer.

While it started as a coding tool, Claude Code is equally capable with non-technical work: drafting investment memos, cleaning up spreadsheets, summarizing research, organizing files, generating reports, reviewing documents, and automating repetitive tasks. If it involves reading, writing, or transforming information on your machine, Claude Code can likely help.

But how does it actually work? What is happening under the hood? This guide walks through the six building blocks that make Claude Code tick, using everyday language and familiar analogies. Think of it as a tour of a well-organized workshop, where each section shows you a different part of how the work gets done.

---

## How Can You Use Claude Code?

One of Claude Code's strengths is that it meets you where you already work. The same powerful assistant -- the same brain, tools, and capabilities -- is available through five different surfaces, each designed for a different way of working:

| Surface | Installation | Local File Access | IDE Context | Best For |
|---|---|---|---|---|
| **Terminal (CLI)** | `npm install -g @anthropic-ai/claude-code` | Full | No | Power users, automation, remote servers |
| **VS Code** | Install extension from marketplace | Full | Yes -- sees open files, selections, project | Day-to-day development in VS Code |
| **JetBrains** | Install plugin from marketplace | Full | Yes -- sees open files, selections, project | Development in IntelliJ, PyCharm, WebStorm |
| **Desktop App** | Download from Anthropic | Full | No | Non-technical users, document workflows |
| **Web App** | None -- [claude.ai/code](https://claude.ai/code) | No -- cloud only | No | Quick access, no-install trial |
| **Remote Control** | `claude remote-control` or `/rc` inside a session | Full -- files stay on your local machine | No | Control your local session from a browser or the Claude mobile app on any device |

All six surfaces connect to the same Claude brain and support the same core features: commands, skills, MCP servers, memory, and the full agentic loop. The difference is where and how you interact with them. Choose the one that fits your workflow -- or use several for different situations, the way you might check email on your phone, laptop, and tablet depending on where you are.

For full details on each surface, see the official [Claude Code Overview](https://code.claude.com/docs/en/overview#web).

---

## 1. The Brain: The Claude AI Model

At the heart of Claude Code is an AI model -- a "brain" that has been trained on enormous amounts of text to understand language, reason through problems, and generate helpful responses. This brain is what lets Claude Code understand your request, figure out a plan, and write actual working code.

Anthropic offers this brain in three sizes, each named after poetic forms:

- **Haiku** -- The quick thinker. Like a sharp colleague who gives you a fast, reliable answer in seconds. Haiku is best for simple, high-volume tasks where speed matters more than depth. Think of it as the express checkout lane.

- **Sonnet** -- The everyday workhorse. Like a seasoned team member who balances quality and speed well. Sonnet handles most tasks capably and is the model most people interact with day to day. It is the reliable all-purpose vehicle in the fleet.

- **Opus** -- The deep expert. Like a senior architect who takes more time but produces the most thoughtful, highest-quality work. Opus is for complex problems that require careful reasoning -- the kind of challenge where you want someone to really sit down and think it through.

Why have three sizes? For the same reason a company has different roles. You would not ask your most senior engineer to rename a variable, and you would not ask an intern to redesign the system architecture. Different tasks call for different levels of capability (and cost). Teams can choose the right brain for the right job.

Switching between models is simple. In the **terminal**, type the `/model` slash command during a session to see and select a different model. In the **VS Code extension**, click the model name displayed in the Claude Code panel header to switch -- or use the `/model` command in the chat input. You can also launch Claude Code with a specific model from the terminal using `claude --model opus` (or `sonnet` or `haiku`).

---

## 2. The Conversation Loop: How Claude Code "Thinks"

![The Agentic Loop -- How Claude Code thinks in a cycle](https://mintcdn.com/claude-code/c5r9_6tjPMzFdDDT/images/agentic-loop.svg?w=1100&fit=max&auto=format&n=c5r9_6tjPMzFdDDT&q=85&s=448a4456db3f9d4fbf35660604f24ca5)

*Source: [How Claude Code Works -- Official Documentation](https://code.claude.com/docs/en/how-claude-code-works)*

Claude Code does not just answer a question and stop. It works in a continuous cycle, much like a skilled craftsperson tackling a home renovation project:

1. **Listen** -- The craftsperson hears what you want. ("I'd like to add a new feature to the login page.")
2. **Think** -- They consider the best approach. ("I should first look at the existing login code, then figure out where to add this.")
3. **Act** -- They pick up a tool and do something. (They read the relevant files, or make an edit.)
4. **Observe** -- They step back and check their work. ("Okay, I made the change. Did anything break? Let me run the tests.")
5. **Repeat** -- Based on what they see, they decide what to do next. Maybe the tests passed and they are done. Maybe something broke and they need to fix it. The cycle continues.

This loop can run dozens of times for a single task. Claude Code might read 15 files, make changes to 5 of them, run tests, notice one failure, fix it, run the tests again, and only then report back to you with the finished result.

This loop is also the fundamental reason why AI agents like Claude Code produce significantly better results than web chat interfaces like claude.ai or chatgpt.com. Web chat has a limited agentic loop and a limited set of tools. For example, if you ask a web chat to fix a bug in your code, it will give you a suggested fix -- but it has no way to actually build the project and verify that the code compiles without errors. You have to copy the code, paste it into your editor, run the build yourself, and if it fails, go back to the chat and try again. An agent like Claude Code, by contrast, writes the fix, builds the project, sees the error, adjusts the code, and rebuilds -- all on its own, in seconds. It can check its own work, catch mistakes before they compound, self-correct when it drifts, and improve as it iterates -- much like how a draft that goes through multiple rounds of revision will almost always be better than a first attempt. Anthropic's own research confirms that this iterative cycle makes agents "fundamentally more reliable" than single-pass responses, particularly for complex, multi-step tasks.

Here are three distinct ways to consume LLMs, each suited to different needs:

- **Web Chat** (e.g., claude.ai, chatgpt.com) -- Best for ad hoc, conversational tasks where a human is in the loop: brainstorming ideas, asking questions, drafting prose, exploring a topic, or getting a quick code suggestion you will review and paste yourself. Use web chat when the task is one-shot, does not require access to your local files or systems, and a human will act on the output. It is the lowest barrier to entry -- no setup, no code, just a browser.

- **API** (e.g., Anthropic Messages API, OpenAI Chat Completions API) -- Best for programmatic, automated tasks that are well-defined and self-contained: classifying support tickets, summarizing documents in a pipeline, extracting structured data from emails, generating personalized content at scale, or embedding intelligence into an existing application. Use the API when you need to call the model from your own code, process inputs in bulk, or integrate LLM capabilities into a product or workflow -- and when each call can succeed in a single pass without needing to read files, run commands, or self-correct.

- **Agent SDK / Framework** (e.g., Anthropic's Claude Agent SDK, OpenAI's Agents SDK, LangChain, CrewAI, or tools like Claude Code itself) -- Best for complex, multi-step tasks that require autonomy, tool use, and self-correction: building a feature across multiple files, debugging a failing test suite, researching a topic across several sources and synthesizing the results, or orchestrating a workflow that involves reading data, making decisions, and taking actions. Use an agent framework when the task cannot be solved in a single LLM call -- when the AI needs to plan, act, observe results, and iterate, much like the agentic loop described above.


This distinction becomes especially important when you want to automate tasks using AI. Before building an automation, it is worth asking: does this task actually need the full power of an agent -- the agentic loop, the tool use, the self-correction? If so, you should reach for an Agent SDK (such as Anthropic's Claude Agent SDK, OpenAI's Agents SDK, or similar frameworks) that gives you all of those capabilities out of the box. But if the task is simple and well-defined -- say, summarizing a document, classifying a support ticket, or extracting key details from an email -- a direct call to an LLM API is faster, cheaper, and perfectly sufficient. Anthropic themselves advise teams to "find the simplest solution possible, and only increase complexity when needed" In other words, match the tool to the job: use the full workshop when you need it, but do not bring a construction crew to hang a picture frame.

The rule of thumb: start with the simplest option that gets the job done. If a web chat conversation is enough, use that. If you need to automate it, use the API. If the automation requires judgment, iteration, and tool use, reach for an agent.

---

## 3. The Toolbox: What Claude Code Can Actually Do

An AI brain that can only talk is like a carpenter who can describe beautiful furniture but has no hands. "Without tools, Claude can only respond with text. With tools, Claude can act: read your code, edit files, run commands, search the web, and interact with external services"

Tools in Claude Code are not directly invoked by users. They are invoked autonomously by the agent as part of the agentic loop. When Claude Code encounters a task, it reaches for the right tool: "I need to understand this file" (grabs the reading tool), "I need to change this function" (grabs the editing tool), "I need to make sure nothing broke" (grabs the command-running tool to execute tests). It chooses which tool to use and in what order, just as an experienced worker would.

For a complete list of all tools available in Claude Code, see the official [Tools Reference](https://code.claude.com/docs/en/tools-reference).

---

## 4. The Commands: Your Reusable Shortcuts

While tools are used by Claude Code on its own (you never call them directly), **commands** are the opposite -- they are shortcuts that you, the user, trigger whenever you want. Think of them as recipe cards in a box: you flip through, pick one, and hand it to the chef. The chef only cooks that dish when you ask.

For example, imagine you frequently ask Claude Code to review a document using the same checklist every time. Instead of typing out that request over and over, you can save it as a command. The next time, you just type `/project:review` and the full set of instructions runs automatically.

Commands are simple Markdown files stored in specific folders:

| Scope | Where to save | How to invoke |
|---|---|---|
| **Project commands** (shared with your team) | `.claude/commands/review.md` | `/project:review` |
| **Personal commands** (just for you) | `~/.claude/commands/review.md` | `/user:review` |

The filename becomes the command name -- a file called `weekly-report.md` becomes `/project:weekly-report`.

You can even include a placeholder called `$ARGUMENTS` so the command adapts to different inputs. For example, a command file containing "Summarize the key risks in $ARGUMENTS" lets you type `/project:summarize-risks Q3 earnings call transcript` and Claude will fill in the blanks.

Common things people save as commands include: code review checklists, commit message workflows, report generation templates, PR description drafters, and issue triage procedures -- any task you find yourself repeating. For a complete list of all built-in commands that Claude Code offers out of the box, see the official [Commands Reference](https://code.claude.com/docs/en/commands).

Commands are evolving into a newer, more powerful concept called **skills** (stored in `.claude/skills/`), which can include supporting files, templates, and more sophisticated behavior. But the core idea remains the same: capture a repetitive task once, reuse it forever.

## 5. Skills: The Smarter, Self-Activating Successor

Skills are the next evolution of commands -- and they represent a meaningful leap forward. If commands are recipe cards, skills are an intelligent recipe system -- one that organizes your recipes, knows which dish pairs with which occasion, and can suggest the right recipe before you even ask. The chefs (agents and subagents) use this system to know exactly what to cook and how.

A skill lives in its own folder (`.claude/skills/name/`) and is defined by a file called `SKILL.md`. But unlike a command's single markdown file, a skill folder can also contain supporting materials: templates, reference documents, example outputs, helper scripts -- everything Claude needs to do the job well. Think of it as giving your assistant not just the instructions, but also the style guide, the boilerplate, and the sample deliverables.

The most powerful difference is **auto-invocation**. Commands sit in a drawer until you explicitly call them. Skills, by contrast, can activate themselves. Each `SKILL.md` file includes a description and trigger conditions. When Claude detects that your request matches those conditions, it loads and follows the skill automatically -- no slash command required. For example, if you have a skill for generating IC memos and you say "draft a memo for the Warburg Pincus fund," Claude recognizes the match and activates the skill on its own, applying all the formatting rules, templates, and conventions bundled inside.

You can still invoke a skill manually with `/name` (for project skills) or `/user:name` (for personal skills), just as you would with commands. But the auto-invocation means you do not have to remember what skills exist -- Claude will find and use the right one when the moment calls for it.

Skills also support **tool restrictions** via an `allowed-tools` field in their frontmatter. This lets you limit what Claude can do while executing a particular skill. For instance, a research skill might be restricted to read-only tools, ensuring it can explore and analyze but never modify your files. This is like telling a consultant: "You can look at anything, but do not change anything."

Because skills are folder-based and self-describing, they are also the building blocks of **plugins** -- shareable packages that bundle skills, MCP servers, hooks, and subagents into one installable unit. When someone shares a plugin with you, the skills inside it become available to Claude automatically, no configuration required.

Skills work across platforms -- not just in Claude Code, but also in claude.ai, the API, and other tools that support the skills format. This cross-platform portability means you can build a skill once and use it everywhere.

## 6. Subagents: Your Custom Specialist Team

If commands are the recipe cards and skills are the intelligent recipe system, then **agents and subagents are the chefs** -- the ones who actually do the cooking. The main agent is the head chef running the kitchen, and subagents are the specialist cooks brought in for specific stations, each with a defined role, a specific set of tools, and clear boundaries around what they can and cannot do.

A subagent is a pre-configured agent definition that lives in your project (`.claude/agents/name.md`) or your personal setup (`~/.claude/agents/name.md`). Each one is a Markdown file with frontmatter that defines the agent's personality, its allowed tools, and its constraints. When the main Claude Code session encounters a task that matches a subagent's expertise, it can spawn that subagent to handle it -- or you can invoke one explicitly by name.

Think of it this way: imagine you run a restaurant kitchen. The head chef (the main agent) plans the menu, coordinates everything, and talks to the customer. But for a big event, the head chef brings in specialist cooks -- a pastry chef, a sushi chef, a grill master -- each with their own expertise and station. The head chef briefs them on what is needed, they go work independently, and they bring the finished dish back. That is exactly how subagents operate.

Here is what makes subagents distinct from the main agent:

- **Isolation** -- Each subagent gets its own context window, completely separate from the main conversation. It cannot see what you discussed with the main agent before it was spawned. This keeps each specialist focused on their assigned task without being distracted or confused by unrelated context.

- **Tool restrictions** -- You can limit what tools a subagent has access to. A research-focused subagent might only be allowed to read files and search the web, with no ability to edit or run commands. A code review subagent might be read-only. This is like giving each consultant a badge that only opens certain doors -- the compliance reviewer can read the contracts but cannot rewrite them.

- **No nesting** -- Subagents cannot spawn their own subagents. This is a deliberate design choice that prevents runaway delegation chains. The head chef delegates to the station cooks, but the station cooks cannot hire their own assistants.

- **Parallelism** -- The main agent can run multiple subagents simultaneously -- up to ten at once. Need to research three competing frameworks, review a security policy, and scan a codebase for deprecated patterns? Five subagents can tackle all of those in parallel, each returning their findings to the main agent for synthesis.

Claude Code comes with several **built-in subagent types** that are always available, even without any custom configuration:

| Subagent Type | What It Does | Think of It As... |
|---|---|---|
| **Explore** | Fast codebase exploration -- finds files, searches for patterns, answers structural questions | A scout sent ahead to map the terrain |
| **Plan** | Designs implementation strategies, identifies critical files, considers trade-offs | An architect who draws up blueprints before construction begins |
| **General-purpose** | Handles complex, multi-step research and analysis tasks | A versatile senior analyst you can point at any problem |

You can also define your own custom subagents tailored to your team's needs. For example:

- A **security reviewer** subagent with read-only tools that audits code changes against your security checklist
- A **documentation writer** subagent that generates docs following your team's style guide
- A **test designer** subagent that reads a feature specification and proposes test cases

Each custom subagent is just a Markdown file. The filename becomes the subagent's name -- a file called `security-review.md` in `.claude/agents/` creates a subagent the main agent can invoke as `security-review`. Inside the file, you specify the agent's description (so Claude knows when to use it), its allowed tools, and its instructions -- much like writing an onboarding document for a new specialist on your team.

Because subagents are file-based and live alongside your project, they can be version-controlled and shared with your team -- everyone gets the same specialists, configured the same way.

## 7. Memory: The Kitchen's Logbook

Even the best kitchen team forgets things between shifts. What did the health inspector flag last week? Which supplier was unreliable last month? What is the trick to getting that finicky soufflé just right? Without a written record, hard-won lessons evaporate and the same mistakes get repeated.

That is the problem **memory** solves in Claude Code. Memory is the kitchen's **logbook** -- a notebook the chefs write in during service and review before the next shift begins. It captures the lessons, preferences, and context that matter across sessions, so Claude does not start from scratch every time you open a new conversation.

Memory operates on two levels, just like a real kitchen team's knowledge:

**Working memory (the prep board)** -- During a single session, everything is live in front of the chefs. Every file Claude read, every change it made, every test result it saw -- it is all spread out on the prep board (the context window). The chefs can glance at any of it while they are working. But the prep board has a finite size -- roughly 200,000 tokens, equivalent to a 400-page book. When it fills up, Claude tidies by summarizing older work and clearing space, like sweeping aside finished prep to make room for the next course. The key takeaways stay; the granular details get archived.

**Long-term memory (the logbook)** -- When the shift ends and the kitchen closes (you end a session), the prep board gets wiped clean. But before it does, Claude jots down the important lessons in a persistent logbook. The next time the kitchen opens, Claude flips through the logbook to refresh itself: "Ah right, this project uses a specific naming convention. The build command has a quirk. The user prefers concise explanations." It will not remember every word of yesterday's conversation, but it will remember what it learned.

The logbook lives at:

- **`~/.claude/projects/<project>/memory/MEMORY.md`** -- The table of contents. Loaded at the start of every session, like a chef scanning the logbook's index before the first order comes in.
- **`~/.claude/projects/<project>/memory/*.md`** -- Individual topic pages. Each one captures a specific lesson or piece of context -- like separate pages in the logbook for "supplier notes," "plating standards," and "equipment quirks."

The `<project>` folder is derived from your repository path, so all branches and subdirectories of the same project share one logbook. This makes sense: the kitchen's lessons apply whether you are cooking for the lunch service or the dinner service.

Here is how memory fits alongside the other pieces: **CLAUDE.md is the house manual** -- written by you, read by the chefs, stable and deliberate. **Memory is the logbook** -- written by the chefs themselves as they learn, evolving organically over time. The house manual says "this is how we do things." The logbook says "here is what we have discovered along the way." Both are loaded at session start; together they give Claude a rich, up-to-date understanding of your project without you having to repeat yourself.

Memory is also personal -- it is stored in your user directory, not in the project repository. Two people working on the same project will each have their own logbook, shaped by their own conversations and preferences. This is like two chefs who work the same station on different shifts: they share the house manual, but each keeps their own notes.

For a deeper look at how working memory and long-term memory interact -- including how the context window fills and summarizes -- see the official [Memory Documentation](https://code.claude.com/docs/en/memory).

## 8. MCP Servers: The Kitchen's Supply Chain

So far we have recipe cards (commands), an intelligent recipe system (skills), and chefs (agents and subagents). But even the best chefs with the best recipes cannot cook if the kitchen has no ingredients, no specialty equipment, and no connection to the outside world. That is where **MCP servers** come in.

MCP stands for Model Context Protocol, but the name matters far less than what it does. An MCP server is like a **supplier or specialty vendor** that the kitchen relies on. One supplier delivers fresh seafood from the fish market (your database). Another brings exotic spices from overseas (a third-party API like Slack or GitHub). A third installs and maintains a wood-fired pizza oven the kitchen could never build on its own (a specialized tool like a browser automation service or a vector search engine). The chefs do not need to know how the fish was caught or how the oven was built -- they just need to know it is available and how to use it.

In practical terms, each MCP server gives Claude Code access to **new tools and data sources** that do not exist in its built-in toolbox. Without MCP, Claude Code can read your local files, edit them, run shell commands, and search the web. With MCP, the possibilities expand dramatically:

- **Connect to your database** -- The chef can now look up live data to inform decisions, like checking the pantry inventory before planning tonight's menu.
- **Read from your ticketing system** (Jira, Linear, GitHub Issues) -- Instead of you copying and pasting a ticket description, the chef walks over to the order board and reads it directly.
- **Post to Slack or send notifications** -- The chef can call the front of house to let them know a dish is ready, without leaving the kitchen.
- **Access your company's internal documentation** (Confluence, Notion, SharePoint) -- Like having a reference library right in the kitchen, so the chef can look up house recipes, health codes, or supplier contracts on the spot.
- **Use browser automation or web scraping tools** -- Like sending a runner out to the market to check today's prices before placing an order.

MCP servers are configured in a file called `.mcp.json` (for project-level servers shared with the team) or `~/.claude.json` (for personal servers that follow you across projects). The configuration tells Claude Code where each server lives and how to connect to it -- like keeping a supplier directory pinned to the kitchen wall.

Here is the important distinction: **MCP servers do not do the cooking.** They provide ingredients and equipment; the chefs (agents and subagents) decide when and how to use them. When the head chef decides a dish needs data from the database, they reach for the MCP-provided tool the same way they would reach for a built-in tool like reading a file. The chef chooses; the supplier delivers. This means MCP is non-deterministic -- Claude decides when to call an MCP tool based on what the task requires, just as a chef decides when to call the fish supplier based on what is on tonight's menu.

This supplier model also means MCP servers can run **locally** (on your machine, like an on-site herb garden) or **remotely** (on a server somewhere, like a wholesale distributor). Some are open-source and community-maintained, some are official integrations from companies like GitHub or Atlassian, and some are custom-built by your own team for internal systems.

The MCP ecosystem is growing rapidly, and new servers are being published regularly. Major technology companies are building their own official MCP servers -- for example, Microsoft maintains a collection of MCP servers for its products and services at [github.com/microsoft/mcp](https://github.com/microsoft/mcp). For the kitchen, this means the supply chain keeps getting richer -- more ingredients, more specialty equipment, more connections to the outside world -- all without the chefs themselves needing to change how they work.

## 9. Hooks: The Kitchen's Safety Interlocks and House Rules

Every professional kitchen has rules that are non-negotiable -- rules that fire automatically regardless of what the chef wants. The fire suppression system activates if the temperature gets too high. The walk-in cooler alarm sounds if the door is left open. The health inspector's handwashing sign is posted at every station. These are not suggestions the chef can choose to follow or ignore. They are **automatic, deterministic safeguards** built into the kitchen itself.

That is exactly what **hooks** are in Claude Code. A hook is a shell command that fires automatically at a specific point in Claude Code's lifecycle -- before a tool is used, after a tool is used, or when Claude is about to stop and present its final answer. The chefs (agents) have no say in whether a hook runs. If the rule is set, it fires. Every time. No exceptions.

Here are some common ways hooks are used, mapped to the kitchen analogy:

- **Auto-format on save** -- Like the kitchen rule that every plate must be wiped clean before it leaves the pass. Whenever Claude edits a file, a hook automatically runs the code formatter to ensure consistent style. The chef does not have to remember; the kitchen enforces it.

- **Lint before commit** -- Like a quality inspector who checks every dish before it goes to the customer. Before Claude commits code, a hook runs the linter to catch problems. If the linter finds issues, the commit is blocked -- the dish goes back to the kitchen.

- **Block edits to protected files** -- Like a locked spice cabinet that only the head chef has the key to. A hook can prevent Claude from modifying certain critical files (configuration files, security policies, production secrets), no matter what the task requires. If the chef tries to open the cabinet, the lock stops them.

- **Notify on completion** -- Like a bell that rings when an order is ready. A hook can send a notification (a Slack message, a desktop alert, a log entry) whenever Claude finishes a task, so you know to come check the results.

Hooks are configured in `settings.json` (either at the project level in `.claude/settings.json` or globally in `~/.claude/settings.json`). Each hook specifies three things: **when** it fires (the event), **what** it runs (a shell command), and optionally **which** tools or files it applies to (a matcher). This is like writing a house rule on a card and posting it at the relevant station: "At the grill station, after every use, run the cleaning brush."

The critical distinction between hooks and everything else in this section is **determinism**. Commands, skills, MCP tools -- the chefs choose when to use these. They are discretionary. Hooks are not. Hooks are the kitchen's safety interlocks and house rules: they fire based on events, not decisions. The oven shuts off at 400 degrees whether the chef wants it to or not. This makes hooks your most reliable mechanism for enforcing standards, because they bypass the AI's judgment entirely.

## 10. Plugins: The Boxed Meal Kit

We now have all the individual pieces of the kitchen: recipe cards (commands), an intelligent recipe system (skills), chefs (agents and subagents), a supply chain (MCP servers), and safety interlocks (hooks). But imagine you are opening a new restaurant location and you want it to run exactly like the original. You would not hand the new team a pile of loose recipes, a list of suppliers, and a stack of safety rules and say "figure it out." You would give them a **boxed kit** -- everything they need, organized and ready to go.

That is what a **plugin** is. A plugin is a distribution package that bundles skills, MCP servers, hooks, and subagent definitions into a single installable unit. It is not a new type of capability -- it is a container for the capabilities you have already seen.

Think of it like a franchise starter kit for a restaurant:

- The **recipes** (skills) -- all the signature dishes, with instructions and templates
- The **supplier contracts** (MCP servers) -- pre-configured connections to the approved ingredient vendors
- The **house rules** (hooks) -- the safety interlocks and quality standards, ready to enforce from day one
- The **specialist chef profiles** (subagents) -- role definitions for the pastry chef, the grill master, and the prep cook, so the new kitchen knows exactly who to hire and what they should do

When someone shares a plugin with you, you install it with a single command (`/install`), and all of its contents become available to Claude Code immediately. The skills auto-invoke when relevant, the MCP servers connect to the right services, the hooks enforce the right standards, and the subagents are ready to be dispatched. No manual configuration required -- just unbox and cook.

Plugins are defined by a `plugin.json` file inside a `.claude-plugin/` directory. This manifest lists everything the plugin contains and how it should be configured. Teams can publish plugins internally (for company-wide standards) or publicly (for the community), making it easy to share proven workflows and toolchains.

The plugin model is especially powerful for teams and organizations. Instead of every developer configuring their own MCP connections, writing their own hooks, and building their own skills from scratch, a team lead or platform engineer can package the team's entire setup into a plugin. New team members install it on day one and immediately have the same capabilities, the same guardrails, and the same workflows as everyone else -- like a new cook walking into a fully stocked, well-organized kitchen on their first shift.

## 11. CLAUDE.md: The Kitchen's House Manual

Every well-run kitchen has a house manual -- a binder that sits on the counter and tells every chef, from the head chef to the newest line cook, how this particular kitchen operates. What is the plating style? Which suppliers do we prefer? What are the dietary restrictions we always accommodate? How do we label and date prep containers? A new hire reads the manual on day one and immediately understands the house standards.

That is what **CLAUDE.md** is. It is a plain Markdown file that you place in your project, and Claude Code reads it at the start of every session -- like a chef reviewing the house manual before the first ticket comes in. Everything in CLAUDE.md becomes part of Claude's working context: your terminology, your standards, your preferences, your conventions. The chefs (agents and subagents) follow these instructions the same way a kitchen team follows the house manual -- consistently, every service, without being reminded.

CLAUDE.md files stack in layers, just like a restaurant chain might have rules at different levels:

- **`~/.claude/CLAUDE.md`** (Global) -- The corporate manual. Your personal standards that apply to every project you work on, like your preferred writing style or how you like files organized. This is like a chef's personal habits they bring to every kitchen they work in.

- **`CLAUDE.md`** (Project root) -- The restaurant's house manual. Shared with the whole team via version control. This is where you put project-specific standards: naming conventions, architectural decisions, build instructions, domain terminology. Every chef in this kitchen follows the same rules.

- **`CLAUDE.local.md`** (Project root, not shared) -- Your personal sticky notes on the house manual. Maybe you prefer a different editor shortcut, or you want to remind Claude about a quirk in your local setup. These are private to you and not committed to the repository.

If instructions conflict, the more specific layer wins -- just like how a restaurant's "no substitutions on the tasting menu" overrides the corporate policy of "accommodate all requests."

The house manual is not a recipe (that is a command or skill), not a supplier (that is MCP), not a safety interlock (that is a hook), and not a chef (that is an agent). It is the **shared understanding** that makes everything else work together coherently. Without it, every chef would cook the same dish differently. With it, the whole kitchen operates as one.

For a detailed walkthrough of CLAUDE.md -- including examples for both technical and non-technical projects -- see the official [CLAUDE.md Documentation](https://code.claude.com/docs/en/memory#claudemd).

---

## 12. The Safety System: Asking Before Acting

Here is where Claude Code differs sharply from a script that just runs on autopilot. Claude Code operates like a responsible contractor working on your house: it asks before doing anything significant.

Imagine you have hired a contractor to renovate your kitchen. A good contractor does not just start knocking down walls. They say: "I'd like to remove this cabinet to make room for the new island. Is that okay with you?" You can say yes, or say "No, let's keep that one." You stay in control of your home.

Claude Code works the same way. It classifies every action by risk level:

- **Safe actions** (like reading a file) happen automatically -- the contractor does not need your permission to measure a wall.
- **Moderate actions** (like editing a file) get flagged for your approval -- the contractor checks before making changes.
- **Potentially risky actions** (like running a command that could delete things) require explicit permission -- the contractor definitely asks before swinging a sledgehammer.

You can also customize these boundaries by choosing a **permission mode** -- think of it as setting the level of autonomy you give your contractor:

| Mode | Reading Files | Editing Files | Running Commands | Best For |
|---|---|---|---|---|
| **Default** | Automatic | Asks you | Asks you | Beginners -- safest, the contractor checks before every action |
| **Accept Edits** | Automatic | Automatic | Asks you | Prototyping -- the contractor can paint freely but asks before using power tools |
| **Plan** | Automatic | Blocked | Blocked | Research only -- the contractor can inspect and advise but cannot touch anything |
| **Auto** | Automatic | Automatic | AI safety classifier decides | Experienced users -- a supervisor watches and only flags risky commands |
| **Don't Ask** | Automatic | Blocked (unless pre-approved) | Blocked (unless pre-approved) | Automation pipelines -- only pre-approved actions run, everything else is denied |
| **Bypass Permissions** | Automatic | Automatic | Automatic | Isolated containers only -- full autonomy, no questions asked (use with caution) |

You can cycle through the common modes (Default, Accept Edits, Plan) by pressing Shift+Tab inside Claude Code. The more advanced modes (Auto, Don't Ask, Bypass Permissions) are enabled through command-line flags or settings for users who know what they are doing.

Each mode can also be set explicitly when launching Claude Code from the terminal:

| Mode | Command |
|---|---|
| **Default** | `claude --permission-mode default` |
| **Accept Edits** | `claude --permission-mode acceptEdits` |
| **Plan** | `claude --permission-mode plan` |
| **Auto** | `claude --permission-mode auto` (requires `claude --enable-auto-mode` first) |
| **Don't Ask** | `claude --permission-mode dontAsk` |
| **Bypass Permissions** | `claude --dangerously-skip-permissions` (isolated containers only) |

For teams that want a consistent default, any mode can also be set permanently in the project's settings file (`.claude/settings.json`) so that everyone starts in the same mode automatically.

---


## 14. Best Practices: https://code.claude.com/docs/en/best-practices


---

## How It All Fits Together

These six building blocks do not operate in isolation. They form an integrated system, like the organs of a body or the departments of a well-run company:

1. You give Claude Code a task.
2. The **Brain** (AI model) understands your request.
3. The **Conversation Loop** begins: Claude Code thinks about what to do first.
4. The **Thinking Process** kicks in for complex planning -- you can nudge the depth with keywords like `think`, `megathink`, or `ultrathink`.
5. Claude Code reaches into its **Toolbox** to read files, make changes, and run tests.
6. The **Safety System** checks with you before doing anything risky.
7. The **Commands, Skills, CLAUDE.md, Memory, Subagents, MCP servers, Hooks, and Plugins** provide the recipes, house manual, chefs, institutional knowledge, supply chain, safety interlocks, and packaging that make it all work together.
8. The loop repeats until the task is complete.

The result is an assistant that can take a request like "Add a password reset feature to our application" and independently explore the codebase, design an approach, write the code across multiple files, add tests, run them, fix any failures, and present you with the finished result -- all while checking with you at appropriate moments and following your team's standards.

---

## Why This Matters

You do not need to understand any of these building blocks to use Claude Code effectively. Millions of people drive cars without understanding internal combustion engines. But for leaders, stakeholders, and anyone making decisions about whether and how to adopt AI-assisted development, understanding the architecture helps you:

- **Set realistic expectations** -- Claude Code is powerful but not magic. It works within the boundaries of its context window, its tools, and its permissions.
- **Make informed decisions** -- Knowing that different model sizes exist helps you balance cost and quality. Knowing about the permission system helps you assess risk.
- **Communicate with your team** -- When an engineer says "we configured the CLAUDE.md" or "we added an MCP server," you will know what they mean and why it matters.
- **Appreciate the safeguards** -- The permission system, hooks, and human-in-the-loop design mean Claude Code is built to be a powerful tool under human supervision, not an autonomous system running unsupervised.

At its core, Claude Code is a thoughtful combination of a powerful AI brain, a practical set of tools, a disciplined work process, and robust safety guardrails -- all designed to make software development faster and more accessible while keeping humans firmly in the driver's seat.

---

*Sources and further reading:*

- [Claude Code Overview - Official Documentation](https://code.claude.com/docs/en/overview)
- [How Claude Code Works - Official Documentation](https://code.claude.com/docs/en/how-claude-code-works)
- [Claude Code Product Page - Anthropic](https://www.anthropic.com/product/claude-code)
- [How Claude Remembers Your Project - Official Documentation](https://code.claude.com/docs/en/memory)
- [Claude Code Settings and Permissions - Official Documentation](https://code.claude.com/docs/en/settings)
- [Claude's Extended Thinking - Anthropic](https://www.anthropic.com/news/visible-extended-thinking)
- [Enabling Claude Code to Work More Autonomously - Anthropic](https://www.anthropic.com/news/enabling-claude-code-to-work-more-autonomously)
- [Use Claude Code in VS Code - Official Documentation](https://code.claude.com/docs/en/vs-code)
- [The Context Window, Explained - Builder Methods](https://buildermethods.com/library/claude-code-context-window)
- [Claude Code: The Complete 2026 Guide - Medium](https://medium.com/@2315610426/claude-code-the-complete-2026-guide-to-anthropics-agentic-coding-tool-cde4e565725b)
- [How the Agent Loop Works - Claude API Docs](https://platform.claude.com/docs/en/agent-sdk/agent-loop)
- [Connect to External Tools with MCP - Claude API Docs](https://platform.claude.com/docs/en/agent-sdk/mcp)
- [Models Overview - Claude API Docs](https://platform.claude.com/docs/en/about-claude/models/overview)
- [Claude Code Unpacked: Architecture Visual Guide - DEV Community](https://dev.to/subprime2010/claude-code-unpacked-what-the-visual-guide-reveals-about-the-architecture-13le)
- [Claude Ultrathink: Thinking Levels Explained - FindSkill.ai](https://findskill.ai/blog/claude-ultrathink-extended-thinking/)
