# SQL Injection Lab

A **100% client-side** application for a SQL Injection class (Intrusion Testing Techniques).
A **real SQLite database** runs in the student's browser; nothing is sent to any server.
Avaliable here: https://jrafa1607.github.io/sqli-login-lab/.  You can:

- **Create** and **query** users in the `users` table;
- **Exploit the login field** comparing the **vulnerable** version with the **secure** one;
- Reveal **bypass payloads** on demand and see, live, the query being built and why each technique works or fails.

To run locally: <br>
Opening `index.html` directly in the browser works. If your browser blocks WASM over
`file://`, serve the folder:

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## How it works

- `vulnerable_login` builds the query by **concatenating** the input directly into the SQL string.
- `safe_login` uses a **parameterized query**, so the input is treated as **data**, never as code.

The payload list is grouped into those that **work** against this exact query (SQLite) and
those that **fail on purpose** — the lesson being that a payload must match both the
**database** (SQLite uses `--`, not `#`) and the **query shape**.

> Isolated training environment, for educational purposes only.
> Testing SQL Injection on third-party systems without authorization is a crime (Law 12.737/2012, Brazil).


#### ⚖️ Intellectual Property (IP) Notice

All source code, documentation, and research methodologies contained in this repository are the exclusive Intellectual Property of the author. All rights reserved. Use of this content for academic or professional purposes must include proper citation and attribution. See the [`LICENSE`](LICENSE) file for details.

**Copyright © 2026 [João Rafael](https://www.linkedin.com/in/jrafa1607/).**
