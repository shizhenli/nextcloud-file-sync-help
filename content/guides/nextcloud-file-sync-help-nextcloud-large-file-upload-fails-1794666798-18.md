---
title: "Nextcloud Large File Upload Fails Near the End: A Practical Fix"
description: "Fix a self-hosted Nextcloud Windows client when large uploads stall or restart near the end. Step-by-step checks for chunk size, timeouts, and recovery."
seo_title: "Nextcloud Large File Upload Fails Near Completion: Troubleshooting Guide"
seo_description: "Fix a self-hosted Nextcloud Windows client when large uploads stall or restart near the end. Step-by-step checks for chunk size, timeouts, and recovery."
keywords:
  - "nextcloud large file upload fails"
date: 2026-11-28T21:42:25+08:00
publishDate: 2026-11-28T21:42:25+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are uploading a large file with the Windows desktop client to your self-hosted Nextcloud, and it stalls or restarts near the end instead of completing.

## Check chunk size and timeouts first

Open the client settings and look at the network tab. If the chunk size is very large (e.g., above 100 MB), the server may time out before a chunk finishes. Reduce it to 10–50 MB and retry. Also check your web server's upload and timeout limits: for nginx, `client_max_body_size` and `fastcgi_read_timeout`; for Apache, `LimitRequestBody` and `Timeout`. If these are lower than your chunk size or shorter than the upload duration, the connection drops near completion. Increase them to match your expected file size and network speed, then restart the web server.

## Verify with a controlled test

Create a test file of similar size and upload it through the client. If it completes, the issue was chunk or timeout related. If it still fails, check the client log (Settings > Logs) for HTTP 413 or timeout errors. A 413 confirms the server limit is still too low.

## Recovery note

If an upload is stuck, cancel it in the client, delete the partial file from the server's upload folder (usually `data/username/uploads`), and restart the client. This prevents repeated retries from consuming resources.

## When to escalate

If adjusting chunk size and server limits does not resolve the failure, the issue may be a proxy buffering problem or a disk quota limit. For a guided diagnosis of your specific setup,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult). This **nextcloud large file upload fails** scenario is often resolved by aligning client chunk size with server timeouts.
