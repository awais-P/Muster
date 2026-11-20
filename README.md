# Muster

**Your team, accounted for.**

See who's here, what they're working on, and for how long.

Muster is a lightweight replacement for the shared spreadsheet many software teams use to track work. It combines task pipelines, start/pause time tracking, rooms with roll call, and a live supervisor dashboard in one fast app.

> **Status:** early development. The architecture and stack are decided, and phase 1 is being built. Nothing is ready to install yet.

---

## Why Muster

Many small and mid-sized teams track work in a Google Sheet: one row per task and a column for each stage (Dev → Delivery → Testing → Bug report → Final). It's free and familiar, but:

- statuses are typed by hand and drift ("In progress", "in Progress.", blank)
- nobody knows how long a task actually took
- there's no live view of who is working on what right now
- supervisors have to piece reports together by hand

Jira is too heavy and too expensive per seat for these teams, and all-in-one suites are cluttered. Muster aims to be **that sheet, but live and timed**, and just as quick to set up.

## Features

### Tasks and pipelines
- Only supervisors and seniors assign tasks; members work on them.
- **Configurable pipeline:** stages are defined per team (e.g. Dev → Delivery → QA 1 → QA 2 → Final), not hard-coded columns.
- Any number of reviewers or testers per stage.
- **Bug reports** are raised against a task, assigned to a person, and tracked to resolution.

### Time tracking
- Members tap **Start / Pause / Stop** on the task they're working on.
- Times come from the server clock, so they can't be edited on the device.
- One running timer per person at a time.
- Every start and pause is logged, so you can see *when* someone worked, not just the total.

### Rooms and roll call
- Create rooms or groups for meetings, teams or projects.
- Rooms can be **open, locked or restricted** to certain people.
- **Roll call:** who joined, when they joined, and when they left.
- **Hierarchy:** supervisors see every room; members see only the rooms they belong to.

### Supervisor dashboard
- Live view of who is working on which task, and for how long.
- Per-person workload, task history and attendance.
- Search, filter and rank the team.
- Performance combines **output** (tasks completed, tasks sent back from testing, bug reports raised) with time, not hours alone.

### Meetings *(planned)*
- Video and voice meetings inside rooms, powered by LiveKit.

## Roles

| Role | Can do |
|---|---|
| **Supervisor / Senior** | Create rooms, assign tasks, define pipelines, see every room, open the supervisor dashboard |
| **Member** | Join permitted rooms, work on assigned tasks, start/pause timers, move tasks through their stage |

## Tech stack

| Layer | Choice |
|---|---|
| Frontend | React, Vite, TypeScript, Tailwind CSS, shadcn/ui, TanStack Query |
| Backend | [Hono](https://hono.dev) on Node.js, Zod |
| Database | PostgreSQL with Drizzle ORM |
| Real-time | Socket.io |
| Meetings | LiveKit *(phase 3)* |
| Mobile | Installable PWA first, React Native later |

The whole project is TypeScript, so the frontend and backend share types and validation schemas.

### Planned structure

```
muster/
├── apps/
│   ├── web/        # React + Vite frontend
│   └── api/        # Hono API + Socket.io server
└── packages/
    └── shared/     # Shared types and Zod schemas
```

## Roadmap

- [ ] **Phase 1: Tasks and time.** Organizations, roles, configurable pipelines, task assignment, start/pause timers, bug reports, supervisor dashboard
- [ ] **Phase 2: Presence.** Rooms, access control, roll call with join/leave logs, live online status
- [ ] **Phase 3: Meetings.** Video and voice in rooms via LiveKit
- [ ] **Later:** Google Sheets import, mobile app, reports export

## Getting started

Setup instructions will be added once phase 1 is scaffolded.

## License

[MIT](LICENSE) © 2026 Muhammad Awais
