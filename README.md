# 🏋️ SmartFit AI – Real-Time AI Fitness Coaching System

**SmartFit AI** is an AI-powered fitness coach that uses computer vision for real-time pose estimation, exercise tracking, rep counting, and form correction — all running live in your browser.

🌐 **Project Website:** [smartfit-ai-real-time.netlify.app](https://smartfit-ai-real-time.netlify.app/)

🔗 **Live App (Streamlit):** [smartfit-ai-real-time.streamlit.app](https://smartfit-ai-real-time.streamlit.app/)

---

## ✨ Features

- 🎯 **Real-Time Pose Detection** — MediaPipe-powered landmark tracking with skeleton overlay
- 🔁 **Rep & Set Counting** — Automatic counting across 5+ exercises using joint-angle analysis
- 📐 **Form Correction** — 95% form assessment accuracy with ~100ms average latency
- 🗣️ **AI Voice Coaching** — Groq LLM-based coaching intelligence with gTTS voice feedback
- 🔐 **User Authentication** — Login wall with personalized session management
- 📊 **Workout History** — SQLite-backed history tracking with aggregated stats per exercise

---

## 🏃 Supported Exercises

| Exercise | Metrics Tracked |
|---|---|
| Squats | Knee angle, back angle, depth status |
| Push-ups | Elbow angle, body alignment, hip position |
| Biceps Curls | Elbow angle, shoulder stability, swing detection |
| Shoulder Press | Elbow angle, arm extension, back arch |
| Lunges | Front knee angle, torso angle, balance status |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend & App | Streamlit |
| Pose Estimation | MediaPipe Pose Landmarker |
| Computer Vision | OpenCV |
| Video Streaming | WebRTC (streamlit-webrtc + Twilio TURN) |
| AI Coaching | Groq API |
| Text-to-Speech | gTTS |
| Database | SQLite |
| Language | Python |

---

## 🚀 Running Locally

**1. Clone the repo**
```bash
git clone https://github.com/priyagupta-bit/SmartFit.git
cd SmartFit/Main\ App
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Set up secrets**

Create a `.streamlit/secrets.toml` file:
```toml
GROQ_API_KEY = "your_groq_api_key"
TWILIO_ACCOUNT_SID = "your_twilio_sid"
TWILIO_AUTH_TOKEN = "your_twilio_auth_token"
```

**4. Run the app**
```bash
streamlit run main.py
```

---

## 📁 Project Structure

```
SmartFit/
├── Main App/
│   ├── main.py                  # App entry point
│   ├── requirements.txt
│   ├── detectors/               # Per-exercise pose detectors
│   │   ├── squat.py
│   │   ├── pushup.py
│   │   ├── biceps_curl.py
│   │   ├── shoulder_press.py
│   │   └── lunges.py
│   ├── services/
│   │   ├── vision/              # WebRTC video processor
│   │   ├── tracking/            # Metrics sync
│   │   ├── coaching/            # LLM + TTS voice pipeline
│   │   ├── auth/                # Login wall
│   │   ├── persistence/         # SQLite repository
│   │   ├── config/              # Workout config
│   │   └── ui/                  # Styles & CSS
│   ├── ml_models/               # MediaPipe .task model file
│   └── static/                  # CSS & fonts
```

---

## ⚙️ Deployment (Streamlit Cloud)

This app uses **Twilio TURN servers** for WebRTC connectivity on Streamlit Cloud. Add the following to your app's Secrets in the Streamlit Cloud dashboard:

```toml
GROQ_API_KEY = "..."
TWILIO_ACCOUNT_SID = "..."
TWILIO_AUTH_TOKEN = "..."
```
