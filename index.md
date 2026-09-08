---
title: Conch FF — Privacy Policy
---
# Conch FF — Privacy Policy

_Last updated: September 7, 2026_

Conch FF ("the extension") is a browser extension that enhances the Sleeper
fantasy football website with richer stats and a cleaner layout. It can also
connect your **ESPN** leagues to the Conch website, so you can see them
alongside your Sleeper ones — that feature is optional, off until you ask for
it, and described in full in its own section below. Conch FF is an independent
project and is **not affiliated with, endorsed by, or sponsored by Sleeper or
ESPN.**

## The short version

Conch FF does **not** sell or share your personal information, and most of
what the extension does happens locally in your own browser. A few features
talk to servers on the developer's behalf — and one of them, which you have to
ask for by name, sends an authentication credential:

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
- **ESPN connect** — only if you press **"Connect ESPN"** — reads the ESPN
  session cookies your browser already holds and sends them to the FF TV Guide
  service so it can read your ESPN leagues on your behalf. **These are the
  credentials that keep you signed in to ESPN.** Nothing is read and nothing is
  sent unless you press that button. Described in full below.

No other feature contacts any server beyond the public APIs and the FF TV
Guide service described below.

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

The one exception is **ESPN connect** below, which sends ESPN session cookies —
and only when you explicitly ask it to.

## The FF TV Guide backend

When the "Trade history enrichment" feature is enabled (it is by default) and
you open a league's **transactions tab**, the extension contacts the
developer-operated FF TV Guide API to fetch that league's historical trades —
including which players traded draft picks eventually became, which Sleeper
does not show. The first time a league is looked up the service may still be
importing its history from Sleeper's public API; while that runs the extension
polls a **sync-status** endpoint — sending the same league ID — so it can show
you the import's progress instead of an empty panel.

- **What is sent:** the Sleeper **league ID** of the league you are viewing,
  and an **anonymous authentication token**. The extension signs in to the
  service anonymously (via Firebase Authentication); this anonymous identity is
  random, is not linked to your Sleeper account, your name, or your email, and
  is used only to authenticate requests and enforce fair-use rate limits.
- **What is received:** that league's trade history, assembled by the service
  from Sleeper's public API.
- **What the service stores:** league-level fantasy data (leagues, trades,
  drafts) fetched from Sleeper's public API — the same information visible to
  every member of the league on Sleeper. From this feature the service receives
  no personal information, no browsing history, and no page content beyond the
  league ID.
- **What is never sent by this feature:** your name, email, credentials,
  cookies, browsing history, or any data from non-Sleeper sites. (ESPN connect,
  below, is a separate feature you opt into by pressing a button; it is the one
  part of Conch FF that sends a cookie anywhere.)

In the **draft room**, the extension asks the same service for **pick timing**
for the draft you are open on — how long each pick took — so it can show
average pick times alongside the draft. What is sent is the Sleeper **draft
ID** and the same anonymous token; what comes back is timing data for that
draft's picks. This goes off with the draft page enhancements in the popup.

The extension also asks this service for things that are **not** about you
or your leagues:

- **The NFL schedule** (the TV Guide tab): kickoff times and TV networks for the
  season. The request carries no league ID and no identifier beyond the
  anonymous token; every user receives the same answer.
- **Matchup difficulty** (the opponent tint on the team, matchup, and players
  pages): how hard each NFL team's upcoming matchups are. Like the schedule,
  the request carries no league ID and every user receives the same answer.
- **The feature configuration** described above: which parts of the extension
  are currently allowed to run.

Turning off trade-history enrichment stops the trade requests, and turning off
the TV Guide tab stops the schedule request. The feature-configuration check
keeps running while the extension is enabled — it is the switch that turns
things off, so it cannot be behind one of them. Turning the whole extension off
in the popup stops all communication with the service.

## ESPN connect (optional, and off unless you ask for it)

ESPN publishes no API and no sign-in method for third-party apps, so the only
way to show you a private ESPN league is to use the ESPN session your browser
already holds. This is the one feature of Conch FF that sends a credential
anywhere, and none of it happens unless you press the button.

A small script does run on `espn.com` pages, but it is entirely passive: it
waits for a single message from the extension popup and answers it. On its own
it reads nothing, sends nothing, and stores nothing.

If — and only if — you press **"Connect ESPN"** in the extension popup:

- **What is read:** two cookies belonging to `espn.com`, `espn_s2` and `SWID`,
  read from an ESPN page you already have open — the same way ESPN's own page
  scripts read them. These are the credentials that keep you signed in to ESPN.
  No other cookie, for ESPN or for any other site, is ever read.
- **What is sent:** those two values, once, to the FF TV Guide service,
  together with the anonymous authentication token described above.
- **Why:** so the service can call ESPN as you and read the leagues, rosters,
  drafts and scores you can already see on ESPN's own site.
- **What is stored, and where:** the service keeps the two values so it can
  keep your leagues up to date. They are held in storage no app client can
  read, are never returned by any API, and are never written to logs. **The
  extension itself never stores them** — they are read, sent once, and dropped.
- **What is never done with them:** they are used only to *read* your fantasy
  data. Conch FF never sets a lineup, makes a transaction or a trade, posts a
  message, or takes any other action on your ESPN account.
- **Finishing on the website:** after the capture, the popup links you to the
  Conch website to choose which ESPN leagues to add. That link carries a
  single-use code, valid briefly, which lets the account you are signed into
  there take ownership of the connection. The code is not your ESPN
  credentials and it works only once.
- **Removing them:** disconnecting the ESPN connection in the Conch web app
  deletes the stored values. Signing out of ESPN everywhere also invalidates
  them, after which Conch will ask you to reconnect.

If the extension cannot read the session — no ESPN tab open, or you are signed
out of ESPN — it says so and points you to the Conch website, where you can
connect by copying the two values across yourself.

If you never press the button, the extension never reads an ESPN cookie and
never contacts ESPN.

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
  housekeeping timestamps (last analytics ping, last update check). ESPN
  session cookies are **not** among them: as described above, they are sent
  once and never written to extension storage.
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
outside the public APIs above is the developer-operated FF TV Guide service —
which, if you use ESPN connect, is also given your ESPN session cookies so it
can read your leagues on your behalf.

## Permissions

- **`storage` / `unlimitedStorage`** — to cache the player dictionary and your
  settings locally, as described above.
- **`activeTab`** — lets the popup see the address of the tab you are looking
  at, and only while you have the popup open, so it can show the controls that
  apply to that site. It grants nothing for any other tab and nothing in the
  background.
- **Host access** to `sleeper.com`, the Sleeper APIs/CDN, and the FantasyCalc API
  — to read the page you're viewing and fetch the public data that powers the
  enhancements.
- **Host access** to the FF TV Guide API
  (`ff-tv-guide-507152681487.us-east4.run.app`) — to fetch trade-history
  enrichment, draft pick timing, the NFL schedule behind the TV Guide tab,
  matchup difficulty, and the feature configuration, all as described above.
- **Access to `espn.com` pages** — so the passive script described under ESPN
  connect can run there and, when you press "Connect ESPN", hand over the two
  session values. Conch FF requests **no browser-wide cookie permission at
  all**: it can only read what an ESPN page can already read about itself.

Conch FF requests access to no other sites.

## Changes to this policy

If this policy changes, the "Last updated" date above will change and the new
version will be published at this URL.

## Contact

Questions about this policy can be sent to **iam@tedmoke.com**.
