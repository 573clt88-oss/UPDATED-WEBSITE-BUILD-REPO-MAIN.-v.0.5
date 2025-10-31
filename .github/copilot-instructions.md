## Copilot instructions — UPDATED-WEBSITE-BUILD-REPO-MAIN.v.0.5

These instructions give an AI coding agent the minimal, repository-specific knowledge needed to be productive.

Keep edits small and local. If you change behavior across frontend/backend boundaries, update `README.md` and the relevant `.env.example` files.

Key facts (do NOT assume anything not in the repo):
- This is a static React frontend (in `frontend/`) and a FastAPI backend (in `backend/`). They are developed and deployed separately.
- Frontend dev server: run in `frontend/` with `npm install` then `npm start`.
- Backend dev server: run in `backend/` using the venv and `uvicorn server:app --host 0.0.0.0 --port 8001 --reload`.
- Production frontend build lives in `frontend/build/` after `npm run build`.
- The backend is not part of the GitHub Pages deployment (frontend-only). Don’t attempt to deploy the FastAPI server to GitHub Pages.

Where to look for important code patterns:
- React API clients and service patterns: `frontend/src/services/` — prefer editing or adding functions here for API interaction.
- Global state and auth: `frontend/src/context/` — the site uses React Context for auth/cart. Follow the existing context shape when adding values.
- Main entry points: `frontend/src/App.js`, `backend/server.py`.
- Auth and security: `backend/auth.py`, `backend/security.py` — JWT and BCrypt patterns live here; mirror existing token handling and error responses.
- Payments: `backend/stripe_integration.py` — Stripe wrapper logic and example usage; follow the existing abstractions rather than inlining raw Stripe calls in handlers.
- DB and models: `backend/database.py`, `backend/models.py` — MongoDB access patterns use async calls; follow the same async style.
- Seed data & limits: `backend/seed_data.py` shows sample data and the repository enforces a 3-download limit per product (see README). If you change download logic, update any references in docs.

Environment and configuration conventions:
- Backend env file: `backend/.env` (template: `backend/.env.example`). Key names found in README: `MONGO_URL`, `DB_NAME`, `SECRET_KEY`, `CORS_ORIGINS`, `STRIPE_API_KEY`.
- Frontend env file: `frontend/.env` (template in repo). Key used by frontend: `REACT_APP_BACKEND_URL`.
- Never commit secrets. If adding environment-dependent code paths, prefer `.env.example` edits and document in `README.md`.

Build / run / debug quick commands (reproducible from repository contents):
- Dev frontend (Windows PowerShell):
  - cd frontend; npm install; npm start
- Dev backend (Windows PowerShell):
  - cd backend; python -m venv venv; .\venv\Scripts\Activate.ps1; pip install -r requirements.txt; uvicorn server:app --host 0.0.0.0 --port 8001 --reload
- Build frontend for production:
  - cd frontend; npm run build  # output -> frontend/build/

Common patterns & developer expectations (examples):
- API responses: endpoints return JSON with top-level keys like `success`, `data`, `error` — follow existing handlers in `backend/server.py` and routers when constructing responses.
- Async DB usage: use `async`/`await` for DB calls (see `database.py`). Avoid blocking calls in request handlers.
- Stripe flow: use `stripe_integration.py` to create Checkout Sessions and webhooks. Tests or changes should keep card-test flows intact (use Stripe test keys).

When making changes, follow this checklist before committing:
1. Update any affected `.env.example` files with new keys or names.
2. Update `README.md` Quickstart snippets if run commands or ports change.
3. If changing API schemas, update any frontend calls in `frontend/src/services/` and adjust TypeScript/prop shapes if applicable.

Merge guidance (if a previous `.github/copilot-instructions.md` exists):
- Preserve any project-specific notes already present. Merge in new items above only if they reflect discoverable patterns from code or README. Do not remove author-provided warnings about secrets or deployment.

If you need more context or access to runtime logs, ask the repo owner for:
- current `backend/.env` values (never request secrets in public chat; request privately)
- the GitHub Actions workflow files if you must change deployment behavior (not required for frontend edits)

Next step after edits: open a PR with a short summary of the changes, link to any updated docs (`README.md` or QUICKSTART.md), and include a short local verification checklist (commands run + expected result).

If any instruction above is unclear or you want me to expand a specific section (e.g., more examples from `frontend/src/services/` or `backend/stripe_integration.py`), tell me which area to elaborate.
