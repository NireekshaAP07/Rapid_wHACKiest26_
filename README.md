# Rapid_wHACKiest26# Scout Research Agent

Scout is a research workspace for discovering student opportunities such as hackathons, internships, scholarships, tech events, and open-source programs. Search with a natural-language query, review matching opportunities, save items to collections, compare options, and revisit past research.

## Features

- Overview dashboard with suggested research prompts
- Natural-language opportunity search and ranked results
- Opportunity details, eligibility, deadlines, locations, fees, benefits, and source links
- Save opportunities and organize them into collections
- Compare up to four opportunities
- Research history with search and status filters
- Workspace settings for profile, display, notifications, and research preferences
- Persistent workspace state stored by the local API in `.scout-data.json`

The current app uses a bundled sample opportunity catalog. The research endpoint searches that catalog locally; it does not crawl the web or fetch live listings.

## Tech stack

- React 19 and TypeScript
- Vite 8
- Tailwind CSS v4
- Lucide React icons
- A Vite middleware API for research and workspace persistence

## Requirements

- Node.js version specified by `.mise.toml`
- pnpm

## Getting started

Install dependencies and start the development server:

```bash
pnpm install
pnpm dev
```

Vite serves the app on port `8443` by default. Set `PORT` to use another port.

## Available scripts

```bash
pnpm dev       # Start the Vite development server
pnpm build     # Create a production build in dist/
pnpm preview   # Preview the production build
pnpm format    # Format project files with oxfmt
```

## API routes

The Vite server exposes these routes:

- `GET /api/health` — API health check
- `GET /api/bootstrap` — Load the bundled opportunities and saved workspace state
- `PUT /api/state` — Persist saved items, comparisons, collections, history, and current result IDs
- `POST /api/research` — Search the bundled opportunity catalog and record the query in history

Workspace state is written to `.scout-data.json` in the project directory during development or preview. The file is generated at runtime and is not part of the source data.

## Project layout

```text
src/
  App.tsx       Main application and page flows
  api.ts        Client calls to the local API
  data.ts       Opportunity catalog and sample prompts/history
  index.css     Tailwind import, theme tokens, and global styles
  ui.tsx        Shared UI components
server/
  api.ts        Vite middleware API and local search implementation

```

