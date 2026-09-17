# Agent-readiness checklist (23 weighted checks)

Can an AI answer engine find the answer, read it without a browser, and cite it without guessing?

## Crawlability
- [ ] `robots.txt` does not block GPTBot, ClaudeBot, PerplexityBot, Google-Extended, OAI-SearchBot (weight 3)
- [ ] Pages render without JavaScript, or have a no-JS fallback (2)
- [ ] No login wall or consent interstitial in front of the content you want quoted (3)
- [ ] The page returns 200 to a plain `curl` with no cookies (2)
- [ ] One canonical URL per answer — no www/non-www or trailing-slash duplicates (2)

## Answer-ready content
- [ ] Every important page answers one question in the first 60 words (3)
- [ ] Headings are questions a human would type, not internal project names (2)
- [ ] Prices, limits and timeframes are stated as numbers, not "flexible" (3)
- [ ] Claims carry a source or a live URL (2)
- [ ] A definition page exists for the category you want to be cited in (3)

## Machine-readable
- [ ] schema.org markup on service/product pages (Service, Offer, Product, FAQPage) (3)
- [ ] FAQPage/QAPage markup on question pages, answers 40–500 words (2)
- [ ] XML sitemap submitted and every new URL pinged via IndexNow (2)
- [ ] `llms.txt` describes what the site answers and where the canonical pages are (2)
- [ ] Organisation/Person entity ties the page to a verifiable identity (2)

## Someone else's page
- [ ] Present where models already read: registries, repos, docs (3)
- [ ] At least one open, mergeable pull request or discussion contribution (2)
- [ ] Content mirrored somewhere you do not control (2)
- [ ] A third-party page links your canonical URL (3)

## Proof and measurement
- [ ] Every claim is openable in one click (3)
- [ ] One tracked event for the outcome that matters, in your own analytics property (3)
- [ ] Public changelog or artifact list with dates (2)
- [ ] Archived snapshot of the key pages exists (1)

Interactive version with a live score:
https://axelfreeman.github.io/marketing-mindset/tools/aeo-readiness-checklist.html
