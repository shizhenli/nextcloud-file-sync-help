---
title: "Nextcloud Sync Stuck at 99 Percent: Clear the Waiting for Sync State"
description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at waiting for sync with local files unsent. Step-by-step checks, verification, and recovery."
seo_title: "Nextcloud Sync Stuck at 99 Percent: Fix Waiting for Sync"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at waiting for sync with local files unsent. Step-by-step checks, verification, and recovery."
keywords:
  - "nextcloud sync stuck at 99 percent"
date: 2026-11-16T09:00:53+08:00
publishDate: 2026-11-16T09:00:53+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

## Understand the symptom

You are running a self-hosted Nextcloud server with the Windows desktop client, and the status stays at waiting for sync while local files remain unsent. This is a controlled pause, not a crash, so diagnose it in order.

## Check the client and server state

Open the desktop client and select the affected folder. Confirm the status line reads waiting for sync and note the number of pending files. If it shows zero pending but files are missing remotely, the client is idle rather than blocked. Next, open the server web interface and check that the target folder exists and accepts uploads. If the folder is read-only or missing, the client cannot proceed. Also verify free space on both the server volume and the Windows drive; a full disk stops the final write.

## Inspect logs for the blocking entry

In the client settings, open the log file and search for the last sync activity. Look for repeated retries, permission errors, or a single file name that never completes. If one file repeats, move it out of the sync folder and let the queue drain. This is often the cause of a **nextcloud sync stuck at 99 percent** state, where one final item holds the queue.

## Verification test

Create a small text file in the sync folder. Watch the client status change from waiting for sync to up to date within a minute. Then confirm the file appears in the server web interface. If it does, the queue is healthy.

## Rollback and recovery

If the test fails, pause syncing, rename the local sync folder as a backup, and set up a fresh sync to a new local folder. Do not delete the original until the new sync completes. For guided diagnosis,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
