---
title: "Nextcloud Large File Upload Fails Near Completion on Windows: A Step-by-Step Fix"
description: "Troubleshoot a Nextcloud large file upload that stalls or restarts near the end on Windows by checking chunk size, server limits, and client logs, then verify with a test file."
seo_title: "Fix Nextcloud Large File Upload Fails Near Completion on Windows"
seo_description: "Troubleshoot a Nextcloud large file upload that stalls or restarts near the end on Windows by checking chunk size, server limits, and client logs, then verify with a test file."
keywords:
  - "nextcloud large file upload fails"
date: 2026-11-18T08:01:03+08:00
publishDate: 2026-11-18T08:01:03+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're uploading a large file with the Nextcloud Windows desktop client, and it stalls or restarts just before finishing instead of completing. This usually points to a chunking or timeout mismatch between the client and your self-hosted server.

## Check the client's chunk size and upload settings

Open the Nextcloud client settings, go to the General tab, and note the current chunk size. If it's set very high (for example, above 100 MB), lower it to 50 MB and apply. Then check the server's PHP upload limits: in your Nextcloud admin settings under Overview, look for the maximum upload size and PHP timeouts. If the file exceeds the server's limit, the upload will fail near the end. Increase `upload_max_filesize`, `post_max_size`, and `max_execution_time` in php.ini, then restart PHP.

## Inspect the client log for the exact failure

In the client settings, enable logging and reproduce the upload. Open the log file (typically in %APPDATA%\Nextcloud\logs) and search for the last chunk request. If you see a 413 error, the server rejected the chunk as too large. If you see a timeout, the server closed the connection before the final chunk. Each result tells you which limit to adjust: 413 means lower the chunk size; timeout means raise the execution time.

## Verification test

Create a test file slightly larger than the one that failed, upload it through the client, and confirm it appears fully synced on the server. If it completes, the fix is working. If it still fails, repeat the log check with the new file.

## Rollback and recovery

Before changing php.ini, back up the original file. If the upload still fails after adjustments, restore the backup and revert the client chunk size to its previous value to avoid breaking other syncs. For persistent cases,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your log excerpt. This approach resolves most cases of **nextcloud large file upload fails** without a full reinstall.
