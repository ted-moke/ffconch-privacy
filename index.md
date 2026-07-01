---
title: FF Conch — Privacy Policy
---

# FF Conch — Privacy Policy

_Last updated: June 27, 2026_

FF Conch ("the extension") is a browser extension that enhances the Sleeper
fantasy football website with richer stats and a cleaner layout. FF Conch is an
independent project and is **not affiliated with, endorsed by, or sponsored by
Sleeper.**

## The short version

FF Conch does **not** collect, store, sell, or transmit any of your personal
information to the developer or to any third party. There are no analytics, no
tracking, and no developer-operated servers. Everything the extension does
happens locally in your own browser.

## What data the extension accesses

When you view a page on `sleeper.com`, FF Conch reads the fantasy football data
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

## What data the extension stores

To stay fast and reduce network requests, FF Conch caches data **locally in your
browser** using the standard extension storage APIs:

- **`chrome.storage.local`** — a cached copy of the NFL player dictionary and
  short-lived league/matchup data.
- **`chrome.storage.sync`** — your FF Conch settings (which features are turned
  on). If you are signed into Chrome, your browser may sync these settings across
  your own devices; this is handled entirely by Chrome, not by FF Conch.

This data never leaves your browser except as the Chrome sync of your own
settings described above. You can clear it at any time by removing the extension.

## What data the extension shares

None. FF Conch has no backend server and sends no data to the developer or to any
advertiser, analytics provider, or other third party.

## Permissions

- **`storage` / `unlimitedStorage`** — to cache the player dictionary and your
  settings locally, as described above.
- **Host access** to `sleeper.com`, the Sleeper APIs/CDN, and the FantasyCalc API
  — to read the page you're viewing and fetch the public data that powers the
  enhancements. FF Conch requests access to no other sites.

## Changes to this policy

If this policy changes, the "Last updated" date above will change and the new
version will be published at this URL.

## Contact

Questions about this policy can be sent to **iam@tedmoke.com**.
