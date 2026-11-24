---
title: "Two-Way Sync Creates Conflict Files: Run a Controlled Test Before You Merge"
description: "Both sides of a self-hosted Nextcloud folder have edits and the Windows client creates conflict copies instead of merging. Run a controlled two-way sync test to confirm the client is behaving as designed."
seo_title: "Nextcloud Two Way Sync Test: Diagnose Conflict Copies on Windows"
seo_description: "Both sides of a self-hosted Nextcloud folder have edits and the Windows client creates conflict copies instead of merging. Run a controlled two-way sync test to confirm the client is behaving as designed."
keywords:
  - "nextcloud two way sync test"
date: 2026-11-24T10:00:54+08:00
publishDate: 2026-11-24T10:00:54+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You edited a file on your Windows PC while a colleague edited the same file on the server, and now the desktop client has dropped a conflict copy beside it instead of keeping the version you intended.

## Confirm what the client actually did

Before changing anything, open the folder in File Explorer and look for files named like `Report (conflicted copy 2024-06-12).docx`. If a conflict copy exists, the client detected overlapping changes and preserved both versions; that is expected behavior, not a sync failure. Next, open the Nextcloud desktop client, click the activity icon, and read the most recent log entries for that path. A line such as `Conflict while uploading` or `ETag mismatch` confirms the server saw a different version than the one the client based its edit on. If instead you see repeated `Waiting for sync`, the issue is connectivity, not conflict handling.

## Run the verification test

Create a small text file in a test folder and let it sync fully. Edit it on the server through the web interface, save, then edit the same file locally before the client pulls the server change. Watch the client activity window. A successful **nextcloud two way sync test** ends with a conflict copy appearing and both versions intact. If no conflict copy appears and one edit silently disappears, stop and check the server log for overwrite warnings before trusting the folder.

## Recover and roll back

Keep the conflict copy until you have compared both versions. Rename the intended file, delete the unwanted copy, and let the client sync the result. If you need the earlier state, restore it from the server's file versions panel rather than re-editing blindly.

If the test still produces unexpected results,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the activity log excerpt and file names.
