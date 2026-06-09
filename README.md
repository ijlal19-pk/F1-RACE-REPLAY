# 🏎️ F1 REPLAY

**F1 REPLAY** is a high-performance Python and React application that brings Formula 1 race telemetry to life. It combines real-world F1 data extraction with an AI-driven dashboard and an interactive 2D arcade-style race replay engine.

---

## ✨ Features

- **📊 Real-Time Telemetry Processing**: Uses the `fastf1` library to automatically download, parse, and cache official Formula 1 race data, lap times, and track statuses.
- **🎮 Arcade Replay Engine**: An immersive, custom-built 2D replay module (`arcade_replay.py`) that visually simulates the race on the track geometry.
- **🧠 AI Strategy Dashboard**: A real-time AI engine that continuously evaluates driver telemetry (tire compound, temperature, degradation, and gap to leader) to formulate dynamic pit stop strategies.
- **⚡ Modern Tech Stack**: A Python backend seamlessly connected to a React frontend (built with Vite) using [Eel](https://github.com/python-eel/Eel) for lightning-fast Desktop UI rendering.

---

## 🏗️ Architecture & Tech Stack

| Component | Technology | Purpose |
|-----------|------------|---------|
| **Backend Core** | Python 3 | Manages data pipelines, logic, and AI loops. |
| **Data Engine** | `fastf1`, `pandas`, `numpy` | Fetches and computes race telemetry and lap data. |
| **Frontend UI** | React, Vite, HTML/CSS | Renders the dashboard and AI strategy overlays. |
| **Integration** | Eel | Bridges Python logic with the JavaScript frontend. |

### 📂 Project Structure
```text
F1 REPLAY/
├── main.py              # Main entry point and Eel server initialization
├── src/
│   ├── f1_data.py       # fastf1 telemetry downloader and processor
│   ├── arcade_replay.py # 2D Race simulation engine
│   ├── track_geometry.py# Track plotting calculations
│   └── backend/
│       └── ai_engine.py # Telemetry evaluation and strategy AI
├── web/                 # React frontend
│   ├── src/             # Frontend source code
│   ├── package.json
│   └── vite.config.js
├── computed_data/       # Cached processed JSON data
└── .fastf1-cache/       # Raw fastf1 API cache
```

---

## 🚀 Getting Started

### Prerequisites
- **Python 3.9+**
- **Node.js 16+**

### 1. Backend Setup (Python)

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/F1-REPLAY.git
   cd F1-REPLAY
   ```

2. **Set up a Virtual Environment (Recommended):**
   ```bash
   python -m venv .venv
   # Windows
   .venv\Scripts\activate
   # macOS/Linux
   source .venv/bin/activate
   ```

3. **Install Python Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

### 2. Frontend Setup (React/Vite)

You need to compile the frontend before running the Eel application.

```bash
cd web
npm install
npm run build
```
*(This generates the `dist` folder which `main.py` uses for the UI.)*

### 3. Running the Application

Return to the root directory and start the main application:

```bash
cd ..
python main.py
```
The application will launch a native desktop window via Eel.

---

## 🏎️ How It Works

1. **Data Loading:** When you launch the app, `f1_data.py` kicks in. It downloads the target race session via the `fastf1` API. If it has been downloaded previously, it loads from `.fastf1-cache` and `computed_data` to save time and bandwidth.
2. **AI Telemetry Loop:** The `ai_engine.py` runs a continuous background thread, simulating live race telemetry (tire temps, gaps, wear) and projecting pit strategies.
3. **Replay Mode:** Hitting "Launch" triggers `arcade_replay.py`, rendering the actual track geometry and plotting driver markers based on precise X/Y telemetry coordinates.

---

## 📜 License

This project is licensed under the MIT License.
