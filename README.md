# SQL Injection Lab

A **100% client-side** application for a SQL Injection class (Intrusion Testing Techniques).
A **real SQLite database** runs in the student's browser (via [sql.js](https://sql.js.org)); nothing is sent to any server.
Avaliable here: https://jrafa1607.github.io/sqli-login-lab/

You can:
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

- `vulnerable_login` builds the query by **concatenating** the input directly into the SQL
  string, so text like `admin' --` changes the query's logic.
- `safe_login` uses a **parameterized query** (`... WHERE username = ? AND password = ?`),
  so the input is treated as **data**, never as code — and the injection stops working.

The payload list is grouped into those that **work** against this exact query (SQLite) and
those that **fail on purpose** — the lesson being that a payload must match both the
**database** (SQLite uses `--`, not `#`) and the **query shape**.

> Isolated training environment, for educational purposes only.
> Testing SQL Injection on third-party systems without authorization is a crime (Law 12.737/2012, Brazil).

## Credits

Built with [sql.js](https://github.com/sql-js/sql.js) (SQLite compiled to WebAssembly).
Payload reference inspired by the OWASP SQL Injection materials.

## Author

**João Rafael** — Intrusion Testing Techniques, UNINOVE
GitHub: [@jrafa1607](https://github.com/jrafa1607)

## License

Distributed under the **MIT License**. See the [`LICENSE`](LICENSE) file for details.

© 2026 João Rafael. Educational use — provided "as is", without warranty of any kind.
