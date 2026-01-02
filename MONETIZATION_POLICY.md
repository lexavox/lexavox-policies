# LexaVox Monetization & Token Policy

_Last updated: 2026-01-15_

This document describes how LexaVox rewards, tokens, transcription minutes, and paid packs operate. It supplements the Terms and Privacy disclosures by providing a transparent overview of how cloud features are funded and consumed. Future changes will be versioned in this repository; refer to the app for the currently active policy date.

## 1. Token Basics
- **LexaTokens** power all cloud features (OCR, translation, summarization, Q&A, neural TTS). Offline features remain free.
- Tokens are issued monthly to premium subscribers and can also be earned through rewarded ads or purchased as packs.
- All tokens (included, earned, and purchased) **reset on the first day of each month** to keep liabilities bounded. Unused tokens do not roll over.
- The app displays current balances and burn estimates before each cloud action. The backend enforces balances using Firebase Auth + Firestore; no API call executes without authorization.

## 2. Monthly Allowances
| User Type | Monthly Tokens | Ads | Notes |
| --- | --- | --- | --- |
| Free | 0 | App open ads, interstitials + optional rewarded ads | Must watch ads or buy packs to access cloud features. |
| Premium Monthly ($7.99) | 300 | Ad-free (no app open or interstitials) unless user opts into rewarded videos | Same allowance for annual plan to keep UX simple. |
| Premium Annual ($59.99/yr) | 300 | Ad-free (no app open or interstitials) unless user opts into rewarded videos | Effective $4.99/mo; still profitable at full usage. |

## 3. Token Burn Rates (per action)
| Action | Token Cost | Notes |
| --- | --- | --- |
| OCR (per page) | 1 | Advanced parsers may cost more when introduced. |
| Translation (~1,000 chars) | 1 | Per-page size cap enforced. |
| Summarize document | 2 | Tiered by length; warnings at 80% balance. |
| Q&A / rewrite turn | 2 | Cooldowns prevent infinite loops. |
| Neural TTS (1,000 chars) | 2 | Free tier uses Standard voices to avoid loss; neural voices require tokens. |
| Cloud STT | _Not tied to tokens_ | See Section 5 for dedicated packs. |

### Rewarded Ads → Tokens
- Completing a rewarded video yields **2 tokens**.
- Caps: max 2 rewarded ads per hour, 10 per day, resetting daily. Ads are optional and user-initiated.
- Tokens from ads follow the same monthly reset rule.

### When No Ad Is Available
- The app informs the user ("No ad available right now. Please try again later or purchase a pack.").
- No courtesy tokens are granted; users may continue offline or buy the Offline Pack for $9.99 to remove offline ads entirely.

## 4. Token Packs (non-STT)
- Freemium packs are priced to nudge toward subscription:
  - 100 tokens for $2.99
  - 500 tokens for $9.99
  - 1,000 tokens for $17.99
- Premium subscribers receive discounted top-ups (example ranges):
  - 100 tokens for $1.99
  - 500 tokens for $6.99
  - 1,000 tokens for $11.99
- Pack pricing may vary by market and is controlled via Remote Config; updates will be reflected in app storefronts.
- Pack tokens reset monthly just like included tokens.

## 5. Cloud STT Minutes (Separate Packs)
- Cloud-based transcription minutes are **not** funded by tokens or ads.
- Both free and premium users must purchase dedicated STT packs; premium users receive a discount.
- Purchased minutes **roll over until consumed** and do not expire.

| Pack Size | Freemium Price | Premium Price |
| --- | --- | --- |
| 100 minutes | $4.99 | $2.99 |
| 300 minutes | $12.99 | $7.99 |
| 600 minutes | $19.99 | $13.99 |

- Each minute of Google STT costs roughly $0.01; the above pricing maintains healthy margins even under heavy usage.
- The first 30 minutes of cloud STT are complimentary for new accounts (one-time). Once exhausted, users must purchase a pack.
- Minutes are consumed in whole-minute increments; the app shows remaining balance prominently. When a pack reaches zero minutes, transcription stops and the user is prompted to purchase more.

## 6. Ads & Promotions

### Ad Types and Placement

#### App Open Ads
- **Who sees them:** Free tier users only
- **When:** Displayed when app launches or resumes from background after being minimized
- **Frequency:** Natural app usage pattern; follows Google AdMob guidelines
- **Exemptions:** Premium subscribers and Offline Pack ($9.99) owners never see app open ads
- **User Control:** Users can upgrade to premium or purchase Offline Pack to remove

