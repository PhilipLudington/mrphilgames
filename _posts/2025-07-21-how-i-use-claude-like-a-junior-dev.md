---
title: "How I Use Claude Like a Junior Dev (and When It Goes Off the Rails)"
date: 2025-07-21
author: MrPhil
categories: [News]
layout: custom-post
---

## How I Use Claude Like a Junior Dev (and When It Goes Off the Rails)

When I started building *Stellar Throne*, it began as an experiment in **Agentic Coding**—using AI not just to generate code snippets, but to act like a coworker with goals. Instead of giving Claude step-by-step instructions, I'd hand it a clear objective and let it figure out how to execute.

I really leaned into this approach. Whenever I hit a snag or wasn't sure what to do next, I asked Claude what it recommended. To my surprise, it could do a lot more than I expected.

It didn't just help me code—it helped me design the game. Claude co-wrote the Game Design Document (GDD), filling in details I had glossed over. If it suggested something I didn't like, I simply asked it to revise that section. The result? Probably the most complete and thoughtful GDD I've ever produced.

Then I asked Claude to generate a development roadmap from that GDD—and again, it delivered. The roadmap was thorough, detailed, and far more structured than anything I would have written alone. From there, implementation became simple: I'd ask what the next task was, and Claude would jump into action. Full systems that would've taken me days—or even weeks—to build were drafted in hours. It felt like I had a small team of engineers working alongside me.

This shift has allowed me to focus less on coding problems and more on design and player experience. And while I still enjoy programming, I've realized that I love shaping mechanics, systems, and game feel even more.

## How My Workflow Actually Works

Most mornings, I sit down, fire up Claude, switch into planning mode, and ask:

> "What's next on the roadmap?"

Claude usually responds with a 5–6 step implementation plan. Before we start, I almost always reply with something like:

> "This is a good plan—but make sure to follow TDD, DOD, JSON, and best practices. Save the plan to PLAN.md and keep it updated as you go."

These terms—TDD (Test-Driven Development), DOD (Data-Oriented Design), JSON (JavaScript Object Notation), and general best practices—are already defined in `CLAUDE.md`, a spec file loaded into Claude's context at startup. But I've found it still needs a little nudging to stick to them. TDD, especially, is the one it tends to skip if I don't remind it.

## Where It Shines (and Struggles)

Claude is great at broad strokes. If I give it a strong plan and clear context, it can happily work for 20–30 minutes and produce high-quality output. But it sometimes stumbles on small, specific details.

For example, Claude once built a notification system. I playtested it, and sure enough, the notifications slid beautifully onto the screen—but they were text-only. No icons. Getting it to add a sprite next to the text took several back-and-forth iterations. Part of the issue was my lack of precise language to describe the problem; part of it was Claude simply misinterpreting my request.

## The Role of ChatGPT

I also use ChatGPT, especially for image generation. Claude can't generate images, and most image tools I tried were frustrating. Game assets require lots of specifics: style cohesion, transparent backgrounds, no lens flares, and more. Many tools just don't offer that level of control.

ChatGPT, however, lets me iterate prompts. I give it an initial idea, then adapt it based on results—usually after 5 or so cycles, I start getting usable assets. I even developed a reusable partial prompt for consistency. ChatGPT's memory is a big plus; it remembers my palette and aesthetic preferences.

I also use ChatGPT for learning. I ask it to explain Zig syntax I see Claude using, or teach me more about agentic workflows. I've even used it to brainstorm new game titles—*Stellar Throne* came out of that process. I asked ChatGPT to find available names not already on Steam or heavily represented on Google, and it delivered.

Eventually, I asked ChatGPT to improve my workflow. It suggested a morning/evening reflection structure. Now I do that daily, and it's been easy to turn those reflections into blog posts.

## Downtime and Parallel Development

