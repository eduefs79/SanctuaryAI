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
- Battle.net OAuth 2.0 authentication for user login

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
- Scikit-learn / LightGBM / PySpark MLlib (for regression and classification)
- Streamlit or Dash (for UI)
- PostgreSQL (structured data, encrypted battletag only)
- MongoDB or CosmosDB (flexible data like OCR/LLM logs)
- Apache Spark (data processing, scoring, clustering at scale)
- Delta Lake / Parquet (feature store and inference output)
- Ollama (local LLMs like LLaMA 3, Mistral, Phi-3)
- Nginx API Gateway (TLS, auth, OWASP filtering, routing)
- Optional: Overwolf SDK for in-game overlay

---

## ☁️ DevOps Infrastructure

### ⚙️ Architecture
- **Docker** for each service (FastAPI, Ollama, Nginx, Postgres, MongoDB)
- **Kubernetes** for orchestration (via GKE, EKS, or local K3s)
- **Nginx API Gateway** for routing, SSL, authentication, and OWASP protections
- **FastAPI** core backend with AI and data logic
- **Ollama** for local LLMs and fine-tuned response generation
- **PostgreSQL** for user data, encrypted battletags, predictions, structured queries
- **MongoDB/CosmosDB** for unstructured build data, JSON uploads, LLM logs
- **Apache Spark** for ingestion, feature extraction, ML pipelines, scoring

### 🔁 CI/CD with GitHub Actions
```yaml
on:
  push:
    branches: [main]
jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Build Docker Image
        run: docker build -t yourrepo/sanctuary-backend ./backend
      - name: Push to DockerHub
        run: docker push yourrepo/sanctuary-backend
      - name: Deploy to K8s
        run: kubectl apply -f k8s/deployment.yaml
```

### ☁️ Terraform Infrastructure-as-Code
Modular provisioning:
```
terraform/
├── main.tf              # Entry point
├── modules/
│   ├── network/         # VPC, subnets
│   ├── kubernetes/      # Cluster
│   ├── postgres/        # Managed DB with encrypted battletags
│   ├── mongo/           # Document DB
│   ├── spark/           # Optional EMR or Dataproc cluster
│   ├── nginx/           # API Gateway and proxy layer
│   └── compute/         # Optional Ollama VM
```
Example:
```hcl
resource "google_container_cluster" "primary" {
  name     = "sanctuary-cluster"
  location = var.region
  ...
}
```

---

## 🧪 Stretch Goals
- PIT level predictor (how far your build can go)
- Upload-and-analyze from video clips (via frame extraction)
- Augmented Reality overlays for gear comparison
- Fine-tune LLaMA with LoRA using user builds and PIT predictions
- SHAP-enhanced explanations injected into LLM prompts
- Natural language interface over structured PIT/gear data
- Optional public leaderboard (linked by encrypted Blizzard battletag)

---

## 🙌 Get Involved
Contributors welcome! We're building this for the community, and with the community. Open issues, suggest features, or bring your builds!