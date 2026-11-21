---
title: "Nextcloud Folder Not Syncing on Windows: Clear the 'Waiting for Sync' Stall"
description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at 'waiting for sync' with local files unsent. Step-by-step checks, verification, and rollback."
seo_title: "Fix Nextcloud Folder Not Syncing on Windows (Waiting for Sync)"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at 'waiting for sync' with local files unsent. Step-by-step checks, verification, and rollback."
keywords:
  - "nextcloud folder not syncing windows"
date: 2026-11-21T14:46:28+08:00
publishDate: 2026-11-21T14:46:28+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're running a self-hosted Nextcloud server and the Windows desktop client sits at 'waiting for sync' while local files remain unsent, and you want a controlled way to clear that stall.

## Check the sync engine state first

Open the client, click the account, and look at the activity list. If it shows only 'waiting for sync' with no file names moving, the engine is idle rather than transferring. Next, right-click the tray icon and choose Quit, then relaunch the client. Watch the status for 60 seconds. If it returns to 'waiting for sync' without uploading, the queue is blocked, not slow.

## Inspect the local folder and server reachability

Confirm the folder is inside a synced root and not excluded by a selective-sync checkbox. In the client settings, open the account's folder list and verify the checkbox is ticked. Then open a browser on the same PC and load your Nextcloud URL. If the page loads, the server is reachable; if it times out, fix connectivity before touching the client. Also check that the folder name has no trailing space or reserved Windows characters, which silently block uploads.

## Verification test

Create a small text file inside the affected folder. Wait two minutes. If the client still shows 'waiting for sync' and the file has no green check, the queue is confirmed stuck. Remove the test file afterward.

## Recovery and rollback

If the stall persists, pause sync, rename the local folder, and let the client recreate it, then copy files back in small batches. Keep the renamed folder until sync completes so you can roll back. For a persistent **nextcloud folder not syncing windows** issue,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) before deleting any local data.
