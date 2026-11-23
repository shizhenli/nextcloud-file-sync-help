---
title: "Windows Client Can Browse but Cannot Upload: Resolving a Permission Denied Error"
description: "Self-hosted Nextcloud with Windows desktop client can browse but fails to upload into a target folder with permission denied. Follow these checks to restore upload access."
seo_title: "Fix Nextcloud Upload Permission Denied on Windows Client"
seo_description: "Self-hosted Nextcloud with Windows desktop client can browse but fails to upload into a target folder with permission denied. Follow these checks to restore upload access."
keywords:
  - "nextcloud upload permission denied"
date: 2026-11-23T12:00:58+08:00
publishDate: 2026-11-23T12:00:58+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are using the Nextcloud Windows desktop client to upload a new file into a specific folder, but the client can browse the folder and the server returns a permission denied error.

## Check the folder's sharing and permission settings

In the Nextcloud web interface, navigate to the target folder and open its sharing panel. Confirm that your user account has upload (create) permission for that folder. If the folder is shared with you, the owner must grant you "can edit" or at least "can upload" rights. A read-only share will allow browsing but reject new files. Also check if the folder is inside a group folder or external storage where permissions are managed separately.

## Verify the Windows client's local sync status

On the Windows machine, right-click the Nextcloud tray icon and open the client's activity log. Look for the exact error message; it should mention permission denied or access forbidden. If the client shows a green checkmark for browsing but a red error for the upload, the issue is server-side permissions, not network connectivity.

## Test with a small file in a different folder

Create a tiny text file and try uploading it to your personal root folder (not the target folder). If that succeeds, the problem is isolated to the target folder's permissions. If it also fails, your account may lack upload rights globally, or the server's storage quota is full.

## Rollback and recovery

If you changed folder permissions and uploads still fail, revert the permission change to avoid breaking other users' access. Then ask the folder owner or Nextcloud administrator to review the share settings and storage quota. For persistent **nextcloud upload permission denied** errors,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the exact error text and folder path.

## Verification test

After adjusting permissions, delete the failed upload from the client's queue (if visible), then re-add the file. A successful upload will show a green checkmark and the file will appear in the web interface. If the error returns, capture the client log and server log entries for that timestamp.
