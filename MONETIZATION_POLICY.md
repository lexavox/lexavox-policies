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

## 7. Backend Safeguards & Enforcement
- Every cloud action goes through the backend, which verifies Firebase Auth, checks token or minute balance, and debits atomically before calling external APIs.
- Remote Config provides kill switches for each feature, as well as adjustable token costs, ad reward amounts, and per-user caps.
- OpenTelemetry logging + Cloud Armor rate limits monitor abuse and allow rapid response to anomalies.

## 8. Future Changes
- Any adjustments to token burn, ad exchange, or STT pack pricing will be documented here and reflected in-app.
- The Terms will reference this document so users can review the latest monetization policy easily.
