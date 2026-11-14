---
title: "Nextcloud Sync Stuck at Conflict Creation: Diagnose Status, Permissions, and Conflicts"
description: "Fix a Windows Nextcloud client stuck at the two-way sync conflict creation step. Check status, permissions, and conflict files to restore expected behavior."
seo_title: "Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts"
seo_description: "Fix a Windows Nextcloud client stuck at the two-way sync conflict creation step. Check status, permissions, and conflict files to restore expected behavior."
keywords:
  - "Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts"
date: 2026-11-14T19:21:33+08:00
publishDate: 2026-11-14T19:21:33+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You're running a self-hosted Nextcloud with the Windows desktop client, and sync appears stuck right at the two-way sync creates conflict files step, leaving you with conflict copies instead of the merged version you expected.

## Check the client status first

Open the Nextcloud client window and look at the activity list. If the last entry shows a conflict file name like `filename (conflicted copy).txt`, the client has already created the copy and is waiting for you to resolve it. That is not a hang; it is a paused state. If the status is still "Waiting for sync" with no conflict entry, the client has not reached the conflict step yet, so the problem is upstream.

## Verify permissions on both sides

On the server, confirm the sync account has write access to the target folder. A read-only share will let the client download edits but block the merge, so it creates conflict copies. On Windows, right-click the local sync folder, choose Properties, and confirm your user has Full control. If either side is read-only, correct it before continuing.

## Inspect the conflict files

Open the folder containing the conflict copy. Compare the modification times: the newer file is usually the intended version. Rename the conflict copy to a backup name, then rename the intended file to the original name. Do not delete either file yet.

## Verification test

Create a small text file on the server and edit the same file locally while the client is paused. Resume sync. The expected result is a single merged file with no new conflict copy. If a conflict copy appears again, permissions or timestamps are still mismatched.

## Recovery note

If the merge produces the wrong content, restore the backup conflict copy and pause sync before retrying. For a controlled diagnosis of this **Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts** scenario,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult).
