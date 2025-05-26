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

## 🧠 Future Features

- Gear image OCR and stat extraction
- PIT leaderboard comparison
- Glyph synergy mapping
- Community build analyzer (compare vs top players)
- Streamlit UI for non-technical users

## 🚀 Quickstart (Planned)

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

## 📜 License

MIT License © 2025 Eduardo Silva and contributors
