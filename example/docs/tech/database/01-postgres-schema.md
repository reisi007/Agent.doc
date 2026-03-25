---
domain: technical
topic: database
status: open
---

# Technical Concept: PostgreSQL User Schema

## 🛠 Technical Details & Architecture
- **Table:** `users`
- **Encryption:** `bcrypt` for passwords (Salting Rounds: 10).
- **Schema:**
  - `id` (UUID, Primary Key, Auto-Generate)
  - `email` (Varchar, Unique, Not Null)
  - `password_hash` (Varchar, Not Null)
  - `email_verified` (Boolean, Default: false)
  - `created_at` (Timestamp with Timezone)
