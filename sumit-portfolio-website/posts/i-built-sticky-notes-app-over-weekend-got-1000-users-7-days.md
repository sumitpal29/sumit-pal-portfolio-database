---
title: 'A Weekend project Got 1,000+ Users in 7 Days'
slug: i-built-sticky-notes-app-over-weekend-got-1000-users-7-days
createdAt: '2026-06-26T17:02:16.696Z'
updatedAt: '2026-06-26T18:56:12.209Z'
metadata:
  title: 'I Built a Sticky Notes App Over a Weekend — It Got 1,000+ Users in 7 Days'
  description: ''
  draft: true
  publishedAt: '2026-06-26T11:31:00.000Z'
  slug: i-built-sticky-notes-app-over-weekend-got-1000-users-7-days
description: All Sticky Notes - my first pet project that blasted and users are loving it around the world
draft: true
publishedAt: '2026-06-25T19:01:00.000Z'
heroImage: 'https://raw.githubusercontent.com/sumitpal29/sumit-pal-portfolio-database/main/sumit-portfolio-website/assets/sticky-notes-mini-apps.png'
---
I didn't plan to build a product. I just wanted a sticky notes app that actually felt good to use.

That was the weekend idea. Six weeks later, [AllStickyNotes.com](https://allstickynotes.com) had crossed 1,000 unique users in its first week — with zero paid ads, no Product Hunt launch, just genuine word of mouth from people who found it useful.

Here's the honest story of how it happened.

---

## It Started With an Itch

Like most developers, I had a dozen tabs open at any time. To-dos scattered across Notion, random reminders in iPhone notes, Pomodoro apps switching between 3 different tools.

I wanted one thing: **a digital corkboard that lives in the browser tab**. No sign-up. No account. Just open it and start pinning things.

So I built it. A simple sticky notes board. Drag them around. Color-code them. Pin your thoughts. That was it.

![Early version — simple sticky notes board](https://raw.githubusercontent.com/sumitpal29/sumit-pal-portfolio-database/main/sumit-portfolio-website/assets/sticky-notes-with-pomodoro.png)

The first version was genuinely bare. Notes with a header, a text area, and physics-based wind that made them sway slightly (that part was honestly just for fun). You could drag, resize, change colors and fonts, and archive notes you didn't want to delete.

I shared it with a few friends. They liked it. I put it live and mostly forgot about it.

---

## Reddit Changed Everything

A few weeks in, I posted it on Reddit — in communities like r/webdev and r/productivity. The response surprised me.

People weren't just saying "cool project." They were asking for things. Specific things.

> "Can you add a Pomodoro timer? I want one widget instead of switching apps."
> "What about a habit tracker? Something simple, not like a whole app."
> "I'd love a mood journal on here — just a daily emoji check-in."

I read every single comment. And instead of building what *I* thought was cool, I started building what people actually asked for.

That's when things got interesting.

---

## From Sticky Notes to a Mini App Platform

Over the next few weeks, the board evolved into something bigger — a canvas where you can drop different productivity widgets, each living on its own draggable card.

Here's what AllStickyNotes has today:

### The Core — Sticky Notes
The original. Write in Markdown — headings, bold, italic, code blocks, bullet lists. Six color themes, six fonts (including a pixel font and a retro cursive). You can tilt them, resize them, and the wind physics still make them sway. It sounds like a silly detail but people genuinely comment on it.

### Pomodoro Timer
The most-requested feature. Classic 25/5 work-break cycle, with custom durations and six color themes. It runs quietly in the corner of your board while you work.


### Task Checklist
Simple to-do lists, right on the canvas. Click to check things off. A progress bar fills as you complete items. Double-click any item to edit it in place. No friction.

### Habit Trackers (Two Kinds)
There's the **All Habits** tracker — track multiple habits at once, see your last 7 days as circle buttons you tap to fill. Good for a quick daily check-in across several habits.

And the **Monthly Habit** card — one habit, full calendar view for the month. Tap each day. Watch your consistency build. It sounds simple, but users told me this alone made them more consistent.

### Mood Journal
Five emoji moods. Log once per day. A small bar chart shows your emotional week at a glance. A few users told me they use this as a lightweight mental health check — no therapist app vibes, just honest daily tracking.

### Water Tracker
Tap droplets to log glasses or liters. Set your daily goal. The card resets at midnight. Exactly one user told me this made them drink more water than any dedicated hydration app they'd tried. I'll take it.

### Calendar
A clean monthly calendar always showing today. Navigate months, jump to any year, set whether your week starts on Sunday or Monday. Nothing fancy — just genuinely useful to have on the board.

### Analog Clock
A live analog clock with a smooth-sweeping second hand. Theme-matched colors. Optional digital display. Some people run it in a corner of their workspace all day.

### Image Card
Pin any image by URL. Add a caption. Control alignment and padding. Good for pinning mood boards, reference images, or project inspiration right into your workspace.

### Link Preview
Paste any URL and get a rich preview card automatically — title, description, image, favicon. Works like an unfurled link in Slack, but on your corkboard.

### Countdown Timer
Set a custom countdown, watch a circular progress ring drain down. When it hits zero, an Apple-style chime plays. Useful for meetings, cooking timers, short deadlines.

<!-- IMAGE SLOT -->
<!-- [Insert: Board showing multiple mini apps together — pomodoro, habits, clock, water tracker] -->

---

## The Tech Stack (For the Curious)

I chose tools that let me move fast without fighting infrastructure.

**[Astro](https://astro.build)** is the backbone. It builds extremely fast static sites with a concept called "islands" — React components that hydrate on the client only where needed. The result is a site that loads almost instantly, which matters a lot for a productivity tool someone opens every morning.

**React** handles all the interactive components — the board, the mini apps, dragging, state. Each mini app is a React island that manages its own behavior.

**Tailwind v4** for styling. The new `@tailwindcss/vite` plugin made configuration nearly zero. Three themes — Candy (dark charcoal + yellow), Light, and Dark — all applied as CSS classes on the `<html>` element with no flash of unstyled content.

**Framer Motion** for animations that don't feel janky. The wind physics uses **simplex-noise** to generate natural-feeling movement on each note.

**Radix UI** for accessible primitives — popovers, sliders, switches, dialogs. These are the UI building blocks that would otherwise take days to get right.

Everything stores in **localStorage**. No backend. No database. Your notes never leave your browser — which is both a privacy feature and why the app works offline instantly.

For deployment: **Cloudflare Pages + Workers**. The link preview API runs as a Cloudflare Worker — it fetches Open Graph metadata server-side so the browser doesn't hit CORS walls. The whole site deploys globally in under a minute.

---

## SEO Without the Dark Arts

I'm not going to pretend I did anything revolutionary here. But a few things worked:

**Semantic page structure.** Astro generates clean HTML. I made sure every page had a proper `<h1>`, accurate meta descriptions, and Open Graph tags for social sharing. The basics that most SPAs skip.

**A dedicated features page.** Instead of a generic landing page, I wrote out every mini app in plain English — what it does, who it's for, what makes it different. Google can read that. People searching for "pomodoro app no sign up" or "habit tracker browser" started landing there.

**Targeted copy.** Terms like "no account required," "browser-based," "privacy-first" appear naturally throughout the site because they're genuinely true. These happen to match how people search for tools they don't want to commit to.

**Real use cases.** The feature descriptions talk about what you actually do with the tool, not what it technically does. "Log how you feel each day" rather than "mood tracking widget." Small difference, big impact on resonance.

No backlink campaigns. No keyword stuffing. Just clear writing about a real product.

---

## Why Free Matters

People ask me if I plan to add a paid tier. Maybe someday. But I think about what made this reach 1,000 users in 7 days — and it wasn't anything I built. It was people sharing it.

"Hey, you don't need to sign up, just open it" is a sentence that makes sharing effortless. There's no barrier. You send a link, they click it, they're using the thing immediately.

Free also means students, freelancers, people building side projects, people who just want something simple without adding another subscription. Some of the nicest messages I got were from people who said they'd tried expensive tools and ended up here.

A productivity tool that costs nothing and respects your privacy ends up in a different conversation than one you have to pay for. That matters.

---

## What I Learned

A few things stuck with me from building this:

**Listen to the community before building.** The app's best features came from Reddit comments, not from my own wishlist. People tell you what they need if you ask.

**Ship the imperfect version.** The first week's build had rough edges. Wind physics that didn't always look right. Mobile that kind of worked. But having it live meant getting real feedback from real users, not imaginary users in my head.

**Small details earn trust.** The chime on the countdown timer. The smooth second hand on the clock. Notes that sway in wind. None of these are features anyone asked for — but they're the things people screenshot and share.

**No-account apps spread organically.** The biggest growth driver was that there's nothing to install or commit to. Word of mouth works when the barrier is zero.

---

## What's Next

The board keeps growing. A few things I'm working on or thinking about:

- Better mobile experience (the canvas is desktop-first right now)
- Export and import (so your notes can survive a browser clear)
- More mini apps based on community requests

If you want to follow along, or just try it out: **[allstickynotes.com](https://allstickynotes.com)**

And if you have a feature you wish existed — open an issue or drop a comment. That's exactly how the Pomodoro timer ended up here.

---

*I'll share the full technical journey of building this with AI in the next post — the architecture decisions, what worked, what broke spectacularly, and how I moved fast without cutting corners on quality. Stay tuned.*

*— Sumit | [sumitpal.in](https://sumitpal.in)*
I didn't plan to build a product. I just wanted a sticky notes app that actually felt good to use.

That was the weekend idea. Six weeks later, [AllStickyNotes.com](https://allstickynotes.com) had crossed 1,000 unique users in its first week — with zero paid ads, no Product Hunt launch, just genuine word of mouth from people who found it useful.

Here's the honest story of how it happened.

---

## It Started With an Itch

Like most developers, I had a dozen tabs open at any time. To-dos scattered across Notion, random reminders in iPhone notes, Pomodoro apps switching between 3 different tools.

I wanted one thing: **a digital corkboard that lives in the browser tab**. No sign-up. No account. Just open it and start pinning things.

So I built it. A simple sticky notes board. Drag them around. Color-code them. Pin your thoughts. That was it.


The first version was genuinely bare. Notes with a header, a text area, and physics-based wind that made them sway slightly (that part was honestly just for fun). You could drag, resize, change colors and fonts, and archive notes you didn't want to delete.

I shared it with a few friends. They liked it. I put it live and mostly forgot about it.

---

## Reddit Changed Everything

A few weeks in, I posted it on Reddit — in communities like r/webdev and r/productivity. The response surprised me.

People weren't just saying "cool project." They were asking for things. Specific things.

> "Can you add a Pomodoro timer? I want one widget instead of switching apps."
> "What about a habit tracker? Something simple, not like a whole app."
> "I'd love a mood journal on here — just a daily emoji check-in."

I read every single comment. And instead of building what *I* thought was cool, I started building what people actually asked for.

That's when things got interesting.

---

## From Sticky Notes to a Mini App Platform

Over the next few weeks, the board evolved into something bigger — a canvas where you can drop different productivity widgets, each living on its own draggable card.

Here's what AllStickyNotes has today:

### The Core — Sticky Notes
The original. Write in Markdown — headings, bold, italic, code blocks, bullet lists. Six color themes, six fonts (including a pixel font and a retro cursive). You can tilt them, resize them, and the wind physics still make them sway. It sounds like a silly detail but people genuinely comment on it.

### Pomodoro Timer
The most-requested feature. Classic 25/5 work-break cycle, with custom durations and six color themes. It runs quietly in the corner of your board while you work.


### Task Checklist
Simple to-do lists, right on the canvas. Click to check things off. A progress bar fills as you complete items. Double-click any item to edit it in place. No friction.

### Habit Trackers (Two Kinds)
There's the **All Habits** tracker — track multiple habits at once, see your last 7 days as circle buttons you tap to fill. Good for a quick daily check-in across several habits.

And the **Monthly Habit** card — one habit, full calendar view for the month. Tap each day. Watch your consistency build. It sounds simple, but users told me this alone made them more consistent.

### Mood Journal
Five emoji moods. Log once per day. A small bar chart shows your emotional week at a glance. A few users told me they use this as a lightweight mental health check — no therapist app vibes, just honest daily tracking.

### Water Tracker
Tap droplets to log glasses or liters. Set your daily goal. The card resets at midnight. Exactly one user told me this made them drink more water than any dedicated hydration app they'd tried. I'll take it.

### Calendar
A clean monthly calendar always showing today. Navigate months, jump to any year, set whether your week starts on Sunday or Monday. Nothing fancy — just genuinely useful to have on the board.

### Analog Clock
A live analog clock with a smooth-sweeping second hand. Theme-matched colors. Optional digital display. Some people run it in a corner of their workspace all day.

### Image Card
Pin any image by URL. Add a caption. Control alignment and padding. Good for pinning mood boards, reference images, or project inspiration right into your workspace.

### Link Preview
Paste any URL and get a rich preview card automatically — title, description, image, favicon. Works like an unfurled link in Slack, but on your corkboard.

### Countdown Timer
Set a custom countdown, watch a circular progress ring drain down. When it hits zero, an Apple-style chime plays. Useful for meetings, cooking timers, short deadlines.

---

## The Tech Stack (For the Curious)

I chose tools that let me move fast without fighting infrastructure.

**[Astro](https://astro.build)** is the backbone. It builds extremely fast static sites with a concept called "islands" — React components that hydrate on the client only where needed. The result is a site that loads almost instantly, which matters a lot for a productivity tool someone opens every morning.

**React** handles all the interactive components — the board, the mini apps, dragging, state. Each mini app is a React island that manages its own behavior.

**Tailwind v4** for styling. The new `@tailwindcss/vite` plugin made configuration nearly zero. Three themes — Candy (dark charcoal + yellow), Light, and Dark — all applied as CSS classes on the `<html>` element with no flash of unstyled content.

**Framer Motion** for animations that don't feel janky. The wind physics uses **simplex-noise** to generate natural-feeling movement on each note.

**Radix UI** for accessible primitives — popovers, sliders, switches, dialogs. These are the UI building blocks that would otherwise take days to get right.

Everything stores in **localStorage**. No backend. No database. Your notes never leave your browser — which is both a privacy feature and why the app works offline instantly.

For deployment: **Cloudflare Pages + Workers**. The link preview API runs as a Cloudflare Worker — it fetches Open Graph metadata server-side so the browser doesn't hit CORS walls. The whole site deploys globally in under a minute.

---

## SEO Without the Dark Arts

I'm not going to pretend I did anything revolutionary here. But a few things worked:

**Semantic page structure.** Astro generates clean HTML. I made sure every page had a proper `<h1>`, accurate meta descriptions, and Open Graph tags for social sharing. The basics that most SPAs skip.

**A dedicated features page.** Instead of a generic landing page, I wrote out every mini app in plain English — what it does, who it's for, what makes it different. Google can read that. People searching for "pomodoro app no sign up" or "habit tracker browser" started landing there.

**Targeted copy.** Terms like "no account required," "browser-based," "privacy-first" appear naturally throughout the site because they're genuinely true. These happen to match how people search for tools they don't want to commit to.

**Real use cases.** The feature descriptions talk about what you actually do with the tool, not what it technically does. "Log how you feel each day" rather than "mood tracking widget." Small difference, big impact on resonance.

No backlink campaigns. No keyword stuffing. Just clear writing about a real product.

---

## Why Free Matters

People ask me if I plan to add a paid tier. Maybe someday. But I think about what made this reach 1,000 users in 7 days — and it wasn't anything I built. It was people sharing it.

"Hey, you don't need to sign up, just open it" is a sentence that makes sharing effortless. There's no barrier. You send a link, they click it, they're using the thing immediately.

Free also means students, freelancers, people building side projects, people who just want something simple without adding another subscription. Some of the nicest messages I got were from people who said they'd tried expensive tools and ended up here.

A productivity tool that costs nothing and respects your privacy ends up in a different conversation than one you have to pay for. That matters.

---

## What I Learned

![Insert: Pomodoro timer card on the board](https://raw.githubusercontent.com/sumitpal29/sumit-pal-portfolio-database/main/sumit-portfolio-website/assets/all-sticky-notes-review.png)

A few things stuck with me from building this:

**Listen to the community before building.** The app's best features came from Reddit comments, not from my own wishlist. People tell you what they need if you ask.

**Ship the imperfect version.** The first week's build had rough edges. Wind physics that didn't always look right. Mobile that kind of worked. But having it live meant getting real feedback from real users, not imaginary users in my head.

**Small details earn trust.** The chime on the countdown timer. The smooth second hand on the clock. Notes that sway in wind. None of these are features anyone asked for — but they're the things people screenshot and share.

**No-account apps spread organically.** The biggest growth driver was that there's nothing to install or commit to. Word of mouth works when the barrier is zero.

---

## What's Next

The board keeps growing. A few things I'm working on or thinking about:

- Better mobile experience (the canvas is desktop-first right now)
- Export and import (so your notes can survive a browser clear)
- More mini apps based on community requests


If you want to follow along, or just try it out: **[allstickynotes.com](https://allstickynotes.com)**

And if you have a feature you wish existed — open an issue or drop a comment. That's exactly how the Pomodoro timer ended up here.

---

*I'll share the full technical journey of building this with AI in the next post — the architecture decisions, what worked, what broke spectacularly, and how I moved fast without cutting corners on quality. Stay tuned.*

*— Sumit | [sumitpal.in](https://sumitpal.in)*
