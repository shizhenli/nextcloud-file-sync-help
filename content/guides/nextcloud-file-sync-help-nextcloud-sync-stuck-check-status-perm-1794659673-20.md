---
title: "Nextcloud Conflict Copies Instead of Merging: A Step-by-Step Fix"
description: "Self-hosted Nextcloud with Windows desktop client creating conflict copies instead of merging edits. Learn how to check status, permissions, and resolve conflicts to restore two-way sync."
seo_title: "Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts"
seo_description: "Self-hosted Nextcloud with Windows desktop client creating conflict copies instead of merging edits. Learn how to check status, permissions, and resolve conflicts to restore two-way sync."
keywords:
  - "Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts"
date: 2026-11-21T14:40:13+08:00
publishDate: 2026-11-21T14:40:13+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are running a self-hosted Nextcloud with the Windows desktop client, and at the two-way sync creates conflict files step, the client keeps producing conflict copies instead of merging your intended version.

## Check sync status and permissions

First, open the Nextcloud client and look at the status icon. If it shows a red circle or a paused state, click it and note the exact message. A message like "conflict" or "permission denied" points to the next check. Then, verify that the affected folder has write permissions for your Windows user. Right-click the folder, choose Properties, and confirm that "Read-only" is not checked. On the server side, ensure the folder is not locked by another process or user. If permissions are correct, proceed to the conflict check.

## Inspect and resolve conflicts

Open the folder containing the conflict files. Nextcloud names them like "filename (conflicted copy 2025-01-01).ext". Compare the conflicted copy with the original. Decide which version is correct, then delete or rename the unwanted copy. After resolving, wait for the client to sync. If conflicts keep appearing, the root cause is often that both sides edited the same file before sync completed. This is a classic case of **Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts** where the client cannot merge automatically.

## Verification test

Create a small test file in the folder, edit it on one side only, and wait for sync. Then edit the same file on the other side after sync finishes. The client should merge without creating a conflict copy. If it does, the issue is resolved.

## Rollback and recovery

If you deleted the wrong version, restore it from the Nextcloud trash bin or your local backup. For persistent issues,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
