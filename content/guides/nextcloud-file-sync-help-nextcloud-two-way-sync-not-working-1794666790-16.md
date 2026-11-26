---
title: "Nextcloud Two-Way Sync Not Working: When Conflict Files Appear Instead of Merging"
description: "Troubleshoot Nextcloud two-way sync creating conflict files instead of merging edits. Step-by-step checks for self-hosted Nextcloud with Windows desktop client."
seo_title: "Nextcloud Two-Way Sync Not Working: Fix Conflict File Creation"
seo_description: "Troubleshoot Nextcloud two-way sync creating conflict files instead of merging edits. Step-by-step checks for self-hosted Nextcloud with Windows desktop client."
keywords:
  - "nextcloud two way sync not working"
date: 2026-11-26T10:00:06+08:00
publishDate: 2026-11-26T10:00:06+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You have edited the same file on two devices, and instead of merging, the Nextcloud Windows client keeps generating conflict copies.

## Check the client's conflict log

Open the Nextcloud desktop client, click the activity icon, and filter for conflicts. Note the exact filenames and timestamps. If conflicts appear for files you did not edit on both sides, the client may be misreading modification times. Compare the file's local modified time with the server's last-modified timestamp in the web interface. A mismatch of more than a few minutes suggests clock drift or a stale sync database.

## Verify the sync database state

Pause sync, then inspect the client's log file (typically in %APPDATA%\Nextcloud\logs). Look for lines containing "conflict" or "etag mismatch." If the log shows repeated etag changes without corresponding local edits, the server may be updating metadata unexpectedly. In that case, run a controlled test: create a small text file on the server only, let it sync down, then edit it locally only and sync up. If a conflict appears, the client's file watcher is likely triggering false positives.

## Reset the sync pair safely

Before resetting, back up any conflict files you want to keep. Remove the folder from the client's sync list, then re-add it. Choose to keep local files when prompted. This rebuilds the sync database without deleting data. After re-sync, repeat the controlled test above. If conflicts persist, the issue is server-side; check for external file modifications or cron jobs altering files.

## Recovery note

If you already have conflict copies, open both versions and manually merge the intended content, then delete the conflict file. Do not delete the original until you confirm the merged version is correct.

If these steps do not resolve your **nextcloud two way sync not working** issue,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your client log and conflict filenames.
