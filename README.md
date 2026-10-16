# CBN ProjectHub downloads and user guide

[Download Windows 0.1.14](https://github.com/intCRMBilling/cbn-projecthub-downloads/releases/download/v0.1.14/CBN-ProjectHub-0.1.14-x64-nsis.exe) · [User guide](USER-GUIDE.md) · [All releases](https://github.com/intCRMBilling/cbn-projecthub-downloads/releases)

Install, approve publisher trust if setup requests it, then sign in with Microsoft. No separate login-configuration file or monthly configuration renewal is required from 0.1.14 onward. Initial Windows warnings/policies still apply; never bypass organizational security policy. Existing custom pilot profiles require explicit migration before normal Start-menu use. Database access and project permissions remain separate company-controlled setup.

This release is for internal Windows x64 use. Source is maintained in a private repository. Only the owner-approved public Microsoft tenant/client identifiers are bundled for login; no credentials, private keys, database settings or company documents are included. No Mac installer is published.

Releases contain installers and required update metadata. Keep latest.yml, release.json and blockmaps. GitHub-generated Source code archives contain only this public repository's documentation, not the private development repository.

Never upload credentials, private keys, database settings, user profiles, signed legacy provisioning or company documents here. Use the internal support channel for sensitive information. Existing publisher trust expires January 13, 2027 and requires a reviewed rotation before then.
