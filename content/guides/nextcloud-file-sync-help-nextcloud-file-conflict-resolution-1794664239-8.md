---
title: "Nextcloud Two-Way Sync Creates Conflict Files: Resolve Duplicate Edits"
description: "Both sides have edits and the Windows client creates conflict copies instead of merging. Follow these checks to restore expected two-way sync conflict behavior."
seo_title: "Nextcloud File Conflict Resolution: Fix Two-Way Sync Conflict Copies"
seo_description: "Both sides have edits and the Windows client creates conflict copies instead of merging. Follow these checks to restore expected two-way sync conflict behavior."
keywords:
  - "nextcloud file conflict resolution"
date: 2026-11-21T14:46:28+08:00
publishDate: 2026-11-21T14:46:28+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You edited a file on your Windows desktop while someone else changed the same file on the server, and now the client keeps producing conflict copies instead of the version you intended.

## Check the conflict file pattern first

Open the folder containing the conflict copy. The filename typically includes "conflicted copy" and a timestamp. Confirm both the original and the conflict file exist and that each contains different edits. If the conflict file is empty or zero bytes, stop and check disk space and antivirus quarantine before continuing.

## Verify the client's conflict settings

Right-click the Nextcloud tray icon, open Settings, and go to the General tab. Confirm the sync folder is not paused and that no selective sync exclusions are hiding the parent folder. Then check the server's file versioning app is enabled, because versioning helps you compare edits later. If the conflict file reappears immediately after you delete it, the client is still seeing two changed copies; do not delete again until you compare timestamps.

## Run a controlled verification test

Create a small text file in the synced folder. Edit it on the desktop, wait for sync, then edit the same file in the Nextcloud web interface before the desktop syncs again. Watch the client status. Expected result: one conflict copy appears, and both versions are readable. If no conflict copy appears, the client may be merging silently or the server may be rejecting the upload.

## Rollback and recovery

Before resolving, copy both versions to a local backup folder outside the sync tree. Use the web interface's version history to restore the intended server version if needed. For persistent cases, consult

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult). This **nextcloud file conflict resolution** approach keeps your edits recoverable while you confirm the client is behaving as expected.
