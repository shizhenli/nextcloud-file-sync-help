---
title: "Nextcloud Desktop Client Stuck at 'Waiting for Sync' on Windows: A Practical Fix"
description: "Troubleshoot a self-hosted Nextcloud Windows desktop client that stays at 'waiting for sync' while local files remain unsent. Follow specific checks, a verification test, and recovery steps."
seo_title: "Nextcloud Not Syncing: Fix Desktop Client Stuck at 'Waiting for Sync'"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows desktop client that stays at 'waiting for sync' while local files remain unsent. Follow specific checks, a verification test, and recovery steps."
keywords:
  - "nextcloud not syncing"
date: 2026-11-23T08:00:58+08:00
publishDate: 2026-11-23T08:00:58+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are running a self-hosted Nextcloud server and the Windows desktop client stays at 'waiting for sync' while your local files remain unsent.

## Check the client's sync status and server connection

Open the desktop client window and look at the status line. If it says 'waiting for sync' indefinitely, first confirm the server is reachable: in the client settings, check the server URL and click the account name to see connection details. A green check means the client can talk to the server; a red or yellow icon means it cannot. Next, open the client's log file (Settings > Logs) and search for recent errors. If you see repeated 'connection refused' or timeout messages, the problem is network or server-side, not file-level.

## Verify local folder permissions and file locks

Right-click the local sync folder, choose Properties > Security, and confirm your Windows user has full control. Then check for files held open by another program: use Resource Monitor (resmon.exe) and look under the Disk tab for handles on files inside the sync folder. Close any program locking those files. If the client still waits, pause sync, rename the local sync folder, and let the client recreate it, then move files back in small batches.

## Run a verification test

Create a small test file in the sync folder. Watch the client status for two minutes. If it changes to 'syncing' and then 'up to date', the original blockage was a locked or permission-denied file. If it stays at 'waiting for sync', the issue is server-side or account-level.

## Rollback and recovery

If renaming the folder caused problems, restore the original folder name and re-enable sync. Before making changes, export the client log for reference. For persistent **nextcloud not syncing** cases,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the log attached.
