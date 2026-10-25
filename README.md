# CBN ProjectHub downloads and user guide

[Download the latest Windows installer](https://github.com/intCRMBilling/cbn-projecthub-downloads/releases/latest) · [User guide](USER-GUIDE.md) · [Panduan Pengguna (PDF, Bahasa Indonesia)](https://github.com/intCRMBilling/cbn-projecthub-downloads/releases/download/v0.1.23/CBN-ProjectHub-0.1.23-Panduan-Pengguna.pdf) · [All releases](https://github.com/intCRMBilling/cbn-projecthub-downloads/releases)

The current release is 0.1.23. Install it, approve publisher trust if setup requests it, then sign in with Microsoft. Installed copies from 0.1.14 onward update from **Settings → About CBN ProjectHub**. No separate login-configuration file or monthly configuration renewal is required. Initial Windows warnings/policies still apply; never bypass organizational security policy. Existing custom pilot profiles require explicit migration before normal Start-menu use. Database access and project permissions remain separate company-controlled setup.

This release is for internal Windows x64 use. Source is maintained in a private repository. Only the owner-approved public Microsoft tenant/client identifiers are bundled for login; no credentials, private keys, database settings or company documents are included. No Mac installer is published.

Releases contain installers and required update metadata. Keep latest.yml, release.json and blockmaps. GitHub-generated Source code archives contain only this public repository's documentation, not the private development repository.

Never upload credentials, private keys, database settings, user profiles, signed legacy provisioning or company documents here. Use the internal support channel for sensitive information. Versions 0.1.20 to 0.1.23 prepare the publisher-certificate transition. Setup may ask once to trust "CBN ProjectHub Publisher"; choose Yes so future updates signed by that publisher keep working. The current signing certificate expires January 13, 2027.

Version 0.1.21 makes code audits read a set share of each module's code (by default 80% of the lines and files), continuing in passes until it is reached, so audits of large modules take longer than before. Version 0.1.22 adds archive, bulk delete and Trash for artifacts, short audit histories with View all, audits of both sides at the same time, a shared list of running audits, and Continue for an interrupted audit, with a progress bar of how much the AI has read.

Version 0.1.23 fixes clipped action menus so Delete stays reachable, with scrolling and keyboard navigation improvements.
