# Installation

Static CMS is a monorepo containing a backend API server and a frontend editor UI. Both run locally during authoring.

## 1. Clone the Repository

```bash
git clone https://github.com/sumitpal29/static-cms.git
cd static-cms
```
2. Install All Dependencies
From the project root, a single install command handles both the frontend and backend:


```bash
npm install
```
This installs root-level dependencies (including concurrently, which is used to run both servers together) and then installs the frontend/ and backend/ packages.

If the workspace install does not automatically install sub-packages, run them manually:


```bash
cd backend && npm install
cd ../frontend && npm install
cd ..
```
3. Start the Development Servers
From the root directory:


```bash
npm run dev
```
This starts both servers in parallel:

Server	URL	Purpose
Backend	`http://localhost:4000`	API + static file serving
Frontend	`http://localhost:5173`	Editor UI
Open `http://localhost:5173` in your browser. You should see the Static CMS home screen.

Verifying the Backend
To confirm the backend is running, visit `http://localhost:4000` directly. A JSON response or a 404 from Express confirms the server is up.

Stopping the Servers
Press `Ctrl + C` in the terminal where npm run dev is running. Both servers stop together.

Notes
The backend serves files from your configured projects folder via the `/projects-static` endpoint. This is used by the editor to show image thumbnails locally.
No environment variables are required for basic usage. The defaults work out of the box.
Port conflicts: if `4000` or `5173` are already in use, the startup will fail with an EADDRINUSE error. Stop whichever process is holding the port and retry.

