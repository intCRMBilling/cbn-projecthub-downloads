# CBN ProjectHub user guide

Applies to **CBN ProjectHub 0.1.17 for Windows x64**. Features needing company services or an AI provider are conditional on those services being configured and on your permissions. Screens may differ in later releases.

The installer is public; company access is not. Application source is maintained separately in a private repository. This guide contains no company connection settings, account identifiers, private keys or operational examples. This release retains the existing installation identity for update compatibility and includes company Microsoft sign-in without a separate configuration file. Publisher trust remains required for verified updates and setup offers an explicit consent step. No Mac installer is currently published.

## Contents

1. [Install and sign in](#1-install-and-sign-in)
2. [Connect the company database](#2-connect-the-company-database)
3. [Create, open and switch projects](#3-create-open-and-switch-projects)
4. [Navigate and organize modules](#4-navigate-and-organize-modules)
5. [Create and edit artifacts](#5-create-and-edit-artifacts)
6. [Versions, reviews and approvals](#6-versions-reviews-and-approvals)
7. [Diagrams, designs and specifications](#7-diagrams-designs-and-specifications)
8. [Attachments, links and export](#8-attachments-links-and-export)
9. [Knowledge and source documents](#9-knowledge-and-source-documents)
10. [Team, invitations and synchronization](#10-team-invitations-and-synchronization)
11. [AI assistance and external clients](#11-ai-assistance-and-external-clients)
12. [Checks and project audit](#12-checks-and-project-audit)
13. [Settings reference](#13-settings-reference)
14. [Application updates](#14-application-updates)
15. [Keyboard shortcuts](#15-keyboard-shortcuts)
16. [Recovery and troubleshooting](#16-recovery-and-troubleshooting)

## 1. Install and sign in

1. Download the installer from the [latest Windows release](https://github.com/intCRMBilling/cbn-projecthub-downloads/releases/latest). No GitHub account is needed. Follow the internal operator's hash/publisher verification guidance. Windows may still warn or block initial execution of a self-signed installer; do not bypass organizational policy.
2. Run setup. If the publisher is not already trusted, setup asks permission to trust **CBN ProjectHub Local Test** for your Windows account. Review the publisher and expiry before agreeing. No private key is installed and no manual certificate-manager steps are required. If you decline or Windows blocks trust, setup reports the issue; automatic updates cannot work until trust is approved. Silent setup never adds trust automatically.
3. Start **CBN ProjectHub** from the Start menu. Click **Sign in with Microsoft**, complete normal browser sign-in/MFA and return to the app. Version 0.1.14 and later do not need auth-provisioning.json or monthly configuration renewal. Microsoft session expiry, account policy and permissions still apply; registration changes are delivered through reviewed app updates.
4. If browser sign-in is waiting, use Cancel before retrying. Use saved-session recovery only when indicated. Never paste passwords, tokens or MFA codes into chat or a public issue.
5. Existing custom pilot profiles still need an explicit verified migration before ordinary Start-menu use; do not merge populated profiles. A fresh employee must use their own Microsoft login, not another person's profile. Obtain database settings privately after login.
6. Use the account menu to sign out. A restored session may require online confirmation before a protected action. Downloading an installer never grants project membership or database access.

After sign-in, **Settings** is available even before a workspace or database is ready, for application updates. Full project Settings becomes available inside an open workspace.

## 2. Connect the company database

Project access requires the company PostgreSQL service, including when artifact files are stored locally. This release is not a fully offline project editor.

1. Obtain connection details and the chosen transport mode from your administrator privately. New connections default to **No TLS**. This mode does not encrypt database traffic; choose it explicitly for a server without TLS. Existing saved TLS connections are preserved and never silently downgraded. Expand **Server uses TLS?** when the server supports TLS. Do not copy example values from documentation or put real values in a GitHub issue.
2. On the company database setup screen, enter the provided connection details. Use **Test and save** to test the entered details before saving. A failed test preserves the working configuration; **Save anyway** is an explicit separate choice. The summary provides connection and recovery actions.
3. Initialize membership only when the application explicitly requires it and the administrator authorizes it. Do not repeatedly initialize a database to fix a network or login error.
4. Connect the approved office VPN if this database needs it. The app can offer **Open FortiClient** when appropriate; it does not install or purchase a VPN service. Use the configured transport mode; a TLS failure does not automatically switch to No TLS.
5. With multiple database profiles, select the intended database. Project lists and the remembered project follow that selection. Switching may close the current project and can be refused while work or a review is pending. Save or resolve the pending work first.

The database status indicator can be clicked to check again. Database access does not replace SharePoint/project membership. Changing a saved connection target, username or trust may require entering its password again. Administrator-managed service acceptance is separate from installer/update verification.

## 3. Create, open and switch projects

Choose the intended storage option on the workspace picker:

- **Local:** create a project workspace in an approved folder, or open an existing workspace folder. Enter the project's code, name and description when creating it. Do not select a folder merely because it contains unrelated documents. Local access does not require a project invitation, but still requires Microsoft sign-in and the company database readiness checks.
- **SharePoint:** select the organization-provided location through the supported picker and open/create only where your permissions allow. Shared project membership and SharePoint authorization must both be valid. A managed cache is not an independent local project.

Each project workspace contains its modules and artifact files. Use the project name in the top bar to switch projects. A failed switch should leave the current workspace available. To close a project, use **Settings → Workspace**. Closing a project does not mean deleting its files.

Keep project folders in the approved storage location. Do not copy application profiles or encrypted account settings between PCs. Use the application's SharePoint synchronization for managed projects instead of manually treating its cache as a shared folder.

## 4. Navigate and organize modules

### Pin modules

Hover or keyboard-focus a module row to show its **Pin** button. Pinned modules stay at the top,
in pin order, including inactive modules. Click the filled pin to unpin. The module page also
offers **More → Pin to the top of Modules / Unpin from the top of Modules**. The collapsed rail
keeps the same order and identifies pinned modules in its tooltip.

The five recent active modules and **View all modules** exclude pins; a selected module remains
visible. Pins belong to your signed-in Microsoft account on this computer and survive restarts,
but do not synchronize across computers. Up to 50 modules per account and 20 accounts are kept.
Pins from other projects still occupy slots. Unpin one when the list is full. A save failure is
reported explicitly; the failed change is not shown as saved.

1. Open the project overview to see modules, artifact counts and progress information.
2. Create modules for areas of the project, then open a module to add and browse artifacts. Use the available module actions to organize hierarchy, rename or maintain relationships. Review deletion confirmations and their scope before proceeding.
3. Use the navigation tree to move between modules and artifact types. Use the top bar/project switcher to change projects, not module actions.
4. Use **Search** or **Ctrl+K** to find artifacts, jump to modules/pages or run available actions. Review result titles and context before opening them; knowledge search is also available on the Knowledge page.
5. On an artifact, use its details tabs for links, history, checks and activity. **Focus** hides surrounding navigation/details; Escape exits Focus. Layout controls can show/hide navigation and details without changing project data.

Module relationships describe dependencies or related areas. When AI proposes relationships, review the proposal and accept only the intended changes; a suggestion is not established project truth.

## 5. Create and edit artifacts

Open the intended module and use its new-artifact action. Select a type, give it a clear title/slug and review the starting template. The supported types are:

| Type | Purpose                         |
| ---- | ------------------------------- |
| MB   | Module brief                    |
| PC   | Project charter                 |
| PRD  | Product requirements document   |
| DSN  | Design                          |
| TC   | Test cases                      |
| BPMN | BPMN process model              |
| BPF  | Business process flow           |
| SPEC | Story/development specification |
| OTH  | Other supporting artifact       |

Edit drafts in the appropriate editor. Markdown supports editing and preview; supported preview cells can be edited in place. **Ctrl+S** saves the current draft, and editors also perform their supported autosave. Check the save/error state before switching, closing or sharing. Preview is a rendering of the artifact, not a separate published copy.

Files are the source of truth. If a file changes externally while you have unsaved edits, stop and review the conflict/reload prompt. Reload can discard the pending editor buffer; do not repeatedly save over someone else's version. Invalid diagram/document data should be repaired or restored deliberately rather than replaced with an empty file.

Use the artifact menu for rename/delete actions where available. Confirm the exact target; deleting an artifact is different from removing a link or attachment reference.

## 6. Versions, reviews and approvals

1. Finish a draft, inspect its content and run relevant checks.
2. Use the status/workflow actions offered for your role. The artifact shows its current status and the available next step; open **All status steps** to understand the workflow.
3. Published versions are preserved. Use the next-version action to make changes rather than trying to overwrite published bytes.
4. Reviewers should read the version and its changes before taking the allowed review/approval action. **In review**, **Approved** and **Superseded** describe workflow state; availability depends on policy and role.
5. Use version history/diff to compare versions. Where permitted, **Mark developed** records which approved version was implemented; it is distinct from document approval. Compare against that baseline when reviewing later changes.
6. Read the activity history for authorship, status and version changes. The signed-in Microsoft identity supplies attribution; changing display text is not a substitute for another person's approval.

Completeness findings help review but are not a guarantee of business correctness. Respect the effective policy displayed in **Settings → Roles & workflow** rather than assuming every team member can approve or publish.

## 7. Diagrams, designs and specifications

### BPMN and business process flow

Open BPMN artifacts in the BPMN editor. Use the searchable element menu to place the intended BPMN element, connect it and edit its properties. Save, reopen and inspect the model before publishing. Use the BPF canvas for free-form process flows; save and review the diagram as an artifact version. A malformed BPF should show a load error, not silently become a new blank diagram.

### Design workbench

Open a DSN artifact to use the supported design workbench. HTML designs can contain a page set: create/select pages, edit and preview them, then save and review the whole set. When available, generate designs from the PRD using a connected approved AI provider. Review proposed/generated files before adopting and publishing them.

Use **Playbooks & templates → Design system** to import/preview supported design-system files, inspect changes/history and apply approved changes to selected drafts. Applying a design system is an explicit change, not an instruction to rewrite published versions.

### Story specifications

In a module, the Specs area groups PRD stories by epic and shows their specification state, source alignment and findings. Resolve the displayed prerequisites before **Generate specs**; the released workflow requires an approved design. Select the intended stories, review the plan and monitor progress. After source changes, review stale indications and use **Regenerate stale** where appropriate. Generated specs remain drafts for human review. Inspect source/baseline information rather than assuming an older spec still matches the current PRD.

## 8. Attachments, links and export

- Use attachment controls to import/reuse files and link them to the artifact. Review previews and reference scope. Replacing a draft attachment must not modify a published version's bytes; unlinking a reference is not the same as deleting a shared asset everywhere.
- Use the artifact menu's **Add link** action, choose the relationship and target, then inspect the Links details tab and backlinks. Remove an incorrect relationship from its source.
- Use supported export actions to create a separate deliverable such as Word. Word export uses Pandoc and may require that approved tool to be available locally. An unavailable exporter should be resolved with the operator, not by uploading company documents to an arbitrary conversion site.
- Exporting is not publishing/approving the source artifact. Check the generated file before sending it through an authorized channel.

## 9. Knowledge and source documents

1. Open **Knowledge** to import approved Word, Excel, PowerPoint, PDF or image source files into the project knowledge collection.
2. Review the selected files and extraction/import job status. Text extraction occurs on the device; scanned/image content may need OCR. Inspect extracted text and citations, especially where OCR is uncertain.
3. Search the knowledge collection and open matching passages with their source citations. A missing passage may mean extraction failed or the search did not match; it is not evidence that the source never contained the information.
4. When converting knowledge into an artifact with AI, choose the intended output type/module, review the generated draft and citations, then explicitly save/file it. Do not assume imported reference material is an approved artifact.

Files attached only to an AI conversation are separate from project knowledge. Promote a chat attachment into knowledge only when intended. Imported content can later be supplied to an AI provider when you request AI work; follow your organization's data-sharing policy.

## 10. Team, invitations and synchronization

Open **Team** for project participants and roles. Available roles include Steering Chair, System Analyst, Product Owner, Business Sponsor, Advisor, Project Manager, Business Analyst, Developer, Quality Assurance, Designer and Stakeholder. A person may hold multiple roles; effective permissions follow workflow policy.

For a shared project, authorized members create invitations from the open project. Review the recipient and roles before creating one. The app renews project access first, so an expired access check does not require a preliminary sync; a failed renewal still prevents the invitation. A registered colleague accepts a pending invitation from the invitation interface. An email invitation is matched when its recipient signs in with that email address. The app does not send an email: share any displayed guest-onboarding link yourself. An authorized inviter can revoke a pending invitation. Installing the app alone does not grant project membership; inspect the invitation state.

SharePoint projects synchronize saved changes and receive colleague changes automatically when authenticated/connected. Use the sync status and explicit sync controls when available. The first synchronization can hold editing; ongoing edits or AI operations can defer a synchronization pass. Resolve conflicts explicitly before continuing. Signing out stops automatic synchronization.

If the connection drops, editing may pause while the unsaved buffer remains on screen. Restore the required network/Microsoft/database access and use the recovery action. Do not close a paused editor on the assumption that its unsaved text is already on disk.

## 11. AI assistance and external clients

AI is optional. CBN ProjectHub does not supply an AI subscription and does not collect AI-vendor API keys. Use only an already approved provider/account and permitted data. Provider subscriptions, quotas and usage charges are separate; this guide does not authorize buying or enabling them.

1. Open **Settings → AI assistance**. Detect an existing supported Claude/OpenAI agent installation, or review the offered official setup instructions. Any install action or custom executable path should be reviewed locally by the user/IT. Sign in through the provider's own flow.
2. Select the provider/model available to your account. A model catalog entry is not proof of entitlement. If a saved model is unavailable, choose a supported model or retry the catalog explicitly.
3. Open the AI chat, write the request and review the context/attachments before **Ctrl+Enter**. Chat attachments are read/extracted before sending; only attach information approved for the chosen provider.
4. Monitor progress, cancel when needed and inspect all generated changes. AI-written artifacts are drafts, attributed as AI and logged; they do not replace review/approval. Manual editing remains available when AI is disconnected, subject to normal workspace connectivity.
5. Use conversation history to reopen a transcript, start a new chat or explicitly file a transcript as an OTH draft. Confirm conversation deletion; it does not mean all related project artifacts have been deleted.
6. Artifact audit playbooks start a marked conversation with relevant context. Batch audit/spec actions show progress and require review of their output. Read the selected playbook and scope before starting.
7. AI illustrations are generated/validated as drafts; inspect them and attach them deliberately. Content-language views can offer a read-only translated view without changing the original artifact; verify meaning against the source.
8. For an approved external AI client, use the app's MCP setup snippets for the open workspace. The companion exposes workspace operations under its access rules; AI writes remain drafts. Do not paste private paths or project contents into public support requests.

If setup fails, follow the local reconnect/recovery instructions and review safe diagnostics. Do not bypass provider authentication or put keys in project files.

## 12. Checks and project audit

Open an artifact's checks/details area to inspect completeness findings. Re-check after saving a correction. The project **Audit** page provides coverage/gap views, a module/type matrix, filters and explanations of scores/findings. Filter by module, artifact type, finding or search text, then open the referenced artifact to investigate.

Use audit/batch plans to review the selected scope before starting AI work. Inspect progress, failures and resulting drafts. A score is explained by the applicable rules and evidence; it is not a certification or automatic permission to publish. Review relationship gaps and stale-source findings alongside content quality.

### Code repositories and code audits

Code audits are available from 0.1.15. Shared permissions, finding status and reference freshness need the four code-audit tables and grants described in the internal PostgreSQL readiness guide. Until an administrator prepares them, the app explains which shared features are unavailable. Local automated acceptance does not replace testing with your company's repositories, installed AI providers and a second member.

A code audit reads one module's frontend or backend code and files a report of findings, each with its reason, impact and recommendation, for the developers to follow up. CBN ProjectHub never changes, runs, builds or tests the code, never pulls, checks out, commits or pushes, and never fixes anything itself.

1. **Register the repositories.** Open **Code** in the side bar. With **Manage code repositories**, add the project's one frontend repository and each backend repository (its GitLab URL, without a password, and its default branch or tag); a backend repository lists the modules it serves. In **Modules**, give each module's frontend and backend folders, the shared code the audit may read for context, extra exclusions, or mark a side Not applicable. The **YAML** view shows the same mapping, and **History** shows who changed what. When someone else saved the mapping while you were changing it, your save is refused and the newer version is shown; in the YAML view your text stays below it to copy from. **Repositories** also shows each repository's open findings, from the newest audit of each module; a finding in shared code counts once.
2. **Choose this laptop's checkout.** Each person clones the repositories with their own git and chooses the clone's top folder in **Code → Repositories** (**Choose folder**). CBN ProjectHub checks that a remote of the folder is the registered repository and shows **Matches (origin)**; until you choose one it shows **Not set on this laptop**. Git 2.31 or later is needed; when it is not found, **Choose git…** on the Code page or **Settings → Account** lets you choose `git.exe`. A partial ("blobless") clone is read only as far as it has the files; CBN ProjectHub never downloads missing ones.
3. **Designate a code auditor.** Running audits is for designated code auditors by default. In **Settings → Roles & workflow → Code audit**, those who may manage roles choose the auditors and who holds each of the four permissions; in a local project you can designate yourself. An auditor who has left the project is shown so you can untick them.
4. **Audit.** On the module page, **Audit code** opens a preview: the sides, the branch, tag or commit (or your working folder with uncommitted changes), whether to fetch first, and then exactly what will be read — the commit, the files in scope and shared, which files were left out and why, and the playbook. When the fetch fails, the preview says why and when this laptop last fetched the branch. Files that hold secrets by their name (such as `.env` or private keys) are never read, and secret values in other files are removed before anything is sent. The preview says that the listed files go to your own signed-in AI account. **Start audit** runs it. **Stop** (on the module page or the Audit page) ends it: a stopped run files no report, unless the AI had already filed one, which is then linked. If the AI fails early after valid findings, CBN ProjectHub files a partial report so they are not lost; **Retry** runs the failed or stopped sides again. In working-folder mode the report says whether your files changed while the audit ran.
5. **Follow up.** The report is an AI draft in the module, and it is never edited — not by the AI and not by hand; a new audit gives a new report. Its **Findings** tab shows whether the report is still current (the code, and the playbook and mapping, separately), filters, each finding with its GitLab links and "also affects" for shared code, and the conversation when the audit ran on your laptop under your account. A finding whose citation could not be checked is shown as **Cannot verify**, never as proven. With **Change finding status**, mark a finding Fixed, False positive or Accepted risk with a reason; a later audit keeps the status of the same finding and shows Reopened when a fixed one is found again.

Code-audit playbooks are listed separately in **Settings → Playbooks & templates**; changing them (also restoring or resetting from **History**) needs **Edit code-audit playbooks**, and their operating rules cannot be edited away. A playbook edited while an audit runs takes effect from the next audit.

## 13. Settings reference

| Section               | What to do there                                                                                                                                                                                                                                                                                   |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Account               | Inspect the signed-in identity and author attribution, select git for code audits, and sign out from the account menu.                                                                                                                                                                             |
| AI assistance         | Configure/detect provider tools, connection/model preferences and external-client MCP setup.                                                                                                                                                                                                       |
| Playbooks & templates | Review/edit permitted playbooks, new-artifact templates, completeness and project coverage/link rules, design-system inputs, spec house rules and field-length rules. Preview imports and use history/reset deliberately. Project templates take precedence over workspace, then bundled defaults. |
| Roles & workflow      | Read effective permission rules; authorized shared-project role managers can edit the policy, designate code auditors and configure the four code-audit permissions.                                                                                                                               |
| Databases             | Manage the account's local connection profiles and choose the active database. Keep real settings private.                                                                                                                                                                                         |
| Workspace             | Inspect the workspace location/storage information and close the project.                                                                                                                                                                                                                          |
| About CBN ProjectHub  | Check version/schema information and application update controls.                                                                                                                                                                                                                                  |

Rebuild index, where offered, reconstructs artifact metadata/search from files. It is not a backup restore and does not grant/change project membership. Backups must include the actual approved workspace files/assets and use the organization's database backup procedures separately.

## 14. Application updates

1. Sign in and open **Settings** on the workspace picker/database-setup screen, or **Settings → About CBN ProjectHub** inside a project.
2. The app checks automatically. Use **Check for updates** when enabled; it is disabled during an active check/download.
3. Wait for a verified update to be ready. **Later** postpones installation; **Show update** returns to the ready state.
4. Save/resolve pending work, then choose **Restart to update**. The app verifies the installer, closes safely, installs and opens again automatically. Ordinary quit does not authorize installation.
5. Confirm the new version. If verification fails, do not manually force the rejected download to run; contact the operator with only the safe error code.

The owner reports successful second-PC updates through 0.1.11, automatic reopening and preserved login. Each additional PC needs its own approved trust and login setup. The existing publisher certificate expires on 2027-01-13 and still needs a reviewed rotation before then. Version 0.1.14 removes monthly login-configuration renewal; it does not extend or rotate that publisher certificate.

Release metadata (`release.json`, `latest.yml`, `.blockmap`) supports the updater and should not be deleted. Users download the EXE; the app handles metadata. GitHub's Source code archives are snapshots of this public documentation repository, not the private application repository.

## 15. Keyboard shortcuts

| Keys         | Action                                            |
| ------------ | ------------------------------------------------- |
| Ctrl+K       | Search/jump to a module, artifact, page or action |
| Ctrl+B       | Show/hide navigation                              |
| Ctrl+Shift+B | Show/hide artifact details                        |
| Ctrl+S       | Save the current draft                            |
| Ctrl+Enter   | Send the AI chat message                          |
| ?            | Show keyboard shortcuts                           |
| Esc          | Close dialog/menu/quick search or leave Focus     |

Shortcuts depend on focus; typing in an editor can have editor-specific behavior. The current public package is Windows-only.

## 16. Recovery and troubleshooting

| Symptom                                                 | Next step                                                                                                                                              |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Missing/expired login configuration on an older version | Update to 0.1.14 or later using the verified installer. Older releases retain their local provisioning requirement; new releases do not use that file. |
| Microsoft login/consent blocked                         | Complete the normal browser flow; involve the organization's administrator for policy/assignment issues.                                               |
| Database disconnected                                   | Verify the selected profile, approved VPN, server reachability and TLS with IT. Do not guess credentials or disable validation.                        |
| Wrong project's database                                | Review the app's switch confirmation and choose the intended database; preserve pending work first.                                                    |
| Editing paused after connection loss                    | Keep the editor open, restore access and refresh/retry. Do not assume unsaved text is committed.                                                       |
| SharePoint conflict/first sync                          | Wait for the first pass or review the conflict; avoid manual cache edits.                                                                              |
| Corrupt settings or legacy state                        | Follow the explicit recovery instructions. Archive/reset only after reviewing the effect; retain recovery material privately.                          |
| Search/index out of date                                | Save/check the underlying files, then use the supported rebuild action. Rebuild is not a substitute for restoring missing files.                       |
| AI unavailable                                          | Check tool installation, provider sign-in, selected model and quota; use approved local diagnostics.                                                   |
| Export unavailable                                      | Ask the operator to verify the required local exporter; no external upload is needed.                                                                  |
| Update integrity/trust failure                          | Stop; report the safe error code, version and expected publisher to the operator. Never bypass security warnings.                                      |

For support, share only a sanitized description, application version and safe error codes through the approved internal channel. Do not post company documents, screenshots with account/connection details, full profiles, signed company provisioning or raw logs to this public repository.
