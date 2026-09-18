# Chapter 6 — Distribution with no budget: what ships where, and the rule that cuts the list in half

A published artifact that nobody reads is a diary. The chapters before this one build the page, the
schema, the floors and the kill rules; this one is about the part most teams skip — putting the work
somewhere it stays, and measuring whether it was ever read.

## The rule

**Ship only what leaves a permanent trace in a place the seller already has access to.**

Two clauses, both load-bearing:

- *permanent trace* — the artifact has a URL that still resolves in a year, that a stranger can open
  without an account, and that an answer engine can quote. A post in someone else's Discord is not that.
- *already has access* — an account, token or credential that exists today. Every registration wall,
  captcha and "request access" form converts a 10-minute job into a lost week. If the credential is
  missing, the channel is not rejected, it is parked until the credential arrives on its own.

Apply the rule to a list of fifteen channels and roughly half of them die immediately. That is the
point of the rule: it makes the cut mechanical instead of a matter of taste.

## What actually ships (and where the link goes)

| Artifact | Home | What it is for |
|---|---|---|
| Offer page with schema markup | your own domain | the only page you control end to end; every other channel points here |
| AEO pages for real questions | your own domain | one page per question a buyer types, each with a price and a date |
| Free tool with a score | your own domain or GitHub Pages | earns a link and a reason to return; must compute something real |
| Method as a CLI | npm | the method becomes installable and the package page is indexed |
| Chapters as a repository | GitHub | quotable, diffable, linkable from a README and from issues |
| Articles with canonical urls | dev.to or similar | borrowed audience, canonical pointing at your own page |
| Entries in awesome-lists | GitHub pull requests | a permanent link from a high-authority list if the PR is merged |

The order matters. Build the page first: every later artifact links to it, and a canonical url that
points at a 404 wastes the whole article.

## The mechanics that are easy to get wrong

1. **Sitemap and ping.** A new URL is added to the sitemap in the same commit, then pinged through
   IndexNow with the key file served on the domain. Two minutes of work, and it is what makes the
   difference between "published" and "discoverable".
2. **Canonical before publication, not after.** When a borrowed platform hosts the article and your
   own page hosts the same text, the canonical tag decides which one accrues. Set it in the API call.
3. **One artifact per channel per window.** Two tasks hitting the same platform in parallel trips
   rate limits and looks like a bot. Four channels in parallel, one thread per channel.
4. **Verify the artifact the way a stranger would.** A publish command returning success is not
   evidence. Open the URL, follow the plan: the page returns 200, the file exists on disk, the
   package installs from the registry into a clean directory, the pull request shows as open.
5. **Archive what matters.** A Wayback snapshot is a second, third-party copy of a page you control.
   Request it once per page, and take the verdict from the archive's own index rather than from the
   save endpoint's response code.

## What it measured

Field notes, not projections, from running this playbook on a single domain over one night:
the artifacts are listed with openable links on the proof page, the analytics property reports the
sessions that arrived, and the npm package page reports installs. The numbers are small and that is
the honest starting state: each page and each package is a position that can be linked to, quoted and
improved, while paid reach is rented and stops the day the invoice stops.

## Failure modes worth writing down

- **Volume without a reader.** Twenty pages published in one night, zero sitemap entries, zero pings:
  nothing indexes, and the work is invisible. The indexing step is part of the artifact.
- **Borrowed platform, missing canonical.** The article ranks, your page does not, and the audience
  belongs to someone else's domain.
- **Registrations as progress.** An afternoon spent creating accounts on forums with captchas leaves
  no trace and produces no link. Park it, ship the artifact instead.
- **Publishing in the platform's own house style.** Articles that read like everyone else's on the same
  platform get no citation. The floors, the numbers and the kill rules are what make the text quotable;
  without them it is one more opinion with a byline.
