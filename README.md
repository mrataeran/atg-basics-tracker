# ATG Basics Tracker

A mobile-first, installable web app for running the ATG Basics routine.

**Live:** https://mrataeran.github.io/atg-basics-tracker/

## Features

- Three workout days (Lower Mon, Upper Wed, Spine Fri) plus a session log
- Per-set weight and rep logging with completion circles and a progress bar
- Tempo prescriptions expanded into plain English (41X1, 4010, 5010, 31X1)
- Rest timer with beep and vibration, auto-started when a set is checked
- Per-exercise scratch notes
- Encrypted video vault, plus a YouTube search link per exercise as a fallback
- Installs to the home screen and works offline (manifest + service worker)

## The video vault

Exercise video links are **not** stored in the clear. They are encrypted with
AES-256-GCM using a key derived from your passphrase with PBKDF2-SHA256
(310,000 iterations) and committed as `vault.json`.

Anyone can download `vault.json`, but without the passphrase it is just noise.
On first load the app shows a lock screen; enter the passphrase once per device
and tick *Remember on this device* to decrypt the links into localStorage.
You can re-lock (and wipe the decrypted links) with the padlock icon in the header.

Everything is done in the browser with the Web Crypto API. No server, no account,
no key is ever transmitted.

### Changing the passphrase or the links

1. Open the app and unlock it.
2. Tap the gear icon. The current links appear as editable JSON.
3. Enter a new passphrase twice and press **Encrypt into vault.json**.
4. Press **Copy vault** (or **Download vault.json**).
5. Replace `vault.json` in this repo with the new blob and commit.

Every device then needs the new passphrase.

## Privacy

Sets, notes and history live in localStorage under `atgb.v1` and never leave the device.
The gear menu can export and import that blob if you want to move it between devices.

## Install on a phone

Open the live URL, then Share -> Add to Home Screen (iOS) or the install prompt (Android).

## Editing the routine

All exercise data is in the `DAYS` array near the top of the script block in `index.html`.
