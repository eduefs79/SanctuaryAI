# SanctuaryAI Engines Architecture

## 🔧 Overview
SanctuaryAI is designed to support multiple RPGs by abstracting game-specific logic into modular, plug-and-play "engines." Each engine implements a standard interface for build parsing, performance estimation, and personalized feedback.

This document defines the structure and responsibilities of each engine.

---

## 🧱 Core Engine Interface
Each game engine must implement the following components:

### 1. `parse_build(input_data)`
- Input: JSON, screenshot parse result, or user form
- Output: Structured build dictionary (skills, gear, affixes, glyphs, stats)

### 2. `estimate_performance(build)`
- Input: Parsed build dictionary
- Output: Performance metric (e.g., predicted damage, estimated tier clear, resource regen, survivability)

### 3. `recommend_changes(build)`
- Input: Parsed build dictionary
- Output: List of recommended improvements (gear swaps, skill changes, affix priorities)

### 4. `get_prompt_template(language)` *(optional)*
- Input: Language code (e.g., `en`, `pt`, `es`)
- Output: Localized LLM prompt template for build feedback

---

## 🗂️ Folder Structure
```
sanctuaryai/
├── engines/
│   ├── diablo4/
│   │   ├── parser.py
│   │   ├── estimator.py
│   │   ├── recommender.py
│   │   └── prompts.py
│   ├── poe/
│   ├── lostark/
│   └── common/
```

---

## ✅ Diablo IV Engine (Reference)
- Implements formula-based PIT prediction
- Uses screenshot parser + JSON loader
- Integrates with multilingual prompt engine
- Recommends aspects, glyphs, gear upgrades based on VecYou similarity model

---

## 🔮 Future Engines
| Game | Notes |
|------|-------|
| Path of Exile | PoB integration, cluster jewel optimization, DPS simulator |
| Lost Ark | Engravings, tripods, class engravings synergy |
| Last Epoch | Affix-based scaling, mono tier prediction |
| WoW | PvE talent trees, DPS modeling, dungeon viability |

---

## 🤝 Contributing a New Engine
1. Fork the repo
2. Add your game engine folder under `sanctuaryai/engines/`
3. Implement the required interface methods
4. Add documentation and example input JSON
5. Submit a PR and tag it `engine` + `game-name`

---

## 💬 Questions?
Open a GitHub discussion or tag @eduardo-sanctuary in your PR.
