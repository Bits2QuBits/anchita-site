# anchita.ai — landing site

The public landing page for **Anchita LLC**, served free via GitHub Pages at the
custom domain **anchita.ai**. Single self-contained `index.html` — no build step,
no dependencies (fonts load from Google Fonts, the flow-field is inline canvas).

This repo is intentionally **separate** from the technical documentation site
(`anchita-banking`), so the brand page can own the domain root while the docs keep
their own URL.

## Deploy (one time)

1. Create a new **public** repo on GitHub — suggested name: `anchita-site`.
2. Push these files:
   ```bash
   cd ~/Learning/anchita-site
   git init && git branch -M main
   git add -A && git commit -m "Add anchita.ai landing page"
   git remote add origin https://github.com/bits2qubits/anchita-site.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages** → Source = "Deploy from a branch",
   Branch = `main` / `/ (root)` → Save.
4. In the same **Pages** panel, set **Custom domain** = `anchita.ai`
   (the `CNAME` file already declares it) and tick **Enforce HTTPS** once the
   certificate is issued.

## DNS (at Squarespace / your domain registrar)

Point the apex domain at GitHub Pages. In Squarespace DNS settings, remove the
default parking records and add:

| Type  | Host | Value            |
|-------|------|------------------|
| A     | @    | 185.199.108.153  |
| A     | @    | 185.199.109.153  |
| A     | @    | 185.199.110.153  |
| A     | @    | 185.199.111.153  |
| CNAME | www  | bits2qubits.github.io |

(Optionally add the four AAAA records for IPv6:
`2606:50c0:8000::153`, `…8001::153`, `…8002::153`, `…8003::153`.)

DNS can take from a few minutes to a couple of hours to propagate. Once it does,
`https://anchita.ai` serves this page instead of the Squarespace default.

> Note: pointing anchita.ai's DNS at GitHub Pages means the domain no longer
> serves the Squarespace site builder. You keep the domain (registered via
> Squarespace); only where it *points* changes.
