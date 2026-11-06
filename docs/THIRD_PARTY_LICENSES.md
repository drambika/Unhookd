# Third-party libraries, fonts and services

Everything else in this archive (code, design, Finn the fish, the journey map, all illustrations, text and documents) is original work: © 2026 Ambika Thangaraju. All rights reserved.

## Bundled in `vendor/`

| Item | Version | Licence | Licence file | Source |
| --- | --- | --- | --- | --- |
| qrcodejs (by davidshimjs) | 1.0.0 | MIT | `vendor/qrcodejs/LICENSE` | npm package `qrcodejs@1.0.0`; the app's CDN copy is `cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js` |
| jsQR (by cozmo) | 1.4.0 | Apache License 2.0 | `vendor/jsqr/LICENSE` | npm package `jsqr@1.4.0`, file `dist/jsQR.js`; the app's CDN copy is the minified `jsQR.min.js` of the same version |
| Nunito font (weights 500, 600, 700, 800; latin and latin-ext) | Fontsource build | SIL Open Font License 1.1 | `vendor/fonts/nunito/OFL-LICENSE.txt` | Google Fonts via Fontsource |
| Baloo 2 font (weights 600, 700, 800; latin and latin-ext) | Fontsource build | SIL Open Font License 1.1 | `vendor/fonts/baloo-2/OFL-LICENSE.txt` | Google Fonts via Fontsource |

Note: the vendored qrcodejs file came from npm and could not be compared byte for byte with the cdnjs copy from inside the build environment (cdnjs was not reachable there). Both are version 1.0.0 of the same project. It was tested and draws working QR codes.

## Loaded from the internet by `index.html` (exact copy)

| Service | Purpose | Terms |
| --- | --- | --- |
| Google Fonts (`fonts.googleapis.com`, `fonts.gstatic.com`) | Nunito and Baloo 2 | fonts under SIL OFL 1.1; Google Fonts terms of service |
| cdnjs (`cdnjs.cloudflare.com`) | qrcodejs 1.0.0 | MIT library; cdnjs terms |
| jsDelivr (`cdn.jsdelivr.net`) | jsQR 1.4.0, loaded only when scanning | Apache-2.0 library; jsDelivr terms |

## Linked services (opened only when the user taps)

WhatsApp (`wa.me`), the phone's SMS and dialer apps (`sms:`, `tel:`), Google Maps search links, and findahelpline.com. Unhookd sends no data to them; the user's own phone opens them.

## Not used

No analytics, advertising, tracking, error-reporting, payment or AI services. No server-side code.
