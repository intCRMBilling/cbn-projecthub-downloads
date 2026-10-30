# CBN ProjectHub downloads and user guide

[Download the latest Windows installer](https://github.com/intCRMBilling/cbn-projecthub-downloads/releases/latest) · [User guide](USER-GUIDE.md) · [Panduan Pengguna (PDF, Bahasa Indonesia)](https://github.com/intCRMBilling/cbn-projecthub-downloads/releases/download/v0.1.18/CBN-ProjectHub-0.1.18-Panduan-Pengguna-r2.pdf) · [All releases](https://github.com/intCRMBilling/cbn-projecthub-downloads/releases)

The current release is 0.1.27. Install it, approve publisher trust if setup requests it, then sign in with Microsoft. Installed copies from 0.1.14 onward update from **Settings → About CBN ProjectHub**. No separate login-configuration file or monthly configuration renewal is required. Initial Windows warnings/policies still apply; never bypass organizational security policy. Existing custom pilot profiles require explicit migration before normal Start-menu use. Database access and project permissions remain separate company-controlled setup.

This release is for internal Windows x64 use. Source is maintained in a private repository. Only the owner-approved public Microsoft tenant/client identifiers are bundled for login; no credentials, private keys, database settings or company documents are included. No Mac installer is published.

Releases contain installers and required update metadata. Keep latest.yml, release.json and blockmaps. GitHub-generated Source code archives contain only this public repository's documentation, not the private development repository.

Never upload credentials, private keys, database settings, user profiles, signed legacy provisioning or company documents here. Use the internal support channel for sensitive information. Versions 0.1.20 to 0.1.24 prepared the publisher-certificate transition. This release is signed with the new CBN ProjectHub Publisher certificate. If the automatic update says it could not be verified, download and run the installer once by hand and answer Yes when asked to trust CBN ProjectHub Publisher; automatic updates work again after that. The new certificate is valid until October 21, 2029.

Version 0.1.21 makes code audits read a set share of each module's code (by default 80% of the lines and files), continuing in passes until it is reached, so audits of large modules take longer than before. Version 0.1.22 adds archive, bulk delete and Trash for artifacts, short audit histories with View all, audits of both sides at the same time, a shared list of running audits, and Continue for an interrupted audit, with a progress bar of how much the AI has read.

Version 0.1.23 fixes clipped action menus so Delete stays reachable, with scrolling and keyboard navigation improvements.

Version 0.1.24 adds "Use SharePoint copy for all" for sync conflicts, embeds only project images in Word exports, serves Open in browser previews from this computer only with a strict content policy, refuses plain http Git remotes unless allowed, lets role managers govern shared project settings, and includes other hardening.

Version 0.1.25 improves stopped code audits: Continue picks the audit up with the same AI, Audit again starts over, and a new Cancel button closes the result without auditing again. Parallel audits now check the AI account once per batch, which fixes the "Claude Code is already running" error when both sides of a module were audited together.

Version 0.1.26 makes setup always install CBN ProjectHub for your own Windows account, in your user folder (`%LOCALAPPDATA%\Programs\CBN-ProjectHub`), without asking where to install or who to install it for. Choosing C:\Program Files used to fail with "Error opening file for writing"; that choice is no longer offered.

Version 0.1.27 makes writing in the Markdown editor easier (pasted screenshots become picture files, find and replace, pasting from Word keeps formatting, a formatting bar, an outline, spelling suggestions and several cursors), adds follow-up and bulk actions (continue a stopped audit, one status for several findings, read again or cancel several knowledge imports), and lets a SharePoint sync conflict keep your local copy. Setup still installs for your own Windows account in `%LOCALAPPDATA%\Programs\CBN-ProjectHub`.
