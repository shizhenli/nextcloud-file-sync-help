---
title: "Nextcloud Two-Way Sync Test: When Both Sides Edit and Conflict Copies Appear"
description: "A practical troubleshooting guide for self-hosted Nextcloud on Windows when both sides have edits and the client creates conflict copies. Run a controlled nextcloud two way sync test to verify expected behavior."
seo_title: "Nextcloud Two-Way Sync Test: Fix Conflict Copies from Dual Edits"
seo_description: "A practical troubleshooting guide for self-hosted Nextcloud on Windows when both sides have edits and the client creates conflict copies. Run a controlled nextcloud two way sync test to verify expected behavior."
keywords:
  - "nextcloud two way sync test"
date: 2026-11-21T14:43:13+08:00
publishDate: 2026-11-21T14:43:13+08:00
draft: false
categories:
  - "File Sync"
category_slug: "file-sync"
---

You edited a file on your Windows PC while a colleague changed the same file on the server, and now the Nextcloud desktop client has left you with conflict copies instead of the merged version you expected.

## Confirm the conflict pattern

Open the local sync folder and look for files ending in `conflicted copy`. Check the server side in the Nextcloud web interface for the same file. If both locations show different modification times and neither is a clear winner, the client is behaving as designed: it cannot merge text automatically, so it preserves both versions. This is the expected outcome of a two-way sync conflict, not a sync failure.

## Run a controlled **nextcloud two way sync test**

Create a small test folder with one plain text file. Edit it only on the Windows client and wait for the green checkmark. Then edit the same file only in the web interface and wait for the client to poll. You should see one updated file and no conflict copy. Now edit both sides within the same sync interval. The client should produce exactly one conflict copy. If it produces more than one, or none, note the timestamps and file names.

## Verify and recover

After the test, delete the test folder. For real conflicts, open both copies, compare the intended changes, and save the correct version under the original name. Move the conflict copy to a backup folder before deleting it. If the client keeps generating conflict copies without dual edits, pause sync, check server and client clocks, then resume.

If the pattern persists after these checks,

![Network server cabling representing the Nextcloud storage backend](/images/service-detail-960.webp "Nextcloud two-way sync verification")

[Ask for help](/#consult) with your client log and the test results.
