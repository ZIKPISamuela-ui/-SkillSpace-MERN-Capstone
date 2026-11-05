# SkillSpace Learning Hub — MERN Stack Capstone

**Tagline:** Explore skills and build your future.

SkillSpace is a responsive learning hub built with MongoDB, Express, React and Node.js. Students can create accounts, browse courses and enroll in learning paths. Admin users can publish and delete courses.

## Features
- Student registration and login with hashed passwords.
- JWT-based authentication and protected routes.
- Browse and search courses; filter by category.
- Enroll in courses and view the personal learning list.
- Admin-only course creation and deletion.
- Responsive dark-purple UI.
- MongoDB persistence and sample course seeding.

## Requirements
- Node.js 18 or newer
- MongoDB Atlas account (or local MongoDB)
- npm

## 1. Configure MongoDB
Create a MongoDB database named `skillspace`. In MongoDB Atlas, create a database user and allow your development IP address in Network Access.

Copy `server/.env.example` to `server/.env` and set:
- `MONGO_URI` to your MongoDB connection string.
- `JWT_SECRET` to a long random secret.
- Leave `CLIENT_URL=http://localhost:5173` for local development.

## 2. Install and run
From the project root:

```bash
npm install
npm install --prefix server
npm install --prefix client
npm run seed
npm run dev
```

Open **http://localhost:5173**. The API runs on **http://localhost:5000**.

The seed command inserts four sample courses. Run it once on a fresh database; it replaces the existing course list when run again.

## 3. Create an admin
Register normally in the app. In MongoDB Atlas, open the `users` collection and change that account's `role` field from `student` to `admin`. Log out and log back in. The **Add course** button and delete controls will appear.

## Main API routes
| Method | Endpoint | Access | Purpose |
|---|---|---|---|
| POST | `/api/auth/register` | Public | Create student account |
| POST | `/api/auth/login` | Public | Login |
| GET | `/api/auth/me` | Logged in | Current user |
| GET | `/api/courses` | Public | List courses |
| GET | `/api/courses/:id` | Public | Course details |
| POST | `/api/courses/:id/enroll` | Logged in | Enroll |
| DELETE | `/api/courses/:id/enroll` | Logged in | Unenroll |
| POST | `/api/courses` | Admin | Create course |
| DELETE | `/api/courses/:id` | Admin | Delete course |

## Deployment
### Backend (Render)
1. Push this repository to GitHub.
2. Create a new Web Service on Render and select the repository.
3. Set **Root Directory** to `server`.
4. Build command: `npm install`
5. Start command: `npm start`
6. Add environment variables `MONGO_URI`, `JWT_SECRET`, `CLIENT_URL` and `PORT` (Render supplies PORT; it is okay to omit it).
7. After deployment, copy the backend URL.

### Frontend (Vercel)
1. Import the same GitHub repository into Vercel.
2. Set **Root Directory** to `client`.
3. Add environment variable `VITE_API_URL` with the backend URL plus `/api`, e.g. `https://your-api.onrender.com/api`.
4. Deploy the frontend.
5. Update backend `CLIENT_URL` to the deployed Vercel URL and redeploy the backend.

## Suggested project details for the batch sheet
- Project title: **SkillSpace Learning Hub**
- Stack: **MongoDB, Express.js, React.js, Node.js**
- Short description: **A full-stack learning platform where students can explore courses, create accounts, enroll in learning paths and track their selected courses, while administrators manage course content.**

## Team submission checklist
The sheet asks for your project title, all 3 members' registration numbers, GitHub repository link and live deployment link. The title and source project are ready here. Add your real team details, push the code to your own GitHub repository, and deploy it to obtain genuine live links. Do not submit placeholder links.
