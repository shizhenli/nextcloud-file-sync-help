---
title: "Nextcloud Conflict Files: Why They Appear and How to Resolve Them"
description: "Learn why Nextcloud creates conflict files during two-way sync on Windows and follow a controlled diagnosis to resolve them without losing edits."
seo_title: "Nextcloud Conflict Files: Fix Two-Way Sync Conflicts on Windows"
seo_description: "Learn why Nextcloud creates conflict files during two-way sync on Windows and follow a controlled diagnosis to resolve them without losing edits."
keywords:
  - "nextcloud conflict files"
date: 2026-11-14T19:21:33+08:00
publishDate: 2026-11-14T19:21:33+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You edited a file on your Windows PC while a colleague edited the same file on the server, and now Nextcloud has created a conflict copy instead of merging your intended version.

## Confirm the conflict pattern

Open the affected folder in File Explorer and look for filenames containing "conflicted copy" plus a timestamp and device name. Check the server side in the Nextcloud web interface for the same file. If both the original and the conflict copy contain recent edits, the client detected overlapping changes and preserved both rather than overwriting either. That is expected behavior, not a sync failure.

## Check the sync log and file timestamps

Right-click the Nextcloud tray icon, open Settings, then the Activity tab. Filter for the affected filename. A conflict entry means the client saw a local modification and a remote modification after the last common sync point. Compare the modified time of the local file with the server version shown in the web interface. If the local timestamp is later than the last successful sync and the server timestamp is also later, the conflict is legitimate.

## Verification test

Create a small test file in a synced folder. Edit it on the server, wait for the client to show a green check, then edit the same file locally before the next sync cycle completes. A conflict copy should appear within one sync interval. If it does, conflict detection is working correctly and your original issue was a timing overlap, not a broken client.

## Resolve and recover

Compare both versions, keep the intended content in the original filename, and delete the conflict copy. If you are unsure which edit to keep, copy both files to a backup folder before deleting anything. For persistent or unclear conflicts,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) before removing files. Remember that **nextcloud conflict files** are safety copies, so recover from them rather than assuming data loss.
