---
title: "Agentic Game Development: How AI Became My Thinking Partner"
date: 2025-07-29
author: MrPhil
categories: [News, Development]
layout: custom-post
---

# 🧠 Agentic Game Development

*How AI became my thinking partner while building a strategy game from scratch*

## 🔧 Weekly Progress: From Code Cleanups to Celestial Phenomena

This past week, Stellar Throne saw a wave of architectural improvements, feature expansions, and quality-of-life upgrades across nearly every subsystem.

It began with a major refactor, standardizing the entire codebase to camelCase and implementing a robust event-driven communication system. All core managers — including FleetManager, ColonyManager, VictoryManager, TradeManager, and more — now communicate via the unified GameMessage enum and a central EventManager.

The user interface also leveled up, with contextual action buttons added throughout the HUD:
- 🛠️ Build buttons in star and planet panels
- 🧠 Research and 🤝 Diplomacy buttons in the Empire HUD
- ⚔️ Invasion buttons for enemy worlds
- 🚀 Manage button in the Fleet HUD to open the new Fleet Composition Panel
A key milestone landed with the completion of Phase 6: Galaxy Generation, introducing customizable celestial phenomena — including nebulae, asteroid fields, and spatial anomalies — that now dynamically impact gameplay and exploration.

On the stability front, the dev cycle focused heavily on bug fixes and infrastructure:
- Persistent colony and shipyard notifications now restore correctly
- Construction queues and colony projects save/load reliably
- Memory leaks and double-free issues in PersistentNotificationManager were resolved
- The save directory is now configurable
- A major test suite cleanup squashed symbol collisions, fixed failing tests, and added a test_saves directory to isolate test data
It was a big week — both in code and in cosmos.

Behind all these systems and improvements is something more foundational: a development process shaped around AI as a thinking partner. That's what I want to unpack in this post.

---

## 🧠 Agentic Game Development

I didn't stumble into this workflow. I started here on purpose.

When I began *Stellar Throne*, I wasn't just building a game — I was running an experiment. Could I treat an AI not as a code generator, but as a junior developer? Could I hand it design goals, give it architectural guidance, and let it figure out the rest?

This wasn't a case of discovering agentic workflows after using autocomplete.  
This was **agentic from day one**.

I designed the project to see what an AI could do when treated as a collaborator — not a helper. Not a chatbot. Not a glorified linter.

The answer turned out to be: a lot more than I expected.  
But also: only if I gave it the right setup.

---

## 🧹 What Is Agentic Development?

Agentic development is goal-based collaboration with AI.

Instead of telling the model what to type, you tell it what to achieve. You treat it like a junior (sometimes senior) dev that can reason, plan, and take initiative — within bounds.

If prompt engineering is scripting, agentic development is **directing**.

Where prompt-tweaking tries to get a perfect paragraph, agentic coding builds a feedback loop. You give a goal, the AI proposes a plan, you critique, it adjusts. You're in the creative lead seat — the AI is in the dev chair.

> **You stop telling it what to do — and start telling it what you want.**

---

## 🚀 Why Start from Scratch with AI?

I didn't retrofit AI into an existing codebase. I built *Stellar Throne* for this exact kind of collaboration.

That gave me a huge advantage:

- I could write `CLAUDE.md` up front
- I could establish naming conventions and architectural rules with AI in mind
- I could shape every system — from messaging to input to combat — as something an agent could understand and extend

Because of that, I skipped the frustrating "autocomplete but wrong" phase many devs hit when first using LLMs. I didn't get annoyed when it hallucinated. I expected it.  
Instead, I asked: *How can I give it better grounding?*

That question shaped my entire workflow.

---

## 📇 The Foundation: CLAUDE.md

Most AI devs hit a wall because their tools don't know the codebase.

The trick is: *tell them*.

`CLAUDE.md` is my project's operating manual. It's written *for the AI*, and includes:

- File and folder layout  
- Architectural rules (e.g. who owns turn flow, who handles rendering)  
- Coding conventions (**camelCase**, modular system managers, no globals)  
- Messaging system (`GameMessage`, `UIMessage`)  
- What not to do (e.g. don't invent new managers, don't bypass input queues)

Every time I give Claude a task, it has `CLAUDE.md` to reference. It's like onboarding a new dev — once. Then giving them a desk and a TODO list.

The difference was night and day.

---

## 🛠️ How I Work With AI — Agentically

### 1. Start With a Goal

Example prompt:
> "Design and implement a supply depot mechanic that supports range extension for fleets, integrates with the fuel system, and supports AI evaluation."

