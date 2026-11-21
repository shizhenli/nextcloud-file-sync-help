---
title: "Nextcloud Client Waiting for Sync: A Controlled Diagnosis for Windows"
description: "Troubleshoot a self-hosted Nextcloud Windows desktop client that stays at 'waiting for sync' while local files remain unsent. Follow these checks and a verification test."
seo_title: "Fix Nextcloud Client Stuck at 'Waiting for Sync' on Windows"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows desktop client that stays at 'waiting for sync' while local files remain unsent. Follow these checks and a verification test."
keywords:
  - "nextcloud client waiting for sync"
date: 2026-11-21T14:43:13+08:00
publishDate: 2026-11-21T14:43:13+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are running a self-hosted Nextcloud server and the Windows desktop client is stuck at 'waiting for sync' while your local files remain unsent.

## Check the client status and logs

Open the Nextcloud desktop client window. Look at the status line: if it says 'waiting for sync' without a progress bar or file count, the client is not actively transferring. Next, open the client's log file (Settings > Logs, or the log file in %APPDATA%\Nextcloud). Search for recent lines containing 'sync' or 'error'. If you see repeated connection timeouts or 'CSync failed' messages, the client cannot reach the server. If the log shows no activity at all, the sync engine may be paused.

## Verify server reachability and account state

In a browser on the same machine, open your Nextcloud server URL. If the page loads, the server is reachable. If it times out, check your network or server status first. Then, in the client, right-click the account and choose 'Pause sync' then 'Resume sync'. If the status changes to 'syncing' or shows a file count, the pause was the cause. If it stays at **nextcloud client waiting for sync**, proceed to the verification test.

## Verification test

Create a small test file in your local sync folder. Watch the client status for 30 seconds. If the file appears on the server (check via the web interface), sync is working. If the file remains local and the status does not change, the sync engine is still blocked.

## Rollback and recovery

If the test file does not sync, remove the test file. Then, in the client settings, remove the account and re-add it using the same local folder. This resets the sync database without deleting your files. If the problem persists,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your log excerpt.
