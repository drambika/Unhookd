# Verification report

Date: 6 November 2026. Environment: Linux build container, Chromium (Playwright) at phone size 390 × 844, files served by a local static web server (`python3 -m http.server`), which serves the folder the same way Netlify does. Internet access to Google Fonts, cdnjs and jsDelivr was blocked in this environment.

**Not tested:** deployment on Netlify itself, real phones, Safari and Firefox, real fingerprint sensors, real camera scanning. See `NOT_EXPORTED_AND_DEPENDENCIES.md`.

## 1. Exact copy check

- SHA-256 of the published app downloaded from claude.ai: `fef370b704ad00b43e315c58cf97f0db45fc914a8fc91f5b4747fdad74c8b45f`
- SHA-256 of `index.html` in this archive: `fef370b704ad00b43e315c58cf97f0db45fc914a8fc91f5b4747fdad74c8b45f`
- Result: **identical**

## 2. Asset checks

- All files requested by the app over the local server returned HTTP 200. No missing local files (0 errors of 404 or similar).
- All 55 SVG files in `assets/illustrations/` open as valid images.
- `index-selfhosted.html` loaded the bundled fonts (Nunito and Baloo 2 reported as loaded by the browser) and both QR libraries from `vendor/`.

## 3a. Interaction test: `index.html`

Result: 37 passed, 0 failed, 1 skipped. JavaScript errors on the page: 0. Requests to claude.ai or Anthropic: 0.

Web addresses the page tried to reach: `127.0.0.1:8765` (200), `fonts.googleapis.com` (failed), `cdnjs.cloudflare.com` (failed).

| # | Step | Result | Detail |
| --- | --- | --- | --- |
| 1 | Splash screen shows on open | PASS | shown, then dismissed |
| 2 | Onboarding 1: welcome | PASS |  |
| 3 | Onboarding 2: 4-card tour | PASS |  |
| 4 | Onboarding 3: name, colour, accessory | PASS |  |
| 5 | Onboarding 4: substance must be picked | PASS |  |
| 6 | Onboarding 5: ADHD hurdles | PASS |  |
| 7 | Onboarding 6: clinic code (paste) + trusted person | PASS |  |
| 8 | Consent required before finish | PASS | You're all set, Test! -> Today |
| 9 | Data persists after reload (localStorage) | PASS | name, 2 trackers, 1 person, 2 meds, clinic kept |
| 10 | Quest tick + Finn dance celebration | PASS | overlay shown |
| 11 | Add own quest | PASS |  |
| 12 | Check-in with strong craving -> support sheet | PASS |  |
| 13 | Tracker +/- counter | PASS |  |
| 14 | Get support (slip) sheet + heavy drinking flag | PASS |  |
| 15 | Call button opens call screen | PASS | Sunrise Clinic (sample) |
| 16 | Slip restart keeps map progress | PASS |  |
| 17 | Journey map renders | PASS |  |
| 18 | Dance moves: play unlocked, locked hint | PASS |  |
| 19 | Shop: not enough seeds explains | PASS | You need 21 more seeds. Quests earn them |
| 20 | Care: edit and save clinic | PASS |  |
| 21 | Care: add medicine | PASS |  |
| 22 | Care: if-then plan builder | PASS |  |
| 23 | Plan "Do it now" starts 10-min timer | PASS |  |
| 24 | Withdrawal self-check | PASS | Mild symptoms |
| 25 | Safety plan save | PASS |  |
| 26 | Doctor summary | PASS |  |
| 27 | Clinic setup code + QR image | PASS | QR not drawn (library not loaded): The QR image needs an internet connection. The code below works on its own. |
| 28 | Scan QR from a photo | SKIPPED | SKIPPED: no QR image to scan because the QR library could not load (CDN blocked in this test sandbox) |
| 29 | Learn: open and finish a story | PASS |  |
| 30 | Calm corner: bubbles + breathing | PASS |  |
| 31 | Me: country helplines + currency | PASS | UK emergency 999 shown |
| 32 | Me: trusted person hello | PASS |  |
| 33 | Me: sound, vibration, night mode | PASS |  |
| 34 | Me: Pro toggle | PASS |  |
| 35 | PIN lock: set, reload, unlock | PASS |  |
| 36 | Discreet mode + quick hide | PASS |  |
| 37 | Fingerprint (WebAuthn) button responds | PASS | fallback screen shown (no authenticator in test browser) |
| 38 | Sample data + start fresh | PASS |  |

