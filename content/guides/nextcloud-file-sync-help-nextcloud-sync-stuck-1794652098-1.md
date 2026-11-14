---
title: "Nextcloud Desktop Client Stuck at 'Waiting for Sync' on Windows: A Controlled Diagnosis"
description: "Troubleshoot a self-hosted Nextcloud Windows desktop client that stays at 'waiting for sync' while local files remain unsent. Follow these controlled checks to restore sync."
seo_title: "Fix Nextcloud Sync Stuck at 'Waiting for Sync' on Windows"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows desktop client that stays at 'waiting for sync' while local files remain unsent. Follow these controlled checks to restore sync."
keywords:
  - "nextcloud sync stuck"
date: 2026-11-14T19:21:33+08:00
publishDate: 2026-11-14T19:21:33+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're running a self-hosted Nextcloud server and the Windows desktop client stays at 'waiting for sync' while local files remain unsent. This is a **nextcloud sync stuck** state that needs a controlled diagnosis before you change anything.

## Check the client's sync engine status

Open the Nextcloud desktop client, click the account icon, and select 'Recent activity'. Look for repeated 'waiting' entries or errors. If you see a specific file name stuck in the queue, note it. A blank activity log with no progress usually points to a paused sync or a locked database.

Next, check the client's log file. On Windows, open File Explorer and go to `%LOCALAPPDATA%\Nextcloud\logs`. Open the most recent log and search for 'sync paused', 'database is locked', or 'connection refused'. If you find 'database is locked', the client's local database is busy; if you find 'connection refused', the client cannot reach your server.

## Verify server reachability and account state

In a browser on the same Windows machine, open your Nextcloud web interface and log in. If the web interface loads, the server is reachable. Then, in the desktop client, right-click the account and choose 'Open folder'. Confirm the local sync folder exists and is not on a disconnected network drive.

## Verification test

Create a small text file in the local sync folder. Watch the client's activity window for two minutes. If the file uploads and the status changes from 'waiting' to 'up to date', sync is restored. If it remains at 'waiting', the issue is likely the client's local database or a paused sync state.

## Rollback and recovery

Before making changes, back up the client's configuration folder at `%APPDATA%\Nextcloud`. If a restart or re-login does not resolve the stuck state, you can restore this backup to return to the previous client state. For guided recovery,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
