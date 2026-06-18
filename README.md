# CFSB — Sanctions / PEP / Adverse Media List Selection Tool

Single self-contained HTML tool (Sardine-branded). All data and logic are embedded in `index.html`.


## Recommended hosting: GitHub (private) + Cloudflare Pages + Access
GitHub Pages is **public** with no viewer access control, so it is *not* suitable here. Use GitHub for source control and Cloudflare for hosting + the login gate.

### 1. Push this repo to GitHub (private)
```bash
# from this folder
git remote add origin https://github.com/<your-org-or-user>/cfsb-list-selection.git
git branch -M main
git push -u origin main
```


### 2. Connect Cloudflare Pages to the repo
- Cloudflare dashboard → Workers & Pages → Create → Pages → **Connect to Git** → pick this repo.
- Build settings: **Framework preset = None**, Build command = *(blank)*, Output directory = `/`.
- Deploy. You get a URL like `cfsb-list-selection.pages.dev`. Every `git push` auto-redeploys.

### 3. Gate it with Cloudflare Access (who can view + audit log)
- Zero Trust → Access → Applications → Add → Self-hosted, pointing at the Pages URL.
- Policy: **Allow → Emails →** the specific client + Sardine addresses.
- Visitors get a one-time code by email; only allowlisted addresses get in.
- Zero Trust → Logs → Access shows **who logged in and when**. Add/remove emails to grant/revoke.

## Updating the tool
Replace `index.html` with a regenerated version, commit, and push — Cloudflare redeploys automatically. URL and access list stay the same.

