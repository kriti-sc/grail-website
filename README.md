# Grail landing page

A static, single-page site for Grail. Plain HTML and CSS, no build step.

## Files

| File | Purpose |
|---|---|
| `index.html` | The landing page (all CSS is inline; includes JSON-LD structured data) |
| `index.md` | The same page as Markdown, for AI agents |
| `llms.txt` | A precise summary of Grail for AI agents and language models |
| `favicon.svg` | Site icon |
| `robots.txt` | Allows search engines and AI crawlers to read the site |
| `sitemap.xml` | Lists the site's pages for crawlers |
| `_headers` | Security headers and content types applied by Cloudflare Pages |

## Before you deploy: replace the placeholders

Two placeholders need real values:

- `YOUR_FORM_ID`: your Formspree form ID (in `index.html`)
- `YOUR_DOMAIN`: your site's domain without `https://`, e.g. `grail.dev` (in `index.html`, `index.md`, `llms.txt`, `robots.txt`, `sitemap.xml`)

```bash
# macOS (on Linux, drop the '' after -i)
sed -i '' 's/YOUR_FORM_ID/abcd1234/g' index.html
sed -i '' 's/YOUR_DOMAIN/grail.dev/g' index.html index.md llms.txt robots.txt sitemap.xml
```

Until you have a custom domain, you can use your `*.pages.dev` address.

## Keep the agent files in sync

`index.md` mirrors the copy in `index.html`, and `llms.txt` summarizes it. When you change the page copy, update both. If you publish pricing, compatibility, or deployment details, move them out of the "Not yet published" section in `llms.txt`.

## Preview locally

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Connect the signup forms (Formspree)

Create a form at https://formspree.io, copy its form ID (the part after `/f/`), and replace `YOUR_FORM_ID` as shown above. Each form sends a hidden `source` field (`hero` or `cta`) so you can see which one people use.

## Deploy on Cloudflare Pages

1. Push this repo to GitHub.
2. In the Cloudflare dashboard, create a Pages project and connect the repo.
3. Build settings: framework preset **None**, build command empty, output directory `/`.
4. Deploy. Every push to the main branch redeploys the site.
5. Optional: add your custom domain under the project's **Custom domains** tab.

### Check that AI crawlers aren't blocked

Cloudflare can block AI crawlers at the edge regardless of `robots.txt`, and this may be on by default for your domain. In the Cloudflare dashboard, check the AI crawler / bot settings for your domain and make sure AI assistants are allowed if you want them to read and recommend the site.

## Check agent readiness

Chrome's Lighthouse includes an Agentic Browsing audit:

```bash
npx lighthouse@latest https://YOUR_DOMAIN --only-categories=agentic-browsing --output=html --output-path=report.html
```
