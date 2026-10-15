# GameArena — Gaming Tournament Management System

A responsive React demo for a college minor project, with separate Player, Organizer, and Admin experiences.

## Important demo note

This version is a **working front-end prototype**. UI interactions such as creating tournaments, reviewing registrations, submitting scores, verifying results, and suspending/reactivating users work in browser state. Demo changes reset when the page is refreshed. The Express/PostgreSQL API and SQL schema are included as a starting backend, but the React screens are not yet wired to that API. The role selector is for demonstration only; it is **not secure authentication**.

Do not deploy this demo as a production service until authentication, server-side role authorization, validation, and persistence have been implemented.

## Requirements

- Node.js 18+
- npm
- Optional for API/database: PostgreSQL

## Run the website

```bash
npm install
npm run dev
```

Open the local URL Vite prints, usually `http://localhost:5173`.

## Run the API (optional)

1. Create a PostgreSQL database named `gamearena`.
2. Execute `server/schema.sql` against it.
3. Copy `.env.example` to `.env` and update `DATABASE_URL`.
4. Run:

```bash
npm run server
```

The API runs at `http://localhost:4000`. Check `GET /api/health`.

Available starter endpoints:
- `GET /api/health`
- `GET /api/tournaments`
- `POST /api/tournaments`
- `GET /api/registrations`
- `PATCH /api/registrations/:id`

## Roles

### Player
Browse tournaments, view matches and leaderboard, manage a demo team, view notifications and disputes.

### Organizer
Create tournaments, review team registrations, manage matches, submit/verify results, and view tournament analytics. The organizer dashboard is focused on tournament operations.

### Admin
Manage user accounts, approve organizers, moderate all tournaments, handle reports/disputes, view platform-wide analytics and settings. Admin functions are separate from organizer tournament operations.

## Suggested next implementation steps

1. Add real registration/login with password hashing and secure sessions/JWT.
2. Add server-side role middleware; never trust the browser role selector.
3. Connect tournament and registration pages to the API.
4. Implement database-backed teams and match records.
5. Generate single-elimination brackets only after registrations are approved.
6. Verify match results and advance winners transactionally.
7. Add tests and deploy the API/database.
