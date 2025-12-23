# Backend — MovieReviewAppMERNStack

This folder contains the Express/MongoDB backend API for the MovieReviewAppMERNStack project.

## Overview
- Tech: Node.js, Express, MongoDB (Mongoose).
- Purpose: provide REST API endpoints for users, movies, actors, and reviews, plus authentication, email verification, and file uploads (Cloudinary).

## Quick Start
1. Open a terminal in the `backend` folder.
2. Install dependencies:

```bash
cd backend
npm install
```

3. Add environment variables (see next section).
4. Run the server (development):

```bash
npm start
```

By default the code in `app.js` starts the server on port `8000`.

## Environment Variables (.env)
Create a `.env` file in `backend/` and set the following variables used throughout the app:

- `MONGO_URI` — MongoDB connection string (or `DB_URI` depending on your config)
- `JWT_SECRET` — JSON Web Token secret
- `PORT` — optional, defaults to `8000` per `app.js`
- `CLOUDINARY_CLOUD_NAME` — Cloudinary cloud name (if using image uploads)
- `CLOUDINARY_API_KEY` — Cloudinary API key
- `CLOUDINARY_API_SECRET` — Cloudinary API secret
- `EMAIL_HOST` / `EMAIL_PORT` / `EMAIL_USER` / `EMAIL_PASS` — SMTP settings used by the mail helper
- `NODE_ENV` — `development` or `production`

Tip: add `backend/.env` to `.gitignore` (already present in repository) to avoid committing secrets.

## Scripts
- `npm start` — runs `nodemon app.js` as defined in `package.json`.

## Main Files & Folders
- `app.js` — server entry point and route mounting.
- `db/` — database connection logic.
- `routes/` — Express route definitions (`user`, `actor`, `movie`, `review`, `admin`).
- `controllers/` — request handlers and business logic.
- `models/` — Mongoose schemas.
- `middlewares/` — authentication, validation, file upload helpers, error handler.
- `utils/` — helper functions (mail, genres, etc.).

## API Notes
- Base path for API routes is `/api` (for example `/api/movie`, `/api/user`).
- Authentication uses JWT tokens; protected routes are handled in `middlewares/auth.js`.

## API Endpoints
Below are the main API endpoints provided by the backend. All paths are mounted under `/api/<resource>` as shown.

- `User` (`/api/user`)
	- `POST /create` — Create a new user (signup).
	- `POST /sign-in` — Sign in (returns JWT).
	- `POST /verify-email` — Verify email with token.
	- `POST /resend-email-verification-token` — Resend verification token.
	- `POST /forget-password` — Request password reset (send token).
	- `POST /verify-pass-reset-token` — Verify password reset token.
	- `POST /reset-password` — Reset password using valid token.
	- `GET /is-auth` — Check current auth status (protected: `isAuth`).

- `Actor` (`/api/actor`)
	- `POST /create` — Create actor (protected: `isAuth`, `isAdmin`, supports image upload `avatar`).
	- `POST /update/:actorId` — Update actor (protected: `isAuth`, `isAdmin`).
	- `DELETE /:actorId` — Remove actor (protected: `isAuth`, `isAdmin`).
	- `GET /search` — Search actors (protected: `isAuth`, `isAdmin`).
	- `GET /latest-uploads` — Get latest actor uploads (public).
	- `GET /actors` — Get all actors (protected: `isAuth`, `isAdmin`).
	- `GET /single/:id` — Get a single actor by id (public).

- `Movie` (`/api/movie`)
	- `POST /upload-trailer` — Upload trailer video (protected: `isAuth`, `isAdmin`, `uploadVideo`).
	- `POST /create` — Create movie (protected: `isAuth`, `isAdmin`, supports `poster` upload).
	- `PATCH /update/:movieId` — Update movie (protected: `isAuth`, `isAdmin`, supports `poster`).
	- `DELETE /:movieId` — Remove movie (protected: `isAuth`, `isAdmin`).
	- `GET /movies` — Get movies (protected: `isAuth`, `isAdmin`).
	- `GET /for-update/:movieId` — Get movie data for update (protected: `isAuth`, `isAdmin`).
	- `GET /search` — Search movies (protected: `isAuth`, `isAdmin`).
	- `GET /latest-uploads` — Get latest public movie uploads.
	- `GET /single/:movieId` — Get single movie details (public).
	- `GET /related/:movieId` — Get related movies (public).
	- `GET /top-rated` — Get top-rated movies (public).
	- `GET /search-public` — Public movie search.

- `Review` (`/api/review`)
	- `POST /add/:movieId` — Add review to a movie (protected: `isAuth`).
	- `PATCH /:reviewId` — Update a review (protected: `isAuth`).
	- `DELETE /:reviewId` — Delete a review (protected: `isAuth`).
	- `GET /get-reviews-by-movie/:movieId` — Get reviews for a movie (public).

- `Admin` (`/api/admin`)
	- `GET /app-info` — Get application info/statistics (protected: `isAuth`, `isAdmin`).
	- `GET /most-rated` — Get most-rated movies (protected: `isAuth`, `isAdmin`).

For exact request/response shapes and additional query parameters, see the corresponding controllers in `controllers/` and route definitions in `routes/`.

## Development Tips
- Use Postman or a similar tool to exercise endpoints while developing.
- When changing environment variables, restart the server.
- If using Cloudinary, ensure the Cloudinary keys are set and `cloud/index.js` is configured.

## Troubleshooting
- If the server fails to connect to MongoDB, verify `MONGO_URI` and that MongoDB is reachable.
- If email features fail, check SMTP credentials and port.

## Next Steps (optional)
- I can add `backend/.env.example` listing required env keys.
- I can run the backend locally and report startup logs.

---
Files referenced in this README:
- `app.js` — [app.js](app.js)
- `routes/` — [routes](routes)
- `db/` — [db/index.js](db/index.js)
