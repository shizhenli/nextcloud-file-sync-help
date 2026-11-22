---
title: "Nextcloud Two-Way Sync Not Working: Resolve Conflict Files Instead of Merging"
description: "Troubleshoot Nextcloud two-way sync creating conflict files instead of merging edits. Step-by-step checks for Windows desktop client, verification test, and recovery."
seo_title: "Nextcloud Two-Way Sync Not Working? Fix Conflict Files on Windows"
seo_description: "Troubleshoot Nextcloud two-way sync creating conflict files instead of merging edits. Step-by-step checks for Windows desktop client, verification test, and recovery."
keywords:
  - "nextcloud two way sync not working"
date: 2026-11-22T08:01:00+08:00
publishDate: 2026-11-22T08:01:00+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You have edited the same file on two devices, and the Nextcloud Windows client keeps creating conflict copies instead of merging your changes.

## Check the conflict detection settings

Open the Nextcloud desktop client, go to Settings > General, and verify that "Use conflict detection" is enabled. If it is off, the client may overwrite or duplicate files unpredictably. Also confirm the sync folder is not set to "Upload only" or "Download only"—two-way sync requires the default "Sync everything" mode. After changing any setting, pause and resume sync.

## Inspect file timestamps and server clock

Conflict files appear when the client cannot determine which version is newer. On Windows, right-click the conflicted file, choose Properties, and note the modified time. Compare it with the server's time via the Nextcloud web interface. If the server clock is off by more than a few minutes, the client may treat both edits as simultaneous. Ask your server administrator to enable NTP time sync.

## Verify with a controlled test

Create a new text file in the sync folder, let it sync, then edit it on the server and on Windows within the same minute. If a conflict file appears, the client is not merging—this confirms **nextcloud two way sync not working** as a timing or lock issue. If no conflict appears, the original problem was likely a one-time race condition.

## Rollback and recovery

Before deleting any conflict file, open both versions and copy the intended text into the main file. Then delete the conflict copy. If you are unsure which version is correct, restore the file from the Nextcloud web interface's version history. For persistent cases,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