Sometimes Claude is so productive that I end up with downtime while it works. To make use of that time, I started spinning up a second instance of Claude to work on parallel features. I even rebuilt my website, [mrphilgames.com](https://mrphilgames.com), from scratch using this method—fast and exactly how I wanted it.

I've also begun working in two branches at once, delegating different features to each Claude instance. Occasionally, merges become too complex, and I simply abandon one branch and try again. With Claude's speed, it's often easier to redo work than debug a messy merge.

## The Engine Evolution

There were some early missteps. At first, I tried using Godot with Claude, but it struggled—Claude just didn't have enough grounding in Godot's quirks. That's when I had an aha moment: I asked Claude what engine worked best *for it*.

It compared Unity, Monogame, Godot, and Unreal, listing pros and cons. Based on Claude's recommendation, I tried Monogame. It's lighter than Unity and doesn't rely on a complex IDE, which Claude even said was a bad fit for agentic coding.

Monogame worked for a while—but it had limitations. For example, the rendering class is sealed, which made mocking it for unit tests impossible. Claude floundered around this constraint, and I realized it needed a more minimal, expressive stack.

So I asked again. Claude suggested **Zig + SDL2**. I didn't know Zig well, but I was familiar with its C-like nature. SDL2 was a no-brainer—it's what Monogame is built on, battle-tested, and cross-platform. Switching meant losing progress, but Claude moves so fast I caught up quickly. It was a good call.

Zig gives Claude the expressive power and minimal constraints it needs to shine. I spend less time debugging its misunderstandings and more time refining game design.

## When Things Go Really Wrong

There has been one big misstep. When I revamped my `CLAUDE.md` file, ChatGPT suggested a rule that turned out to be wrong. I didn't catch the issue until after I had done a lot of refactoring.

It recommended adopting snake\_case formatting. That seemed reasonable at the time, so I refactored a large chunk of the codebase from camelCase to snake\_case. But later, I asked Claude to evaluate `CLAUDE.md` against Zig conventions—and it pointed out that this rule didn't conform!

Oh no.

Now I had to undo all of those changes. My lack of experience with Zig got me. The lesson? Don't confuse "reasonable" with "correct." Always verify assumptions against an authoritative source.

In hindsight, I've started to treat "reasonable" as a red flag—an indicator that I might be missing key information. One way I've learned to counter this is by cross-verifying suggestions: ask Claude to review what ChatGPT says, and vice versa.

## Final Thoughts

Agentic coding isn't magic—but when scoped properly, it *feels* like working with a creative partner. I'm building more systems this way every week, and `CLAUDE.md` is evolving into a living playbook for how my AI coworkers should operate. The more consistent I am, the more effective they become.

And no—I don't always rewrite the code myself. If something looks half-baked or Claude goes down a rabbit hole, I roll back to the last commit and improve the prompt. Nine times out of ten, the improved prompt gets us to a better outcome.

## What Happened This Week?

### Accomplishments

- **CLAUDE.md Audit**: Worked with Claude and ChatGPT in tandem, refining the spec until both rated it a 9.5/10.
- **Star Map Overhaul**: Rebuilt the star map using freshly rendered star and planet sprites.
- **Fleet Systems**: Implemented fleet movement, HUD overlays, and user notifications.
- **SpriteSheetMaker**: Built a new tool to stitch GPT-generated sprites into clean, aligned sprite sheets.
- **Colonization System**: Colonies can now be established and influence nearby territory.
- **Territory Borders**: Adjacent colonies now merge borders, creating more realistic territorial control.
- **Sensor Systems**: Colonies now reveal nearby stars; planets require ship presence to uncover.
- **Planet Distribution**: Tweaked generation to make Terran and Ocean worlds rarer, and Gas Giants more common.
- **Fleet Management**: Added support for splitting, merging, and renaming fleets.
- **Ship Components & Retrofitting**: Began work on modular component systems and retrofitting capabilities.
- **Terraforming System**: Initial hooks for terraforming have been added.
- **Trade System**: First pass implemented — basic structure is in place, but destinations are still missing.
- **Victory System**: Victory conditions now track and display progress via a new UI panel.
- **Game Setup Screen**: Added customizable options before galaxy generation.
- **Battle System**: Implemented an auto-resolver and simple battle visualizer.
- **Bombardment**: Ships can now bombard planets. Basic damage logic is in place, with hooks for future visual effects and colony impact.
- **Ground Combat**: First pass at a turn-based invasion system — includes attacker/defender phases and post-battle resolution.
- **Save/Load System**: Added auto-save, quick save, and a full-featured save/load UI for session persistence.
- **Research System**: Framework implemented for unlocking technologies — including tech categories, scaling costs, and placeholder entries.
- **Energy System**: Ships now use energy to power weapons, introducing tactical and strategic outfitting decisions.
- **Smart Notifications**: A new alert system surfaces pending actions — unassigned research, idle shipyards, and colonies needing orders.
- **Fog of War**: Unexplored space is now obscured with a stylized galaxy overlay.

---

## Lessons Learned

- **Letting Claude Run Wild with Python is Risky**: When refactoring, don't let Claude write and execute broad Python scripts — it tends to over-edit and cause chaos.
- **Throwing Away Code is Fine**: Claude writes code so fast that starting over often costs less than debugging.
- **ChatGPT Image Generation is Creative, Not Precise**: It frequently breaks format rules. Solution? Just discard noncompliant images — they're fast and cheap to regenerate, and I can do it in parallel with Claude's work.
- **Mitchell Filter > SDL2 for Scaling**: The Mitchell filter yields much better downscaled image quality than SDL2's built-in methods.
- **When Stuck, Use ChatGPT as a Prompt Architect**: It's great at reframing or structuring prompts when Claude hits a wall.