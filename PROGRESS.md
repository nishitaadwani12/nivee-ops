# Nivee Citizenship Apps — Progress & Runbook

_Last updated: 2026-09-25_

## Overview
Portfolio of 5 citizenship-test study apps (Expo / React Native + TypeScript),
one private repo each, shared architecture. Monetized with subscriptions
(weekly + 3-monthly) + AdMob ads (free users). Publisher: **Nivee**. Support
email: **nivee12@gmail.com**.

## Apps & repos (all private, GitHub @nishitaadwani12)
| App | Repo | Package / bundle id | Exam | Subscription product ids |
|---|---|---|---|---|
| UK — Life in the UK Test | citizenship-test-uk | com.citizenshipapps.lifeintheuk | 24Q / 18 pass | uk_premium_weekly, uk_premium_quarterly |
| Australia | citizenship-test-au | com.citizenshipapps.australiancitizenship | 20Q / 15 pass | au_premium_weekly, au_premium_quarterly |
| Canada | citizenship-test-ca | com.citizenshipapps.canadiancitizenship | 20Q / 15 pass | ca_premium_weekly, ca_premium_quarterly |
| US | citizenship-test-us | com.citizenshipapps.uscitizenship | 20Q / 12 pass (60%) | us_premium_weekly, us_premium_quarterly |
| Germany — Einbürgerungstest | citizenship-test-de | com.citizenshipapps.einbuergerungstest | 33Q / 17 pass | de_premium_weekly, de_premium_quarterly |

Support/legal repos: **nivee-legal** (public, GitHub Pages) · **nivee-ops** (private, this repo).

## Code status — COMPLETE for all 5 apps
- 173–175 unit tests each, 100% coverage, tsc clean, web bundle verified.
- Auth: email/password + phone OTP + Google (Apple removed until iOS track) via Firebase; on-device fallback.
- Stays logged in (Firebase persistence + authStateReady on cold start).
- Free/premium question tiers (~200 free + 15 premium each); practice, mock exam, progress, handbook.
- Subscriptions via react-native-iap (StoreKit/Play Billing); AdMob banner + interstitial for free users; UMP consent + iOS ATT.
- In-app Privacy/Terms/About + account deletion. Interactive UI, back navigation.
- Reviewer demo account **reviewer@nivee.app / Review1234!** is treated as premium in-app.

## Accounts / infrastructure
- Google Play Console: verified (Nivee, Personal, India). 15% service-fee enrollment: optional/TODO.
- Firebase project: **citizenship-apps** (id citizenship-apps-270d1). Providers: Email, Phone, Google enabled. Web keys baked into app config.
- AdMob: account created (India). Identity/payout verification: TODO (test ads until then).
- Payments: BillDesk cross-border KYC **submitted, pending** (required for non-India payouts).
- Hosted legal (GitHub Pages): https://nishitaadwani12.github.io/nivee-legal/ — /privacy.html, /terms.html, /delete-account.html
- EAS/Expo: account nishita_adwani; UK EAS project linked. Build with `mise exec node@20.19.5 -- npx eas-cli@latest build -p android --profile production`.

## UK launch — status
DONE: account verify · app created · store listing (icon/feature graphic placeholders + phone screenshots) · content rating · target audience (18+) · data safety · privacy policy URL · ads declaration · sign-in details (demo account) · app category (Education) · **internal testing rolled out (version code 2)** · **2 subscriptions live** · **closed-testing (Alpha) release SENT FOR REVIEW**.

PENDING / NEXT (UK):
1. Await Google review approval of the closed-testing release.
2. Send closed-test **opt-in link** to the 13 testers (see testers.txt); get **12+ opted-in**.
3. Run the closed test **14 days** with 12+ testers.
4. **Apply for production access** → create Production release → review → live.
5. BillDesk KYC approval (background) before real cross-border charges.
6. Replace placeholder icon/feature graphic with branded art before public launch (optional).
7. Wire Google Sign-In (needs dev-build SHA-1 + Google OAuth client) — deferred; email works.

## Other apps (AU/CA/US/DE) — store setup NOT started
Code is ready. Repeat the UK store process per app: create app in Play Console,
listing, content declarations, upload production AAB, create their `*_premium_*`
subscriptions, closed test (12 testers/14 days), production. Each can reuse the
same Firebase project, legal URLs, and reviewer demo account.

## Key gotchas / notes
- Node 20 required — prefix commands with `mise exec node@20.19.5 --`.
- Personal Play accounts need a **closed test of 12+ testers for 14 days** before production.
- Store prices are per-storefront; set the local-market currency (₹ only reaches India).
- Firebase web keys are public (safe to commit); real secrets never committed.
