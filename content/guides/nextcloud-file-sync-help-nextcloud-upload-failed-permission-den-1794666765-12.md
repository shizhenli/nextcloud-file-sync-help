---
title: "Nextcloud Upload Failed Permission Denied: Fix Folder Upload Rejection"
description: "Troubleshoot a Nextcloud Windows client that can browse but cannot upload into a specific folder, with a permission denied error. Step-by-step checks and verification."
seo_title: "Nextcloud Upload Failed Permission Denied: Fix Folder Upload Rejection"
seo_description: "Troubleshoot a Nextcloud Windows client that can browse but cannot upload into a specific folder, with a permission denied error. Step-by-step checks and verification."
keywords:
  - "nextcloud upload failed permission denied"
date: 2026-11-25T11:00:57+08:00
publishDate: 2026-11-25T11:00:57+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are using the Windows desktop client with a self-hosted Nextcloud, and while uploading a new file into the target folder, the client shows permission denied even though you can browse that folder.

## Confirm the exact error and scope

First, reproduce the upload with a small test file. In the client, open the activity log and note the full error text. If it says permission denied or 403, the server is rejecting the write. Next, try uploading to a different folder where you know you have write access. If that succeeds, the problem is isolated to the target folder, not your account or the client.

## Check folder permissions on the server

Ask your Nextcloud administrator to inspect the target folder's permissions. In the Nextcloud web interface, open the folder's sharing settings and confirm your user or group has create and write permissions. On the server filesystem, verify the folder is owned by the web server user and has write permission for that user. A common cause is a folder created by root or another user, leaving the web server unable to write. The administrator should correct ownership and permissions, then rescan the folder if needed.

## Verify with a direct web upload

After the fix, log in to Nextcloud in a browser and upload a small file directly into the target folder. If the web upload succeeds, the server-side permission is resolved. Then return to the Windows client, right-click the sync folder, and choose to sync again. Upload the same test file. A successful upload confirms the fix.

## Rollback and recovery

If you changed folder permissions and uploads still fail, restore the previous permissions to avoid breaking other users, then collect the client log and server log for the exact timestamp. If you cannot identify the cause,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the error text and folder path. This resolves the specific **nextcloud upload failed permission denied** case without affecting other folders.
