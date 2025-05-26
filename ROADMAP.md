# SanctuaryAI Roadmap

## 🗺️ Vision
To build an intelligent assistant that:
- Helps players understand and optimize their Diablo IV builds
- Uses real game mechanics for precise damage calculations
- Applies machine learning to recommend gear, aspects, and skill setups

---

## 🎯 Core Modules

### 🖼️ 1. Image Parser
- OCR + layout detection
- Extract weapon damage, aspect bonuses, stats, skill tree info

### ⚔️ 2. Damage Calculator
- Use IGV’s formula:

#### 📐 Full Damage Formula (Expanded)
```
Final Damage = Weapon × SkillCoef × (1 + Additive Bonuses)
             × (1 + Mult1) × (1 + Mult2) × ...
             × (1 + Crit Damage) [if crit]
             × (1.2 + VulnBonus) [if vulnerable]
             × Overpower Multiplier [if proc]
```

**Where:**
- `Weapon` = your weapon base damage or DPS
- `SkillCoef` = internal multiplier for the skill (e.g., 1.2 = 120%)
- `Additive Bonuses` = sum of linear modifiers (+% Core, Close, etc.)
- `Multiplicative Bonuses` = unique multiplicative effects (Berserking, Glyphs)
- `Crit Damage` = 50% base + gear/paragon bonuses
- `VulnBonus` = starts at +20%, increased by stats
- `Overpower` = rare proc using [HP + Fortify] × modifiers

### 🤖 3. Recommender Engine
- Collaborative filtering: “Others with your build also use X, Y, Z”
- Content-based filtering: recommend based on your current gear/stats
- Hybrid: combine both for smarter suggestions

### 🧙 4. Build Optimizer
- Suggest most efficient ways to boost damage or survivability
- Recommend paragon boards, glyphs, affixes

### 📈 5. Meta Tracker
- Monitor top used aspects and gear across all users
- Show trending skills and damage meta per class

### 🌐 6. Frontend / API
- FastAPI for serving ML/logic
- Streamlit or Dash for Web UI (or Overwolf overlay)
- Discord bot for in-game help

---

## 🔁 Milestones

| Phase | Description |
|-------|-------------|
| ✅ MVP | Manual input + damage calculator for one class/skill |
| 🔍 Phase 2 | Image parsing: extract gear, skills, stats from screenshot |
| 🤖 Phase 3 | Recommender engine (simple content-based) |
| 🌐 Phase 4 | Web app to upload builds and show results |
| 🧠 Phase 5 | Full AI assistant + trending meta dashboard + build sharing |

---

## 📦 Tech Stack (Planned)
- Python
- OpenCV + Tesseract
- FastAPI
- Scikit-learn / LightFM / TensorFlow (for recommendations)
- Streamlit or Dash (for UI)
- SQLite/PostgreSQL
- Optional: Overwolf SDK for in-game overlay

---

## 🧪 Stretch Goals
- PIT level predictor (how far your build can go)
- Upload-and-analyze from video clips (via frame extraction)
- Augmented Reality overlays for gear comparison

---

## 🙌 Get Involved
Contributors welcome! We're building this for the community, and with the community. Open issues, suggest features, or bring your builds!
