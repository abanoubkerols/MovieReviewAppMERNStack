# MovieReviewAppMERNStack

**Overview**
- **Project**: MovieReviewAppMERNStack — a MERN stack application for uploading, reviewing, and rating movies and actors.
- **Backend**: Node.js + Express + MongoDB (API and auth). See [backend/app.js](backend/app.js).
- **Frontend**: React (Create React App) with Tailwind for styles. See [frontend/src](frontend/src).

**Features**
- **User auth**: signup, signin, email verification, password reset.
- **Movie management**: upload, edit, search, tags, genres.
- **Actor management**: create and manage actor profiles.
- **Reviews & ratings**: add/edit/delete reviews and ratings.

**Repository Structure**
- **backend/**: Express API, controllers, models, routes.
- **frontend/**: React app, components, context providers, API clients.

**Prerequisites**
- **Node.js**: version 16+ recommended.
- **npm**: comes with Node.js.
- **MongoDB**: a running MongoDB instance or Atlas cluster.
- **Cloudinary** (optional): for image uploads if enabled in the backend.

**Environment Variables**
- Create a `.env` file in the `backend/` folder. Typical variables used by the backend (check the code in [backend/app.js](backend/app.js) and [backend/cloud/index.js](backend/cloud/index.js)):
	- `MONGO_URI` or `DB_URI` : MongoDB connection string
	- `JWT_SECRET` : JWT signing secret
	- `PORT` : server port (the app listens on 8000 by default)
	- Cloudinary / email settings if used: `CLOUDINARY_CLOUD_NAME`, `CLOUDINARY_API_KEY`, `CLOUDINARY_API_SECRET`, `EMAIL_HOST`, `EMAIL_PORT`, `EMAIL_USER`, `EMAIL_PASS`

**Setup**
1. Clone the repository and open the workspace root.
2. Backend install & run:

```bash
cd backend
npm install
npm start
```

The backend uses `nodemon` via the `start` script and listens on port `8000` by default (see [backend/app.js](backend/app.js)).

3. Frontend install & run:

```bash
cd frontend
npm install
npm start
```

The frontend runs via `react-scripts` and opens at `http://localhost:3000` by default.

**Build (production)**
- Frontend build:

```bash
cd frontend
npm run build
```

**API & Dev Notes**
- API base routes begin with `/api/` (for example: `/api/movie`, `/api/user`). See route definitions in [backend/routes](backend/routes).
- Server entry: [backend/app.js](backend/app.js).
- Database connection: [backend/db/index.js](backend/db/index.js).

**Useful Files**
- Backend entry: [backend/app.js](backend/app.js)
- Backend routes: [backend/routes](backend/routes)
- Frontend entry: [frontend/src/index.js](frontend/src/index.js)

