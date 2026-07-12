# OnlyHealth — Pinterest + Blog Revenue Project

## Who
Kiko, 34, based in North Macedonia. Remote 9–5 (3–4h active), toddler at home, ~1–1.5 focused hours/day for this project. Prefers direct, honest assessments — no hype. Income target: €2–4k/month (understood to be a 12–24 month build, not a quick win).

## The Decision (already made — don't relitigate)
After evaluating Fanvue AI models, YouTube faceless channels (MMO niche), clipping, and Pinterest/blog, the chosen path is **Pinterest + own blog** in the health/wellness/lifehacks niche. Reasons: proven prior experience, existing assets, most automatable per hour of Kiko's time, compounding asset vs treadmill. Checkpoint: **month 4** — if impressions/traffic climbing, scale; if flat, reassess with data.

## Assets (audited)
- **Domain: onlyhealth.info** — RENEW ($41, decided). WordPress site, live.
  - ✅ AdSense APPROVED (the crown jewel — do not disrupt this setup)
  - ✅ Google Search Console: "No issues detected" on Manual Actions (verified via screenshot, July 2026)
  - ✅ NOT blocked on Pinterest
  - ⚠️ Current content: ~21 pages of 2015-era spun viral clickbait ("lose 4kg in 4 days" type). Liability for Google YMYL health standards. Needs aggressive prune/rewrite.
  - ⚠️ Current branding: "Only Health Fans" (bad — reads as OnlyFans pun). Rebrand to **OnlyHealth**. Footer has lorem ipsum, logo image empty.
- **healthyweb365.com** — BLOCKED on Pinterest (source page shows error, spam history). Do not use.
- **Pinterest accounts**: many, spam history, different IPs, mostly throttled (~600–700 views/month total = effectively dead). Kiko is auditing to find one salvageable account (criteria: alive + some impressions + 6mo+ age). If none qualify, start ONE fresh account. Never resurrect multi-account spam patterns.
- **MGID account** — fallback only. Ladder: AdSense (now) → Journey/Raptive at ~10k+ sessions/month. Avoid chumbox ads on the relaunch.
- **Monetization plan**: AdSense from day 1 + affiliate layered in.

## Architecture Decision
**Path A chosen: keep WordPress**, rebuild on it. Rationale: preserves the AdSense-approved setup, and WordPress REST API enables direct programmatic publishing.
- Kiko needs to create a WordPress **Application Password** (Users → Profile → Application Passwords) for API publishing.
- Publish via REST API: POST to `https://onlyhealth.info/wp-json/wp/v2/posts` with Basic auth (username:application_password).

## The Weekly Pipeline (the product of this project)
Input: Kiko sends a list of blog post titles (health/wellness/lifehacks niche).
Output per title:
1. SEO-optimized article (proper H2/H3 structure, meta description, FAQ section, internal links, genuinely useful — NOT thin spun content; health is YMYL, quality bar is high)
2. Published to onlyhealth.info via WP REST API
3. 2–3 Pinterest pin images (2:3 ratio, 1000×1500) via **Higgsfield MCP** (`generate_image`, model `nano_banana_pro`, text overlay with title). A playful 3D render style was tested and approved; also tested clean photo style.
4. Pinterest title + keyword-rich description + link, ready to paste
Cadence: 3–5 articles/week, pins spread across the week (not dumped at once).
Pinterest posting: MANUAL for months 1–3 (young/recovering account must look human). Possible later upgrades: Pinterest API app (needs Kiko's dev account + approval) or Playwright browser automation — month 3+ decision, not day 1.

## MCP Servers to add to Claude Code
- Higgsfield: `claude mcp add --transport http higgsfield https://mcp.higgsfield.ai/mcp` (image/video gen)
- NexLev: `claude mcp add --transport http nexlev https://prod.dashboard.nexlev.io/api/claude-mcp` (YouTube research — secondary, not core to this project)

## Immediate Next Steps
1. [ ] Kiko: renew onlyhealth.info domain
2. [ ] Kiko: create WP application password, confirm hosting active
3. [ ] Kiko: finish Pinterest account audit, pick the survivor (or decide fresh)
4. [ ] Claude: crawl existing posts → prune/rewrite list (delete worst YMYL offenders, keep/rewrite salvageable)
5. [ ] Claude: rebrand plan — site title "OnlyHealth", fix footer lorem ipsum, new logo, clean theme
6. [ ] Claude: first batch of articles + pins once titles are provided
7. [ ] Set up Pinterest business account features: claim onlyhealth.info website, enable rich pins

## Style & Communication Notes
- Be direct and honest with Kiko; he explicitly prefers candid assessments over validation.
- Watch for shiny-object drift: new side-hustle ideas (clipping, AI-model courses, etc.) have been evaluated and parked. The agreed rule: one channel, 6+ months, judge at the month-4 checkpoint.
- Health content rules: no crash-diet claims, no miracle cures, no medical misinformation — both for AdSense policy and Google YMYL survival.
