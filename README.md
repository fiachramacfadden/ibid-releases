# ibid

ibid is a quiet macOS browser where you can highlight, underline and write in the margin of any
website, as you would in a book you own. Your marks are there when you come back to the page, and
every website you have marked is listed under Highlights.

This repository holds the signed releases. The source is private.

## Download

The latest `ibid.dmg` is on the [Releases](https://github.com/fiachramacfadden/ibid-releases/releases/latest)
page. Open it and drag ibid to Applications. Installed copies update themselves.

Requires macOS 15.2 or later, on Apple silicon or Intel.

## What a developer might want to know

- About 3 MB to download and 7 MB installed. ibid is built on WebKit, the engine inside every
  Mac, so it ships only its own code and the updater.
- Written in Swift 6 with strict concurrency, SwiftUI and AppKit. Marks are drawn by one
  script running in an isolated content world, so pages can neither see nor forge them.
- Runs in the App Sandbox with the hardened runtime, signed with a Developer ID and notarised
  by Apple. The entitlements are the minimum a browser needs: network, downloads, files you
  pick, printing, and camera and microphone for sites that ask.
- Updates come through [Sparkle](https://sparkle-project.org). Each one is EdDSA-signed and
  the feed (`appcast.xml`) is published with every release, so you can inspect exactly what an
  installed copy will fetch.
- Everything you highlight and write is stored on your Mac, encrypted under a key in the
  Keychain. Nothing is collected and nothing is sent anywhere. The privacy manifest in the
  bundle says the same.

To check a download yourself:

    codesign -dv --verbose=2 /Applications/ibid.app
    spctl -a -vv -t exec /Applications/ibid.app
    codesign -d --entitlements - /Applications/ibid.app

## Problems

Something wrong? [Open an issue](https://github.com/fiachramacfadden/ibid-releases/issues/new)
or write to fiki@zhiyin.dev. Say which macOS you are on and which website, if one is involved.
