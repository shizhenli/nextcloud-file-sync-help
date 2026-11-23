---
title: "Windows Client Stuck on Waiting for Sync: Status, Permissions, and Conflict Checks"
description: "Troubleshoot a Windows Nextcloud desktop client stuck at 'waiting for sync' by checking server status, folder permissions, and conflict files, with a verification test and rollback note."
seo_title: "Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts"
seo_description: "Troubleshoot a Windows Nextcloud desktop client stuck at 'waiting for sync' by checking server status, folder permissions, and conflict files, with a verification test and rollback note."
keywords:
  - "Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts"
date: 2026-11-23T10:00:57+08:00
publishDate: 2026-11-23T10:00:57+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

Your Windows desktop client has been sitting at waiting for sync for a while, and the files you edited locally still haven't left your machine.

## Check the sync status and server reachability

Open the client window and look at the account row. If it shows a green check but no activity, the client believes it is idle. Click the three-dot menu and choose to view the sync log; a healthy log shows recent completed operations. If the last entry is hours old, the client is not talking to the server. Test the server URL in a browser on the same PC. A login page means the server is reachable; a timeout means the client cannot proceed until the network or server is fixed.

## Check folder permissions

Right-click the local sync folder, open Properties, and confirm your Windows user has write access. Then check the server side: in the Nextcloud web interface, open the same folder and confirm your account can create files there. A read-only share or a revoked group membership will leave the client waiting indefinitely.

## Check for conflicts

Look for files ending in "conflicted copy" in the sync folder. A conflict can block the queue behind it. Move any conflict files out of the folder to a safe location, then let the client retry. This is the practical core of **Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts**.

## Verification test

Create a small text file inside the sync folder. Within a minute, the client should show it as uploading and then synced, and the file should appear in the web interface. If it does, sync is restored. If not, stop the client, rename the sync database folder to back it up, and restart to force a fresh index; this is your rollback point if the reset misbehaves. For hands-on help,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
