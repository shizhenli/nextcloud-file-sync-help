---
title: "Nextcloud Two-Way Sync Test: When Conflict Files Appear Instead of Merging"
description: "Both sides have edits and Nextcloud creates conflict copies instead of merging. Run a controlled two-way sync test to confirm the cause and restore expected behavior."
seo_title: "Nextcloud Two Way Sync Test: Fix Conflict Files Instead of Merging"
seo_description: "Both sides have edits and Nextcloud creates conflict copies instead of merging. Run a controlled two-way sync test to confirm the cause and restore expected behavior."
keywords:
  - "nextcloud two way sync test"
date: 2026-11-15T18:40:26+08:00
publishDate: 2026-11-15T18:40:26+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You edited a file on your Windows PC and another user edited the same file on the server, and now the desktop client keeps producing conflict copies instead of keeping the intended version.

## Check the conflict pattern first

Open the folder in File Explorer and look at the conflict files. If each conflict copy contains only one side's edits, the client is doing its job: it cannot merge overlapping changes, so it preserves both. That is expected behavior, not a sync failure. If the conflict copies are empty or identical to the original, the client may be misreading timestamps or the file may be locked by another program.

## Run a controlled two-way sync test

Create a small test folder and a plain text file inside it. Let it sync fully. Then edit the file on the PC, wait for the green check, edit the same line on the server, and wait for the client to detect the change. This **nextcloud two way sync test** shows whether the client reports a conflict only when edits truly overlap. If it conflicts on non-overlapping edits, check the client log for timestamp or ETag warnings and confirm the server clock is correct.

## Verify and recover

After the test, open the conflict file and compare line by line. Merge the intended content manually, save, and let it sync. Delete the conflict copy only after confirming the merged file is correct. If you need the previous state, restore the file from the server's version history before deleting anything.

If conflicts persist on non-overlapping edits,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the client log and the test folder details.
