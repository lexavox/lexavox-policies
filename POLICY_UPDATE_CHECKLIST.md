# LexaVox Policies - Update Checklist for GitHub Push

**Date:** January 15, 2026
**Purpose:** Ready policies for public GitHub repository

---

## Changes Summary

### Files to Replace (5 updated files)

| Original File | Updated File | Status | Changes Made |
|---------------|--------------|--------|--------------|
| MONETIZATION_POLICY.md | MONETIZATION_POLICY_UPDATED.md | ✅ Ready | Removed banner ads, added app open ads, added internal promotions section |
| PRIVACY.md | PRIVACY_UPDATED.md | ✅ Ready | Removed Expo reference, added advertising section, updated effective date |
| LEGAL_NOTICE.md | LEGAL_NOTICE_UPDATED.md | ✅ Ready | Removed Expo, kept React Native, added effective date |
| DATA_POLICY.md | DATA_POLICY_UPDATED.md | ✅ Ready | Added effective date, updated email to privacy@lexavox.com |
| SECURITY.md | SECURITY_UPDATED.md | ✅ Ready | Added effective date, updated email to security@lexavox.com |

### Files to Keep As-Is (2 files)

| File | Status | Reason |
|------|--------|--------|
| TERMS.md | ✅ Keep | Already current, just update effective date to match others |
| README.md | ✅ Keep | General index, no changes needed |

---

## Detailed Changes by File

### 1. MONETIZATION_POLICY.md → MONETIZATION_POLICY_UPDATED.md

**Changed:**
- ✅ **Line 3:** Effective date updated to `2026-01-15`
- ✅ **Section 2, Table:** Changed "Banners/interstitials" to "App open ads, interstitials"
- ✅ **Section 6:** Complete rewrite - new ad types section
  - Added **App Open Ads** subsection
  - Added **Interstitial Ads** subsection (kept from original)
  - Added **Rewarded Ads** subsection (kept from original)
  - Added **Internal Promotional Banners** subsection (NEW)
  - Updated implementation details

**Why:**
- Banner ads removed from app (replaced with app open ads)
- Internal promotional banners added (SmartBanner repurposed)
- Needed to reflect current monetization strategy

---

### 2. PRIVACY.md → PRIVACY_UPDATED.md

**Changed:**
- ✅ **Line 3:** Effective date updated to `2026-01-15`
- ✅ **Line 19:** Removed "Expo infrastructure" reference
  - **Old:** "With cloud providers... Expo infrastructure"
  - **New:** "With cloud providers... Google Cloud services for OCR, Translation, STT, TTS, Gemini API"
- ✅ **Added Section:** "Advertising" (after line 22)
  - Documents app open ads, interstitials
  - Notes ad exemptions for premium users
  - Mentions internal promotional banners

