---
title: "Nextcloud Two-Way Sync Not Working: Resolve Conflict File Creation"
description: "Troubleshoot Nextcloud two-way sync not working when conflict files appear instead of merging. Follow checks, interpret results, and verify with a test."
seo_title: "Nextcloud Two-Way Sync Not Working? Fix Conflict Files"
seo_description: "Troubleshoot Nextcloud two-way sync not working when conflict files appear instead of merging. Follow checks, interpret results, and verify with a test."
keywords:
  - "nextcloud two way sync not working"
date: 2026-11-17T11:00:56+08:00
publishDate: 2026-11-17T11:00:56+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You have edited files on both your Windows PC and the Nextcloud server, and now the desktop client keeps creating conflict copies instead of merging your intended version.

## Check the conflict source

Open the client's activity log and locate the conflict file. Its name includes the device name and timestamp. Compare the conflict copy with the original to see which side changed first. If the conflict copy contains the version you want, rename it to replace the original and delete the unwanted file. Then right-click the sync folder and choose 'Force sync now'.

## Verify file timestamps and clock

On Windows, check the modified time of both the local file and its server counterpart in the Nextcloud web interface. A difference of more than a few seconds can trigger conflict creation. Also confirm your PC clock is accurate: open Settings > Time & Language and enable 'Set time automatically'. If the server clock is off, ask your administrator to correct it. After fixing the clock, restart the client.

## Test with a controlled file

Create a small text file in the sync folder. Edit it on the server, wait for sync, then edit it locally without touching the server copy. The client should sync without a conflict. If a conflict still appears, the issue is likely a stale sync database. Pause sync, rename the local sync folder, and set up the account again to rebuild the database. This is your rollback point: keep the renamed folder until the new sync completes.

If **nextcloud two way sync not working** persists after these steps, the conflict may stem from server-side file locking or versioning rules.

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your client log and the conflict filename for a focused review.
