# CBN ProjectHub user guide

Applies to the **0.1.13 internal Windows x64 release**, reviewed 2026-10-16. This guide covers the user-facing feature areas present in that release. Features needing company services or an AI provider are conditional on those services being configured and on your permissions. Screens may differ in later releases.

The installer is public; company access is not. Application source is maintained separately in a private repository. This guide contains no company connection settings, account identifiers, private keys or operational examples. This release retains the existing installation identity for update compatibility and requires approved internal certificate trust and signed login setup. No Mac installer is currently published.

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

1. Ask your operator to prepare this PC. Follow the separate Windows installation guide for certificate verification and signed internal setup. An existing custom pilot profile needs an explicit, verified copy to the normal profile before first Start-menu use; do not merge populated profiles. Never request a private signing key or another person's app profile.
2. Download the [Windows installer](https://github.com/intCRMBilling/cbn-projecthub-downloads/releases/download/v0.1.13/CBN-ProjectHub-0.1.13-x64-nsis.exe). No GitHub account is needed. The operator must verify its hash and publisher before execution. A self-signed certificate may require explicitly approved user/IT trust; do not bypass Windows security warnings.
3. The operator supplies a signed local login configuration separately through an approved internal channel. It is not in the installer or public repository. The signed configuration is short-lived; ask the operator about renewal. A certificate by itself does not configure Microsoft login.
4. Start **CBN ProjectHub** from the Start menu after the operator completes setup or migration. Click **Sign in with Microsoft**, complete browser sign-in/MFA yourself and return to the app. Never paste passwords, tokens or MFA codes into chat or a public issue.
5. If browser sign-in is waiting, use the available cancellation action before retrying. Use the sign-in screen's saved-session recovery only when indicated. Missing or expired company login configuration must be replaced by the operator, followed by a restart.
6. Use the account menu to sign out. A restored session can require renewed online confirmation before a protected action. Downloading an installer never grants project membership or database access.

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

1. Open the project overview to see modules, artifact counts and progress information.
2. Create modules for areas of the project, then open a module to add and browse artifacts. Use the available module actions to organize hierarchy, rename or maintain relationships. Review deletion confirmations and their scope before proceeding.
3. Use the navigation tree to move between modules and artifact types. Use the top bar/project switcher to change projects, not module actions.
4. Use **Search** or **Ctrl+K** to find artifacts, jump to modules/pages or run available actions. Review result titles and context before opening them; knowledge search is also available on the Knowledge page.
5. On an artifact, use its details tabs for links, history, checks and activity. **Focus** hides surrounding navigation/details; Escape exits Focus. Layout controls can show/hide navigation and details without changing project data.

Module relationships describe dependencies or related areas. When AI proposes relationships, review the proposal and accept only the intended changes; a suggestion is not established project truth.

## 5. Create and edit artifacts

Open the intended module and use its new-artifact action. Select a type, give it a clear title/slug and review the starting template. The supported types are:

| Type | Purpose |
|---|---|
| MB | Module brief |
| PC | Project charter |
| PRD | Product requirements document |
| DSN | Design |
| TC | Test cases |
| BPMN | BPMN process model |
| BPF | Business process flow |
| SPEC | Story/development specification |
| OTH | Other supporting artifact |

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

For a shared project, authorized members send invitations from the open project. Review recipient and roles before sending. The recipient signs in with the intended account and accepts the pending invitation from the invitation interface. An authorized inviter can revoke a pending invitation. Do not assume installing the app or receiving an email automatically grants membership. Email delivery can depend on the configured Microsoft permissions; inspect the invitation state.

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

## 13. Settings reference

| Section | What to do there |
|---|---|
| Account | Inspect the signed-in identity and author attribution; sign out from the account menu. |
| AI assistance | Configure/detect provider tools, connection/model preferences and external-client MCP setup. |
| Playbooks & templates | Review/edit permitted playbooks, new-artifact templates, completeness and project coverage/link rules, design-system inputs, spec house rules and field-length rules. Preview imports and use history/reset deliberately. Project templates take precedence over workspace, then bundled defaults. |
| Roles & workflow | Read effective permission rules; authorized shared-project role managers can edit the policy. |
| Databases | Manage the account's local connection profiles and choose the active database. Keep real settings private. |
| Workspace | Inspect the workspace location/storage information and close the project. |
| About CBN ProjectHub | Check version/schema information and application update controls. |

Rebuild index, where offered, reconstructs artifact metadata/search from files. It is not a backup restore and does not grant/change project membership. Backups must include the actual approved workspace files/assets and use the organization's database backup procedures separately.

## 14. Application updates

1. Sign in and open **Settings** on the workspace picker/database-setup screen, or **Settings → About CBN ProjectHub** inside a project.
2. The app checks automatically. Use **Check for updates** when enabled; it is disabled during an active check/download.
3. Wait for a verified update to be ready. **Later** postpones installation; **Show update** returns to the ready state.
4. Save/resolve pending work, then choose **Restart to update**. The app verifies the installer, closes safely, installs and opens again automatically. Ordinary quit does not authorize installation.
5. Confirm the new version. If verification fails, do not manually force the rejected download to run; contact the operator with only the safe error code.

The owner reports successful second-PC updates through 0.1.11, automatic reopening and preserved login. Each additional PC needs its own approved trust and login setup. Local Test certificate expiry is 2027-01-13; login provisioning has a separate shorter renewal schedule. Plan renewals with the operator before expiry.

Release metadata (`release.json`, `latest.yml`, `.blockmap`) supports the updater and should not be deleted. Users download the EXE; the app handles metadata. GitHub's Source code archives are snapshots of this public documentation repository, not the private application repository.

## 15. Keyboard shortcuts

| Keys | Action |
|---|---|
| Ctrl+K | Search/jump to a module, artifact, page or action |
| Ctrl+B | Show/hide navigation |
| Ctrl+Shift+B | Show/hide artifact details |
| Ctrl+S | Save the current draft |
| Ctrl+Enter | Send the AI chat message |
| ? | Show keyboard shortcuts |
| Esc | Close dialog/menu/quick search or leave Focus |

Shortcuts depend on focus; typing in an editor can have editor-specific behavior. The current public package is Windows-only.

## 16. Recovery and troubleshooting

| Symptom | Next step |
|---|---|
| Missing/expired login configuration | Ask the operator for a fresh signed local document; restart. Do not edit it manually. |
| Microsoft login/consent blocked | Complete the normal browser flow; involve the organization's administrator for policy/assignment issues. |
| Database disconnected | Verify the selected profile, approved VPN, server reachability and TLS with IT. Do not guess credentials or disable validation. |
| Wrong project's database | Review the app's switch confirmation and choose the intended database; preserve pending work first. |
| Editing paused after connection loss | Keep the editor open, restore access and refresh/retry. Do not assume unsaved text is committed. |
| SharePoint conflict/first sync | Wait for the first pass or review the conflict; avoid manual cache edits. |
| Corrupt settings or legacy state | Follow the explicit recovery instructions. Archive/reset only after reviewing the effect; retain recovery material privately. |
| Search/index out of date | Save/check the underlying files, then use the supported rebuild action. Rebuild is not a substitute for restoring missing files. |
| AI unavailable | Check tool installation, provider sign-in, selected model and quota; use approved local diagnostics. |
| Export unavailable | Ask the operator to verify the required local exporter; no external upload is needed. |
| Update integrity/trust failure | Stop; report the safe error code, version and expected publisher to the operator. Never bypass security warnings. |

For support, share only a sanitized description, application version and safe error codes through the approved internal channel. Do not post company documents, screenshots with account/connection details, full profiles, signed company provisioning or raw logs to this public repository.
