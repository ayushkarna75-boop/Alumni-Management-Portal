# Alumni Management & Engagement Portal

A full-stack web application for connecting alumni, students, and administrators. Users can create accounts, maintain alumni profiles, explore approved job opportunities, and discover events. Administrators can moderate profiles, jobs, and events.

## Features

- Secure registration and sign-in with hashed passwords and JWT authentication
- Role-based access for **alumni**, **student**, and **admin** users
- Searchable alumni directory and editable alumni profiles
- Job and internship listings with moderation workflow
- Events directory with administrator event creation
- Optional TinyFish-powered live job search
- Responsive React interface backed by a REST API

## Tech Stack

| Layer | Technology |
| --- | --- |
| Frontend | React, Vite, CSS |
| Backend | Node.js, Express |
| Database | MySQL |
| Authentication | JSON Web Tokens, bcrypt |

## Project Structure

```text
alumni-management-portal/
├── backend/                 # Express API
├── frontend/                # React + Vite app
├── database/                # Database schema and demo data
└── START_PORTAL.bat         # Windows convenience launcher
```

## Prerequisites

- Node.js 18 or later (Node.js 20 recommended)
- MySQL 8 or later
- npm

## Getting Started

### 1. Create the database

Open MySQL Workbench or a MySQL command line, then run the contents of [`database/schema.sql`](database/schema.sql). This creates the `alumni_portal` database, required tables, and demo data.

> The demo database includes an administrator account for local testing. Change its password before presenting or deploying the project.

### 2. Configure and run the backend

```bash
cd backend
cp .env.example .env
npm install
npm run dev
```

Update `backend/.env` with your local MySQL credentials and a strong, unique `JWT_SECRET`. The API starts on `http://localhost:5000` by default.

### 3. Configure and run the frontend

Open a second terminal:

```bash
cd frontend
cp .env.example .env
npm install
npm run dev
```

Visit the Vite address printed in the terminal, normally `http://localhost:5173`.

On Windows PowerShell, use `Copy-Item .env.example .env` if `cp` is unavailable.

## Environment Variables

Create the local files from the included templates. Do not commit either `.env` file.

### Backend (`backend/.env`)

| Variable | Purpose |
| --- | --- |
| `PORT` | API port (default: `5000`) |
| `FRONTEND_URL` | Allowed frontend origin |
| `DB_HOST`, `DB_PORT`, `DB_USER`, `DB_PASSWORD`, `DB_NAME` | MySQL connection settings |
| `JWT_SECRET` | Long, random token-signing secret |
| `JWT_EXPIRES_IN` | JWT lifetime, for example `1d` |
| `TINYFISH_API_KEY` | Optional key for live job search |

### Frontend (`frontend/.env`)

| Variable | Purpose |
| --- | --- |
| `VITE_API_URL` | Backend API URL (default: `http://localhost:5000/api`) |

## API Overview

| Area | Example endpoints |
| --- | --- |
| Authentication | `POST /api/auth/register`, `POST /api/auth/login` |
| Profiles | `GET /api/profiles`, `GET /api/profiles/me`, `PUT /api/profiles/me` |
| Jobs | `GET /api/jobs`, `POST /api/jobs`, `PATCH /api/jobs/:id/approve` |
| Events | `GET /api/events`, `POST /api/events` |

## Optional TinyFish Integration

The careers page can query external opportunities through TinyFish Search API. Add `TINYFISH_API_KEY` to `backend/.env` to enable it. The app still runs without this integration.

## GitHub Upload Checklist

1. Create an empty repository on GitHub.
2. Upload the contents of this folder, including `.gitignore`, `README.md`, `backend`, `frontend`, and `database`.
3. Never upload `.env` files, `node_modules`, or private API keys.
4. Add screenshots, a short demo video, and your team members to the repository description for the hackathon submission.

## Future Improvements

- Email verification and password reset
- Event registration and job applications
- Image uploads for profiles
- Pagination and advanced filtering
- Automated tests and deployment configuration

## License

This project is provided for hackathon and educational use. Add your preferred license before public release.
