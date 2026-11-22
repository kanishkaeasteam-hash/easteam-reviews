# EASTEAM Reviews — reviews.easteamny.com (GitHub Pages)

A standalone, schema-rich **EASTEAM Reviews** page, built to be cited by AI engines and to rank for "EASTEAM reviews" / "is EASTEAM legit." Hosted free on GitHub Pages under the subdomain **reviews.easteamny.com**.

**Files**
- `index.html` — the reviews page (brand-styled, self-contained). Reviews come from the `REVIEWS` array near the bottom of the file.
- `CNAME` — tells GitHub Pages to serve the site at `reviews.easteamny.com`. Do not edit.
- `README.md` — this file.

---

## IMPORTANT: real reviews only
The page ships with an **empty** `REVIEWS` array and shows an "importing" message until you add data. Only paste **genuine** customer reviews (fabricated reviews violate FTC rules and will get the page penalized). Each entry:

```js
{
  author: "Maya R.",
  rating: 5,                                   // 1–5 integer
  date: "2026-10-14",                          // YYYY-MM-DD
  product: "Camélia Skirt",
  productUrl: "https://easteamny.com/products/camelia-skirt",
  verified: true,
  body: "The exact text the customer wrote."
}
```

Add your real reviews (export them from the Shopify reviews app) between the `[ ]` in the `REVIEWS` array. The star summary, rating bars, and the JSON-LD `AggregateRating` + `Review` schema all generate automatically from that array.

---

## Deploy (one-time, ~10 min)

### 1. Create the GitHub repo
1. Sign in to GitHub → **New repository**.
2. Name it e.g. `easteam-reviews`, set **Public**, create.
3. Upload all three files (`index.html`, `CNAME`, `README.md`) to the repo root (drag-and-drop in the GitHub web UI → Commit).

### 2. Turn on GitHub Pages
1. Repo → **Settings → Pages**.
2. **Source:** Deploy from a branch → Branch: `main` → Folder: `/ (root)` → Save.
3. Under **Custom domain**, it should already read `reviews.easteamny.com` (from the CNAME file). If not, type it and Save.

### 3. Point the subdomain (DNS)
In whatever manages DNS for **easteamny.com** (e.g. your domain registrar / Shopify-managed DNS / Cloudflare), add **one record**:

| Type | Host / Name | Value / Points to |
|------|-------------|-------------------|
| CNAME | `reviews` | `<your-github-username>.github.io` |

(That's a CNAME record for the `reviews` subdomain pointing to your GitHub Pages host. Do **not** point it at the repo URL — just `username.github.io`.)

### 4. Enable HTTPS
Back in **Settings → Pages**, once DNS resolves (can take 10 min–24 hrs), tick **Enforce HTTPS**. Done — the page is live at `https://reviews.easteamny.com`.

---

## After it's live
1. **Add your real reviews** to the `REVIEWS` array and re-commit `index.html`.
2. **Link to it** from easteamny.com (footer and/or the product pages) so it's discoverable and passes a little authority: add a "Reviews" link pointing to `https://reviews.easteamny.com`.
3. **Submit for indexing** once a Google Search Console property exists — add `reviews.easteamny.com` as a property and request indexing, or just let Google find it via the link from your main site.

## Note on authority
A subdomain is treated as partly separate from easteamny.com, so it inherits less authority than a page on the main domain would. If you later want the stronger version, the same page can live at `easteamny.com/pages/reviews` instead — just ask.