I don't ask for a function. I ask for a feature.  
I don't give it code. I give it purpose.

### 2. Get a Drafted Plan, Not a Code Blob

Claude returns:
- System summary  
- Suggested structs and enums  
- Integration points with `GameMap` and `empireLogistics`  
- Proposed UI states  
- Edge cases (e.g. what happens if a depot is destroyed mid-turn)

Sometimes the code is a mess. That's fine — I'm not judging its syntax.  
I'm evaluating the thinking.

### 3. Critique and Redirect

This is where the real work happens:
- "This breaks encapsulation."  
- "Use the `fleetRangeMap` already defined in `empireMovement`."  
- "Good catch on the AI evaluation function — can you suggest weights?"

The AI adjusts. It adapts.

I iterate until the shape feels right — then I polish it manually or kick it to ChatGPT for cleanup.

### 4. Document and Update CLAUDE.md

Once a new pattern emerges, I update the spec. That way, the next time I prompt something similar, the AI is starting from a more accurate mental model.

---

## 🎮 Real Systems Built Agentically

### 🧠 Diplomacy AI and Personalities

Prompt:
> "Design a personality-driven diplomacy system for 4X empires, with attitudes, thresholds, and memory of past actions."

Claude generated:
- Six archetypes: Isolationist, Opportunist, Zealot, etc.  
- A reaction matrix for treaties, threats, and favors  
- Bias and memory scores  
- Suggested `empireOpinion` struct layout  
- Integration hooks for alliance negotiation and betrayal

It wasn't perfect — I had to restructure half the opinion logic — but it got me 80% of the way, and it triggered design ideas I hadn't considered.

### ⚔️ Ground Combat System

Prompt:
> "Add tactical ground combat that occurs after an invasion begins."

AI returned:
- UI sketch: unit grid with fog-of-war  
- Turn structure: initiative-based  
- Unit stats and modifiers  
- Terrain bonuses  
- Stub for `combatResolution.passTurn()`

This saved days of work. The combat loop came together quickly, and I could focus on *designing interesting units*, not plumbing mechanics.

### 📅 Development Roadmap

I gave Claude the GDD and asked for a milestone plan. It returned:
- Suggested sprint phases  
- Dependency ordering  
- Risk flags (e.g. "diplomacy will require UI and AI coordination")  
- Estimated time ranges

It even split tasks between "needs game logic" and "needs UI" — a smart separation that I kept.

---

## ⚠️ Where Agentic Coding Fails (and How I Catch It)

AI isn't magic. Here's what still goes wrong:

- **Hallucinated APIs**: Calls functions that don't exist  
- **Overconfidence**: Suggests changes that break flow  
- **Bad system boundaries**: Mixes responsibilities across modules  
- **Stale assumptions**: Doesn't realize `empireEconomy` was refactored

That's why you still need to:
- Guide  
- Review  
- Test  
- Integrate manually

But for every one mistake, I get five solid suggestions.  
And every pass improves alignment.

---

## 🧑‍🎨 The Real Payoff: Creative Bandwidth

This workflow changes what it means to be a solo developer.

You stop spending 70% of your time on scaffolding and boilerplate.  
You stop getting bogged down in decision paralysis.  
You get to prototype faster, explore alternatives, and focus on what matters.

Your job becomes:
- Give vision  
- Set constraints  
- Evaluate results  
- Refine the game

In other words: **design at scale**, without a full team.

---

## 🔮 Where Agentic Game Development Is Headed

The next wave is coming. Here's what I see on the horizon:

- **Persistent agents**: Memory across sessions, style retention  
- **Multi-agent teams**: UI Claude, AI Claude, Logic Claude  
- **Codebase-embedded models**: AI that knows your full repo and commit history  
- **Simulation-aware agents**: AI that runs a test game loop before proposing code  
- **Integrated editors**: AI that works live inside your game engine with contextual awareness
- **Libraries for AI**: Game development libraries designed for AI to use instead of humans

The future isn't "AI writes your game."  
The future is: **you build like a director** with a crew of agents that speak game design fluently.

---

## 💡 Final Thoughts

Agentic Game Development has redefined how I build.

It's not faster *just* because AI types quickly — it's faster because I spend more time making decisions, and less time typing glue code.

It's not better *just* because AI helps me think — it's better because it frees me to *focus*.

If you're a game developer:
- Don't wait for AGI to start experimenting.  
- Set up a spec file.  
- Prompt with goals, not syntax.  
- Review, correct, and iterate.

It won't always get it right. But it will push you forward.

**This is how I'm building *Stellar Throne*.**  
With agents. With intention. With vision.

And you can too.