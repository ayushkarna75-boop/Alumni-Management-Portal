# Alumni Management & Engagement Portal

Beginner-friendly full-stack starter project using React + Vite, Node.js + Express, and MySQL.

## Features
- Register and log in (JWT; passwords hashed with bcrypt)
- Role-based access: `alumni`, `student`, `admin`
- Alumni directory with keyword search
- Alumni profile creation/update
- Job and internship listings; signed-in users can post opportunities
- Events listing and admin event creation
- Admin approval of pending alumni profiles and moderation of jobs
- Simple responsive UI

> This is an educational starter. Before production use, add stronger validation, rate limiting, email verification, password reset, audit logging, and deployment secrets management.

## Requirements
- Node.js 18+ (20+ recommended)
- MySQL 8+
- npm

## 1. Create the database
Open MySQL Workbench or the MySQL CLI and run:

```sql
SOURCE database/schema.sql;
```

Or paste the contents of `database/schema.sql` into a SQL editor.

The schema creates database `alumni_portal` and a default admin:
- Email: `admin@alumni.local`
- Password: `password`

Change this password immediately after your first login. The demo seed uses a known bcrypt hash for the password `password`. Change it immediately after your first login.

## 2. Configure and start the backend
```bash
cd backend
cp .env.example .env
```
Edit `.env` with your MySQL username/password and a long random JWT secret.

```bash
npm install
npm run dev
```
API runs at `http://localhost:5000`; health check: `http://localhost:5000/api/health`.

## 3. Start the frontend
In a second terminal:
```bash
cd frontend
cp .env.example .env
npm install
npm run dev
```
Open the Vite URL shown in the terminal (usually `http://localhost:5173`).

## Project structure
```text
alumni_management_portal/
├── database/schema.sql
├── backend/
│   ├── src/server.js
│   ├── src/db.js
│   ├── src/middleware/auth.js
│   ├── src/routes/auth.js
│   ├── src/routes/profiles.js
│   ├── src/routes/jobs.js
│   ├── src/routes/events.js
│   ├── package.json
│   └── .env.example
└── frontend/
    ├── src/main.jsx
    ├── src/App.jsx
    ├── src/api.js
    ├── src/styles.css
    ├── package.json
    └── .env.example
```

## Useful API endpoints
- `POST /api/auth/register`
- `POST /api/auth/login`
- `GET /api/profiles`
- `GET /api/profiles/me` (authenticated)
- `PUT /api/profiles/me` (authenticated)
- `PATCH /api/profiles/:id/approve` (admin)
- `GET /api/jobs`
- `POST /api/jobs` (authenticated)
- `PATCH /api/jobs/:id/approve` (admin)
- `GET /api/events`
- `POST /api/events` (admin)
- `GET /api/tinyfish/jobs?q=frontend developer` (authenticated; requires TinyFish API key)

## Common issues
- **Access denied for MySQL user:** update `DB_USER` and `DB_PASSWORD` in `backend/.env`.
- **Unknown database:** run `database/schema.sql` first.
- **CORS/network error:** make sure backend is running on port 5000 and frontend `.env` has `VITE_API_URL=http://localhost:5000/api`.
- **Invalid token:** log out and sign in again.
- **Admin login fails:** check the seeded admin row in `users`; if you changed seed credentials, use those instead.

## TinyFish integration
The Careers page can search live web results for job/internship listings through TinyFish Search API. Signed-in users can submit a selected result to the portal for admin approval. Set `TINYFISH_API_KEY` in `backend/.env`; get a key at https://agent.tinyfish.ai/api-keys. The key stays on the server. Documentation: https://docs.tinyfish.ai/search-api.

## Suggested next improvements
Add automated tests, profile-photo storage, email notifications, event registration, job applications, pagination, and deployment configuration.
