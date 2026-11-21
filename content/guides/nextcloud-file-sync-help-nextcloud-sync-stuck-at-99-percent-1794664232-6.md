---
title: "Nextcloud Sync Stuck at 99 Percent: Resolve the 'Waiting for Sync' State on Windows"
description: "Troubleshoot a self-hosted Nextcloud Windows desktop client that stays at 'waiting for sync' with local files unsent. Step-by-step checks and verification."
seo_title: "Nextcloud Sync Stuck at 99 Percent: Fix 'Waiting for Sync' on Windows"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows desktop client that stays at 'waiting for sync' with local files unsent. Step-by-step checks and verification."
keywords:
  - "nextcloud sync stuck at 99 percent"
date: 2026-11-21T14:43:13+08:00
publishDate: 2026-11-21T14:43:13+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are running a self-hosted Nextcloud server with the Windows desktop client, and the status remains at waiting for sync while local files sit unsent. This article walks through a controlled diagnosis for that exact state.

## Check the client's sync status and logs
Open the Nextcloud desktop client and click the status icon. If it shows waiting for sync, note the last activity timestamp. Then open the client's log file (Settings > Logs) and search for recent entries around that time. Look for repeated retries, HTTP 423 (locked), or 507 (insufficient storage) errors. If you see a specific file name repeating, that file is likely blocking the queue. If the log shows no activity after the timestamp, the sync engine may be paused or waiting on a network timeout.

## Verify server-side locks and storage
On the server, check the Nextcloud admin panel for any locked files under Settings > Administration > File locking. A stale lock on a large file can hold the queue at the final step. Also confirm available disk space and that the user account has not exceeded its quota. If a lock exists for a file you recognize, release it. If quota is full, free space or raise the limit.

## Reset the client's sync state safely
Before making changes, back up the local sync folder. Then in the client, remove the account and re-add it without deleting local data. This forces a fresh sync state. If the problem persists, rename the client's database file (typically in %APPDATA%\Nextcloud) to .old and restart the client; it will rebuild the database. This is your rollback point: if sync behaves worse, restore the renamed database and restart.

## Verification test
Create a small test file in the sync folder and watch the client status. It should change from waiting for sync to up to date within a minute. If it does, the original blockage is cleared. If the client again shows **nextcloud sync stuck at 99 percent**, collect fresh logs and

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
