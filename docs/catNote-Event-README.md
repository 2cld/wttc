Here is a comprehensive, production-ready README.md file for your project. It maps out your directory structure, documents installation steps, and acts as a quick-reference guide on meet morning.

---
🤸‍♂️ WTTC Event Kernel & Live Scoring System

An offline-first, real-time Progressive Web App (PWA) scoring and event management platform designed specifically for independent Trampoline & Tumbling (T&T) invitational meets. Built for Waterloo Tumbling and Trampoline Center LLC (WTTC).
This system runs completely locally on a single host laptop acting as a server and communicates with judge tablets and spectator screens over a local travel router—no internet connection required.

---
🛠 Tech Stack Overview

  - Backend: Python 3.11, FastAPI (Async WebSockets + REST API), SQLModel (Pydantic + SQLAlchemy)
  - Database: SQLite (Single-file database, persistent local mounts)
  - Frontend: Single Page Application (SPA) built with Vanilla JS, HTML5, and Tailwind CSS
  - PWA Layer: Service Workers + Client-Side localStorage background synchronization queue
  - E2E Testing: Playwright + Cucumber JS (Gherkin BDD syntax)

📂 Project Directory Structure

```text
wttc-scoring-kernel/
├── Dockerfile                  # Production container assembly blueprint
├── docker-compose.yml          # Container volume mapping & port exposures
├── requirements.txt            # Python dependencies (fastapi, sqlmodel, uvicorn)
├── main.py                     # Central FastAPI application server & WebSockets hub
├── models.py                   # SQLModel DB Schema entities definition
├── test_loader.py              # Mock data seed generator script
│
├── routers/                    # Modular API route subdivisions
│   ├── admin_router.py         # Marshalling, athlete activation controls
│   ├── import_router.py        # CSV mass file ingestion parsing rules
│   ├── edit_router.py          # Score overrides, data manipulation matrix
│   ├── backup_router.py        # SQLite manual hot-copy backup engines
│   └── export_router.py        # Award report streaming CSV compiles
│
├── static/                     # Frontend PWA Static Assets (Served by FastAPI)
│   ├── index.html              # Main App Shell
│   ├── manifest.json           # PWA standalone device installation manifest
│   ├── service-worker.js       # Asset fetch caching worker script
│   ├── css/
│   │   └── tailwind.min.css    # High-contrast UI styles compile
│   └── js/
│       └── judge_app.js        # Offline-first sync UI state machine logic
│
└── features/                   # Cucumber BDD E2E Test Suite
    ├── meet_operations.feature # Core lifecycle Gherkin scenarios
    ├── admin_override.feature  # Manual override Gherkin scenarios
    ├── simulated_meet.feature  # Unified multi-user integration simulation
    ├── fixtures/
    │   └── roster_sample.csv   # Mock testing upload payload matrix
    └── steps/
        ├── meet_steps.js       # Playwright browser event assertions
        └── override_steps.js   # Playwright form automation steps
```

Use code with caution.

---
---
🚀 Quick Start (Local Setup)

If you are running the system directly on your local system python environment:

1. Environment Setup

```bash
# Clone and enter the repository folder
cd wttc-scoring-kernel

# Install python application requirements
pip install -r requirements.txt

# Install E2E automation frameworks
npm install @cucumber/cucumber @playwright/test
```

Use code with caution.

2. Run Database Seeding (Optional Testing Step)

```python
# Generates a fresh wttc_meet.db with synthetic athlete and gym profiles
python test_loader.py
```

Use code with caution.

3. Launch App Server Process

```bash
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

Use code with caution.

🐳 Meet Morning Deployment (One-Click Docker)

To run the system without managing language runtimes on meet morning, ensure Docker Desktop is installed, plug in your local network travel router, assign your laptop a static IP (192.168.1.50), and use the automated launch targets:

  - • Windows Launch: Double-click launch_meet.bat on your desktop.
  - • Mac/Linux Launch: Execute ./launch_meet.sh inside your shell path.

The script runs docker-compose up -d --build, spinning up the infrastructure and creating a safe folder container mount target (./meet_data) on your computer so your database records are protected against unexpected laptop restarts.

---
📡 Networking & Interface Mapping Matrix

Once your server node process is running locally on your static network interface (192.168.1.50), judges and spectators can connect their tablets or display sticks to your travel router and open these address pathways:

Interface Target	Router Network Endpoint URL	Purpose
Head Table Admin	http://localhost:8000/admin	Flight marshalling, CSV imports, file generation, and system snapshots.
Judge Panel Pad	http://192.168.1	Installable high-contrast deduction keypad running local offline-caches.
Spectator Leaderboard	http://192.168.1	Public standings board view optimized for projecting onto TVs.

---
🧪 Running Automated E2E Simulation Tests

To execute a complete synthetic simulation of a meet lifecycle (simultaneously launching an admin browser, a judge tablet browser, and a spectator canvas to test data streaming through your system components), execute:

```bash
npx cucumber-js features/simulated_meet.feature
```

Use code with caution.

---
---
🛡 Meet Day Best Practices

1. PWA Standalone Setup: On your judging iPads/tablets, open Safari, type http://192.168.1, tap Share, and click Add to Home Screen. This locks the screen orientation to landscape and runs it like a native application without browser URL header distraction boxes.
2. Snapshot Timing: Take manual snapshots using the System Integrity Tools pane on the Head Table Dashboard immediately after completing your initial CSV roster uploads, and directly after wrapping up complete morning session flights.
3. Offline Tolerance Recovery: If a judge panel tablet displays the [OFFLINE MODE] banner, tell the judge to keep scoring normally. The device continues collecting entries inside local browser memory storage cache and flushes them back into your main SQLite server node automatically the exact moment local travel router connection parameters are re-established.
Your complete technical workspace setup is now detailed and fully documented. If you need any final refinements, let me know:
• Would you like any adjustments to the README command targets or layout structures?
• Or are you ready to save this out and begin building out your project files?
