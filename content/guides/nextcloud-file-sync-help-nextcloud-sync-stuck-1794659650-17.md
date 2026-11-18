---
title: "Nextcloud Sync Stuck on Windows: Fix the 'Waiting for Sync' State"
description: "Troubleshoot a self-hosted Nextcloud Windows client that stays at 'waiting for sync' with unsent local files. Follow these checks to restore syncing."
seo_title: "Nextcloud Sync Stuck: Resolve 'Waiting for Sync' on Windows"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows client that stays at 'waiting for sync' with unsent local files. Follow these checks to restore syncing."
keywords:
  - "nextcloud sync stuck"
date: 2026-11-18T12:01:32+08:00
publishDate: 2026-11-18T12:01:32+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

Your self-hosted Nextcloud Windows client stays at 'waiting for sync' while local files remain unsent, and you want to get it moving again without guesswork.

## Check the client's sync status and logs

Open the Nextcloud desktop client and click the activity icon. If the status still reads 'waiting for sync', open the client's log file (usually in %APPDATA%\Nextcloud\logs). Look for repeated lines such as 'sync engine waiting' or 'requesting lock'. If you see 'requesting lock' for more than a minute, the client is likely blocked by a server-side lock or a local file lock. If the log shows no new entries, the sync engine may have stalled internally.

## Verify server reachability and account state

In the client, open Settings > Account. Confirm the server URL responds and the account shows as connected. Then, in a browser, log in to your Nextcloud instance and check Settings > Security for any session or app-password warnings. If the account is connected but the client still waits, the issue is local to the sync engine, not the network.

## Run a controlled verification test

Create a small test file named sync-test.txt in your local sync folder. Watch the client for two minutes. If the file uploads, the original blockage was transient; if it stays unsent, proceed to recovery. This test tells you whether the queue is fully stuck or only specific files are blocked.

## Recovery and rollback

Before changing anything, copy the client's log file and note your sync folder path. In the client, pause sync, then resume it. If that fails, remove the account and re-add it, pointing to the same local folder. Do not delete local files. If the problem persists, this is a **nextcloud sync stuck** condition that may need server-side lock inspection. For guided help,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
