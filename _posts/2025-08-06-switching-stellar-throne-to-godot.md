---
title: "Why I'm Switching Stellar Throne to Godot — And How I'm Making It Work"
date: 2025-08-06
author: MrPhil
categories: [News, Development]
layout: custom-post
---

# 🎮 Why I'm Switching *Stellar Throne* to Godot — And How I'm Making It Work

*From low-level power to high-level polish — how a week-long experiment with Godot reshaped my AI-assisted workflow on Stellar Throne.*

When I began building *Stellar Throne*, I was deep in the weeds of learning how to make games with AI. I tried several different tech stacks, but landed on Zig and SDL2 — they worked well with Claude, were flexible enough to build with, and offered a low-friction workflow. But as the game matured, the visuals weren't living up to my vision.

After a couple hundred hours, I hit a crossroads:Should I keep building everything myself — or switch to an engine designed for human beings *and* playtests?

I seriously considered my options and decided to experiment with porting to Godot. According to Claude, it would take about a week — a low price to pay to see how Godot's advantages would translate to my workflow. I went for it, and the results were better than expected. The port took 3 days of full-time work and retained at least 70% of the functionality. I suspect I'll regain the final 30% with less than a week's effort of bug hunting and polish.

So, after completing the port, I chose Godot. Here's why — and how I'm keeping Claude in the loop.

---

## 📅 The Porting Timeline: Day by Day

- **Day 1:** Foundation, galaxy rendering, core logic migration
- **Day 2:** Combat, military systems, strategic layer, UI scaffolding
- **Day 3:** Integration, polish, enhancements, initial bug hunting
- **Day 4–7:** Continued bug fixes, feature parity improvements

---

## ⚔️ Zig vs. Godot: The Tradeoffs

| Factor                   | ⚙️ **Zig + SDL2**                 | 🎮 **Godot 4.2.2**                                         |
| ------------------------ | --------------------------------- | ---------------------------------------------------------- |
| **AI-Assisted Coding**   | ✅ Claude loves clean, static Zig  | ⚠️ GDScript and scenes create ambiguity                    |
| **UI & Visual Tools**    | ❌ Manual, slow to iterate         | ✅ Drag-and-drop editor, animations, polish                 |
| **WebGL Export**         | ❌ Complex WASM toolchain          | ✅ One-click HTML5 build (perfect for Itch.io)              |
| **Compile-Time Safety**  | ✅ Statically typed, robust        | ❌ Dynamic typing, runtime surprises                        |
| **Architecture Control** | ✅ Total freedom                   | ⚠️ Some engine constraints                                 |
| **Time to Demo**         | ⏳ Slower                          | 🚀 Much faster                                             |
| **Debug Tools**          | ❌ Print statements                | ✅ Profiler, remote debugger, live scene edits              |
| **Platform Exporting**   | ⚠️ Native only, custom toolchains | ✅ Built-in export to PC, Mac, Linux, Web, Android, and iOS |

---

## 🧠 Why Godot Wins — *For Now*

I didn't leave Zig because it was wrong.I left because **Godot gets me to a polished, playable demo faster.**

It unlocks:

- Rapid UI design and animation
- Seamless WebGL testing on Itch.io
- A better showcase for players and potential supporters
- More time spent on *gameplay*, less on infrastructure

The tradeoff? Losing Claude's flawless understanding of Zig and that beautiful low-friction feedback loop.

But I've found a way to bring Claude back into the fold.

---

## ✍️ Code vs Click: Two Ways to Build

Watching Claude write Zig code felt like magic. Even when bugs happened, Claude could parse logs, reason through issues, and generate solid fixes. I'd nudge it if needed, but most of the time it exceeded my expectations.

UI work in Zig, though? Painful. I had to describe everything instead of just *click and edit*. Godot's UI tools are miles better.

But in Godot, Claude can't run the project or read logs directly — I have to take screenshots, run tests manually, and copy-paste errors. It adds friction.

Still, Claude gets a lot done quickly. I may have to lift more fingers, but the benefits are worth it. I still have creative energy left for writing these blog posts and designing the game — in fact, Claude is working while I write this.

---

## 🤖 What About Claude?

Claude + Zig was magic. In fact, I'm continuing to use Zig for tools.The minimal syntax and static structure meant I could say, *"Add combat resolution to FleetManager"*, and get clean, working code.

In Godot? It's trickier. Claude struggles with:

- GDScript's duck typing
- Deep scene hierarchies
- Implicit node paths
- Editor-generated structure it can't "see"
- Not being able to run the project or parse logs itself

But I've built a bridge — and it works.

---

## 🔧 How I Keep Claude Productive in Godot

### 1. **📜 Write a `CLAUDE.md` Spec**

A blueprint + style guide that teaches Claude how *my* Godot project works. It defines:

- Folder layout
- Naming conventions
- Data resources
- Logic/UI separation rules
- What a "manager" or "panel" actually means

It gives Claude the structure it needs to behave like a junior developer who understands the project.

---

### 2. **🧠 Keep Logic Typed and Pure**

I move core systems out of scenes and into clean, typed scripts:

```
FleetManager.gd
ColonyManager.gd
TurnManager.gd
```

Claude edits these confidently, without tripping on engine internals.

---

### 3. **🧹 Separate Logic from UI**

Claude writes logic. I connect it to the UI — or ask Claude to build UI panels separately.

Example:

- Claude writes `ColonyManager.gd`
- I manually link it to `ColonyPanel.tscn`, or let Claude generate the scene with some scaffolding

---

## ✅ Why This Hybrid Works

- **Godot gives me** polish, portability, and playability
- **Zig gave me** power, precision, and deep AI synergy
- **Claude still helps** — as long as I structure the collaboration well

This hybrid lets me:

- Move faster toward a WebGL demo
- Refactor, test, and extend core systems with AI
- Reach a real audience *without* sacrificing creative control

---

## 💡 What I've Learned from Switching Engines

This decision was tough. I loved the seamless collaboration between Claude and Zig — I got to direct the work while Claude delivered sophisticated systems at speeds I couldn't match. Godot slows that down and forces me to do more by hand.

But I knew it was worth sacrificing that harmony to gain UI tooling, cross-platform exports, debugging, and faster iteration.

I was pleasantly surprised by how good Godot's node system is for building UIs. I had a bad experience the first time I tried Godot at the start of this project. I think what changed was asking Claude which version it knew best — version 4.2.2 — instead of defaulting to the latest.

If anything, this port made me more impressed with Claude. The transition wasn't perfect — I had to intervene at times, especially to stop it from oversimplifying certain systems. But it got the job done incredibly fast. Most of the friction came from Godot's design, not Claude's limitations.

Honestly, I can imagine someone forking Godot to make a version *for* AI-driven development. That would bring back the seamless synergy I had with Zig.

---

## 🤔 What If You Don't Use Claude?

Honestly? I'd hate it. Claude accelerates development in ways that feel superhuman. Sure, a human dev could do the same — but much slower.

Using AI hasn't compromised my vision. If anything, it's helped me move through the compromises *all* projects require, just faster.

---

## 🚀 What's Next for the Godot Build

At this point, Godot is the main version of *Stellar Throne*. My focus now is:

- Enhancing visuals
- Smoothing out gameplay
- Adding strategic depth and balance
- Preparing a demo for real playtests

But right now?

> **Godot is my engine. Claude is my coworker. *Stellar Throne* is my mission.**> Let's build something amazing.

---

**Subscribe** if you want more behind-the-scenes devlogs on Agentic Game Development.