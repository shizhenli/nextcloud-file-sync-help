---
title: "Nextcloud Client Stuck on 'Waiting for Sync'? Here's How to Diagnose It"
description: "Troubleshoot a Windows Nextcloud desktop client stuck at 'waiting for sync' with local files unsent. Step-by-step checks, verification, and recovery."
seo_title: "Fix Nextcloud Not Syncing: Stuck on 'Waiting for Sync'"
seo_description: "Troubleshoot a Windows Nextcloud desktop client stuck at 'waiting for sync' with local files unsent. Step-by-step checks, verification, and recovery."
keywords:
  - "nextcloud not syncing"
date: 2026-11-14T19:21:33+08:00
publishDate: 2026-11-14T19:21:33+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're running a self-hosted Nextcloud server and the Windows desktop client sits at 'waiting for sync' while your local files remain unsent.

## Check the client's connection and activity

Open the Nextcloud desktop client and click the status icon. If it says 'waiting for sync' with no progress, the client may be unable to reach the server or is blocked by a local conflict. First, confirm the server is reachable: open a browser and log in to your Nextcloud web interface. If the web interface loads, the server is up. Next, in the client, go to Settings > General and check the server URL. A typo or an expired certificate will stall sync silently. If the URL is correct, click 'Check connection' if available; a failure here points to network or certificate issues.

## Inspect the sync folder and logs

Right-click the client tray icon and choose 'Open folder' to confirm the sync folder exists and is accessible. Then open the client's log file (Settings > General > 'Open log file'). Search for 'error' or 'timeout'. A common cause is a file locked by another program or a path exceeding Windows limits. Close any program using the files, then pause and resume sync from the tray menu. If the log shows repeated connection errors, restart the client service via Task Manager.

## Verification test

Create a small text file in the sync folder. Watch the client status for two minutes. If it changes to 'syncing' and then 'up to date', the issue is resolved. If it stays at 'waiting for sync', the problem persists.

## Rollback and recovery

If changes make things worse, remove the sync folder from the client (not from disk) and re-add it. This forces a fresh sync without deleting local files. For persistent **nextcloud not syncing** issues,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
