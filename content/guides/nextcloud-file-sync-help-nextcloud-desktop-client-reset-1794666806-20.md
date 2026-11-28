---
title: "Nextcloud Desktop Client Offline on Windows: A Controlled Reset"
description: "Troubleshoot a Nextcloud desktop client that stays offline on Windows despite working browser access. Follow a controlled diagnosis and reset to restore sync."
seo_title: "Fix Nextcloud Desktop Client Offline on Windows with a Controlled Reset"
seo_description: "Troubleshoot a Nextcloud desktop client that stays offline on Windows despite working browser access. Follow a controlled diagnosis and reset to restore sync."
keywords:
  - "nextcloud desktop client reset"
date: 2026-11-28T22:10:24+08:00
publishDate: 2026-11-28T22:10:24+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're running a self-hosted Nextcloud and the Windows desktop client tray icon stays offline, even though the same server loads fine in your browser.

## Confirm the failure is client-side

First, verify the browser works on the same machine. Open your Nextcloud URL in Edge or Chrome and log in. If the web interface loads, the server and network are reachable. Next, right-click the tray icon and check the account status. If it shows offline while the browser works, the client's local state is likely stale.

## Check the client's connection details

Open the client settings and confirm the server address exactly matches your browser URL, including https and any subfolder. A trailing slash or http instead of https can cause a silent offline state. Then check the log file for recent errors: in the client, go to Settings > General and click "Open log file." Look for repeated connection refused or SSL errors. If the log shows certificate errors, fix the certificate trust before resetting.

## Perform a controlled reset

A **nextcloud desktop client reset** clears local sync metadata without deleting your server files. Before doing this, note your local sync folder path and pause any large uploads. In the client, remove the account, then quit the client completely from the tray. Rename the configuration folder at %APPDATA%\Nextcloud to Nextcloud.old as a backup. Restart the client and add your account again, pointing to the same local folder. The client will re-scan and reconcile.

## Verify the fix

After re-adding the account, watch the tray icon for two minutes. It should turn green and show "Up to date" or begin syncing. Create a small test file in the local folder and confirm it appears in the browser. If the icon stays offline, restore the renamed folder to roll back, then

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with the log file.
