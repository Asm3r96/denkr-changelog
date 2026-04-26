# denkr changelog

Public release notes and Android beta distribution for denkr.

denkr is a calm, private mobile assistant where the assistant is the product. It is built around one continuous relationship, not a dashboard full of tools pretending to be a product. Chat is home. Memory, reminders, notebooks, skills, and connectors exist to strengthen that relationship without taking it over.

This repository is the public release surface for denkr beta builds. It is intentionally separate from the private app source repository.

## What denkr is

- One assistant. Yours.
- Calm by design.
- Private by default.
- Local-first in its core architecture.
- Built around chat, memory, reminders, and notebooks.

denkr should feel modern, quiet, dark, mobile-native, and personal. It should not feel like a generic AI wrapper, a cluttered productivity dashboard, or a collection of disconnected mini apps.

## What this repo is for

- Publish Android beta release notes
- Attach signed APK files to GitHub Releases
- Expose a tiny `latest.json` manifest for in-app update checks
- Give humans and agents one clean public place to read what changed

## Repository layout

```text
README.md
latest.json
notes/
  0.2.0.md
  _template.md
```

## How the app should use this repo

The app should fetch `latest.json` only.

It should not fetch or parse markdown notes for update logic. The markdown files are for humans, support, and agents that want more context.

Expected app flow:

1. Fetch `latest.json`
2. Compare installed Android version against `versionCode`
3. If a newer version exists, show an update row or page
4. Open `apkUrl` when the user chooses to update

## How humans and agents should use this repo

- Read `README.md` for the product framing
- Read `notes/*.md` for release details
- Use the GitHub Release page for the APK download

Suggested note structure for each release:

- Summary
- What changed
- How to use it
- Known issues

That shape is easier for testers to scan and easier for agents to reason over.

## Release workflow

1. Build a signed Android release APK from the private `denkr` app repo
2. Create or update `notes/<version>.md`
3. Update `latest.json`
4. Create a GitHub Release tagged like `android-v0.2.0`
5. Upload the APK asset to that release
6. Confirm the URLs in `latest.json` point to the uploaded release asset and raw markdown note

## Current channel

- Android beta via direct APK install
- Not on Google Play yet

## Notes

- Keep the main source repository private
- Keep APK binaries in GitHub Releases, not committed into this repo
- Keep `latest.json` small and stable because the app will depend on it