**Why:**
- Expo removal complete (5 utility packages don't constitute "infrastructure")
- Need to disclose advertising practices for Play Store compliance
- Internal promotions should be mentioned for transparency

---

### 3. LEGAL_NOTICE.md → LEGAL_NOTICE_UPDATED.md

**Changed:**
- ✅ **Added Line 3:** Effective date `2026-01-15`
- ✅ **Line 22 (old 20):** Removed Expo from third-party services
  - **Old:** "Expo / React Native: App framework and build tools"
  - **New:** "React Native: App framework and build tools"
  - **Added:** "Google Cloud Platform: Infrastructure for backend services"

**Why:**
- Expo framework removed (only 5 utility packages remain)
- More accurate to list Google Cloud Platform as infrastructure provider

---

### 4. DATA_POLICY.md → DATA_POLICY_UPDATED.md

**Changed:**
- ✅ **Added Line 3:** Effective date `2026-01-15`
- ✅ **Line 17 (old ~17):** Fixed placeholder email
  - **Old:** "contact us at [Insert Contact Email]"
  - **New:** "contact us at privacy@lexavox.com"
- ✅ **Line 24 (old ~22):** Updated Google reference
  - **Old:** "e.g., Google Gemini"
  - **New:** "e.g., Google Cloud services, Gemini API"

**Why:**
- Email address needs to be real for GDPR/CCPA compliance
- More accurate service naming

---

### 5. SECURITY.md → SECURITY_UPDATED.md

**Changed:**
- ✅ **Added Line 3:** Effective date `2026-01-15`
- ✅ **Line 13 (old ~13):** Fixed placeholder email
  - **Old:** "report it to [Insert Security Email]"
  - **New:** "report it to security@lexavox.com"

**Why:**
- Email address needs to be real for responsible disclosure
- Professional security contact point

---

### 6. TERMS.md (Minor Update Needed)

**Change Needed:**
- Update effective date from `December 1, 2025` to `January 15, 2026`
- No content changes needed (already accurate)

---

## Email Addresses Used

**IMPORTANT:** Ensure these email addresses are configured before pushing to GitHub:

- ✅ **privacy@lexavox.com** - Privacy/GDPR requests
- ✅ **security@lexavox.com** - Security vulnerability reports

**Action Required:**
1. Set up email forwarding at domain registrar OR
2. Configure Google Workspace/Microsoft 365 with custom domain OR
3. Use email alias service

**Test both addresses** before making repo public!

---

## Pre-Push Checklist

### Before Pushing to GitHub:

- [ ] **Verify email addresses are configured:**
  - [ ] Send test email to privacy@lexavox.com - verify receipt
  - [ ] Send test email to security@lexavox.com - verify receipt

- [ ] **Replace old files with updated versions:**
  - [ ] Delete `MONETIZATION_POLICY.md`, rename `MONETIZATION_POLICY_UPDATED.md` to `MONETIZATION_POLICY.md`
  - [ ] Delete `PRIVACY.md`, rename `PRIVACY_UPDATED.md` to `PRIVACY.md`
  - [ ] Delete `LEGAL_NOTICE.md`, rename `LEGAL_NOTICE_UPDATED.md` to `LEGAL_NOTICE.md`
  - [ ] Delete `DATA_POLICY.md`, rename `DATA_POLICY_UPDATED.md` to `DATA_POLICY.md`
  - [ ] Delete `SECURITY.md`, rename `SECURITY_UPDATED.md` to `SECURITY.md`

- [ ] **Update TERMS.md effective date:**
  - [ ] Change from `December 1, 2025` to `January 15, 2026`

- [ ] **Review all files one final time:**
  - [ ] No placeholder text remains
  - [ ] All dates are January 15, 2026 (or later)
  - [ ] All email addresses are real and working
  - [ ] Expo references removed (except legacy docs if kept)

- [ ] **Commit to GitHub:**
  ```bash
  cd D:/LexaVox/LexaVox-policies
  git add .
  git commit -m "Update policies for Jan 2026 launch - remove banner ads, add app open ads, fix Expo references"
  git push origin main
  ```

---

## Commands to Execute

### Step 1: Replace Files

```bash
cd D:/LexaVox/LexaVox-policies

# Backup old versions (optional)
mkdir _old_versions_2026-01-01
move MONETIZATION_POLICY.md _old_versions_2026-01-01/
move PRIVACY.md _old_versions_2026-01-01/
move LEGAL_NOTICE.md _old_versions_2026-01-01/
move DATA_POLICY.md _old_versions_2026-01-01/
move SECURITY.md _old_versions_2026-01-01/

# Rename updated files
move MONETIZATION_POLICY_UPDATED.md MONETIZATION_POLICY.md
move PRIVACY_UPDATED.md PRIVACY.md
move LEGAL_NOTICE_UPDATED.md LEGAL_NOTICE.md
move DATA_POLICY_UPDATED.md DATA_POLICY.md
move SECURITY_UPDATED.md SECURITY.md
```

### Step 2: Update TERMS.md

Open TERMS.md and change line 3:
```markdown
**Effective Date:** January 15, 2026
```

### Step 3: Commit and Push

```bash
git status
# Review changes

git add MONETIZATION_POLICY.md PRIVACY.md LEGAL_NOTICE.md DATA_POLICY.md SECURITY.md TERMS.md

git commit -m "Update policies for 2026 launch

- Replace banner ads with app open ads in monetization policy
- Add advertising disclosure to privacy policy
- Remove Expo references (migration complete)
- Fix placeholder email addresses
- Update all effective dates to Jan 15, 2026
- Add internal promotional banner disclosure"

git push origin main
```

---

## Play Store Compliance

### These Policies Meet Requirements For:

✅ **Google Play Store:**
- Privacy policy with data collection disclosure
- Ad disclosure (AdMob integration)
- Third-party service disclosure
- User rights (GDPR/CCPA)
- Children's privacy (COPPA)

✅ **AdMob:**
- Ad types disclosed
- User control documented
- Privacy practices clear
- Compliance with Google policies

✅ **RevenueCat (In-App Purchases):**
- Subscription terms clear
- Token/credit system explained
- Pricing transparency
- Refund policy referenced in Terms

---

## Post-Push Actions

After pushing to GitHub:

1. **Update Play Store listing:**
   - Privacy policy URL: `https://github.com/yourusername/LexaVox-policies/blob/main/PRIVACY.md`
   - Terms URL: `https://github.com/yourusername/LexaVox-policies/blob/main/TERMS.md`

2. **Update Firebase Hosting** (when website is deployed):
   - Host policies at `https://lexavox.com/policies/privacy`
   - Host policies at `https://lexavox.com/policies/terms`

3. **Reference in app:**
   - Settings screen should link to policy URLs
   - First-run onboarding should reference privacy policy

---

## Verification

After push, verify on GitHub:

- [ ] All 7 files present (6 policies + README)
- [ ] No `*_UPDATED.md` files remain
- [ ] All files have matching effective dates (Jan 15, 2026)
- [ ] No placeholder text `[Insert Email]` anywhere
- [ ] Expo only mentioned in historical context (if at all)
- [ ] Banner ads not mentioned (replaced with app open ads)
- [ ] Repository is public (or ready to make public)

---

## Summary of Updates

**Total Files Updated:** 5
**Total Files Kept:** 2
**New Effective Date:** January 15, 2026

**Major Changes:**
1. ✅ Monetization policy reflects app open ads instead of banner ads
2. ✅ Internal promotional banner strategy documented
3. ✅ Expo infrastructure references removed
4. ✅ All placeholder emails replaced with real addresses
5. ✅ Advertising disclosure added to privacy policy
6. ✅ All effective dates synchronized

**Compliance Status:** ✅ Ready for Play Store submission

---

**Ready to push to GitHub!** Just complete the pre-push checklist above.
