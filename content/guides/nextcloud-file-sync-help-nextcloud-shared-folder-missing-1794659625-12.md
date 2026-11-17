---
title: "Nextcloud Shared Folder Missing from Windows Client: A Controlled Diagnosis"
description: "Troubleshoot a missing shared folder in the Nextcloud Windows desktop client with step-by-step checks, verification, and recovery."
seo_title: "Nextcloud Shared Folder Missing from Windows Client: Fix It"
seo_description: "Troubleshoot a missing shared folder in the Nextcloud Windows desktop client with step-by-step checks, verification, and recovery."
keywords:
  - "nextcloud shared folder missing"
date: 2026-11-17T12:00:54+08:00
publishDate: 2026-11-17T12:00:54+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're using the Nextcloud Windows desktop client, and a folder shared with you by another account is simply absent from the client's file tree. Before you reinstall or reset anything, work through these checks in order.

## Confirm the share exists on the server

Open Nextcloud in a browser and log in as the account that should receive the share. Go to the Files app and look for the shared folder. If it's missing here too, the problem is on the server side: ask the owner to re-share it, or check that the share hasn't expired. If it appears in the browser but not in the client, continue below.

## Check the client's account and sync scope

In the desktop client, open Settings and select the account. Under the folder list, confirm the shared folder is enabled for sync. A folder can be excluded from sync without being deleted. Also verify you're logged into the correct account; a second account may be hiding the share.

## Force a refresh and inspect logs

Right-click the client tray icon and choose to pause and then resume sync. Then open the client's log file and search for the folder name. Look for permission errors or "not found" entries. If the log shows the folder was removed remotely, the owner may have unshared it.

## Verification test

Create a small test file inside the shared folder using the web interface. Wait a minute, then check whether it appears in the desktop client. If it does, sync is working and the original folder was likely excluded locally. If not, the share is not reaching your account.

## Rollback and recovery

If you changed sync settings, you can re-enable the folder in the client's settings without losing local data. Avoid deleting the local sync database unless instructed; instead, remove and re-add the account as a last resort, which preserves server data. For persistent cases,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your logs. A **nextcloud shared folder missing** from the client is usually a scope or permission issue, not data loss.
