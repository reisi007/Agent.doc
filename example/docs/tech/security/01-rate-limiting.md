---
domain: technical
topic: security
status: draft
---

# Technical Concept: API Rate Limiting

## 🛠 Target State Specifications
To prevent brute-force attacks on the login route, we must implement rate limiting.
- **Limit:** Max 5 failed login attempts per IP within 15 minutes.
- **Storage:** Use Redis as an in-memory store for counters.
