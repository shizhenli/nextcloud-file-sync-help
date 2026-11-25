---
title: "Nextcloud File Conflict Resolution: When Both Sides Have Edits and Conflict Copies Appear"
description: "Stop Nextcloud from creating conflict copies when both sides have edits. Follow these checks to complete a controlled diagnosis and restore two-way sync."
seo_title: "Nextcloud File Conflict Resolution: Fix Conflict Copies on Windows"
seo_description: "Stop Nextcloud from creating conflict copies when both sides have edits. Follow these checks to complete a controlled diagnosis and restore two-way sync."
keywords:
  - "nextcloud file conflict resolution"
date: 2026-11-25T10:00:54+08:00
publishDate: 2026-11-25T10:00:54+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You edited a file on your Windows PC while someone else changed the same file on the server, and now Nextcloud keeps producing conflict copies instead of merging the intended version.

## Check the conflict file names and timestamps
Open the folder in File Explorer and look for files ending in "conflicted copy." Compare the timestamp embedded in each name with the modified date of the original file. If the conflict copy is newer than the original, the client is preserving both edits rather than overwriting one. That is expected behavior, not a bug.

## Confirm the sync state before touching anything
Right-click the Nextcloud tray icon and open the activity window. If the file shows a green check, the conflict copy is already uploaded and safe to reconcile. If it shows a spinning icon or "waiting," let it finish; resolving early can create a second conflict.

## Verify which version is intended
Open both the original and the conflict copy side by side. The conflict copy contains the edits from the side that lost the race. Decide which content you want to keep, then copy the needed text into the original and delete the conflict copy. This is the core of **nextcloud file conflict resolution**: reconcile manually, then let the client sync the single clean file.

## Run a verification test
Create a small test file on the PC, wait for the green check, then edit the same file from the Nextcloud web interface and save. Return to the PC and confirm the client downloads the server version without generating a new conflict copy. A clean download confirms two-way sync is healthy again.

## Rollback note
Before deleting any conflict copy, move it to a local backup folder outside the sync root. If you later discover the wrong version was kept, restore that copy and repeat the reconciliation.

If conflicts persist after these checks,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
