# SQL Injection Lab

A **100% client-side** application for a SQL Injection class (Intrusion Testing Techniques).
A **real SQLite database** runs in the student's browser (via [sql.js](https://sql.js.org)); nothing is sent to any server.

Students can:
- **Create** and **query** users in the `users` table;
- **Exploit the login field** on a realistic sign-in page, comparing the **vulnerable** version (string concatenation) with the **secure** one (parameterized query);
- Reveal **bypass payloads** on demand and see, live, the query being built and why each technique works or fails.

> Isolated training environment, for educational purposes only. Testing SQL Injection on third-party systems without authorization is a crime (Law 12.737/2012, Brazil).

## Publish on GitHub Pages

1. Create a new repository (e.g. `sqli-lab`) and upload **`index.html`** to the root.
2. In the repository: **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Under **Branch**, select **main** and the **/ (root)** folder, then click **Save**.
5. Wait ~1 minute. The URL appears at the top of the Pages screen, in the form:
   `https://YOUR-USERNAME.github.io/sqli-lab/`

That's it — just share the URL with the class. Requires an internet connection (the SQLite
engine is loaded from a public CDN, with an automatic fallback).

## Run locally (optional)

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
