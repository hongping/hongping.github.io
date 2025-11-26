---
title: From Vibe Coding to Spec Driven Development with Antigravity
date: 2025-11-27
categories:
  - development
tags:
  - vibe coding
  - antigravity
published: true
---
I was curious when Google announced Antigravity, mostly because I wasn’t sure what it was trying to be. After giving it a try, it became clear it’s not a “vibe coding” tool, and it’s not a typical Copilot-style editor either. It feels more like an agent-driven IDE. You don’t sit there typing line after line of code. You operate more like a program manager: laying out requirements, reviewing the agent’s proposed plan, clarifying its questions, and firing back your own to tighten the design before anything gets executed. It’s essentially a spec-driven development workflow baked right into the environment.

![Antigravity welcome page](assets/img/antigravity_greeting.jpg)

When you open Antigravity, it doesn’t ask you to create or open a file. Instead, it asks how you want to interact with the LLM. And once you launch the Agent Manager, the interface feels very familiar, almost like using ChatGPT or Claude, except you’re chatting with an LLM inside a workspace designed for development.

![Antigravity Agent Manager](assets/img/antigravity_agent_manager.jpg)

After experimenting with [vibe coding](https://www.linkedin.com/pulse/vibe-coding-gemini-code-assist-hong-ping-tan-3l5fc/?trackingId=MoeD%2FNdxTli21zFbfDYLUA%3D%3D) and using Antigravity while building the [CSVKernel in PyTBV](https://www.linkedin.com/pulse/proof-concept-pytbv-stream-recorded-transactions-from-hong-ping-tan-4seoc/?trackingId=MoeD%2FNdxTli21zFbfDYLUA%3D%3D), I wanted to see how it handles a project built entirely from scratch. So I picked a simple example to demonstrate the workflow — a classic game: Breakout.

So how to start? We no longer need to code anything, but you need to specify what you want. In the case of Breakout development, I stated out what I want:

> I want to create a classic breakout game that can be hosted in Github pages and playable on mobile web as well. Meaning we have to use Javascript to code the game. Let's start a draft plan such that we can review and add feature accordingly.

It is important to list all the things you want as much as possible, but not like vibe coding where the LLM will start coding, Antigravity works in a way that it forces the LLM to understand the requirements first and populate an implementation plan first.

![AI agent thinking](assets/img/antigravity_first_prompt_thinking.jpg)

It’s important to lay out everything you want up front. But unlike vibe coding where the LLM immediately jumps into writing code, Antigravity forces the model to understand the requirements first and produce an implementation plan. Once that plan is generated, you have to review it and respond to any questions the agent raises. Through this back-and-forth, the agent tightens the design and finalizes the plan before executing anything. Once you’re satisfied with the plan, you let the agent run it. Antigravity will ask for permission before executing commands unless you’ve set it to auto-approve. When the agent finishes, it provides a walkthrough of everything it did. You can review the results, give feedback, and let the agent refine the work further.

![AI agent done and produced walkthrough](assets/img/antigravity_first_prompt_initial_finishing.jpg)

And here’s the [result](https://hongping.github.io/gemini-breakout/). You can try it yourself on mobile web or desktop.

![Breakout by Gemini 3](assets/img/gemini-breakout.gif)

* * *

# Thoughts

This completely changes the unpredictability of vibe coding. It forces you, especially if you don’t have a software background, to think through what you actually need. For experienced developers, it’s fantastic. It feels like having a small team of programmers turning your ideas into working code.

AI is reshaping software development at a pace that’s hard to ignore. We’ve moved from vibe coding to spec-driven development, and there’s clearly more on the way. It’s tough to keep up unless you keep trying the new tools as they appear. At the same time, I do worry that leaning too heavily on them might weaken a developer’s skills—even if it doesn’t make them disappear entirely.