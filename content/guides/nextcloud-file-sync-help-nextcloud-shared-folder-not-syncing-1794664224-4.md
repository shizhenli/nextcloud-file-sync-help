---
title: "Nextcloud Shared Folder Not Syncing: Fix a Stuck 'Waiting for Sync' on Windows"
description: "Troubleshoot a Windows Nextcloud client stuck at 'waiting for sync' when a shared folder won't upload. Step-by-step checks, verification test, and recovery note."
seo_title: "Nextcloud Shared Folder Not Syncing: Fix Stuck 'Waiting for Sync' on Windows"
seo_description: "Troubleshoot a Windows Nextcloud client stuck at 'waiting for sync' when a shared folder won't upload. Step-by-step checks, verification test, and recovery note."
keywords:
  - "nextcloud shared folder not syncing"
date: 2026-11-21T14:43:13+08:00
publishDate: 2026-11-21T14:43:13+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're running a self-hosted Nextcloud with the Windows desktop client, and a shared folder stays at 'waiting for sync' while local files remain unsent. This article walks through a controlled diagnosis for that specific stuck state.

## Check the client's sync status and activity

Open the Nextcloud desktop client and click the folder showing the issue. In the Activity tab, look for the last completed action and any error text. If the list shows only 'waiting' with no recent transfer, the client is not receiving a sync decision from the server. Note the exact message; 'waiting for sync' with no error usually points to a stalled sync engine rather than a permissions rejection.

## Inspect the shared folder's permissions and lock state

In the Nextcloud web interface, open the shared folder and check that your account has write permission. A read-only share will leave local changes unsent. Also look for a lock icon on files; a stale lock from another client can block the queue. If the share is read-only, ask the owner to grant edit rights, then recheck the client.

## Verify server reachability and client logs

Confirm the client can reach your server by opening the account settings and checking the connection status. Then open the client log (Settings > Logs) and search for recent sync errors around the shared folder path. A repeating connection or 423 Locked entry explains the stall. This is a common cause of **nextcloud shared folder not syncing** on self-hosted setups.

## Verification test

Create a small test file inside the shared folder locally. Watch the Activity tab for two minutes. If it uploads and the status returns to 'up to date', the queue is moving. If it stays at 'waiting', restart the client and repeat once.

## Rollback and recovery

Before changing permissions or removing locks, note the original share settings. If a fix makes things worse, restore those settings and pause sync on the folder until you can review the logs. For hands-on help,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
