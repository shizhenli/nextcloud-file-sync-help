---
title: "Shared Folder Missing from Windows Client: A Controlled Diagnosis"
description: "Shared folder absent from your Windows Nextcloud client? Follow these checks to diagnose and restore the missing share without guesswork."
seo_title: "Fix: Nextcloud Shared Folder Not Syncing on Windows Client"
seo_description: "Shared folder absent from your Windows Nextcloud client? Follow these checks to diagnose and restore the missing share without guesswork."
keywords:
  - "nextcloud shared folder not syncing"
date: 2026-11-21T14:43:13+08:00
publishDate: 2026-11-21T14:43:13+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

A folder shared by another account is absent from your Windows desktop client tree, and you want to restore it without guesswork.

## Confirm the Share Exists and Is Accepted

Open the Nextcloud web interface as the recipient account. Go to Files and check whether the shared folder appears. If it does not, the share was never accepted or was removed. If it appears in the web interface but not in the client, the issue is client-side. Also check the sharing account's settings: the share must be active and the recipient must have accepted it. A pending share will not sync.

## Check Client Account and Sync Scope

In the desktop client, open Settings and verify you are signed into the correct account. Then open the account's folder list. If the shared folder is listed but unchecked, enable it. If it is not listed at all, remove the account and re-add it; this refreshes the share list without touching local files. Do not delete the local sync folder.

## Verify Permissions and Server Logs

On the server, confirm the share has read permission at minimum. A share with no permissions may be hidden. Check the Nextcloud log for share-related errors. If the share was created by a user whose account is disabled, it may not propagate.

## Verification Test

Create a small test file inside the shared folder from the web interface. Wait for the client to show activity, then check the local folder. If the file appears, the share is syncing. If not, the client is not receiving the share metadata.

## Rollback Note

If re-adding the account causes duplicate folders, remove the duplicate local folder only after confirming the server copy is intact. Keep a backup of any local-only files before changes.

If the folder remains absent, this is a **nextcloud shared folder not syncing** case that may need server-side share repair.

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) before making further changes.
