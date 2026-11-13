---
title: 'Nextcloud Sync Stuck: Check Status, Permissions, and Conflicts'
description: A controlled Nextcloud desktop sync test that separates a stuck client from permission and conflict problems.
seo_title: Nextcloud Not Syncing? Status, Permissions, Conflict Checks
seo_description: A controlled Nextcloud desktop sync test that separates a stuck client from permission and conflict problems.
keywords:
- nextcloud not syncing
- nextcloud sync stuck
- nextcloud conflict files
date: '2026-11-13'
draft: false
categories:
- File Sync
category_slug: file-sync
---

<p>Nextcloud sync failures often look alike in the tray icon. Use one folder and read the actual client state before changing server configuration.</p>
<h2>Before you start</h2><ul>
<li>Nextcloud desktop client version</li>
<li>One account with access to a test folder</li>
<li>Server URL and the client's recent log</li>
<li>Permission to create and delete a test file</li>
</ul>
<h2>Step-by-step checks</h2>
<h3>Step 1: Capture the client state</h3>
<p>Open the Nextcloud client's activity window and note the last completed action, the current error, and the time. Export or copy the relevant log lines before restarting.</p>
<p><strong>Check:</strong> You have a timestamped error or a clear “up to date” state.</p>
<h3>Step 2: Create a clean test folder</h3>
<p>Make a new folder on the server and connect only this client to it. Do not reuse a folder with existing conflict files or selective-sync exclusions.</p>
<p><strong>Check:</strong> The client shows the new folder with no excluded subfolders.</p>
<h3>Step 3: Test local to server</h3>
<p>Create a small text file locally, wait for the client to report completion, and open the server copy in a browser. Compare content and modification time.</p>
<p><strong>Check:</strong> The server copy appears with the same content.</p>
<h3>Step 4: Test server to local</h3>
<p>Edit the server copy, wait for the client to fetch it, and open the local file. If only one direction works, record the permission or error message.</p>
<p><strong>Check:</strong> The local copy reflects the server edit after a refresh.</p>
<h3>Step 5: Check restart persistence</h3>
<p>Restart the client, make one more edit, and confirm it syncs without a manual rescan. Review whether a conflict file was created.</p>
<p><strong>Check:</strong> The change syncs after restart and no new conflict appears.</p>
<h2>Verify the result</h2>
<p>Both directions work, the timestamps are plausible, and no new conflict file appears after restart. Keep the test folder until the next normal sync cycle succeeds.</p>
<h2>Rollback</h2>
<p>Remove only the test folder after verification. Do not delete conflict files or server data as part of the test.</p>
<p><a href="/#consult">Ask for help with this exact symptom</a> · <a href="/guides/">All troubleshooting guides</a></p>
