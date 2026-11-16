---
title: "Nextcloud Upload Failed: Permission Denied on a Specific Folder"
description: "Troubleshoot a Nextcloud Windows client that can browse but cannot upload to a target folder, with a permission denied error. Step-by-step checks and a verification test."
seo_title: "Fix Nextcloud Upload Failed Permission Denied (Windows Client)"
seo_description: "Troubleshoot a Nextcloud Windows client that can browse but cannot upload to a target folder, with a permission denied error. Step-by-step checks and a verification test."
keywords:
  - "nextcloud upload failed permission denied"
date: 2026-11-16T12:04:29+08:00
publishDate: 2026-11-16T12:04:29+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're uploading a new file into a target folder with the Windows desktop client, but the server returns permission denied even though you can browse the folder.

## Confirm the exact error and folder

Open the Nextcloud client's activity window and note the full error text and the folder path. A permission denied message on upload usually means the server rejected the write, not that the client lost connection. If browsing still works, the account and sync connection are fine; the problem is write access to that folder.

## Check server-side permissions

In the Nextcloud web interface, open the target folder and look at its sharing and permissions. Select the folder, open sharing details, and confirm your account has create and write permission. If the folder is shared with you, the owner may have granted read-only access. Ask the owner to enable editing, or move the file to a folder where you have write rights.

Next, check the parent folder. A restrictive parent can block new files even when the child looks writable. Also verify the file name does not contain characters the server rejects.

## Check the Windows client

Right-click the sync folder in the client, open settings, and confirm the folder is not set to read-only locally. Then pause and resume sync to clear a stale state. If the error persists, remove and re-add the folder connection, which forces a fresh permission check.

## Verification test

Create a small test text file directly in the target folder from the web interface. If that upload succeeds but the desktop client still fails, the client's cached permissions are stale; re-add the sync connection. If both fail, the server permission is the cause.

## Rollback note

Before changing sharing settings, record the current permissions so you can restore them. If a re-add makes things worse, remove the new connection and reconnect the original folder.

If the **nextcloud upload failed permission denied** error continues after these checks,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the exact error text and folder path.
