---
title: "My Copilot Doesn't Write Code"
slug: "copilot-obsidian-executive-function-adhd"
date: 2026-05-15T11:50:00-04:00
draft: false
description: "How I use GitHub Copilot and Obsidian as executive function scaffolding for my AuDHD brain. Not a coding tool. A thinking tool."
tags: ["copilot", "obsidian", "adhd", "accessibility", "productivity", "engineering-management", "neurodivergent"]
categories: ["workflow"]
---

## My Copilot Doesn't Write Code

**Subtitle:** How I use GitHub Copilot and [Obsidian](https://obsidian.md) as executive function scaffolding for my AuDHD brain.

### Resources

- [Copilot CLI](https://github.com/github/copilot-cli)
- [Obsidian](https://obsidian.md)
- Plugins: [Tasks](https://publish.obsidian.md/tasks/), [Dataview](https://blacksmithgu.github.io/obsidian-dataview/), [Templater](https://silentvoid13.github.io/Templater/), Daily Notes (core)

---

### The Problem Nobody Talks About

I'm an Engineering Manager. I have direct reports, a dozen active projects, weekly 1:1s, sprint planning, cross-team coordination, incident response, weekly updates and the kind of context-switching that would make Chrome crash.

I'm also AuDHD (Autistic + ADHD). Which means my brain is simultaneously capable of hyperfocusing on a single thread for six hours and completely forgetting that I had a commitment five minutes from now. Executive function isn't my strong suit. Working memory is a suggestion. And "just write it down" only works if you also remember to look at where you wrote it down.

For years I tried every system. Bullet journals. [Notion](https://notion.so). [Todoist](https://todoist.com). Reminders. Sticky notes. The problem was never capturing information. It was retrieving it at the right moment and deciding what to do next without burning all my energy on the meta-work of managing my own brain.

Then I found a combination that actually works: Obsidian as the structure, and [GitHub Copilot](https://github.com/features/copilot) as the brain that surfaces all the relevant info as I need it, including when I don't know I need it.

What I've built is a hybrid of a few systems: GTD (David Allen's Getting Things Done) for the capture-and-process mindset, Bullet Journaling for the daily log as a real-time record, and PARA (Tiago Forte's Projects/Areas/Resources/Archive from "Building a Second Brain") for the folder structure. None of them worked for me on their own. GTD requires too much processing discipline. Bullet journaling requires consistency I don't have. PARA gives great structure but no active retrieval. The combination, with Copilot as the glue, is what finally stuck.

I wanted to call it LCARS, but Starfleet's lawyers are no joke. So: PCARD. Make it so.

**Prepare → Capture → Automate → Retrieve → Decide**

Templates and structure prep your day before you start. You capture frictionlessly in the moment. Automation (Dataview, Tasks, Templater) keeps things connected without effort. Copilot retrieves what you need at the right time. And then you decide what to do. The system does everything up to the decision. The decision is always yours.

---

### The Setup: Obsidian as Structured External Memory

My Obsidian vault isn't fancy. It's a folder of markdown files with a deliberate structure:

```
Dailies/          → One file per day (schedule, notes, real-time log)
People/           → One file per person I work with
Projects/         → One file per active project
Areas/            → Ongoing responsibilities
Archive/          → Completed/superseded stuff (out of sight, not deleted)
Templates/        → Templater templates for daily notes, people, projects
```

The key insight: information lives where it's born, not where I'll need it.

When I'm in a 1:1 with Sarah and she mentions a blocker, I write it in her People file under today's date header (which Copilot already prepped for me). I don't go hunting for the right project file. I don't context-switch to a task manager. I stay where I am.

The magic happens later, automatically. Dataview queries, Tasks plugin searches, and Copilot all know how to find things by tag, by person reference, by date. So I can write wherever I am, and the system handles retrieval.

---

### Daily Notes: My Real-Time Operating Log

I use Obsidian's built-in Daily Notes plugin (set to create files in `Dailies/` with a Templater template). Every day when I open Obsidian, I get a fresh daily note. But here's what makes it work for ADHD: I manually time-block my schedule at the top, then use it as a real-time log throughout the day.

Here's what a typical daily looks like after I set it up in the morning:

```
09:00 - 10:00 Sprint Planning
10:30 - 11:00 1:1 [[People/Sarah|Sarah]]
11:00 - 11:30 1:1 [[People/Marcus|Marcus]]
13:00 - 13:30 1:1 [[People/Jordan|Jordan]]
14:00 - 14:45 1:1 [[People/Alex|Alex]]
15:00 - 15:30 [[Projects/Platform Migration]] sync

- [ ] Follow up with [[People/Marcus|Marcus]] about the API thing #followup
```

The time blocks serve two purposes:

1. I can see what's coming without switching to a calendar app (context switch = lost focus)
2. They're wikilinked to People/Project files, which means they're clickable portals

After I manually build my timeblocks (I could automate it, but I like the manual routine and awareness of doing it), I run a 'prep my day' skill:

```
Copilot, prep my day
```

And this is where Obsidian's wikilinks become the killer feature for ADHD: the daily note is the scaffold, not the notebook. The wikilinks let Copilot use the entire vault as a graph database, traversing connections between people, projects, dates, and tasks.

---

### "Prep My Day": The Actual Process

Here's what happens when I type those three words. Copilot reads my schedule, identifies each 1:1, and works through them one at a time:

**Step 1: Priority review.** Before anything else, it finds all my `#today` tagged tasks that are still open across the vault. Those stay in place wherever they live (People files, Project files, wherever). It asks me to make a decision on each one: keep it for today, bump it (adds a ➡️ arrow to track that I rolled it over), or drop it. Those accumulated arrows become urgency signals later.

**Step 1.5: Daily task consolidation.** Before the 1:1 prep kicks off, Copilot sweeps every past daily note for open `- [ ]` tasks and moves them into today's note. Not copies. Moves. The source task gets marked `- [>]` (Obsidian's "forwarded" status), and the task appears in today's note with a `[[Dailies/2026-04-17|2026-04-17]]` wikilink back to where it was born. If it already had a 📅 due date, that date gets wikilinked too.

People files and Project files don't get this treatment. Tasks in those files stay where they are; that's what the Dataview queries are for. But daily notes are different. They're temporal. Once a day passes, an open task sitting in last Tuesday's daily is invisible unless you go looking for it. And you won't. The consolidation step makes sure nothing gets lost in the stack of old dailies.

The moved tasks land in a `### 📥 Moved Open Tasks` section, sorted by priority markers and date (oldest first). Duplicates are detected automatically. If I already manually pulled something into today's note, it just marks the source as forwarded and moves on.

**Step 2: 1:1 prep for each person.** For each meeting on my schedule, it kicks off a full prep workflow:

- Reads their Person file for open items, stale follow-ups, patterns
- Fetches their last 7 days of [GitHub](https://github.com) activity via MCP (PRs authored, merged, reviews given)
- Scans recent dailies for mentions of their name
- Cross-references any `#feedback` or `#followup` tagged items referencing them
- Writes structured talking points directly into their Person file under today's date

The output isn't generic "ask how they're doing." It's specific: "Sarah has 3 open PRs on the database refactor, 2 stale follow-ups from April 20 about the API docs, and she merged a security update yesterday. The comment she left on Joe's PR went above and beyond on security considerations; worth calling out."

**Step 3: Pattern detection.** In the background, I also have signals running that look for things I'd normally catch manually if I had infinite time: engagement in new areas I wasn't aware of, changes in PR/review cadence, cross-team collaboration that's new. The kind of stuff that makes the difference between a reactive manager and a proactive one. I don't ferret out the information anymore. I review the impact and decide what to do with it.

**Step 4: Priority focus.** After all the 1:1 prep is done, Copilot writes a "Today's Priority Focus" section into my daily note. This is a live Dataview query that surfaces all open `#today` items across the vault, sorted by how many times they've rolled over. No duplication. Just one live view of what I committed to.

That's the kind of prep I know I should do. It's the kind of prep that makes me a better manager. And without Copilot, I'd skip it 80% of the time because the activation energy of "open 4 files, check GitHub, cross-reference notes" is just too high.

---

### The GitHub Connection: Data-Driven Management

One of the biggest upgrades was connecting Copilot to the [GitHub MCP server](https://github.com/github/github-mcp-server). This lets it pull real data into my notes instead of relying on my (unreliable) memory of what happened this week.

**For 1:1 prep:** Copilot fetches authored PRs, merged PRs, and review activity for the last 7 days. It highlights things worth recognizing ("that detailed review comment on the security PR caught a real auth issue") and surfaces patterns I might miss ("this is the third week of low review count; worth checking in on bandwidth").

**For weekly team updates:** Instead of me trying to remember every detail, Copilot queries every team member's GitHub activity, cross-references the project board, and drafts my status update with specific PR numbers, issue links, and context.

**For on-call reviews:** It fetches shift issue data, parses checkbox completion, reads comments, and gives me a picture of operational health without me manually reading every detail of every issue unless there are anomalies to focus on.

**For bias reduction:** When I'm preparing feedback or performance context, having actual data (PR counts, review quality, cross-team contributions) keeps me honest. It's harder to fall into recency bias or squeaky-wheel bias when the data is right there.

The key thing: none of this is "AI writing my feedback." It's surfacing information so I can make better decisions faster. The judgment is still mine. The data gathering just isn't eating my entire morning anymore.

---

### Wikilinks and the People File: Your 1:1 is Already Prepped

When my 1:1 with Sarah starts, I don't type notes in the daily. I click `[[Sarah|Sarah]]` in the time block and I'm instantly in her file. Today's 1:1 is already prepped under today's date as a header with talking points, open follow-ups, and recognition items:

```
#### [[Dailies/2026-05-04|2026-05-04]] 1:1

**Platform Migration** (Follow-up)
- The PR is stalled waiting on API team review
- Ask: do we need to escalate, or is this normal queue time?

**Security Review PR** (Recognition)
- The comment she left on Joe's PR caught a real auth issue others missed
- Call out: this is exactly the kind of senior-level review work we want to see more of
```

I take all my notes right there. When the meeting ends, I click back to my daily. Zero friction. No copy-pasting. No "I'll organize this later." The notes are already in the right place, linked to the right date, and will surface automatically in future queries.

**How the Person file works:** Each Person file has a DataviewJS query at the top that aggregates all open tasks referencing that person from anywhere in the vault. I never have to manually track "what do I owe Sarah?" or "what's open from our last 3 meetings?" It just shows up. Tasks from three weeks ago in a random daily note? There. A follow-up I captured in a project file? There too. This is what I mean by "information lives where it's born." I don't reorganize it. Queries find it.

Project files work the same way. Each one has a template with links to related people, a Dataview block for open tasks mentioning the project, and sections for status/context/decisions. When I create a new project file in the `Projects/` folder, Templater auto-applies the structure. Zero setup friction.

The daily note itself becomes my catch-all for everything that isn't person or project specific: general to-dos, follow-ups that don't belong to anyone yet, random thoughts, things I need to figure out. It's the inbox of my day.

```
- [ ] Follow up with platform team on the security review process #followup
- [ ] Dig into why the deploy pipeline is flaky #figureout
- that new RFC from the architecture guild looks relevant to our scale discussion
```

This separation is what makes the system sustainable. The daily is low-friction capture. The People/Project files are organized history. And jumping between them is just a click on a wikilink, not a context switch that costs me 15 minutes of refocusing.

---

### Templater: Automated Structure Without Effort

This is where [Templater](https://silentvoid13.github.io/Templater/) earns its keep. I have a single Daily Run-Book template that fires automatically when a new daily note is created. It sets up my day with zero effort.

I also use Templater folder templates so that any new file created in `People/` automatically gets the Person template (with the Dataview open-tasks query, relationship metadata, and section structure), and any new file in `Projects/` gets the Project template (with status fields, people links, and task aggregation). Zero setup friction for new things. If creating a new thing requires decisions, you won't create it. Folder templates remove that barrier.

The daily template includes a default runbook (things I should do every day) plus day-specific blocks that only appear on the right day automatically when I create a new Daily file.

```
// Daily Run-Book Template (simplified)

**Morning**
- [ ] Empty Inbox, make to-dos
- [ ] Empty unread slack messages and make to-dos
- [ ] Review Team check-ins

**After Lunch**
- [ ] Empty Inbox, make to-dos
- [ ] Empty Notification un-reads

**End of Day**
- [ ] Convert daily notes to to-dos
- [ ] Move to-do inbox items to backlog

// Templater logic (pseudocode):
// if today is Monday → inject Weekly Kickoff block
// if today is Friday → inject Weekly Review block
```

The Monday block drops in a full weekly kickoff checklist:

```
## Weekly Kickoff
**Update personal backlog**
- [ ] Review last weeks notes and add to-dos
- [ ] Review 1:1 schedule and add to-dos for open items
- [ ] Freshen up on open Epics and where they stand
- [ ] Review PTO and make to-dos for schedule changes
- [ ] Sort backlog, remove any dead items

**Prepare Weekly Goals**
- [ ] What's due this week or next week?
- [ ] Define 3 weekly goals
- [ ] Block out work time for weekly goals

**Schedule / Review Meetings**
- [ ] Reschedule anything overlapping
- [ ] Scan project meetings + 1:1s
- [ ] Check sprint status + PRs
```

The Friday block gives me a weekly wrap-up:

```
## Weekly Review
**Weekly Summary**
- [ ] Create next week's template
    - [ ] Move forward any open items
- [ ] Send "I didn't forget, it's next week" messages

**Wins / Brags / Feedback**
- [ ] What did I accomplish this week?
- [ ] Update each team member's doc with wins
    - [ ] Add constructive feedback
    - [ ] Note any new patterns

**Update status for each open project**
- [ ] Share anything major
- [ ] Add blockers or follow-ups for next week
```

Why this matters for ADHD: I don't have to remember what day-of-week routines look like. Monday's checklist reminds me to set up the week. Friday's checklist reminds me to close it out. Without this, I'd skip both 90% of the time, not because I don't care, but because "figure out what to do on Monday morning" is itself a task that requires executive function I don't have at 9am.

---

### Tags as Retrieval Hooks (Not Categories)

This is a subtle but critical design choice. My tags aren't folders. They're not organizational buckets. They're retrieval hooks that make things findable later without any effort at capture time.

- `#today` — this is my priority for today. Applied in-place on the task wherever it lives. Never moved to a different file.
- `#followup` — I owe someone something, or something needs checking on.
- `#figureout` — needs thinking time, not just doing. A signal to future-me that this can't be knocked out in 5 minutes.
- `#weeklyupdate` — might belong in my weekly status update. I tag it when it happens and forget about it until Friday.
- `#feedback` — something I want to deliver in a 1:1. Tagged when I notice it, surfaced when I prep.

The magic is that I never have to decide where to put something. I write it wherever I am (daily note, person file, project file) and slap a tag on it. The system finds it later through queries. Copilot finds it later through search. The tag is the only metadata I need to add in the moment.

Why this matters for ADHD: Traditional systems want you to categorize things at capture time. "Is this a task? A note? A project? What priority? What context?" Every one of those decisions costs executive function. My system has exactly one decision at capture time: "does this need a tag?" And even that's optional. The capture is the important part. The tag just helps with retrieval.

---

### The Rollover System: Visual Urgency Without Guilt

This one's my favorite because it works with my ADHD instead of against it.

When I tag something `#today` and don't do it, it doesn't disappear. It doesn't silently age in a backlog where I'll never look at it again. Instead, when I run my daily priorities review the next morning, Copilot asks me what to do with it. If I say "keep it," it adds a ➡️ arrow:

```
- [ ] Follow up on API deprecation ➡️ #today          ← rolled over once
- [ ] Send request to DevEx team ➡️➡️ #today           ← twice
- [ ] Write feedback doc ➡️➡️➡️ #today                  ← three days
```

The arrows accumulate. They're visual. They create a gradient of urgency that I can feel without having to mentally calculate "how long has this been here?"

At 2 arrows, Copilot flags it: "This has been on your list for 2 days. Want to keep it, reschedule, or drop it?"

At 3+ arrows, it gets more direct: "This has been here for 4 days. Either do it today or acknowledge it's not happening this week and remove the tag."

**Why this works for ADHD:**

Traditional todo systems have two failure modes for ADHD brains: invisible (out of sight, out of mind; the task ages silently in a backlog until it's a crisis) or overwhelming (200 items, no priority, instant executive function shutdown). The arrow system creates a third option: graduated urgency that builds naturally without manual triage.

I don't have to remember to prioritize. I don't have to do a weekly review to catch stale items. The arrows do it for me. And because they live on the task itself (not in a separate priority system), I see them in any Dataview query, in any file that references that task, in my daily focus section. They follow the item everywhere.

The Dataview query in my daily note sorts by arrow count, so the most-procrastinated items float to the top. Items with 3+ arrows are basically yelling at me. Items with 0 arrows are fresh. The visual gradient is immediate.

And here's the key psychological piece: it's not punitive. The system doesn't say "you failed." It says "you chose not to do this yesterday, and that's data. What do you want to do with that data today?" That reframe, from guilt to decision-making, is what keeps me actually engaging with the system instead of avoiding it.

There's a related but separate mechanism for daily notes specifically: task forwarding. The `#today` tag and ➡️ arrows are for priority management. They mark what you've committed to and track procrastination. Forwarding (`[>]`) is for consolidation. It sweeps orphaned tasks out of old dailies so they don't silently age in files you'll never open again. A forwarded task might not be tagged `#today` at all. It might be a `#followup` or `#figureout` that I captured two weeks ago and haven't triaged yet. The sweep brings it back to my attention. What I do with it from there is a separate decision.

---

### Weekly Updates: Remembering What You Did

Every week I write a status update for my manager and team. This used to take me 45 minutes of staring at a blank page thinking "what did I even do this week?" ADHD time blindness means Monday might as well have been three months ago.

Now Copilot:

1. Reads last week's snippet for continuity (what was "upcoming" that should have shipped?)
2. Fetches every team member's GitHub activity for the past 7 days
3. Cross-references with the project board
4. Scans for `#weeklyupdate` tags I dropped throughout the week
5. Drafts the whole thing in my established format with specific PR numbers, people credit, and context

I don't have to remember anything. The `#weeklyupdate` tag is the bridge between "something interesting happened" and "it shows up in my weekly update." When something happens during the week and I think "that's an update thing," I just tag it in whatever note I'm in. One word. That's it. I don't have to stop and write the update right then. I don't even have to remember it happened. Copilot finds them all on demand when I need it.

The output has sections for Wins (what shipped, who did it, why it matters), Upcoming Ships (what's in flight and what's the risk), and Top of Mind (strategic concerns, patterns I'm noticing). Each section includes links to PRs and issues so my manager can drill into anything that catches their eye.

---

### The Accountability Mirror

Here's the part that's hardest to explain but most important: Copilot holds me accountable to my own intentions without judgment.

When I say "I'll follow up with Marcus about the deployment thing," Copilot doesn't let that evaporate. It's tagged `#followup` in my daily note (or in Marcus's file where I wrote it). The next time I prep for a Marcus 1:1, it's there under "Open follow-ups." When I run my daily priorities, if I tagged it `#today`, it's there. If I didn't do it, the arrow appears tomorrow.

I'm not disciplined enough to review every open item every day. But I don't have to be. The system reviews them for me and puts the right ones in front of me at the right moment. It's not nagging. It's surfacing. The difference is that nagging says "you should do this." Surfacing says "this exists; what do you want to do with it?"

---

### The Data Flow (How It All Connects)

Here's how a single piece of information travels through the system without me ever manually moving it:

**Tuesday 11:00am** — In my 1:1 with Jordan, they mention the deployment is blocked on a security review. I write in Jordan's file under today's date header:

```
- deployment blocked on security review, needs sign-off from platform team
- [ ] Follow up with platform team on security sign-off for [[Jordan|Jordan]] #followup
```

**Tuesday end of day** — I don't do anything. The task just sits there in Jordan's file.

**Wednesday morning** — I ask Copilot for today's priorities. It finds the `#followup` item, sees Jordan's name, and surfaces it: "You have an open follow-up about Jordan's security sign-off from yesterday." I don't tag it `#today` yet because I have other fires.

**Thursday** — I prep for my manager 1:1. Copilot includes "Jordan's deployment is blocked on platform team security review" in the talking points because it found the mention in Jordan's file.

**Friday** — Copilot is drafting my weekly snippet and includes: "Deployment for [project] is blocked on platform security review; following up next week."

**Next Tuesday** — Copilot preps my 1:1 with Jordan. Under "Open follow-ups" it shows: "From last week: deployment blocked on security review (➡️, 7 days). Did this get unblocked?"

I never manually moved that information anywhere. I wrote it once, in the moment, in the place I was already writing. The system carried it forward through every relevant context.

---

### What This Isn't

This isn't "AI does my job for me." Copilot doesn't make decisions. It doesn't write my feedback. It doesn't decide what's important.

What it does is eliminate the meta-work that exhausts neurodivergent brains before the real work even starts:

- Finding information (where did I write that?)
- Prioritizing (what should I do first?)
- Remembering context (what happened last time we talked?)
- Starting (what's the first step?)

That's not laziness. That's accessibility. The same way a ramp doesn't climb the stairs for you, it just removes the barrier. It also lets me run multiple time-heavy tasks in the background while I focus on the actual work: the conversations, the feedback, the decisions.

---

### The Technical Setup (For Those Who Want to Build This)

**Obsidian Plugins:**

- [Daily Notes](https://help.obsidian.md/Plugins/Daily+notes) (core plugin) — auto-creates daily files in `Dailies/` with a Templater template
- [Templater](https://silentvoid13.github.io/Templater/) — template engine with logic (day-of-week conditionals, folder templates for auto-structure)
- [Dataview](https://blacksmithgu.github.io/obsidian-dataview/)/DataviewJS — dynamic queries across the vault; the backbone of automatic retrieval
- [Tasks](https://publish.obsidian.md/tasks/) — task management with tags, dates, and query blocks that work across the vault

**Copilot Setup:**

- Custom instructions that teach Copilot your vault structure, file conventions, and workflows
- Skills/prompts for each workflow (prep my day, weekly snippet, today's priorities, 1:1 prep)
- Team roster in a JSON file so Copilot knows relationships (direct report, peer, manager)
- Integration with [GitHub MCP server](https://github.com/github/github-mcp-server) for fetching real activity data (PRs, reviews, issues)

**Design Principles:**

1. Capture is instant, retrieval is automatic. Never make yourself organize at capture time.
2. Tags are retrieval hooks, not categories. `#followup` means "surface this when relevant," not "file this under follow-ups."
3. Tasks stay where they're born (mostly). In People and Project files, tasks never move. Queries find them. But daily notes are temporal; an open task in last Tuesday's daily is effectively invisible. So each morning, open tasks from past dailies get forwarded to today's note (marked `[>]` at the source, wikilinked to the original date at the destination). The daily is an inbox, not an archive.
4. Templates remove activation energy. If creating a new thing requires decisions, you won't create it.
5. Graduated urgency beats binary priority. The ➡️ system scales naturally without manual triage.
6. The AI is the active agent, the human is the decision-maker. Copilot proposes; I dispose.

---

### Why This Matters Beyond My Brain

I'm writing this because when people talk about AI accessibility, they usually mean screen readers or alt text. Those matter enormously. But cognitive accessibility is real too.

Executive function disabilities affect millions of people. ADHD alone affects roughly 4-5% of adults. Autism often co-occurs. And the workplace accommodations for these conditions are... basically nothing. "Try a planner." "Set reminders." "Just break it into smaller steps."

Tools like Copilot, when configured intentionally, can serve as genuine cognitive scaffolding. Not a crutch. Not a replacement for effort. Scaffolding. The kind that lets you build something you're fully capable of building, just with fewer invisible barriers in the way.

If you're neurodivergent and you've been writing off AI tools as "just for code," give this a shot. Your brain deserves good tooling too.

---

*The author is an Engineering Manager who's been building systems to work around his brain for 20+ years and this is the best one (for now).*