#### Interstitial Ads
- **Who sees them:** Free tier users only
- **When:** Shown between tasks, never mid-workflow
- **Frequency:** No more than once per 30 minutes of active use
- **Exemptions:** Premium subscribers and Offline Pack owners never see interstitials
- **Placement Guidelines:** Never interrupt OCR scanning, transcription, or TTS playback

#### Rewarded Ads
- **Who sees them:** All users (free and premium) - opt-in only
- **Reward:** 2 tokens per completed rewarded video
- **Frequency Caps:**
  - Maximum 2 rewarded ads per hour
  - Maximum 10 rewarded ads per day
  - Caps reset daily at midnight UTC
- **User Control:** 100% user-initiated; never shown automatically
- **Token Rules:** Rewarded tokens follow same monthly reset as other tokens

#### Internal Promotional Banners
- **Delivery:** In-app promotional banners (not ads)
- **Purpose:** Promote premium subscriptions, Offline Pack, feature tips
- **Placement:** Tips section at top of main screens
- **Who sees them:** All users (content varies by user tier)
- **No Rewards:** Internal promotions do not grant tokens
- **AdMob Compliant:** Internal product promotion is encouraged by Google

### Ad Implementation & Compliance
- **Mediation:** AdMob mediation only; never manually chained SDKs
- **Reward Verification:** Tokens awarded exclusively via AdMob's `onUserEarnedReward` callback
- **Privacy:** Ad personalization respects user consent (GDPR/CCPA)
- **Platform Compliance:** Follows Google AdMob policies and Play Store requirements
- **Measurement:** Firebase Analytics tracks ad performance (non-identifying data)

## 7. Referral Program

### Overview
LexaVox offers a referral program that rewards users for inviting new users to the app with a 7-day Premium trial.

### How It Works
1. **Share Your Code:** Authenticated users receive a unique 8-character referral code (e.g., `AB3K7XYZ`)
2. **Invite Friends:** Share your referral link (`https://lexavox.app/invite?ref=AB3K7XYZ`) via any channel
3. **New User Installs:** When someone installs LexaVox via your link and creates an account
4. **Claim Reward:** The new user claims the referral, granting you 7 days of Premium access
5. **Server-Authoritative:** All trial grants are managed by our backend via Firestore to prevent tampering

### Rewards
- **7 days of Premium access** per successful referral
- Premium access includes:
  - 300 monthly tokens for cloud features
  - No app open ads or interstitial ads
  - Full access to all Premium features

### Abuse Prevention & Limitations
To ensure fairness and prevent abuse, the following limits apply:

**Referrer Limits:**
- Maximum **3 successful referrals** per 30-day rolling window
- Maximum **30 days of bonus trial time** can accumulate at once
- Bonus time is additive (3 referrals = 21 days total)

**Referee Limits:**
- Each user can claim **only one referral** (lifetime)
- Self-referral is blocked (cannot claim your own code)
- Deep link must be from a new installation (existing users cannot claim)

**Technical Safeguards:**
- Firestore atomic transactions prevent duplicate claims
- IP address and user agent logged for fraud analysis (not linked to personal identity)
- Server validates all claims; client requests can be rejected

### Trial vs Paid Subscription
- Referral trials grant temporary Premium access but do not constitute a paid subscription
- Trials expire after the grant period ends
- Users can upgrade to a paid subscription at any time to maintain Premium access
- Paid subscriptions and referral trials can coexist (e.g., if you have 10 days of trial remaining and purchase Premium, you keep Premium after the trial ends)

### Implementation Status
- **Current:** Deep links work for existing users who install via referral link
- **Coming Soon:** Firebase Dynamic Links for deferred deep linking (install attribution for new users who don't have the app yet)

## 8. Backend Safeguards & Enforcement
- Every cloud action goes through the backend, which verifies Firebase Auth, checks token or minute balance, and debits atomically before calling external APIs.
- Remote Config provides kill switches for each feature, as well as adjustable token costs, ad reward amounts, and per-user caps.
- OpenTelemetry logging + Cloud Armor rate limits monitor abuse and allow rapid response to anomalies.
- Referral system uses Firestore transactions for atomic claim processing and abuse prevention.

## 9. Future Changes
- Any adjustments to token burn, ad exchange, STT pack pricing, or referral rewards will be documented here and reflected in-app.
- The Terms will reference this document so users can review the latest monetization policy easily.
