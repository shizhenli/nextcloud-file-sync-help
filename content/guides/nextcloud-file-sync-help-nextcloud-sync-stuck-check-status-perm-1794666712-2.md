---
title: "Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts — Resolve Conflict File Creation"
description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at two-way sync conflict file creation. Check status, permissions, and conflicts to restore expected behavior."
seo_title: "Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at two-way sync conflict file creation. Check status, permissions, and conflicts to restore expected behavior."
keywords:
  - "Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts"
date: 2026-11-23T11:01:04+08:00
publishDate: 2026-11-23T11:01:04+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are running a self-hosted Nextcloud server with the Windows desktop client, and the two-way sync is stuck at the step where it creates conflict files, leaving you with conflict copies instead of your intended merged version. This article helps you diagnose and fix that specific failure using **Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts** as your framework.

## Check Sync Status and Permissions

Open the Nextcloud desktop client and click the status icon. If it shows "Waiting for sync" or a spinning icon with no progress, the client is not communicating properly. Check the server log (nextcloud.log) for errors like "Permission denied" or "Locked". On the server, verify that the user account has write access to the target folder: run `ls -l` on the directory and ensure the web server user (e.g., www-data) owns it or has write permissions. If permissions are wrong, the client cannot create conflict files and will stall.

## Inspect Conflict Files

Look in the sync folder for files named like `filename (conflicted copy 2025-01-01).ext`. These appear when both sides have edits. The client creates them instead of merging. If you see many, the sync is looping. Delete or rename them after backing up, then restart the client.

## Verification Test

Create a small text file on the server and edit the same file locally. Wait for sync. If a conflict file appears within two minutes, the client is working. If not, recheck permissions.

## Rollback and Recovery

If you accidentally delete conflict files, restore them from the server's trash bin (Files > Deleted files) or your local backup. For persistent issues,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
