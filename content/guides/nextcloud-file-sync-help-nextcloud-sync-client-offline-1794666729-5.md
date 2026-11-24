---
title: "Nextcloud Sync Client Offline on Windows: Restore the Tray Icon"
description: "Troubleshoot a Nextcloud desktop client that stays offline on Windows even though the browser works. Step-by-step checks to restore sync."
seo_title: "Fix Nextcloud Sync Client Offline on Windows"
seo_description: "Troubleshoot a Nextcloud desktop client that stays offline on Windows even though the browser works. Step-by-step checks to restore sync."
keywords:
  - "nextcloud sync client offline"
date: 2026-11-24T09:00:58+08:00
publishDate: 2026-11-24T09:00:58+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're using the Nextcloud desktop client on Windows with a self-hosted server, and the tray icon stays offline even though the browser connects fine. This guide walks you through a controlled diagnosis to get the client back online.

## Check the client's connection status

Right-click the tray icon and open Settings. Under the General tab, look at the account status. If it says offline, click the account and select Check connection. A message like "Connection refused" or "SSL error" points to a client-side network or certificate issue, not a server outage. If it says "Connected," the offline state may be a stale display—restart the client.

## Verify server URL and credentials

In Settings, confirm the server address exactly matches what you use in the browser (including https:// and any port). A trailing slash or http:// instead of https:// can cause the client to fail silently. Next, remove and re-add the account: click Remove account, then Add account and sign in again. This refreshes the token without touching local files.

## Test with a direct connection

Temporarily disable any VPN or proxy, then restart the client. If the icon turns green, the proxy was blocking the sync endpoint. Re-enable it and add an exception for your server's domain. Also check Windows Firewall: allow nextcloud.exe for both private and public networks.

## Verification test

Create a small text file in your local sync folder. Watch the tray icon—it should show a sync animation and then return to green. Open the browser and confirm the file appears on the server. If it does, the client is online.

## Rollback note

If re-adding the account causes issues, you can restore the previous configuration by renaming the Nextcloud config folder (typically %APPDATA%\Nextcloud) before restarting. This resets client settings but leaves your synced files intact.

If the client still shows **nextcloud sync client offline** after these steps,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your client log for a deeper review.
