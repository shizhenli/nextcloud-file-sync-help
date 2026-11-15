---
title: "Shared Folder Not Syncing: Fix the Windows Client Stuck at 'Waiting for Sync'"
description: "Self-hosted Nextcloud with Windows desktop client stuck at 'waiting for sync' and shared folder files unsent? Follow these checks to restore sync."
seo_title: "Nextcloud Shared Folder Not Syncing on Windows: Fix 'Waiting for Sync'"
seo_description: "Self-hosted Nextcloud with Windows desktop client stuck at 'waiting for sync' and shared folder files unsent? Follow these checks to restore sync."
keywords:
  - "nextcloud shared folder not syncing"
date: 2026-11-15T18:40:26+08:00
publishDate: 2026-11-15T18:40:26+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are running a self-hosted Nextcloud with the Windows desktop client, and a shared folder stays at 'waiting for sync' while local files remain unsent.

## Check the client status and logs
Open the desktop client, select the shared folder, and look at the status line. If it says 'waiting for sync' without progress, open the log file from the client settings. Search for the folder name and note any 'permission denied', 'conflict', or 'server error' entries. A permission error means the share is read-only for your account; a conflict means a file with the same name exists remotely.

## Verify server-side share permissions
In the Nextcloud web interface, open the shared folder and check the share settings. Confirm your account has edit and create permissions. If the share was created by another user, ask them to review the permissions. A read-only share will never upload local changes, and the client may wait indefinitely.

## Test with a single small file
Create a new text file inside the shared folder locally. Watch the client activity. If the file uploads, the folder is writable and the original issue may be a conflict or a large file. If it stays waiting, remove the test file and re-check permissions.

## Reset the sync state for that folder
If permissions are correct, pause sync, remove the shared folder from the client (do not delete local data), then re-add it. This clears a stale sync journal. Before doing so, copy any unsent files to a safe location; re-adding may overwrite local changes.

If the folder still shows **nextcloud shared folder not syncing** after these steps, collect the client log and server log for review.

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the exact error lines.
