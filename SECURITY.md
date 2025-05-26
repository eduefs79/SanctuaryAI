# SanctuaryAI – Security Strategy

## 🔐 Overview
SanctuaryAI integrates multiple layers of application, infrastructure, and user data security with a focus on protecting player privacy, securing API endpoints, and complying with OWASP Top 10 recommendations.

---

## 🔑 Authentication
- **Battle.net OAuth 2.0** integration for user login
- Only the `battletag` is stored (encrypted) in PostgreSQL
- No email, password, or sensitive Battle.net data is ever collected or stored

---

## 🔒 Data Security
### PostgreSQL:
- Uses field-level encryption via `pgcrypto` to store battletags
- User data identified internally via UUIDs, not PII

### MongoDB:
- Stores gameplay data only (builds, skills, stats)
- No personal identifiers saved — only `user_id` references

### Internal IDs:
- All systems (SQL, NoSQL, LLM) communicate using anonymized UUIDs
- Enables secure linkage without exposing identity

---

## 🧱 API Gateway (Nginx)
- Acts as reverse proxy for all microservices
- Enforces:
  - TLS termination
  - JWT or token validation
  - Rate limiting
  - IP filtering (optional)
  - Request size limits
- Protects against OWASP Top 10 vulnerabilities including:
  - Broken Authentication
  - Excessive Data Exposure
  - Rate Limit Bypass
  - Injection attacks (SQL/JSON)

---

## 🧪 OWASP Alignment
| OWASP Risk | Mitigation |
|------------|------------|
| API1: Broken Auth | OAuth + token validation via Nginx |
| API2: Broken AuthZ | Role enforcement at service layer |
| API3: Excessive Data | Response schema contracts enforced via FastAPI |
| API4: Resource Limits | Nginx rate limiting, max body size |
| API10: SSRF, Injection | Sanitization and validation via FastAPI Pydantic models |

---

## 🔁 Logging & Monitoring
- All API activity can be logged via gateway
- Optional integration with tools like Prometheus/Grafana for alerting
- Authentication failures and suspicious patterns flagged for review

---

## ✅ Additional Notes
- No persistent user sessions stored on server
- Future roadmap includes optional 2FA via Battle.net or Discord
- Contributions must comply with security best practices and may be reviewed

---

## 📬 Questions / Reporting
Please open a GitHub issue or contact the maintainers if you discover a potential vulnerability.
