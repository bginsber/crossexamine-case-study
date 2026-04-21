# CrossExamine.AI — Technical Case Study (GitHub Pages)

Single-file technical case study showcasing the CrossExamine.AI build. Designed for
SWE hiring managers — reads as a senior engineering write-up, not a marketing page.

## Deploy to GitHub Pages (≈ 3 minutes)

```bash
# 1. From this folder
cd crossexamine-case-study

# 2. Initialize + first commit
git init
git add .
git commit -m "Initial: CrossExamine.AI technical case study"

# 3. Create a public repo and push (requires `gh` CLI, authenticated)
gh repo create crossexamine-case-study --public --source=. --remote=origin --push

# 4. Enable GitHub Pages on main / root
gh api --method PUT "/repos/$(gh api user -q .login)/crossexamine-case-study/pages" \
  -f "source[branch]=main" -f "source[path]=/"

# 5. Open to confirm
gh repo view --web
```

Live URL pattern: `https://<your-username>.github.io/crossexamine-case-study/`

First build takes ~30–60s; refresh until it loads.

## Optional — custom subdomain

If you own `benginsberg.com` (or similar):

```bash
echo "crossexamine.benginsberg.com" > CNAME
git add CNAME && git commit -m "Add custom domain" && git push
```

Then add a DNS CNAME: `crossexamine` → `<your-username>.github.io`. HTTPS
cert provisions in ~10 minutes.

## What's in the page

- Hero + 4 headline metrics (82 endpoints, 2256 tests, 0.976 recall, 9 weeks)
- Problem framing (why privilege review breaks naive LLM approaches)
- Full architecture ASCII diagram
- 5 key architectural decisions with rationale
- 3-stage ML pipeline walkthrough + why sparse autoencoders
- Faithfulness gate (ablation / contrastive / stability)
- Claude Agent SDK integration with quoted-span quality guard
- Results table + engineering stats
- "How this gets built in 9 weeks" — the AI-native workflow argument
- Honest tradeoffs I'd revisit at team scale

All self-contained in `index.html` — no external scripts, no CDN dependencies,
no analytics, no fonts loaded from the network. Ships fast and stays fast.

## Where to link it

- Resume (top of summary, or a "portfolio" line)
- LinkedIn headline link
- Sidecar Health application cover letter
- Email signature
