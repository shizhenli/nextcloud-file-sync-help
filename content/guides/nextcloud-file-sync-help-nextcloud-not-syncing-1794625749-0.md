---
title: "Nextcloud Not Syncing: Resolve a Stuck 'Waiting for Sync' Status"
description: "Troubleshoot a Nextcloud client stuck on 'Waiting for Sync' with step-by-step checks, exact result interpretation, a verification test, and recovery notes."
seo_title: "Nextcloud Not Syncing: Fix a Stuck 'Waiting for Sync' Status"
seo_description: "Troubleshoot a Nextcloud client stuck on 'Waiting for Sync' with step-by-step checks, exact result interpretation, a verification test, and recovery notes."
keywords:
  - "nextcloud not syncing"
date: 2026-11-14T11:11:53+08:00
publishDate: 2026-11-14T11:11:53+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

Your Nextcloud desktop client shows "Waiting for Sync" indefinitely and no files move, even though the network is up. Let's walk through a targeted fix for that specific stall.

## Check the client's sync status and conflict markers

Open the Nextcloud client window and look at the status line. If it says "Waiting for Sync" but the activity list is empty, the client is likely blocked by a local file conflict or a locked database. First, right-click the tray icon and choose **Pause sync**, wait five seconds, then **Resume sync**. If the status changes to "Syncing" and files begin transferring, the queue was temporarily stuck. If it returns to "Waiting for Sync" within a minute, continue below.

Next, inspect the local sync folder for files ending in `.sync-conflict` or `.~lock`. A single conflict file can halt the entire queue. Move any conflict files to a temporary folder outside the sync root, then restart the client. If the status changes to "Up to date" or "Syncing," the conflict was the blocker.

## Verify with a controlled test file

Create a small text file named `sync-test.txt` inside the local sync folder. Watch the client activity window for 30 seconds. If the file appears in the Nextcloud web interface, sync is working. If it does not appear and the status remains "Waiting for Sync," the client's local database is likely corrupted.

## Recovery and rollback

If the test file fails, quit Nextcloud completely, rename the local sync folder to `Nextcloud_old`, and restart the client to create a fresh folder. Do not delete the old folder until you confirm all files are present in the web interface. This is your rollback point: if anything is missing, restore from `Nextcloud_old`.

![Technician checking sync status on a laptop screen](/images/service-detail-960.webp "Checking sync status")

If the **nextcloud not syncing** issue persists after these steps, the server-side app password or background job may be at fault. [Ask for help](/#consult) and include your client log excerpt.
