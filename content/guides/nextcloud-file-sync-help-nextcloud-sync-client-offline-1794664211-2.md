---
title: "Nextcloud Sync Client Offline on Windows: A Controlled Diagnosis"
description: "Troubleshoot a Windows Nextcloud desktop client that stays offline while the browser works. Follow these checks to diagnose and restore sync."
seo_title: "Nextcloud Sync Client Offline on Windows: Fix Tray Icon"
seo_description: "Troubleshoot a Windows Nextcloud desktop client that stays offline while the browser works. Follow these checks to diagnose and restore sync."
keywords:
  - "nextcloud sync client offline"
date: 2026-11-21T14:40:13+08:00
publishDate: 2026-11-21T14:40:13+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are running a self-hosted Nextcloud and the Windows desktop client tray icon stays offline even though the browser reaches your server fine.

## Confirm the client's connection state

Right-click the tray icon and open Settings. Under the account, check the status line. If it says offline or disconnected, the client is not reaching the server. Click the status to force a reconnect and watch for a change. If it remains offline, continue.

## Check the server URL and certificate

In Settings, verify the account URL exactly matches what works in the browser, including https and any port. Then open the browser to that same URL and confirm the certificate is trusted without warnings. A self-signed or expired certificate will make the client stay offline while the browser may still load after a warning. If the certificate is invalid, fix it on the server or import the root CA into Windows Trusted Root Certification Authorities, then restart the client.

## Test proxy and firewall paths

The client uses its own network stack. In Settings, check whether a proxy is configured and whether it matches the browser. Temporarily set the client to no proxy if the browser uses none. Also confirm Windows Firewall or endpoint protection is not blocking the client executable. As a verification test, open a command prompt and run curl -I https://your-server/status.php. A 200 response means the network path is open; a timeout points to proxy, firewall, or DNS.

## Reset and recover

If settings are suspect, use the client's Remove account option, then re-add it. Before doing so, note your local sync folder path so you can reconnect the same folder and avoid re-downloading. If the problem persists, this is a **nextcloud sync client offline** condition that may need log review. For guided diagnostics,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
