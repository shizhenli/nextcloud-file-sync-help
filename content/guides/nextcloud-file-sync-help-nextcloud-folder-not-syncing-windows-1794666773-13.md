---
title: "Nextcloud Folder Not Syncing on Windows: Fix the Stuck 'Waiting for Sync' Status"
description: "Self-hosted Nextcloud Windows client stuck at 'waiting for sync'? Follow these controlled checks to diagnose and restore folder sync."
seo_title: "Nextcloud Folder Not Syncing Windows: Resolve 'Waiting for Sync'"
seo_description: "Self-hosted Nextcloud Windows client stuck at 'waiting for sync'? Follow these controlled checks to diagnose and restore folder sync."
keywords:
  - "nextcloud folder not syncing windows"
date: 2026-11-25T12:00:59+08:00
publishDate: 2026-11-25T12:00:59+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are running a self-hosted Nextcloud server with the Windows desktop client, and the client stays at 'waiting for sync' while local files remain unsent. This article walks through a controlled diagnosis for that specific stuck state.

## Check the client's sync status details

Open the Nextcloud desktop client and click the system tray icon. Select the affected folder and look at the status message. If it says 'waiting for sync' without a progress bar or file count, the client is not receiving a sync instruction. Next, open the client's log file (Settings > Logs) and search for 'sync' or 'error' near the latest timestamp. A repeated 'waiting' entry with no file activity confirms the client is stalled before upload.

## Verify server connectivity and folder permissions

From the same Windows machine, open a browser and log in to your Nextcloud web interface. Navigate to the target folder and confirm you can upload a small test file manually. If the upload fails, the issue is server-side (permissions or storage). If it succeeds, return to the desktop client, right-click the folder, and choose 'Force sync now'. Watch for any change in status. A brief 'syncing' message followed by 'waiting' again suggests a local client cache problem.

## Reset the local sync database

Close the Nextcloud client completely. In File Explorer, navigate to %APPDATA%\Nextcloud and rename the folder 'sync.db' to 'sync.db.old'. Restart the client. It will rebuild the database and attempt a fresh sync. This is your rollback point: if the client behaves worse, close it, delete the new sync.db, and rename sync.db.old back to sync.db.

## Verification test

Create a new text file inside the affected local folder. Within 30 seconds, check the client tray icon: it should show 'syncing' then 'up to date'. Confirm the file appears in the web interface. If the client still shows 'waiting for sync', the problem is likely a **nextcloud folder not syncing windows** conflict between client version and server. For guided assistance,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
