---
title: "Nextcloud Conflict Files: Why Both Sides Get Edited and How to Regain Control"
description: "Stop Nextcloud from creating conflict copies when both sides have edits. Follow these checks to diagnose and restore expected two-way sync behavior."
seo_title: "Fix Nextcloud Conflict Files on Windows Desktop Client"
seo_description: "Stop Nextcloud from creating conflict copies when both sides have edits. Follow these checks to diagnose and restore expected two-way sync behavior."
keywords:
  - "nextcloud conflict files"
date: 2026-11-21T14:40:13+08:00
publishDate: 2026-11-21T14:40:13+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You edited a file on your Windows PC while a colleague changed the same file on the server, and now Nextcloud keeps producing conflict copies instead of merging your intended version.

## Confirm the conflict pattern

Open the affected folder in File Explorer and look for files ending in `conflicted copy`. Note the timestamp in each name. Then open the Nextcloud desktop client, click the activity icon, and filter by the file name. If the log shows two uploads with overlapping modification times, the client is correctly detecting simultaneous edits rather than failing to merge. That distinction matters: conflict files are a safety feature, not a sync error.

## Check clock and version state

On the Windows machine, run `w32tm /query /status` in Command Prompt. If the offset exceeds a few seconds, resync the clock with `w32tm /resync`. Nextcloud compares modification times, so a drifting clock makes ordinary edits look simultaneous. Next, open the file's version history in the Nextcloud web interface. If the server holds a version newer than your local copy, the client has no safe merge path and will keep generating **nextcloud conflict files** until one side is reconciled.

## Verification test

Create a small test document in a synced folder. Edit it on the PC, wait for the green check, then edit the same file in the web interface and save. Wait for sync. A single conflict copy should appear, confirming detection works. Now resolve it by keeping the intended version and deleting the copy, then edit again from one side only. No new conflict file should appear.

## Recovery note

Before deleting any conflict copy, move it to a local backup folder. If you resolve the wrong version, restore from the server's version history or your backup. For hands-on diagnosis,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
