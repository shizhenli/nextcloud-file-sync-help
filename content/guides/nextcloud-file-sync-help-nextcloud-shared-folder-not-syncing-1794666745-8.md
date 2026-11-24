---
title: "Shared Folder Missing from Windows Client: A Focused Fix"
description: "A shared folder is absent from the Windows desktop client tree. Follow these focused checks to diagnose and restore the missing folder without guesswork."
seo_title: "Nextcloud Shared Folder Not Syncing on Windows: Fix Missing Folder"
seo_description: "A shared folder is absent from the Windows desktop client tree. Follow these focused checks to diagnose and restore the missing folder without guesswork."
keywords:
  - "nextcloud shared folder not syncing"
date: 2026-11-24T12:01:18+08:00
publishDate: 2026-11-24T12:01:18+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

A folder shared by another account is absent from the desktop client tree, leaving you unable to access files you expect to see.

## Confirm the share exists on the server

Open the Nextcloud web interface as the recipient account. Check the Shares section and the folder list. If the folder appears there, the share exists and the problem is client-side. If it does not appear, ask the owner to re-share it and confirm the recipient username is exact. This distinction prevents wasted client troubleshooting.

## Check client account and sync scope

In the desktop client, open Settings and verify you are signed into the correct account. A common cause of **nextcloud shared folder not syncing** is a second account or a renamed user. Next, open the account's folder selection. Shared folders must be enabled and the specific folder checked. If the folder is unchecked, select it and apply. If it is checked but absent, remove the account from the client and add it again; this rebuilds the local folder tree without deleting server data.

## Verify with a controlled test

Create a small test file inside the shared folder through the web interface. Watch the client activity window for that filename. If it appears locally within a minute, sync is restored. If it does not, note the exact client status message before changing anything else.

## Rollback and recovery

Before removing and re-adding the account, note any local-only files in the sync folder and copy them elsewhere. Re-adding the account may move or rename the local sync directory. If the folder still does not appear, stop and

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the client log and the web interface share details.
