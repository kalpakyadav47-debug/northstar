# Northstar — Hiring Platform

A modern, end-to-end corporate hiring platform built with Next.js 14, TypeScript, and Tailwind CSS. Track candidates from application to billable employee — including campus drives, interview rounds, offers, the 100-day bootcamp, and full workforce management.

> **For absolute beginners** — this README walks you through everything: running it on your laptop, then publishing it to the internet via Vercel. No prior experience needed.

---

## What's inside

- **Public job board** — Browse openings, filter by department, view full job details, apply with a multi-step form
- **Candidate database** — Centralized record of every applicant with name, college, contact info, source, skills, and full pipeline history
- **End-to-end pipeline** — 11 stages: Applied → Screening → GD → Assessment → L1 → L2 → L3 → L4 → HR → Offer → Joined
- **Interview rounds** — Capture round type (GD / assessment / technical / HR / managerial), date, panel, mode, outcome, feedback, and rating
- **Interview scheduling** — Week-strip calendar with upcoming and completed views
- **AI agent** — Surfaces reminders, follow-ups, alerts, and bottleneck insights with one-click acknowledge
- **Dashboard** — KPIs, hiring funnel with auto-detected bottlenecks, agent preview, upcoming interviews
- **Analytics** — 14-day application trend, funnel chart, source mix, round outcomes, college breakdown
- **100-day bootcamp** — Per-candidate progress bar, module checklist with scores, mentor notes, employment status (billable / non-billable / bench / bootcamp)
- **Role-based UX** — Switch between Admin, Recruiter, Interviewer, and Candidate roles from the navbar
- **Light & dark mode** — Toggle in the navbar, preference is saved
- **No database needed** — All data persists in the browser (localStorage), so it just works on Vercel with zero configuration

---

## Prerequisites

You need **Node.js 18 or newer** installed on your computer. Check by opening a terminal and running:

```bash
node --version
```

If it says `v18.x.x` or higher, you're good. If not, download it from [nodejs.org](https://nodejs.org) (pick the **LTS** version) and install it.

You'll also need:
- A **GitHub** account (you have one ✓)
- A **Vercel** account (you have one ✓)

---

## Step 1 — Run it on your laptop

Open a terminal in the project folder (the one with `package.json`) and run:

```bash
npm install
```

