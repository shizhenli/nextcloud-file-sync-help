---
title: "Nextcloud Folder Not Syncing on Windows: Resolve a Stuck 'Waiting for Sync' State"
description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at 'waiting for sync' with local files unsent. Follow checks, interpret results, and verify sync recovery."
seo_title: "Nextcloud Folder Not Syncing Windows: Fix Stuck 'Waiting for Sync'"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at 'waiting for sync' with local files unsent. Follow checks, interpret results, and verify sync recovery."
keywords:
  - "nextcloud folder not syncing windows"
date: 2026-11-17T08:01:53+08:00
publishDate: 2026-11-17T08:01:53+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

## Troubleshooting

Your Windows desktop client shows 'waiting for sync' and local files in a folder remain unsent, so you need to confirm whether the client is paused, blocked by a file, or unable to reach the server. Start by opening the Nextcloud client window and checking the account status line. If it says paused or offline, resume or reconnect and watch for the status to change to syncing within one minute. Next, right-click the affected folder and confirm it is not excluded from sync; if it is, remove the exclusion and let the client rescan. Open the client's activity log and look for repeated errors on a specific file. A single locked or oversized file can hold the queue, so close any program using it and retry. If the log shows connection errors, test the server URL in a browser on the same PC; a login page means the client credentials need re-entering, while a timeout points to network or server availability. To verify recovery, create a small test text file inside the folder and confirm it appears on the server web interface within two minutes. If it does, the queue is moving. If the client still stalls, pause sync, remove and re-add the folder connection, then resume; this is your rollback step and does not delete local files. For persistent cases of **nextcloud folder not syncing windows**, collect the client log timestamp and

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).

Repeat the same check after a restart and confirm the result twice.
