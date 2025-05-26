# SanctuaryAI

**SanctuaryAI** is an AI-powered Diablo IV build analyzer and performance predictor. Given a character's class, gear, skills, stats, and Paragon board setup, SanctuaryAI estimates how far they can push in PIT levels and offers data-driven suggestions to optimize damage output and survivability.

## 🔥 What It Does

- Predicts maximum PIT level based on your build
- Analyzes synergy between gear, skills, aspects, and Paragon glyphs
- Identifies optimization opportunities for DPS and defensive layers
- Offers strategic tips for maximizing critical damage, cooldown uptime, and resource management

## 🎮 Input Options

- Character class (e.g., Druid, Sorcerer, Barbarian, etc.)
- Equipped gear (stats, aspects, unique items)
- Paragon board setup (glyphs and node bonuses)
- Skill tree (active and passive skills, enhancements)
- Optional: Upload character screen or stat image (v2 feature)

## 🧠 Key Modules
- **Image Parser**: Extracts skill, gear, stat, and aspect data from screenshots
- **Damage Calculator**: Uses weapon damage, skill coefficients, and multipliers (crit, vuln, overpower) to compute realistic damage estimates
- **Recommender Engine**: Suggests gear and build elements based on other players with similar profiles
- **Build Optimizer**: Ranks builds based on damage, survivability, and effectiveness
- **Meta Tracker**: Monitors trends in top builds, skills, and aspects across the community or uploaded data

## 📦 Tech Stack (Planned)
- Python (core logic)
- OpenCV + Tesseract (image parsing)
- Scikit-learn or LightFM (recommendation engine)
- FastAPI (API backend)
- Streamlit or Dash (Web UI)

## 🚀 MVP Scope
- Support one class (e.g., Necromancer)
- Manual input UI for gear/stats (OCR later)
- Damage calculator for one skill
- Simple recommender for aspects and gear

## 🚀 Installation & Usage (Planned)

```bash
# Install requirements (TBD)
pip install -r requirements.txt

# Run example analysis
python scripts/predict_pit.py --input sample_build.json
```

## 📁 Project Structure

```
sanctuaryai/
├── data/            # Sample builds and stats
├── scripts/         # Main prediction logic and utilities
├── models/          # Trained regression/classification models
├── notebooks/       # Experimentation and model training
└── README.md
```

## 🔮 Planned Enhancements
- PIT prediction model with live tuning
- Screenshot OCR with auto-parsing
- Community leaderboard and trending builds
- Discord bot integration

## 📜 License

MIT License © 2025 Eduardo Silva and contributors
