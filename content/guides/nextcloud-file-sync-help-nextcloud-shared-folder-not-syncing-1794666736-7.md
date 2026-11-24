---
title: "Nextcloud Shared Folder Not Syncing: Diagnose a Stuck 'Waiting for Sync' Status"
description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at 'waiting for sync' when a shared folder's local files remain unsent. Step-by-step checks and a verification test."
seo_title: "Fix Nextcloud Shared Folder Not Syncing on Windows"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows client stuck at 'waiting for sync' when a shared folder's local files remain unsent. Step-by-step checks and a verification test."
keywords:
  - "nextcloud shared folder not syncing"
date: 2026-11-24T11:01:02+08:00
publishDate: 2026-11-24T11:01:02+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are running a self-hosted Nextcloud server with the Windows desktop client, and a shared folder remains stuck at 'waiting for sync' while your local files stay unsent.

## Check the client's sync status and logs

Open the desktop client and click the shared folder. If the status still reads 'waiting for sync' after a minute, the client is not receiving a sync decision from the server. Open the client's log file (Settings > General > Logs) and look for repeated entries about the shared folder. A steady stream of 'waiting' or 'polling' messages without an upload attempt points to a server-side permission or lock issue, not a local file problem.

## Verify server-side access and locks

Log into Nextcloud as the share recipient. Open the shared folder and confirm you can create a test file there. If creation fails, the share is read-only or the folder is locked. Also check the sender's account: if the shared folder was moved or renamed, the client may hold a stale reference. Remove and re-add the share in the client, then let it rescan. This is a common cause of a **nextcloud shared folder not syncing**.

## Run a verification test

Create a small text file inside the shared folder on your PC. Watch the client status for two minutes. If it changes to 'syncing' and the file appears on the server, the issue is resolved. If it stays at 'waiting for sync', note the exact log timestamp and stop.

## Rollback and recovery

Before removing and re-adding the share, copy any unsent local files to a separate folder. If the rescan does not resolve the stall, restore those copies and pause sync to avoid data loss. For guided diagnosis,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
