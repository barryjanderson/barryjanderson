# Barry Anderson

Some side projects I've worked on with the help of Cursor, Claude, Codex, Magic Patterns, Google Stitch, and a handful of other AI tools.  Commit counts are as of 10/1/20206.

## Projects

### [Cook with Herb](https://cookwithherb.com)

- **What it is:** I built an AI recipe generator that turns ingredients you already have into three original recipes with photos and shareable pages.
- **Problem it solves:** Recipe sites expect you to know what you want to make, but sometimes I just have a certain ingredient or handful of ingredients that I want to use up. Herb lets me put in what ingredients I have and gives me a few curated recipes to choose from across any number of cuisines and meal types
- **Who it's for:** Intermediate home cooks who want recipe ideas beyond their usual rotation, using ingredients already on hand. 
- **Stack:** Next.js, TypeScript, Tailwind CSS, OpenAI, Clerk, Neon Postgres, PostHog
- **Contributions:** 348 commits

### [My Old World](https://myoldworldcollection.com)

- **What it is:** I built a web app that tracks which Old World Christmas ornaments you own, with a searchable catalog and shareable read-only collection links.
- **Problem it solves:** My wife used to mark off which ornaments we owned on a series of printed sheets as there was no way to track ownership on the Old World Christmas site. We often misplaced these sheets and had to manually update them when we got an ornament from a new collection. I replaced the paper with a persistent, image-led inventory can be updated anywhere.  Our friends and family can now see our collection online so they know which ornaments we already own when giving one as a gift.
- **Who it's for:** My wife, mainly; but anyone who collects Old World Christmas ornaments, and the friends and family members who buy them gifts.
- **Stack:** Next.js, TypeScript, Clerk, Neon Postgres, PostHog, Vercel
- **Contributions:** 38 commits

### [ESPN Drop Bot](https://github.com/barryjanderson/espn-drop-bot)

- **What it is:** I built a small Python service that watches a fantasy baseball league's transactions and posts a Discord alert when a player is dropped.
- **Problem it solves:** Dropped players are claimed within minutes, and refreshing the league page by hand a few times a day means missing most of them. The bot checks for drops every 10 minutes so I can grab them quickly.
- **Who it's for:** Fantasy baseball managers in ESPN leagues who want first claim on newly available players.
- **Stack:** Python, Vercel, Upstash Redis, GitHub Actions, Discord webhooks, ESPN Fantasy API
- **Contributions:** 13 commits
