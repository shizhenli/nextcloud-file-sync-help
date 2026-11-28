---
title: "Nextcloud Shared Folder Missing from Windows Desktop Client: A Controlled Diagnosis"
description: "A shared folder is absent from your Nextcloud Windows desktop client. Follow these checks to diagnose and restore the missing folder."
seo_title: "Fix: nextcloud shared folder missing from Windows client"
seo_description: "A shared folder is absent from your Nextcloud Windows desktop client. Follow these checks to diagnose and restore the missing folder."
keywords:
  - "nextcloud shared folder missing"
date: 2026-11-28T21:42:25+08:00
publishDate: 2026-11-28T21:42:25+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

A folder shared by another account is absent from your Windows desktop client tree, and you want to restore it without guessing.

## Check the share exists on the server

Open the Nextcloud web interface as the recipient account. Go to Files and look for the shared folder. If it is absent there, the share was removed or never accepted. If it is present, the server side is fine and the issue is client-side.

## Verify the client is syncing the correct account

In the desktop client, right-click the tray icon, open Settings, and check the account list. Confirm the account that received the share is present and shows a green check. If it shows an error or is paused, resume sync and wait for the folder tree to refresh.

## Check selective sync exclusions

In the client settings, open the account and review selective sync. If the shared folder is unchecked, it will not appear locally. Enable it and apply. The client should begin creating the local folder.

## Force a folder refresh

Pause sync, wait five seconds, and resume. Then open the client's activity log and look for entries mentioning the shared folder name. A permission error or a 404 indicates the share is not visible to this account; a successful listing means the client simply had not refreshed.

## Verification test

Create a small test file inside the shared folder via the web interface. Within a minute, check whether it appears in the local client folder. If it does, the **nextcloud shared folder missing** problem is resolved. If not, note the exact error in the log.

## Rollback and recovery

If enabling selective sync causes duplicates or sync errors, disable the folder again and remove only the local copy, never the server copy. Then re-enable it after the client settles. For persistent cases,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your log excerpt.
