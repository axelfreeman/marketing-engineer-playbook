# 02 — Distribution that leaves a trace

Two rules decide what is worth doing without a budget:

1. Only artifacts that outlive the week: a URL, a package version, a merged diff, a crawl signal, an archived
   snapshot.
2. Nothing that needs a new permission: no accounts you do not own, no paid placement, no cold DMs.

## What leaves a trace

| artifact | why it lasts |
|----------|--------------|
| Source page on your own domain | you control it, it is indexable, it can be updated forever |
| Package on a public registry | indexed, cached, mirrored by aggregators, versioned |
| Pull request to a curated list | a merge is a permanent high-trust link; an open PR is a cheap lottery ticket |
| `robots.txt` + sitemap + IndexNow ping | tells crawlers about a page the minute it exists |
| `llms.txt` | describes what the site answers, in the format AI crawlers read |
| Archived snapshot | proof of what the page said on a date, independent of you |

## What evaporates

Posts in someone else's community (rules change, threads die), DM outreach (no artifact), anything requiring the
recipient to remember you.

## The honest clock

Artifacts have near-zero traffic in week one and non-zero value for years. Judge the first 24 hours as an
artifact count; judge traffic at 60 days. Any report that only measures week one will always conclude this work
is worthless — and will be wrong for a reason that takes two months to prove.