This downloads all the dependencies (it'll take 1–2 minutes the first time). Then start the dev server:

```bash
npm run dev
```

You'll see something like:

```
▲ Next.js 14.2.15
- Local: http://localhost:3000
```

Open **http://localhost:3000** in your browser. You should see the Northstar landing page with the job board.

### Try this first
1. Click the **role switcher** in the top-right (it says "Candidate") and switch to **Recruiter** — new menu items appear.
2. Open **Dashboard** — you'll see KPIs, the hiring funnel, and a few AI agent items.
3. Open **Candidates** — there are 8 sample candidates pre-loaded across all pipeline stages.
4. Click any candidate to see their full timeline, rounds, and notes.
5. Click the **sun/moon icon** in the navbar to switch between light and dark mode.
6. Open **Bootcamp** to see the 100-day program tracker.
7. Open **Agent** to see all AI notifications and create your own.

To stop the dev server, press `Ctrl + C` in the terminal.

---

## Step 2 — Push it to GitHub

You'll create a new repository on GitHub and upload this code to it.

### The easy way (browser only)

1. Go to **[github.com/new](https://github.com/new)**.
2. Name the repo something like `hiring-platform` (or whatever you want).
3. Leave it **Public** (or Private — both work).
4. **Don't** check "Add a README" — we already have one.
5. Click **Create repository**.
6. On the next page, copy the URL that ends in `.git` (looks like `https://github.com/YOUR-USERNAME/hiring-platform.git`).

Now in your terminal, inside the project folder, run these commands one at a time:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/hiring-platform.git
git push -u origin main
```

> Replace `YOUR-USERNAME` with your actual GitHub username.

If GitHub asks you to log in, do so. If it asks for a password, you'll need a **personal access token** instead — see [docs.github.com/.../personal-access-tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens). Or use the **GitHub Desktop** app, which handles all of this for you.

Refresh your repo page on GitHub — you should see all the files.

---

## Step 3 — Deploy to Vercel

This is the magical part. Vercel takes your GitHub repo and turns it into a live website in about 60 seconds.

1. Go to **[vercel.com/new](https://vercel.com/new)** (log in if needed).
2. Click **Import** next to your `hiring-platform` repo.
   - If you don't see it, click **Adjust GitHub App Permissions** and grant Vercel access to the repo.
3. On the configure screen, **leave every setting as default**:
   - Framework Preset: Next.js (auto-detected ✓)
   - Build Command: default
   - Output Directory: default
   - Environment Variables: none needed
4. Click **Deploy**.

Wait about 60 seconds. When it's done, click **Visit** and your site is live at a URL like `hiring-platform-xyz.vercel.app`. Share that URL with anyone — it works on any device.

### Want a custom domain?
Inside Vercel, go to your project → **Settings** → **Domains** → add the domain you own. Vercel walks you through DNS in plain English.

### Updating the site
Whenever you make a change locally:

```bash
git add .
git commit -m "describe what you changed"
git push
```

Vercel sees the push and redeploys automatically — usually in under a minute.

---

## File structure

```
hiring-platform/
├── app/                       # All pages (Next.js App Router)
│   ├── layout.tsx             # Root layout — fonts, theme provider, navbar
│   ├── page.tsx               # Public landing page + job board
│   ├── jobs/[id]/page.tsx     # Job detail page
│   ├── apply/[id]/page.tsx    # Candidate application form
│   ├── login/page.tsx         # Role selector
│   ├── dashboard/page.tsx     # Recruiter dashboard
│   ├── candidates/            # Candidate list + detail with pipeline
│   ├── interviews/page.tsx    # Interview calendar
│   ├── analytics/page.tsx     # Charts and reports
│   ├── bootcamp/page.tsx      # 100-day bootcamp tracker
│   ├── agent/page.tsx         # AI agent inbox
│   └── globals.css            # CSS variables, light/dark theme tokens
├── components/
│   ├── Navbar.tsx             # Top navigation with role switcher
│   ├── ThemeProvider.tsx      # next-themes wrapper
│   └── ThemeToggle.tsx        # Sun/moon button
├── lib/
│   ├── types.ts               # TypeScript types for the whole app
│   ├── seed-data.ts           # Mock candidates, jobs, bootcamp records
│   ├── store.tsx              # React Context + localStorage persistence
│   └── utils.ts               # Helpers — formatDate, stageColors, etc.
├── tailwind.config.ts
├── next.config.js
└── package.json
```

---

## Customizing

- **Brand name** — search for `Northstar` in `components/Navbar.tsx` and `app/layout.tsx`.
- **Colors** — edit the CSS variables at the top of `app/globals.css`. The accent (burnt orange) is `--accent`. Change it once and it updates everywhere.
- **Sample data** — edit `lib/seed-data.ts` to change the seeded jobs, candidates, bootcamp records, and AI notifications. After editing, click **Reset data** in the role menu (or clear localStorage) to re-seed.
- **Pipeline stages** — edit the `STAGES` array in `lib/seed-data.ts` and the `Stage` type in `lib/types.ts`.

---

## Where the data lives

Everything is stored in your browser's **localStorage** under the key `hiring-platform-state-v1`. This means:
- ✅ Zero setup — no database, no env vars, no auth provider
- ✅ Each visitor sees their own seed data
- ⚠️ Data is per-browser — clearing your browser data resets it
- ⚠️ Not suitable for real production use across multiple users

When you're ready to make this a real multi-user product, swap `lib/store.tsx` for a real backend — Supabase, Firebase, or a Postgres + Prisma setup. The store interface is intentionally small and easy to replace.

---

## Tech stack

- **Next.js 14** (App Router) + **TypeScript**
- **Tailwind CSS** for styling
- **next-themes** for light/dark mode
- **Recharts** for charts
- **Lucide React** for icons
- **Fraunces** + **Inter** + **JetBrains Mono** fonts (loaded from Google Fonts)

---

## Troubleshooting

**`npm install` fails** — make sure your Node version is 18+. Run `node --version` to check.

**`git push` asks for a password** — GitHub doesn't accept passwords anymore. Either install **GitHub Desktop**, or create a personal access token and use that as the password.

**Vercel build fails** — check the build logs in the Vercel dashboard. Most often it's a syntax error in a file you edited. Run `npm run build` locally first to catch errors before pushing.

**The site looks unstyled** — try a hard refresh (`Ctrl + Shift + R` or `Cmd + Shift + R`).

**I want to start over with fresh data** — open the browser console (`F12`), run `localStorage.clear()`, and refresh the page. Or use the **Reset data** option in the role menu.

---

Built with care. Have fun.
