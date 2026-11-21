---
title: "Nextcloud Upload Permission Denied: Why One Windows Folder Rejects New Files"
description: "Self-hosted Nextcloud with the Windows desktop client can browse a folder but fails to upload new files with a permission denied error. Step-by-step checks to restore uploads to that specific folder."
seo_title: "Nextcloud Upload Permission Denied: Fix a Folder Rejecting Uploads (Windows)"
seo_description: "Self-hosted Nextcloud with the Windows desktop client can browse a folder but fails to upload new files with a permission denied error. Step-by-step checks to restore uploads to that specific folder."
keywords:
  - "nextcloud upload permission denied"
date: 2026-11-21T14:40:13+08:00
publishDate: 2026-11-21T14:40:13+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You can open the target folder in the Windows desktop client and see its contents, but every new file you drop there fails with a permission denied error from the server.

## Confirm the error is folder-specific

Create a small test file and upload it to a different folder you own. If that succeeds, the problem is scoped to the target folder, not your account or the client. Next, open the target folder in the Nextcloud web interface and check the sharing panel. Look for a read-only share, a group share with upload disabled, or a file drop setting. If the web interface also refuses the upload, the restriction lives on the server side and the desktop client is only reporting it.

## Check server-side permissions

On the server, inspect the folder's ownership and mode. The web server user (often www-data) needs write access to the directory. Run a listing on the parent path and confirm the target folder is owned by the web server user or a group it belongs to. Also check whether the folder sits inside an external storage mount configured as read-only, or inside a group folder where your account has view-only rights. Any of these produces the same **nextcloud upload permission denied** message in the client.

## Verification test

After correcting ownership or share rights, create a new text file locally and upload it into the target folder through the desktop client. Then refresh the web interface and confirm the file appears with your account listed as owner. If it uploads in the browser but not the client, remove the local sync pair and re-add it so the client re-reads permissions.

## Rollback note

Before changing ownership or share settings, note the original values so you can restore them if another user loses access. If a change makes things worse, revert to those values and retest with the same small file.

If the folder still rejects uploads after these checks,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the exact error text and the folder's share settings.
