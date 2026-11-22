---
title: "Nextcloud Shared Folder Missing from Windows Desktop Client"
description: "A shared folder absent from your Nextcloud Windows client? Follow these controlled checks to diagnose and restore the missing shared folder."
seo_title: "Fix: nextcloud shared folder missing in Windows Client"
seo_description: "A shared folder absent from your Nextcloud Windows client? Follow these controlled checks to diagnose and restore the missing shared folder."
keywords:
  - "nextcloud shared folder missing"
date: 2026-11-22T09:00:55+08:00
publishDate: 2026-11-22T09:00:55+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are self-hosting Nextcloud and using the Windows desktop client, but a folder shared with you by another account does not appear in your local sync tree. This is a common sync-scope issue, not necessarily data loss.

## Confirm the share exists on the server

Open Nextcloud in a browser and log in as the account that should receive the share. Go to Files and check the left sidebar for Shared with you. If the folder is not there, the owner has not shared it with your account, or the share was removed. Ask the owner to re-share it and confirm the exact username. If it is there, the server side is fine; the problem is client scope or sync state.

## Check the client's folder selection

In the Windows client, open Settings and go to the Folders tab. Select your account and click Add Folder Sync Connection or review the existing connection. The folder selection dialog lists remote folders. If the shared folder is unchecked, check it and confirm. If it is not listed at all, the client has not refreshed its remote tree. Remove the sync connection (this does not delete server data) and re-add it, then select the shared folder.

## Verify the result

After applying the change, wait for the client to show a green checkmark. Open File Explorer and navigate to your local Nextcloud folder. The shared folder should appear and begin syncing. Create a small test file inside it from the web interface and confirm it appears locally within a minute.

## Recovery note

If you removed the sync connection and the folder still does not appear, do not delete local files. Re-add the connection and use selective sync to include the share. If the issue persists,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the client log and the share details. This resolves the **nextcloud shared folder missing** case only when the share exists server-side and the client scope is corrected.
