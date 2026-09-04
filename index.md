---
title: Conch FF — Privacy Policy
---
# Conch FF — Privacy Policy

_Last updated: September 4, 2026_

Conch FF ("the extension") is a browser extension that enhances the Sleeper
fantasy football website with richer stats and a cleaner layout. Conch FF is an
independent project and is **not affiliated with, endorsed by, or sponsored by
Sleeper.**

## The short version

Conch FF does **not** collect, sell, or share your personal information. Most
of what the extension does happens locally in your own browser. A few features
talk to servers on the developer's behalf:

- **Trade-history enrichment** sends the **league ID** of the Sleeper league
  you are viewing to a backend service operated by the developer (**FF TV
  Guide**) so it can return that league's trade history. Switchable off in the
  extension popup.
- **The TV Guide tab** asks that same service for the **NFL schedule** —
  kickoff times and TV networks, which Sleeper's own API does not carry. The
  request identifies no league and no person. Switchable off in the popup.
- **Anonymous usage analytics** sends a random identifier and the extension's
  **version number** to Google Analytics so the developer can tell which
  versions are in use and whether updates are reaching users — never any
  league, roster, or account data. Switchable off in the popup.
- **A feature-configuration check** asks the FF TV Guide service which parts of
  the extension it should run, so a feature that breaks against a change on
  Sleeper's site can be switched off without waiting days for a store update.
  This one is **not** switchable, because it is the mechanism for switching
  other things off. It sends no data about you — only the extension's version
  and which browser it is — and receives a short list of on/off flags.

No other feature contacts any server beyond the public APIs described below.

## What data the extension accesses

When you view a page on `sleeper.com`, Conch FF reads the fantasy football data
that page already deals with (your leagues, rosters, matchups, and standings) so
it can display it more usefully. To enrich that view it fetches additional
**publicly available** data directly from these APIs, from your browser:

- **Sleeper public API** (`api.sleeper.app`, `api.sleeper.com`) — league,
  roster, matchup, and player information.
- **Sleeper CDN** (`sleepercdn.com`) — player avatars and images.
- **FantasyCalc public API** (`api.fantasycalc.com`) — player and draft-pick
  trade values (dynasty or redraft, matching the league's format).

These requests contain only the public identifiers needed to look up that data
(for example, a league ID or player ID). They do **not** include your name,
email, password, or any account credentials.

## The FF TV Guide backend

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

The extension also asks this service for two things that are **not** about you
or your leagues:

- **The NFL schedule** (the TV Guide tab): kickoff times and TV networks for the
  season. The request carries no league ID and no identifier beyond the
  anonymous token; every user receives the same answer.
- **The feature configuration** described above: which parts of the extension
  are currently allowed to run.

Turning off trade-history enrichment stops the trade requests, and turning off
the TV Guide tab stops the schedule request. The feature-configuration check
keeps running while the extension is enabled — it is the switch that turns
things off, so it cannot be behind one of them. Turning the whole extension off
in the popup stops all communication with the service.

## Anonymous usage analytics

So the developer can tell which extension versions are in use and whether
updates are reaching users, the extension sends a small amount of anonymous
usage data to **Google Analytics** (which processes it on the developer's
behalf):

- **What is sent:** a random identifier generated by the extension (not
  derived from your Sleeper account, your browser profile, or any personal
  data), the extension's version number, and the event type — a once-daily
  "installed and running" ping plus install/update events. If Sleeper shows
  you its redesigned site on a page the extension doesn't support yet, the
  extension also reports the **page type** it saw (for example "matchup"), so
  the developer knows to add support — never the league, URL, or any content.
  As with any web request, Google receives your IP address and may derive
  coarse location from it under Google's own policies; the extension itself
  sends no location data.
- **What is never sent:** anything about your Sleeper account, leagues,
  rosters, page content, or browsing. Analytics events contain no fantasy data
  at all.
- **Retention:** analytics data is retained for 14 months, then deleted.
- **Opting out:** turn off **"Share anonymous usage stats"** in the extension
  popup (turning the whole extension off also stops analytics). The Firefox
  build contains no analytics code at all.

## What data the extension stores

To stay fast and reduce network requests, Conch FF caches data **locally in your
browser** using the standard extension storage APIs:

- **`chrome.storage.local`** — a cached copy of the NFL player dictionary,
  short-lived league/matchup data, the anonymous FF TV Guide authentication
  token described above, the random analytics identifier, and a few
  housekeeping timestamps (last analytics ping, last update check).
- **`chrome.storage.sync`** — your Conch FF settings (which features are turned
  on). If you are signed into Chrome, your browser may sync these settings across
  your own devices; this is handled entirely by Chrome, not by Conch FF.
- **Ordinary browser storage on `sleeper.com`** — small display preferences that
  belong to the page you are looking at: the order you dragged your league list
  into, how wide you left the chat panel, which panels you collapsed, and which
  notices you dismissed. These never leave your browser and are not sent
  anywhere.

You can clear all of it at any time by removing the extension.

## What data the extension shares

Nothing is sold or shared with advertisers or data brokers. Anonymous usage
analytics (a random identifier and the extension version — never any fantasy
data) is processed by Google Analytics on the developer's behalf, exactly as
described above. Beyond that, the only party the extension communicates with
outside the public APIs above is the developer-operated FF TV Guide service.

## Permissions

- **`storage` / `unlimitedStorage`** — to cache the player dictionary and your
  settings locally, as described above.
- **Host access** to `sleeper.com`, the Sleeper APIs/CDN, and the FantasyCalc API
  — to read the page you're viewing and fetch the public data that powers the
  enhancements.
- **Host access** to the FF TV Guide API
  (`ff-tv-guide-507152681487.us-east4.run.app`) — to fetch trade-history
  enrichment, the NFL schedule behind the TV Guide tab, and the feature
  configuration, all as described above. Conch FF requests access to no other
  sites.

## Changes to this policy

If this policy changes, the "Last updated" date above will change and the new
version will be published at this URL.

## Contact

Questions about this policy can be sent to **iam@tedmoke.com**.
