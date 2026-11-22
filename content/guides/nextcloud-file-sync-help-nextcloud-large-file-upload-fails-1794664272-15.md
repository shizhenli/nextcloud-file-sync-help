---
title: "Nextcloud Large File Upload Fails Near Completion on Windows: Diagnose the Stall"
description: "Troubleshoot a self-hosted Nextcloud Windows client when large uploads stall or restart near the end. Check chunk size, timeouts, and server limits, then verify with a test file."
seo_title: "Fix Nextcloud Large File Upload Fails Near Completion on Windows"
seo_description: "Troubleshoot a self-hosted Nextcloud Windows client when large uploads stall or restart near the end. Check chunk size, timeouts, and server limits, then verify with a test file."
keywords:
  - "nextcloud large file upload fails"
date: 2026-11-22T10:00:59+08:00
publishDate: 2026-11-22T10:00:59+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You are uploading a large file from the Windows desktop client to your self-hosted Nextcloud, and it stalls or restarts near the end instead of completing.

## Check the client log for the last chunk

Open the Nextcloud client, go to Settings, then Logs. Look for the last upload entry and note whether it shows a chunk number, a timeout, or a connection reset. If the log stops at a chunk near the total, the transfer is failing during chunk assembly, not at the start. A repeated retry of the same chunk points to a timeout or size limit rather than a credentials problem.

## Confirm server upload limits

On the server, check php.ini for upload_max_filesize, post_max_size, and max_execution_time. If max_execution_time is low, large chunks can be cut off before assembly. Also check the reverse proxy for client_max_body_size and proxy_read_timeout. Raise these values, restart PHP and the proxy, then retry. If the log shows a 413 response, the proxy limit is the cause.

## Verify with a controlled test

Create a test file about half the size of the failing upload. Upload it through the desktop client and watch the log. If it completes, the original file is crossing a limit; if it also stalls near the end, the limit is lower than expected. This isolates whether the issue is file size or a general timeout.

## Recovery note

If a partial upload remains, delete the incomplete file in the web interface before retrying, so the client does not resume a corrupt chunk set. Keep the original file until the test succeeds.

If these checks do not resolve your **nextcloud large file upload fails**, gather the client log and server limits, then

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
