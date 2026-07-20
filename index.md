---
title: FF Conch — Privacy Policy
---

# Conch FF — Privacy Policy

_Last updated: July 19, 2026_

Conch FF ("the extension") is a browser extension that enhances the Sleeper
fantasy football website with richer stats and a cleaner layout. Conch FF is an
independent project and is **not affiliated with, endorsed by, or sponsored by
Sleeper.**

## The short version

Conch FF does **not** collect, sell, or share your personal information. It has
no analytics and no tracking. Most of what the extension does happens locally
in your own browser. One feature — trade-history enrichment — talks to a
backend service operated by the developer (**FF TV Guide**): it sends the
**league ID** of the Sleeper league you are viewing so the service can return
that league's trade history. You can turn this feature off in the extension
popup ("Trade history enrichment"), and no other feature contacts the
developer's servers.

## What data the extension accesses

When you view a page on `sleeper.com`, Conch FF reads the fantasy football data
that page already deals with (your leagues, rosters, matchups, and standings) so
it can display it more usefully. To enrich that view it fetches additional
**publicly available** data directly from these APIs, from your browser:

- **Sleeper public API** (`api.sleeper.app`, `api.sleeper.com`) — league,
  roster, matchup, and player information.
- **Sleeper CDN** (`sleepercdn.com`) — player avatars and images.
- **FantasyCalc public API** (`api.fantasycalc.com`) — dynasty player and draft-pick
  trade values.

These requests contain only the public identifiers needed to look up that data
(for example, a league ID or player ID). They do **not** include your name,
email, password, or any account credentials.

## The FF TV Guide backend (trade-history enrichment)

When the "Trade history enrichment" feature is enabled (it is by default) and
you open a league's **transactions tab**, the extension contacts the
developer-operated FF TV Guide API to fetch that league's historical trades —
including which players traded draft picks eventually became, which Sleeper
does not show.

- **What is sent:** the Sleeper **league ID** of the league you are viewing,
  and an **anonymous authentication token**. The extension signs in to the
  service anonymously (via Firebase Authentication); this anonymous identity is
  random, is not linked to your Sleeper account, your name, or your email, and
  is used only to authenticate requests and enforce fair-use rate limits.
- **What is received:** that league's trade history, assembled by the service
  from Sleeper's public API.
- **What the service stores:** league-level fantasy data (leagues, trades,
  drafts) fetched from Sleeper's public API — the same information visible to
  every member of the league on Sleeper. The service does not receive or store
  your personal information, browsing history, or any page content beyond the
  league ID.
- **What is never sent:** your name, email, credentials, cookies, browsing
  history, or any data from non-Sleeper sites.

Turning the feature off in the popup stops all communication with the FF TV
Guide backend.

## What data the extension stores

To stay fast and reduce network requests, Conch FF caches data **locally in your
browser** using the standard extension storage APIs:

- **`chrome.storage.local`** — a cached copy of the NFL player dictionary,
  short-lived league/matchup data, and the anonymous FF TV Guide
  authentication token described above.
- **`chrome.storage.sync`** — your Conch FF settings (which features are turned
  on). If you are signed into Chrome, your browser may sync these settings across
  your own devices; this is handled entirely by Chrome, not by Conch FF.

You can clear all of it at any time by removing the extension.

## What data the extension shares

Nothing is sold or shared with advertisers, analytics providers, or data
brokers. The only party the extension communicates with beyond the public APIs
above is the developer-operated FF TV Guide service, exactly as described in
the previous section.

## Permissions

- **`storage` / `unlimitedStorage`** — to cache the player dictionary and your
  settings locally, as described above.
- **Host access** to `sleeper.com`, the Sleeper APIs/CDN, and the FantasyCalc API
  — to read the page you're viewing and fetch the public data that powers the
  enhancements.
- **Host access** to the FF TV Guide API
  (`ff-tv-guide-507152681487.us-east4.run.app`) — to fetch trade-history
  enrichment, as described above. Conch FF requests access to no other sites.

## Changes to this policy

If this policy changes, the "Last updated" date above will change and the new
version will be published at this URL.

## Contact

Questions about this policy can be sent to **iam@tedmoke.com**.
