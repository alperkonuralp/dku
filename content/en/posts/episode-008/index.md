+++
title = "Episode 008 - CLI or Editor for AI Tools?"
date = "2026-03-01"
description = "When using AI tools, should you prefer an editor or the CLI? Alper is on the CLI side, Burak is on the editor side. An honest debate between two dinosaurs."
youtube_url = "https://youtu.be/uToDVhVwktU"
youtube_id = "uToDVhVwktU"
duration = "28:14"
tags = ["CLI", "editor", "Claude Code", "VS Code", "Copilot", "Cursor", "Windsurf", "MCP", "agent", "AI tools"]
notebooklm_url = "https://notebooklm.google.com/notebook/9bb8cd8a-6b64-4a22-a835-92f60209b8ec"
draft = false
+++

## Summary

Should you prefer an editor or the CLI when using AI tools? Alper is on the CLI side (Claude Code), Burak is on the editor side (VS Code + Copilot). From the black-screen culture of the DOS era to today, from agent systems and parallel workflows to MCP server integration and token economics — we debated the strengths and weaknesses of both approaches. Conclusion: Step outside your comfort zone!

## Video

{{< youtube uToDVhVwktU >}}

## Topics

- VS Code + Copilot vs Claude Code CLI comparison
- Love of the terminal: black-screen culture from DOS to today
- Agents, multi-agent systems, and parallel workflows
- The importance of proper documentation and prompt preparation
- Cursor, Windsurf, Anti-Gravity: VS Code alternatives
- The plugin ecosystem and the editor lock-in problem
- Writing your own CLI tools and MCP server integration
- The token cost of running multiple agents simultaneously
- Which profile suits CLI, which suits editors?

## Deep Dive

### The Developer's New Dilemma in the AI Age: CLI or Editor?

#### Introduction: The Return of the Terminal and the Modern Developer's Dilemma

For those with "dinosaur" experience in the software world — those who came from Windows 3.1 black screens and pure Linux terminals — the command line was always a safe harbor. The comfort offered by modern IDEs kept the terminal in the shadows for a long time. Today, with the rise of AI tools, this old friend has returned more powerful than ever. The question is no longer just a matter of interface preference; it's a debate about whether using AI tools through the CLI or through a visual editor is more productive.

#### Speed and Efficiency: Why the CLI Can Be a Secret Weapon

Modern CLI tools like Claude Code have transformed the terminal from a mere text input field into an autonomous development center. Without the overhead of visual rendering, they offer a much faster experience than editors — especially for multi-file operations.

The real difference emerges in **"Agent Mode"** capabilities. Modern CLI agents no longer just write code; they recognize the operating system they're running on, can correct their own path when they enter the wrong directory, and can autonomously run tests.

> "If you don't want to touch the code itself, the CLI side offers a much simpler and faster solution. I think the CLI gets results much faster and creates many files much more quickly."

#### The Power of Editors: Control, Visualization, and the Plugin Trap

Around 80% of developers still prefer editors like VS Code where they can maintain visual control. "See-and-approve" (diff) operations are a great source of confidence for those who want to track AI-suggested changes in real time.

However, there is a critical **"plugin trap."** When Microsoft open-sourced the VS Code infrastructure, powerful alternatives like Cursor, Windsurf, and Anti-Gravity emerged. But some tools — like the critical Docker management extension — only work on the original VS Code. Developers who switch to alternative editors for the latest AI features can suddenly find themselves without essential plugins.

#### A Strategic Shift: "Measure Twice, Cut Once"

AI usage in modern software architecture requires a strategic preparation phase rather than jumping straight into writing code. Language models can perform up to 100% better when working on well-known industry standards. So instead of starting directly in the CLI or IDE, maturing documents with Claude Desktop or browser-based interfaces first, then handing those standardized documents to code development agents, minimizes the margin for error.

#### The Rise of Agents: MCP, Token Economics, and the Time-Cost Balance

AI usage has evolved from simple conversation to self-correcting agent systems. The most notable part of this evolution is **MCP (Model Context Protocol)** servers. We can now write CLI tools specific to our own domain and define them as "capabilities" for agents via MCP.

Parallel workflows — where a review agent oversees a developer agent as it writes code — can complete work that would normally take an hour in just 10 minutes. Technically, this means buying time with token cost — but for an architect, it's a deliberate investment that shortens a project's time-to-market.

#### Conclusion: Step Outside Your Comfort Zone

Choosing CLI or editor isn't just a tool preference — it's a way of managing the developer experience. If you're an editor fan, try CLI tools like Claude Code; if you only live in the terminal, explore the visual diff advantages of tools like Cursor.

**Are you using a tool just out of habit, or does that tool genuinely offer the most efficient solution for your project's architectural needs?**

## Infographic

{{< infografik src="infografik.webp" alt="AI Development Tools: CLI or Editor?" >}}

## Audio Summaries

### Brief Summary
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-008/audio-brief.m4a" >}}

### Deep Dive
{{< audio src="https://media.dinozorlarlakafautuleme.com/bolum-008/audio-deepdive.m4a" >}}

---

📓 [Explore the NotebookLM workspace for this episode](https://notebooklm.google.com/notebook/9bb8cd8a-6b64-4a22-a835-92f60209b8ec)
