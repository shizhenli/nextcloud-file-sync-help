---
title: "Shared Folder Missing from Windows Client: A Focused Diagnosis"
description: "A shared folder is absent from your Windows Nextcloud client tree. Follow these checks to confirm whether the share is accepted, visible, and within sync scope."
seo_title: "Nextcloud Shared Folder Not Syncing: Missing from Windows Client"
seo_description: "A shared folder is absent from your Windows Nextcloud client tree. Follow these checks to confirm whether the share is accepted, visible, and within sync scope."
keywords:
  - "nextcloud shared folder not syncing"
date: 2026-11-16T08:00:55+08:00
publishDate: 2026-11-16T08:00:55+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You accepted a folder share in Nextcloud, but it never appears in the Windows desktop client tree, leaving you unsure whether the share is broken or simply outside the client's sync scope.

## Confirm the share is accepted and visible

Sign in to the Nextcloud web interface as the recipient account. Open the Files app and look for the shared folder. If it is absent there, the share was not accepted or was removed by the owner. If it appears with a shared icon, the server side is working and the issue is client-side.

## Check the client's account and sync scope

In the desktop client, open Settings and select the affected account. Under the folder sync configuration, confirm the local folder is set to sync the entire account rather than selected subfolders. If you use selective sync, open the list and verify the shared folder is checked. An unchecked shared folder is intentionally excluded and will not download.

## Force a discovery refresh

Pause and resume sync from the client tray menu, then wait for the activity list to settle. If the folder still does not appear, remove the account from the client without deleting local data, then re-add it. This rebuilds the local discovery database. Before doing so, note any local-only files in the sync root and back them up; re-adding can surface conflict copies if the same paths exist on the server.

## Verification test

Create a small test file inside the shared folder in the web interface. Within a few minutes, check whether it appears in the Windows client's local sync folder. If it does, the share is now syncing. If it does not, the problem is likely permissions or a stale client database, and further server-side review is needed.

If these steps do not restore the folder, this is a case of **nextcloud shared folder not syncing** that needs account-level inspection.

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your client logs and the share details.
