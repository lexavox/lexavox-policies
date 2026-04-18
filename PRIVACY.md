# Privacy Policy

**Effective Date:** February 7, 2026
**Controller:** LexaVox

## Data We Collect
*   **User Content:** Images, audio, text you provide for OCR, translation, summarization, TTS.
*   **Age Range:** Age range (not exact birthdate) collected during first-run age verification for COPPA compliance and age-appropriate features.
*   **Device Data:** Basic diagnostics, crash logs, OS version.
*   **Usage Data:** Feature usage (non-identifying), queued jobs status.
*   **Referral Program Data:** If you participate in our referral program:
    * Your unique referral code (8-character alphanumeric)
    * Referral claims (when someone uses your code) - timestamp only, no personal data of referee
    * IP address and user agent (for fraud prevention only, not linked to personal identity)
    * Trial grant status (server-side tracking of promotional trial periods)
*   **No Sensitive Categories** unless you voluntarily include them in User Content.

## How We Use Data
*   Provide OCR, translation, summarization, TTS.
*   Maintain on-device history and durable storage.
*   Improve stability and support (diagnostics).
*   Manage referral program rewards and prevent abuse.
*   Compliance with legal obligations.

## Sharing
*   With cloud providers to perform user-initiated processing (e.g., Google Cloud services for OCR, Translation, STT, TTS, Gemini API).
*   With analytics/diagnostics services as necessary for app stability (non-identifying where possible).
*   **We do not sell User Content.**
*   **We do not use User Content to train models.**

## Advertising
*   Rewarded video ads are shown to free tier users to unlock cloud features (Cloud TTS, Cloud Translation, AI features).
*   Ad providers (Google AdMob) may collect device and usage data per their privacy policies.
*   Premium and Premium+ subscribers do not see ads.
*   Users can opt-out of personalized ads via device settings.
*   Internal promotional banners (not ads) promote our own products and do not share data with third parties.

## Retention
*   On-device history and stored files remain until you delete them or uninstall the app.
*   Temporary cloud processing is transient; data is processed in-memory and immediately deleted.
*   Diagnostics retained per provider policies (Firebase Crashlytics); minimized where feasible.
*   Referral program data (codes, claims, trial grants) retained in Firestore for the duration of your account to enforce abuse prevention rules. Deleted when you delete your account.

## Security
*   Data in transit is encrypted (HTTPS/TLS).
*   On-device storage uses OS-provided sandboxing; you are responsible for device security.

## Your Rights (GDPR/CCPA)
*   Access, correct, delete your data.
*   Opt-out of sale (we do not sell data).
*   Exercise rights via privacy@lexavox.com.
*   Verification may be required.

## Data & Account Deletion

### How Account Authentication Works
LexaVox uses anonymous Firebase authentication. This means:
*   You do not create a username or password account
*   The app generates a unique anonymous identifier (UID) tied to your device
*   This allows cloud features and app sync to work without account creation friction
*   You can use the app fully offline without any authentication

### How to Delete Your Account and Data

#### Option 1: Uninstall the App (Immediate)
Uninstalling LexaVox immediately removes all locally stored data from your device:
*   All documents, scans, history, and bookmarks are deleted
*   All offline language packs are removed
*   All app settings and preferences are cleared
*   No data remains on your device

#### Option 2: Request Cloud Data Deletion (GDPR/CCPA)
If you used cloud features (cloud OCR, translation, TTS, or AI), contact us to delete your Firebase profile and associated cloud processing records:

**Email:** [privacy@lexavox.com](mailto:privacy@lexavox.com?subject=Request%20Account%20Deletion)  
**Subject:** "Request Account Deletion"

Please include:
*   Your email address or any contact information you used
*   A statement that you are requesting deletion of your anonymous Firebase account and any associated cloud processing records
*   Optionally, the date range you used the app

We will:
1. Verify your identity if necessary
2. Delete your anonymous Firebase UID from our backend
3. Remove all associated cloud processing logs and temporary data
4. Confirm deletion within 30 days

#### What Gets Deleted
*   Your anonymous Firebase UID and all related backend records
*   Cloud processing history and logs
*   Referral program data (codes, claims, trial grants) if applicable
*   Any analytics records tied to your device

#### What Does NOT Get Deleted (Cannot Be Deleted)
*   Locally stored documents on your device (can only be deleted by uninstalling the app)
*   Aggregated, anonymized usage statistics (cannot be tied to individuals)
*   Published content you shared publicly (if any)

### Important Notes
*   **Deletion is permanent:** Once deleted, we cannot recover your data
*   **Cloud processing is transient:** Cloud features do not permanently store your content—data is processed in-memory and deleted immediately
*   **No payment account:** LexaVox uses RevenueCat for subscriptions, not a personal account. Subscription cancellation is handled through your device's app store (Apple or Google)
*   **Verification may be required:** To prevent abuse, we may require proof of device ownership or email verification before processing deletion requests

### Regional Rights
*   **EU (GDPR):** You have the right to access, correct, and delete your personal data
*   **California (CCPA):** You have the right to know, delete, and opt-out of sale of personal information
*   **Other Jurisdictions:** We honor similar data privacy rights in your region

For any questions about account deletion or data privacy, contact **[privacy@lexavox.com](mailto:privacy@lexavox.com)**.

## Children's Privacy (COPPA Compliance)
*   **Age Requirement:** LexaVox is for users 13 years of age or older.
*   **Age Verification:** Users select their age range during first use. Users under 13 are blocked from accessing the app.
*   **Age-Based Features:**
    * Users under 18 have profanity filter permanently enabled for text-to-speech
    * Users under 18 receive child-directed advertising (non-personalized, age-appropriate)
    * Users 18+ can optionally disable the profanity filter in settings
*   **Data Minimization:** We collect age range only (e.g., "13-17"), not exact birthdates, to minimize personal data collection.
*   **No Knowingly Collecting from Under 13:** We do not knowingly collect personal data from children under 13. If we discover such data, we will delete it promptly.

## International Transfers
Data may be processed in multiple regions by third-party processors; protections via contractual safeguards.

## Contact
[privacy@lexavox.com](mailto:privacy@lexavox.com) for privacy requests.

## Changes
Updates will be posted; continued use constitutes acceptance.
