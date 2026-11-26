---
title: "Windows Tray Icon Shows Offline While Browser Works: Diagnosing the Nextcloud Desktop Client"
description: "Troubleshoot the Nextcloud desktop client on Windows when the tray icon stays offline despite browser access. Step-by-step checks, verification, and recovery."
seo_title: "Nextcloud Client Offline Windows: Fix Tray Icon Stuck Offline"
seo_description: "Troubleshoot the Nextcloud desktop client on Windows when the tray icon stays offline despite browser access. Step-by-step checks, verification, and recovery."
keywords:
  - "nextcloud client offline windows"
date: 2026-11-26T09:00:06+08:00
publishDate: 2026-11-26T09:00:06+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're running a self-hosted Nextcloud and the Windows desktop client tray icon stays offline even though the web interface loads fine in your browser.

## Check the Client's Connection Status

Right-click the tray icon and open Settings. Under the General tab, look at the account status. If it says "Offline" or shows a red icon, click the three-dot menu and choose "Check connection" or "Reconnect." A green check means the client reconnected; a red exclamation means it still cannot reach the server.

## Verify the Server Address and Certificate

Open the account settings and confirm the server URL matches exactly what you use in the browser (including https:// and any port). A common cause of **nextcloud client offline windows** is a mismatch such as http versus https or a trailing path. Next, check the certificate: if your self-hosted server uses a self-signed certificate, the client may reject it silently. In Settings, look for a certificate warning and compare the fingerprint with the one your browser shows.

## Test With a Direct Connection

Temporarily disable any VPN or proxy, then restart the client from the tray menu. If the icon turns green, the proxy was blocking the sync connection. Re-enable it and add an exception for your Nextcloud host.

## Verification Test

Create a small text file in your local sync folder. Watch the tray icon: it should show a syncing animation and then return to green. Confirm the file appears in the browser's Files view within a minute. If it does, the client is online and syncing correctly.

## Rollback and Recovery

If changes made things worse, revert the server URL and proxy settings to their previous values, then restart the client. As a last resort, remove and re-add the account; local files remain, but let the initial sync finish before editing.

If the icon stays offline after these checks,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your client log.
