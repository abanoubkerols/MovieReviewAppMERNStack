# MovieReviewApp — Frontend

This is the React frontend for the MovieReviewAppMERNStack project. It was bootstrapped with Create React App and uses Tailwind CSS for styling.

**Quick Start**

1. Install dependencies and start the dev server:

```bash
cd frontend
npm install
npm start
```

Open http://localhost:3000 in your browser. The app hot-reloads when you change source files.

**Environment / API configuration**

The frontend expects the backend API to be available at `http://localhost:8000/api` by default. The API client is defined in `src/api/client.js`.

To change the API base URL without editing code, modify `src/api/client.js` or update it to use an environment variable like `REACT_APP_API_BASE_URL`.

Example using `.env` (optional): create `frontend/.env` with:

```
REACT_APP_API_BASE_URL=http://localhost:8000/api
```

Then update `src/api/client.js` to read `process.env.REACT_APP_API_BASE_URL` (I can do this change if you want).

**Available Scripts**

- `npm start` — start development server
- `npm run build` — build production bundle into `build/`
- `npm test` — run tests
- `npm run eject` — eject CRA config (one-way)

**Folder structure (important files)**

- `src/` — application source code
	- `src/index.js` — app entry
	- `src/App.js` — root app component
	- `src/api/` — API clients (`client.js`, `auth.js`, `movie.js`, etc.)
	- `src/components/` — React UI components (user, admin, forms, models)
	- `src/context/` — React context providers (auth, movies, notifications)
	- `src/utils/` — helper utilities and validators

**Connecting to the backend**

The frontend makes requests to the backend API paths described in `backend/routes/` (for example `/api/movie`, `/api/user`). Ensure the backend server is running (see `backend/README.md`) and that `REACT_APP_API_BASE_URL` (or `src/api/client.js`) is set to the correct URL.

**Build & Deploy**

1. Create a production build:

```bash
cd frontend
npm run build
```

2. Serve the `build/` directory using a static server or integrate with your backend server (for example, serve static files from Express in production).

**Development tips**

- Use the browser devtools and network tab to inspect API requests and responses.
- If CORS errors appear, ensure the backend `cors()` middleware is enabled (it is in `backend/app.js`).
- Restart the dev server after changing environment variables.

**Next steps I can do for you**

- Add `frontend/.env.example` and update `src/api/client.js` to use `REACT_APP_API_BASE_URL`.
- Create a small README section listing key UI routes and components.

***
If you want, I can update `src/api/client.js` now to use `process.env.REACT_APP_API_BASE_URL` and add `.env.example`.
***
