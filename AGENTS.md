# AGENTS.md

## Cursor Cloud / Agent Environment Instructions

Polaris is a **native macOS SwiftUI app** (root `Polaris/`, `Polaris.xcodeproj`) plus a small **Node.js/Express companion backend** (`Backend/plaid-server`) that proxies Plaid bank-linking + transaction sync.

### What can and cannot run in cloud / non-macOS environments
- The **macOS app cannot be built or run here** - it requires Xcode/the macOS SDK (`SDKROOT = macosx`) which do not exist on non-macOS/Linux cloud environments. Do not attempt `xcodebuild` on unsupported hosts; the toolchain is absent. Build/test the app on a Mac in Xcode (scheme `Polaris`, targets `PolarisTests`/`PolarisUITests`). `Scripts/swiftdata_doctor.sh` is a macOS-only toolchain diagnostic.
- The **`Backend/plaid-server` Node service is the runnable backend component**.

### Running the Plaid backend
- Standard commands live in `Backend/plaid-server/README.md` and `package.json` scripts (`npm start`, `npm run dev` for `node --watch`). `Scripts/start-plaid-backend.sh` is a convenience wrapper (it does **not** run `npm install`).
- Listens on `127.0.0.1:3847` (override with `PORT`). Health check: `curl http://127.0.0.1:3847/health`.
- **Gotcha:** `server.js` calls `process.exit(1)` on startup unless both `PLAID_CLIENT_ID` and `PLAID_SECRET` are set (see `.env.example`). It does **not** validate that they are real - the server boots with any non-empty values, so `/health` and `/oauth/redirect` work without valid Plaid keys. The Plaid-backed endpoints call the live Plaid API and need valid **Plaid sandbox** credentials (available as env secrets `PLAID_CLIENT_ID` / `PLAID_SECRET`, or via a gitignored `.env`).
- **Gotcha - link token + OAuth redirect URI:** In sandbox, `server.js` always sends `redirect_uri=http://127.0.0.1:3847/oauth/redirect`. If that URI is not registered under [Plaid Dashboard -> Team Settings -> API -> Allowed redirect URIs](https://dashboard.plaid.com/team/api), `POST /api/plaid/link/token/create` fails with `INVALID_FIELD` / "OAuth redirect URI must be configured.". Registering that exact URI unblocks Link-token creation. Exchange + sync still work without it.
- **Headless sandbox hello-world (no Link UI):** Use Plaid's `sandboxPublicTokenCreate` (institution `ins_109508`) -> `POST /api/plaid/item/public_token/exchange` -> `POST /api/plaid/transactions/sync`. Expect an institution name like "First Platypus Bank" and a non-empty transaction list after a short delay.
- State is **in-memory only** (`const items = new Map()` in `server.js`) - linked items and access tokens are lost on restart; there is no database/cache to run. `Scripts/start-plaid-backend.sh` requires a `.env` file to exist; with secrets already in the environment you can just `npm start` from `Backend/plaid-server`.

### Other notes
- No lint/build tooling is configured for the Node backend (no ESLint/tsconfig); it is plain ES-module JavaScript (`"type": "module"`).
- The app's weather widget uses the public Open-Meteo API + CoreLocation and is optional; it does not affect backend setup.
