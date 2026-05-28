---
title: "AI Agent Coding Resistance Is Today's Gatekeeping"
slug: "ai-agent-coding-resistance-is-todays-gatekeeping"
date: 2026-05-28T08:30:00-04:00
draft: false
tags: ["AI", "agents", "vibe-coding", "workflow", "trust", "gatekeeping"]
categories: ["workflow"]
description: "Every argument against AI-generated code is valid. Use it anyway. A 30-year developer on why resistance to agent coding is the same gatekeeping we've always done."
---

Yeah, that title is clickbait. But I'm only like 10% sorry because it's mostly true.

Yes, AI and Vibe coding is messy. Ship it anyway (once you lock it down).

I've been writing code for over 30 years. Lately I've been building with agents, and the code they produce can be insecure, ugly, hard to maintain, inconsistent. The patterns are weird. The variable names are questionable. The architecture sometimes feels like it was designed by committee during an earthquake. I'm not going to argue with any of that. It just doesn't matter as much as you want it to if you address it.

I'd rather be solving 'how do we harden these 10 working prototypes this quarter' than 'how do we ship this one thing this quarter.'

## We've had this fight before

I've watched this play out my entire career. 'I don't need an IDE, I write clean code in vim.' 'Frameworks are a crutch.' 'SCSS is unnecessary abstraction.' 'jQuery is making people forget how the DOM works.' 'Package managers are bloat.' 'I don't need TypeScript, I know my code.'

Same undercurrent every time: *don't devalue me as a developer. I'm a craftsman. I'm an artist. I hand-write elegant code and you're cheapening that.*

I get it. I felt it too, more than once. But looking back? Gatekeeping. Every time. The devs who refused to adopt frameworks didn't ship better software. They shipped less software, slower. The ones who picked up the tools and adapted their workflow kept building things that mattered.

The resistance to agents is the same fear in new clothes. Your job was never to hand-write perfectly magical code. Your job is to make the product better. Increase users, hit the business goal, solve the problem. We orchestrate now. We validate. We make sure what ships is safe, secure, scalable, and quickly iterable.

(I almost went with the calculator analogy here. Engineers refusing calculators because they could do the math by hand. A little on the nose, but the shoe fits.)

This all works the same whether you're starting from scratch on a greenfield app, tinkering on a Saturday, or inside a massive org with millions of lines of code just trying to close tickets.

## The distrust is healthy. The full stop isn't.

The hesitation I hear most from developers: 'I don't trust AI-generated code.' And they stop there. Done. Nope.

That distrust is *good*. Have it. Have it for code from anyone or anything entering your world. A junior dev's PR, a contractor's module, a dependency update, an agent's output. Distrust is where good engineering starts.

But 'I don't trust it' and 'I won't use it' are different sentences. You don't trust random npm packages either, and you've built workflows around validating them. Do the same thing here. Specs that define expected behavior. Standards checks that gate every change. Review loops that catch what slipped through. You know how to do this. You already do it for humans.

Point an agent at a blank canvas and say 'build me an app', yeah, you're going to get a mess. Security holes, spaghetti logic, no coherent domain model. Not a failure of the tools. A failure of approach.

## Change the workflow, not the goal

Don't abandon rigor. Reorder *when* rigor happens.

**Start with business rules, not UI.** Before you touch a component or a template, write down what the system *does*. What are the invariants? What are the edges? Old-school domain-driven thinking. Still matters more than anything else.

**Build the API first.** Domain logic lives here. Get the contracts and validation right. The UI is a skin; treat it like one.

**If you are impatient?** Build a prototype UI first with in-browser memory. Spend an evening fleshing out your ideas, poke and prod, test concepts. But, then throw it all away and update your spec and start over 'the right way'.

**Use BDD and spec-driven development.** Full disclosure: I work at [GitHub](https://github.com), so I'm biased. But [Spec Kit](https://github.com/github/spec-kit) exists for exactly this: define behavior before implementation. Write specs that describe what the system should do, let agents implement against those specs. The specs become guardrails. They're how you stay sane when code is moving faster than you can read it.

The tool is good, but the *idea* matters more than any specific tool. Spec Kit, Cucumber, plain markdown acceptance criteria, whatever works for you. Codify what 'correct' means before you let anything write code.

**Break it up.** Business rules → API → UI. That order. Each layer gets its own specs, its own validation pass. Don't try to 'full stack' everything in one shot.

**Wireframe the UI intentionally.** CSS/App UI reset. Wireframe-based design. No colors. No fancy animations. No design system rabbit holes. Make it *work* before you make it pretty. A surprising number of decisions resolve themselves once you can click through something real.

## Hardening is a phase, not a hope

People see the messy output and think 'this is the final product.' It's not. It's a prototype.

Once you have something working:

- Have agents analyze for security holes. Not a quick scan; a deep, adversarial review.
- Run code reviews that question every assumption. Why is this public? Why isn't this validated? What happens when this is null?
- Challenge the architecture. Right abstraction? Does it scale? What breaks first?

A couple weeks of hardening and cleanup, you're still shipping in a fraction of the time. And you're shipping something you've *seen working*, not something you stared at in a design doc for three months hoping it'd hold together.

## Iteration math

Even if an agent takes ten iterations to get something right, for most things that's *still* faster than writing it by hand. Ten rounds of 'try again, here's what's wrong' at a few minutes each versus hours of manual implementation.

And while one agent iterates on feature A, you have another on feature B, a third on feature C. You're reviewing, directing, and shipping in parallel. Three features moving simultaneously, each one getting your attention when it needs a decision, running on its own the rest of the time.

That changes how you think about building things. When you can see a working version of your idea in hours, you make better calls. Bad assumptions surface early. You don't get attached to architectures that took months to build because nothing took months to build.

The 'move fast and break things' crowd had the right instinct about iteration speed. They just skipped the 'then fix it properly' part. This workflow doesn't skip it. Front-load the building, back-load the rigor.

---

I've been doing this long enough to know what happens next. Some people reading this are already drafting replies about why I'm wrong. Some are nodding along but won't change anything tomorrow. And some are going to try it this week, feel weird about it for a few days, and then realize they shipped more in a sprint than they used to in a quarter.

I was in group two for longer than I'd like to admit. Now I'm solidly in group three, and my only regret is the months I spent arguing with myself about whether it was 'real engineering.'

It is. It just looks different. And that's fine.
