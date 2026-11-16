---
title: "Nextcloud Two-Way Sync Creates Conflict Files Instead of Merging: A Controlled Fix"
description: "Fix Nextcloud two-way sync creating conflict files instead of merging edits. Step-by-step checks, verification test, and recovery note for Windows desktop client."
seo_title: "Nextcloud File Conflict Resolution: Stop Conflict Copies During Two-Way Sync"
seo_description: "Fix Nextcloud two-way sync creating conflict files instead of merging edits. Step-by-step checks, verification test, and recovery note for Windows desktop client."
keywords:
  - "nextcloud file conflict resolution"
date: 2026-11-16T11:00:55+08:00
publishDate: 2026-11-16T11:00:55+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You edited the same file on your Windows PC and on the Nextcloud web interface, and now the desktop client keeps producing conflict copies instead of keeping the version you intended.

## Confirm the conflict is real, not a display lag
Open the local sync folder and look for files ending in `conflicted copy`. In the Nextcloud web interface, open the same folder and check the modification times on both versions. If the timestamps differ by more than a few seconds, both sides genuinely contain edits. If they are identical, the client may simply be re-scanning; wait two minutes and refresh before changing anything.

## Check the sync journal and server clock
Right-click the Nextcloud tray icon, choose Settings, then the Activity tab. A conflict entry should name the file and both timestamps. Next, compare your PC clock with the server time shown in the web interface footer. A drift of more than one minute causes the client to treat older edits as newer. Enable automatic time sync on Windows and restart the client.

## Verify with a controlled test file
Create a small text file named `sync-test.txt` in a synced folder. Edit it locally, wait for the green check, then edit the same file in the web interface within one minute. Watch the Activity tab. If a conflict copy appears again, the two-way sync is still racing; if the file updates cleanly, your **nextcloud file conflict resolution** issue is limited to the original file's history.

## Recover the intended version
Before deleting any conflict copy, open both files and copy the correct paragraphs into one. Rename the losing copy with a `.bak` suffix and keep it for one week. If you overwrite the wrong version, restore it from the Files version history in the web interface.

If conflicts persist after these checks,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your client log and both timestamps.
