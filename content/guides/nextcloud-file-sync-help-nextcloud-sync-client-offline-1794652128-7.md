---
title: "Nextcloud Sync Client Offline on Windows: A Step-by-Step Diagnosis"
description: "Troubleshoot the Nextcloud Windows desktop client staying offline when your browser works. Follow these checks to restore sync."
seo_title: "Nextcloud Sync Client Offline on Windows: Fix Tray Icon Stuck Offline"
seo_description: "Troubleshoot the Nextcloud Windows desktop client staying offline when your browser works. Follow these checks to restore sync."
keywords:
  - "nextcloud sync client offline"
date: 2026-11-15T18:40:26+08:00
publishDate: 2026-11-15T18:40:26+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

**nextcloud sync client offline**. You're running a self-hosted Nextcloud and the Windows desktop client tray icon stays offline even though the web interface loads fine in your browser. This guide walks through a controlled diagnosis to get the client back online.

## Check the Client's Connection Status

Right-click the tray icon and open Settings. Under the General tab, look at the account status. If it says offline, click the three-dot menu and choose Check connection. A quick success message means the client can reach the server; a timeout or certificate error points to a network or trust issue.

## Verify the Server URL and Credentials

In the same Settings window, confirm the server address matches exactly what you use in the browser, including https:// and any port. Then click Reconnect and re-enter your password if prompted. If the client reports invalid credentials, your session may have expired; logging out and back in often resolves this.

## Inspect Proxy and Firewall Settings

Open the Network tab in client settings. If your browser uses a proxy, set the same proxy here. Also check Windows Firewall: ensure nextcloud.exe is allowed on private and public networks. A blocked outbound connection will keep the client offline while the browser, using a different path, still works.

## Verification Test

After making changes, restart the client from the tray menu. Wait 30 seconds, then open a small test file in your sync folder. If the tray icon turns green and the file appears on the server, the issue is resolved. If it remains offline, the problem likely lies in server-side SSL or DNS; try accessing your server URL directly in the browser to confirm.

## Rollback and Recovery

If a recent configuration change caused the problem, revert it: restore the previous server URL or proxy setting, then restart the client. Keep a note of working settings before experimenting.

If the client stays offline after these steps, you may have a deeper certificate or network issue.

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) for a guided review of your setup.