## 3b. Interaction test: `index-selfhosted.html`

Result: 38 passed, 0 failed, 0 skipped. JavaScript errors on the page: 0. Requests to claude.ai or Anthropic: 0.

Web addresses the page tried to reach: `127.0.0.1:8765` (200).

| # | Step | Result | Detail |
| --- | --- | --- | --- |
| 1 | Splash screen shows on open | PASS | shown, then dismissed |
| 2 | Onboarding 1: welcome | PASS |  |
| 3 | Onboarding 2: 4-card tour | PASS |  |
| 4 | Onboarding 3: name, colour, accessory | PASS |  |
| 5 | Onboarding 4: substance must be picked | PASS |  |
| 6 | Onboarding 5: ADHD hurdles | PASS |  |
| 7 | Onboarding 6: clinic code (paste) + trusted person | PASS |  |
| 8 | Consent required before finish | PASS | You're all set, Test! -> Today |
| 9 | Data persists after reload (localStorage) | PASS | name, 2 trackers, 1 person, 2 meds, clinic kept |
| 10 | Quest tick + Finn dance celebration | PASS | overlay shown |
| 11 | Add own quest | PASS |  |
| 12 | Check-in with strong craving -> support sheet | PASS |  |
| 13 | Tracker +/- counter | PASS |  |
| 14 | Get support (slip) sheet + heavy drinking flag | PASS |  |
| 15 | Call button opens call screen | PASS | Sunrise Clinic (sample) |
| 16 | Slip restart keeps map progress | PASS |  |
| 17 | Journey map renders | PASS |  |
| 18 | Dance moves: play unlocked, locked hint | PASS |  |
| 19 | Shop: not enough seeds explains | PASS | You need 21 more seeds. Quests earn them |
| 20 | Care: edit and save clinic | PASS |  |
| 21 | Care: add medicine | PASS |  |
| 22 | Care: if-then plan builder | PASS |  |
| 23 | Plan "Do it now" starts 10-min timer | PASS |  |
| 24 | Withdrawal self-check | PASS | Mild symptoms |
| 25 | Safety plan save | PASS |  |
| 26 | Doctor summary | PASS |  |
| 27 | Clinic setup code + QR image | PASS | QR drawn; poster downloaded as unhookd-clinic-poster.png |
| 28 | Scan QR from a photo | PASS | Scan Clinic |
| 29 | Learn: open and finish a story | PASS |  |
| 30 | Calm corner: bubbles + breathing | PASS |  |
| 31 | Me: country helplines + currency | PASS | UK emergency 999 shown |
| 32 | Me: trusted person hello | PASS |  |
| 33 | Me: sound, vibration, night mode | PASS |  |
| 34 | Me: Pro toggle | PASS |  |
| 35 | PIN lock: set, reload, unlock | PASS |  |
| 36 | Discreet mode + quick hide | PASS |  |
| 37 | Fingerprint (WebAuthn) button responds | PASS | fallback screen shown (no authenticator in test browser) |
| 38 | Sample data + start fresh | PASS |  |

## 4. Other files

- `source-reference/index.html` (split CSS/JS): loads, sample data and all five tabs open, JavaScript errors: 0.
- `versions/v1-earlier-prototype/index.html`: loads, sample data and all five tabs open, JavaScript errors: 0.

## 5. Independence from Claude

- No request to any claude.ai or Anthropic address was made in any test.
- The only Claude-related code path (`window.claude.use("downloads")` in the poster download) fell back to a normal browser download, which succeeded.
- The QR scan test in the exact `index.html` was skipped only because cdnjs was blocked in the test environment, so no QR image could be drawn to scan. The same code path passed in `index-selfhosted.html`, and with internet access the exact copy loads the same library version from the CDN.
