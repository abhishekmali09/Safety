# SafePathAI — AI-Powered Safety Assistance

SafePathAI is a full-stack demo app that helps users discover safe places, ask safety-related questions, interact with community discussions, and call for help. The project combines mapping, community content, and AI-assisted features to support safety-focused applications.

## Contents
- Project overview and goals
- Quick start: install and run backend + frontend
- Architecture: folders and important files
- APIs & routes: available backend routes
- Environment: required environment variables
- Development: useful commands and tips
- Contributing & License

## Project overview
SafePathAI provides a combined backend and frontend application to support community safety features:
- place discovery and favorites
- community Q&A and discussions
- FAQ management
- SOS alerts and saved emergency contacts
- AI-assisted features (chat/assistant endpoints)

The app is intended as a reference/demo for building safety-focused apps that combine mapping, community content, and AI assistance.

## Quick start
Recommended: use `pnpm` (project includes a `pnpm-lock.yaml`), or substitute `npm` if you prefer.

1. Install dependencies (root, then backend and frontend if you prefer per-package installs):

```
pnpm install
```

2. Start backend (open a terminal):

```
cd backend
pnpm install
pnpm run dev    # or: npm run dev
```

3. Start frontend (open another terminal):

```
cd frontend
pnpm install
pnpm run dev    # typically starts Vite dev server
```

4. Open the frontend URL shown by Vite (usually `http://localhost:5173`) and use the API (backend default port often `3000` or as configured).

If you need to seed sample data, check the backend service at [backend/src/services/seedService.ts](backend/src/services/seedService.ts) and run it according to your environment (ts-node or after building the backend).

## Architecture & important files
- **Backend:** [backend/src](backend/src)
  - Entry: [backend/src/index.ts](backend/src/index.ts)
  - Controllers: [backend/src/controllers](backend/src/controllers)
  - Routes: [backend/src/routes](backend/src/routes)
  - Models: [backend/src/models](backend/src/models)
  - Services: [backend/src/services](backend/src/services)
  - Middleware: [backend/src/middleware](backend/src/middleware)

- **Frontend:** [frontend/src](frontend/src)
  - App entry: [frontend/src/main.tsx](frontend/src/main.tsx)
  - Pages: [frontend/src/pages](frontend/src/pages)
  - Components: [frontend/src/components](frontend/src/components)
  - Contexts & hooks: [frontend/src/context](frontend/src/context) and [frontend/src/hooks](frontend/src/hooks)

## API Routes (high-level)
Routes are defined in the backend `routes` folder. Example endpoints you can expect (check the exact route paths in the files):
- Authentication: [backend/src/routes/authRoutes.ts](backend/src/routes/authRoutes.ts)
- Places: [backend/src/routes/placesRoutes.ts](backend/src/routes/placesRoutes.ts)
- FAQ: [backend/src/routes/faqRoutes.ts](backend/src/routes/faqRoutes.ts)
- Community / Q&A: [backend/src/routes/communityRoutes.ts](backend/src/routes/communityRoutes.ts) and [backend/src/routes/qnaRoutes.ts](backend/src/routes/qnaRoutes.ts)
- SOS & favorites: [backend/src/routes/sosRoutes.ts](backend/src/routes/sosRoutes.ts) and [backend/src/routes/favoriteRoutes.ts](backend/src/routes/favoriteRoutes.ts)
- AI endpoints: [backend/src/routes/aiRoutes.ts](backend/src/routes/aiRoutes.ts)

Inspect the corresponding controller files in [backend/src/controllers](backend/src/controllers) for route behavior and request/response shapes.

## Environment variables
Create a `.env` file for the backend (and frontend where necessary). Common variables used by this project may include:

- `PORT` — backend server port
- `MONGO_URI` or `DATABASE_URL` — DB connection string (if the project uses a DB)
- `JWT_SECRET` — authentication secret used by `backend/src/utils/jwt.ts`
- `OPENAI_API_KEY` — if AI features use OpenAI or similar providers

Keep secrets out of version control. See the backend code to confirm the exact variable names required.

## Development notes & tips
- The backend is TypeScript-based. Use `pnpm run build` in `backend` to compile, or `pnpm run dev` to run with a TypeScript-aware watcher (e.g., `ts-node-dev` or `nodemon` + `ts-node`).
- The frontend is built with Vite + React + TypeScript. `pnpm run dev` in `frontend` runs the dev server.
- To inspect or expand AI features, see [backend/src/services/aiService.ts](backend/src/services/aiService.ts) and [backend/src/controllers/aiController.ts](backend/src/controllers/aiController.ts).
- To seed example place data used by the frontend map, see [backend/src/samplePlaces.ts](backend/src/samplePlaces.ts) and the seeding service.

## Testing
This repository does not include a centralized test runner by default. If you add tests, consider `vitest` or `jest` for the frontend and `mocha`/`jest` for the backend.

## Contributing
- Fork the repo, create a branch, and open a pull request with a clear description and focused changes.
- Run linting and type checks before submitting.

## License
This README does not specify a license. Add a `LICENSE` file to define licensing terms for the project.


