---
title: "Nextcloud Upload Permission Denied: Fix a Folder That Rejects New Files"
description: "Fix Nextcloud upload permission denied on Windows when browsing works but uploading to a specific folder fails. Check permissions, verify, and recover safely."
seo_title: "Nextcloud Upload Permission Denied: Folder Upload Fix"
seo_description: "Fix Nextcloud upload permission denied on Windows when browsing works but uploading to a specific folder fails. Check permissions, verify, and recover safely."
keywords:
  - "nextcloud upload permission denied"
date: 2026-11-15T18:40:26+08:00
publishDate: 2026-11-15T18:40:26+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You can browse your self-hosted Nextcloud in the Windows desktop client, but when you try to upload a new file into one target folder, the server rejects it with a permission error.

## Confirm the folder is the problem

In the desktop client, open the target folder and try uploading a tiny test file. If the error repeats only there, the folder's permissions are the cause, not the client or your network. Next, open the same folder in the Nextcloud web interface. If the upload button is missing or the web upload also fails, the server is denying write access. If the web upload succeeds, the desktop client may be using stale permissions; disconnect and reconnect the account in the client settings, then retry.

## Check server-side folder permissions

Ask your Nextcloud administrator to inspect the target folder's sharing and permissions. In the web interface, open the folder's sharing panel and confirm your account has edit or upload rights. On the server, check the folder's filesystem ownership and write bits; the web server user must be able to write there. A common result is that the folder is owned by root or another user, so the server returns permission denied even though browsing works. Correct ownership or add the needed write permission, then let the client resync.

## Verification test

Create a new text file locally and upload it into the target folder through the desktop client. A successful upload shows a green check and the file appears in the web interface. If it still fails, the client is receiving a **nextcloud upload permission denied** response, so recheck the folder's share settings and server ownership.

## Rollback and recovery

Before changing ownership or permissions, record the current values so you can restore them. If a change makes the folder inaccessible, revert to the recorded settings and resync. For persistent cases,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
