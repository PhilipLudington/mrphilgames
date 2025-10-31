---
title: "Stellar Throne Devlog: The Engine Overhaul - 52× Faster Simulation"
date: 2025-10-31
author: MrPhil
categories: [News]
layout: custom-post
---

# Stellar Throne Devlog
## The Engine Overhaul: 52× Faster Simulation
### Three Months of Development: August - October 2025

Hey everyone — MrPhil here with another deep dive into Stellar Throne.

It's been an incredible three months of development, and I'm excited to share what's been happening behind the scenes.

For anyone new: **Stellar Throne** is a turn-based 4X strategy game set in a post-imperial universe, where you're scavenging the remnants of a fallen civilization while rival factions do the same.

## 🧠 The Big Picture — A Dual-Engine Breakthrough

The headline: **massive performance gains**.

Over the past few months, I've built a new high-performance simulation engine in Zig, running alongside Godot.

Think of it as two engines working together:
- **Godot** runs everything you see — UI, graphics, and interaction
- **Zig** handles the heavy number crunching — all the simulation that happens when you end your turn

**The result?** The new Zig engine runs **over 50× faster** than the old implementation.

When you're managing dozens of empires, hundreds of star systems, and thousands of ships, that means instant turn processing — no more long waits between turns. Even huge late-game galaxies now run buttery smooth.

## 🏗️ Building the Foundation (August → Early October)

This started back in August with an upgrade to Godot 4.4 and some much-needed combat UI improvements.

Then came the heavy lift — **rebuilding 23 gameplay systems in Zig** from the ground up. That includes:
- Resource management and production
- Fleet movement and combat resolution
- Diplomacy, fog of war, and territory control
- Colony growth, terraforming, events, and victory conditions

Each system was rebuilt, tested, and tuned to behave exactly like the original. I wrote **340+ tests** to confirm accuracy across all mechanics.

Every part of the 4X core — exploration, expansion, exploitation, extermination — now runs on the new Zig foundation.

## ⚙️ The Configuration Revolution (Mid-October)

Next came a big change under the hood that will pay off long-term: **converting all game data from JSON → TOML**.

This might sound minor, but it's a huge upgrade. It means every gameplay number — from building stats to quest chains — now lives in clean, human-readable files.

### Why it matters:
- Balancing is faster and less error-prone
- Modding will be easier down the line
- There's now a single, unified "source of truth" for the entire game's data

This new structure makes the game more flexible, moddable, and maintainable — key steps for long-term development.

## 🧩 The Simulation Engine (Late October)

Finally, I implemented the full turn simulation system — **all 21 phases** that occur when you click End Turn.

That includes:
- Economic production and resource extraction
- Population growth and infrastructure maintenance
- Fleet movement, combat resolution, and research progress
- Random events, quest progression, diplomacy changes, and victory checks

To verify everything works exactly as it should, I built a parity testing framework that runs identical turns in both Godot and Zig — comparing every detail down to individual resources, fleets, and populations.

The results blew me away: **the Zig engine runs 52.7× faster**.

Processing 100 turns in a large galaxy dropped from **685 ms to just 13 ms**.

## 🔎 Current Status

Right now, Stellar Throne is fully playable and stable in Godot.

The Zig simulation engine sits alongside it, ready to take over once parity is perfect.

I can toggle between them instantly, which has made testing incredibly efficient.

This week I've been squashing the final parity differences — fixing issues with ship upgrades, population calculations, and one last colony growth edge case. Once those are fully aligned, the Zig engine becomes the new default.

## 📊 By the Numbers

Since August 5:
- **476 commits**
- **4,900 lines** of Zig simulation code
- **2,000 lines** of config loaders
- **339 automated tests** — all passing

### Every 4X pillar is now live:
- **Explore:** Fog of war, territory control
- **Expand:** Colonization, construction, terraforming
- **Exploit:** Resource extraction, trade, production chains
- **Exterminate:** Tactical combat and bombardment

The economic simulation tracks population, happiness, stability, and infrastructure upkeep.

Diplomacy, treaties, and technology all interact dynamically — wrapped in a post-collapse world where every choice carries weight.

## 🌌 What This Means for Players

All this technical work directly improves gameplay:
- **Massive galaxies run smoothly**
- **Turns process instantly** — even late-game
- **Balance and tuning are easier**
- **Future modding will be simple and supported**

And it all reinforces the game's theme: **Post-Empire survival**.

You're rebuilding amid decay, managing fragile infrastructure, and contending with rivals doing the same.

The simulation now mirrors that vision — scarcity, tension, and hard choices.

## 🔭 Looking Ahead

With the engine overhaul complete, I'm shifting focus to **content and polish**:
- Expanding the tech tree
- Adding new events and quests
- Refining combat balance and AI
- Improving the UI and player feedback

The heavy lifting is done. The foundation is solid. Now it's time to make the galaxy feel alive.

## 🙏 Thanks for Following Along

These months were all about groundwork — but that groundwork sets up everything to come.

Stay tuned — the next updates will be all about content, art, and the player experience.

You can read more at **mrphilgames.com** and follow dev progress on **YouTube** and **Twitter** at **@MrPhilGames**.

---

*Stellar Throne is a turn-based 4X strategy game set in a post-imperial universe. Built with Godot and Zig, it features deep simulation, tactical combat, and strategic empire management. Development updates are posted regularly at mrphilgames.com*
