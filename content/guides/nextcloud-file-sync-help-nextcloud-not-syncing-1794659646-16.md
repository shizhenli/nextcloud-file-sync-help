---
title: "Nextcloud Client Stuck at 'Waiting for Sync' on Windows: Fix Local Files Not Sending"
description: "Practical fix for a self-hosted Nextcloud Windows desktop client stuck at 'waiting for sync' with local files unsent. Check status, permissions, and logs, then verify."
seo_title: "Nextcloud Not Syncing: Fix Windows Client Stuck at Waiting for Sync"
seo_description: "Practical fix for a self-hosted Nextcloud Windows desktop client stuck at 'waiting for sync' with local files unsent. Check status, permissions, and logs, then verify."
keywords:
  - "nextcloud not syncing"
date: 2026-11-18T11:03:38+08:00
publishDate: 2026-11-18T11:03:38+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

## Check the client's actual state

You are self-hosting Nextcloud and the Windows desktop client sits at waiting for sync while local files remain unsent. First, open the client's activity window and read the status line instead of guessing. If it says waiting for sync with no active transfers, the client believes it has nothing to do or is blocked before transfer. Next, confirm the local folder is not read-only: right-click the folder, choose Properties, and verify the Read-only attribute is cleared. A read-only folder produces exactly this silent wait.

## Inspect server reachability and account state

Open a browser on the same machine and load your Nextcloud URL. If the page fails, the client cannot sync either; fix DNS, TLS, or the reverse proxy first. If the page loads, open the client's account settings and confirm the account shows connected, not paused. Then check the sync log: in the client settings, open the log file location and look for the last lines mentioning the target folder. A permission denied or 403 entry means the server account lacks write access to that folder; correct the share permissions in Nextcloud and restart the client.

## Verification test

Create a small text file inside the synced folder. Watch the activity window for an upload entry within one minute. Then open the Nextcloud web interface and confirm the file appears. If it does, sync is restored. If the client returns to waiting for sync, delete the test file and proceed to recovery.

## Rollback and recovery

Before changing anything, copy the client log file to a safe location. If a configuration change makes things worse, remove and re-add the account in the client without deleting local data, then let it rescan. If the issue persists,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the log excerpt. For persistent **nextcloud not syncing** cases, include the exact status line and the last log entry so support can isolate the block.
