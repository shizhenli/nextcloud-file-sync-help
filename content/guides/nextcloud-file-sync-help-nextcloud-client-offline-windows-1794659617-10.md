---
title: "Nextcloud Client Offline on Windows: A Controlled Diagnosis"
description: "Troubleshoot a Nextcloud desktop client that stays offline on Windows even though the browser works. Follow these checks to restore sync."
seo_title: "Fix Nextcloud Client Offline on Windows: Step-by-Step"
seo_description: "Troubleshoot a Nextcloud desktop client that stays offline on Windows even though the browser works. Follow these checks to restore sync."
keywords:
  - "nextcloud client offline windows"
date: 2026-11-17T10:00:55+08:00
publishDate: 2026-11-17T10:00:55+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're running a self-hosted Nextcloud and the Windows desktop client shows an offline tray icon, even though the same server loads fine in your browser.

## Check the client's connection status
Right-click the tray icon and open the client window. Look at the status line. If it says offline, click the account name and check the server address. A single wrong character or an http/https mismatch will keep the client offline while the browser uses a different, correct URL. Correct the address and save.

## Verify proxy and firewall settings
Open Windows Settings, Network & Internet, Proxy. If a proxy is enabled, the browser may be using it while the client is not, or vice versa. Note the current setting so you can restore it. In the Nextcloud client settings, under Network, set the proxy to match your browser or choose no proxy if the server is on your local network. Then check Windows Defender Firewall and confirm nextcloud.exe is allowed on private networks.

## Test direct server reachability
Open Command Prompt and run: curl -I https://your-server/status.php. A 200 response means the server is reachable from Windows. If curl fails but the browser works, the client is likely blocked by proxy or firewall rules. If curl succeeds, restart the client from the tray menu and watch the status line.

## Verification test
After saving changes, quit the client completely from the tray, reopen it, and wait 30 seconds. The tray icon should turn green and the status should read connected. Create a small test file in your sync folder and confirm it appears on the server.

## Rollback note
If the client still stays offline, revert any proxy changes you made and note the original values. If the issue persists,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your client log and the curl output. This **nextcloud client offline windows** issue is usually resolved by aligning the client's server address and proxy with the browser's working configuration.
