---
title: "Nextcloud Sync Stuck at 99 Percent: What 'Waiting for Sync' Really Means on Windows"
description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at 'waiting for sync' with unsent local files. Step-by-step checks, verification, and recovery."
seo_title: "Nextcloud Sync Stuck at 99 Percent? Fix 'Waiting for Sync' on Windows"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at 'waiting for sync' with unsent local files. Step-by-step checks, verification, and recovery."
keywords:
  - "nextcloud sync stuck at 99 percent"
date: 2026-11-25T08:01:01+08:00
publishDate: 2026-11-25T08:01:01+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

## Troubleshooting

You're running a self-hosted Nextcloud server and the Windows desktop client sits at 'waiting for sync' while local files remain unsent, and you need to know whether this is a transient pause or a real block. Start by opening the client's activity window and noting the exact status line and the last file name shown. If the status says 'waiting for sync' with no progress for more than two minutes and the file count is unchanged, treat it as a genuine stall rather than normal queuing. Next, check the server connection: open the client settings, confirm the account shows connected, and use the 'Check server' option if present. A timeout or certificate warning here points to the server or network, not the files. Then inspect the local sync folder for a file with a lock icon or a conflict marker; a single locked or conflicted file can hold the entire queue. If you find one, close any program using it and rename the conflict copy aside. Also verify free disk space on both the client drive and the server data volume; a full volume stops uploads silently. After these checks, run a verification test: create a small new text file in the sync root, wait sixty seconds, and confirm it appears on the server via the web interface. If it does, the queue has cleared. If it does not, restart the desktop client once and repeat. For a **nextcloud sync stuck at 99 percent** pattern where the last file never completes, remove that single file from the sync folder, let the queue drain, then copy it back. As a recovery note, if you renamed or moved files during diagnosis, restore them from the sync folder's previous state before resuming, and keep a local backup until one full sync completes. If the stall returns,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
