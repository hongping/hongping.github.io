---
title: Vibe Coding with Gemini Code Assist
date: 2025-10-04
tags:
  - vibe coding
  - gemini code assist
published: true
---
I’ve been thinking a lot about [vibe coding](https://en.wikipedia.org/wiki/Vibe_coding) and finally decided to give it a proper shot. I’ve toying with it on and off before, but never really finished a project. This past week, though, FOMO kicked in — so I committed to it, carving out just 20 minutes a day to see what would happen.

First question: _what to create?_ I opted for something simple — a game. Pong felt perfect: it’s classic, visual, and achievable within small daily sessions. Plus, coding it in JavaScript meant I could host it for free on GitHub Pages and share it easily.

There’s also another reason for picking JavaScript: it’s one of the most common languages, and I’m pretty confident most LLMs are well-trained with it. That makes the back-and-forth with an AI smoother.

As for the AI, I went with **Gemini Code Assist** in VSCode. The main factor? It’s free, and Google is generous with the quotas:

*   60 requests per minute
    
*   1000 requests per day
    
*   A **1 million token context window** for local code base
    

That’s plenty of room for simple vibe coding experiments.

Next step — getting started! I’m not exactly fluent in JavaScript. I can read and understand it well enough, but starting something _from scratch_ still feels like a mountain to climb. That actually made this a great test case: to see how well an LLM can handle things when I guide it with the right vibe and clear instructions.

Unfortunately, Gemini Code Assist doesn’t keep a full chat history, so I can’t show my exact starting prompts. But they were nothing fancy — just a few simple requests asking the LLM to create a new game called **JSPong**, with some basic gameplay ideas. Things like having a computer AI player, defining how the ball moves, and how the game should progress through levels. One of the prompt I captured below on how requesting LLM to fine tune the computer player reaction time:

<p style="text-align: center"><img src="assets/img/jspong-prompt-1.jpg" alt="prompt Gemini Code Assist"></p>

The game is live here in [https://hongping.github.io/vibecoding-jspong/](https://hongping.github.io/vibecoding-jspong/), and it is playable with keyboard. To note, though I did edit some of the code, but is mostly cosmetic and does not impact the game mechanics.

## First Impressions

Overall, I’m impressed — though not entirely surprised. I’ve played around with this kind of coding flow before, especially using Claude’s artifact feature. Claude lets you share and even execute web-based code directly, which already felt like a glimpse of this “vibe coding” style — I just didn’t know there is a for the flow.

I’ve also tried getting sample code from ChatGPT before, and it usually produces something close to what I have in mind. So I already had a certain amount of trust in LLM-driven code generation.

For this experiment, though, I went all in with **Gemini Code Assist**. I let it take over almost everything — generating code, committing changes, and even pushing updates. My role was more like a creative director, guiding the direction and letting the AI handle the hands-on work.

## Reflections

If you’ve heard of [mob programming](https://en.wikipedia.org/wiki/Team_programming#Mob_programming), vibe coding feels almost identical — except this time, the LLM is the _driver_ and you’re the _navigator_. You guide, it types. I think this kind of workflow is becoming inevitable as AI agents increasingly integrate into the programmer’s daily routine.

I don’t believe AI will replace programmers. What it does is **ease the work**. We still need to understand the generated code, review logic, and make corrections when things go sideways. The fundamental skill set doesn’t disappear — but those who can communicate effectively with AI will have a huge advantage in productivity and speed.

That said, there’s one thing I’ve started to worry about: overreliance. If we lean too much on LLMs, we risk forgetting the craft itself. I jokingly call this **“AI Down Syndrome”** — that moment when your AI assistant stops responding, and you suddenly feel helpless. I actually experienced it firsthand when Gemini Code Assist briefly stopped working, and I caught myself panicking a little.

So while it’s great to embrace these new tools, we also need to stay grounded — to make sure we can still stand on our own when the AI goes silent.

## What's Next...

For my next experiment, I’ll be testing out **context handling** — asking Gemini Code Assist to understand an existing framework and build something on top of it. Enough of my little detour into the web world; it’s time to head back to my core area: **hardware verification**.

* * *

_Disclaimer: This blog post was drafted with the help of AI (ChatGPT) as well_