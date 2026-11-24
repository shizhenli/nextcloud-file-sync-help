---
title: "Nextcloud Server Not Reachable After an Update: Restore Desktop Client Access"
description: "Self-hosted Nextcloud Windows client says server unreachable after an update, but web UI loads. Follow these checks to restore sync."
seo_title: "Fix Nextcloud Server Not Reachable After Update (Windows Client)"
seo_description: "Self-hosted Nextcloud Windows client says server unreachable after an update, but web UI loads. Follow these checks to restore sync."
keywords:
  - "nextcloud server not reachable"
date: 2026-11-24T08:01:00+08:00
publishDate: 2026-11-24T08:01:00+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You updated your self-hosted Nextcloud server, and now the Windows desktop client reports the server is unreachable even though the web interface still loads.

## Confirm the failure boundary

Open the desktop client and look at the account status. If it shows a red error or “server not reachable,” click the account menu and choose “Check server status” or simply retry the connection. A quick failure (seconds) points to DNS, TLS, or port blocking; a long hang suggests a service or firewall drop. Also open `https://your-server/status.php` in a browser. If it returns JSON with `installed: true`, the web stack is up, so the problem is likely client-side or network-path specific.

## Check the client’s server URL and certificate

In the client settings, verify the server address exactly matches the working web URL, including `https://` and any subpath. Then test the certificate: in Windows, open the site in Edge and check the padlock. If the update replaced the certificate with a self-signed or internal CA certificate, the desktop client may reject it while the browser shows a warning you clicked through. Import the new root CA into Windows Trusted Root Certification Authorities, then restart the client.

## Test network reachability from the client machine

Run `Test-NetConnection your-server -Port 443` in PowerShell. `TcpTestSucceeded : True` means the port is open; `False` means a firewall, NAT rule, or reverse proxy changed during the update. If the port is open, run `curl -I https://your-server/status.php` and compare the HTTP status with the browser result.

## Roll back if the update changed the endpoint

If the checks show the update altered the reverse proxy path, TLS termination, or trusted domains, restore the previous configuration from backup and restart the web server. This is a safe recovery step before deeper diagnosis.

If the client still reports **nextcloud server not reachable** after these checks,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your client log and `status.php` output.
