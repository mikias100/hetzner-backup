\# Member A — Work Log



\*\*Member:\*\* Mikias Woldeyohanes

\*\*Role:\*\* Git Manager \& Lead Documenter

\*\*Project:\*\* Hetzner Cloud Server Alienable Backup



This document is my personal real-time audit log of actions taken as Member A. It captures dates, decisions, and steps in chronological order, separate from the project-level phase documentation.



\---



\## Phase 1 — Setup and Repository Initialization



\### 2026-05-19 — Project kickoff and repo setup



\*\*Role context.\*\* Following the group's task assignment, my responsibilities for Phase 1 are: secure access to the Google Drive folder with SSH credentials, initialize the GitHub repository, configure collaborator access, and push the base README structure.



\*\*Drive access.\*\* Confirmed with Amadeus that I already have access to the shared Google Drive folder containing the SSH credentials for `wordpress.multinomial.se`. No request to Daniel needed.



\*\*GitHub repository creation.\*\*

\- Created private repository `hetzner-backup` under `github.com/mikias100`.

\- Selected MIT License.

\- Added default README.md (replaced later with project-specific content).

\- Visibility set to \*\*Private\*\* to protect references to SSH credentials and infrastructure details.



\*\*Local clone and structure.\*\*

\- Cloned to `C:\\Users\\Mikia\\Documents\\hetzner-backup\\`.

\- Created the agreed folder structure:

&#x20; - `docs/` — Phase documentation (research, implementation, restore, problems \& solutions)

&#x20; - `scripts/` — Backup and conversion scripts (to be added by Amadeus and Member B in Phase 2)

&#x20; - `screenshots/` — Verification screenshots for the final video and report

\- Added `.gitkeep` placeholder files to all empty folders so Git tracks them.



\*\*README content.\*\* Replaced the default GitHub-generated README with a project-specific version covering:

\- Project goal and success criteria

\- Target server identification

\- Team member roles

\- Repository structure

\- Four-phase project plan

\- Git workflow expectations



\*\*Commit history so far.\*\*

\- `Initialize repository structure and project README` — Phase 1 base structure

\- Repository now in line with the requirement \*"Push the base README.md file structure"\*.



\*\*Collaborator setup.\*\*

\- Invited Amadeus (Group Leader, Lead Server Architect) with Write access.

\- Invited Member B (Environment Specialist \& Video Producer) with Write access.

\- Both invitations sent; awaiting acceptance.



\*\*SSH key creation.\*\*

\- Generated an ED25519 SSH key pair on my local machine for future use:

&#x20; - Private key: `C:\\Users\\Mikia\\.ssh\\id\_ed25519`

&#x20; - Public key: `C:\\Users\\Mikia\\.ssh\\id\_ed25519.pub`

\- Initially shared the public key with Amadeus. After clarifying with him, we will use the shared Hetzner SSH key from the Drive folder for all server access, so my personal key was not added to the server. Personal key is retained for GitHub authentication and future projects.



\*\*Authentication for Git pushes.\*\*

\- First push triggered GitHub's browser-based authentication flow via Git Credential Manager.

\- Authenticated successfully — subsequent pushes do not require re-authentication on this machine.



\### Phase 1 status



Member A deliverables complete:



\- Drive access secured

\- GitHub repository initialized

\- Collaborator access configured

\- Base README.md structure pushed

\- Folder structure in place for Phase 2/3 contributions



Ready to support Phase 2 once Amadeus and Member B begin the imaging procedure.



\---



\## Phase 2 — Implementation (in progress)



\*To be filled in real-time as Amadeus performs the live server imaging and Member B handles the local conversion.\*



\### Audit fields for each work session



\- \*\*Date:\*\*

\- \*\*Activity:\*\*

\- \*\*Team member observed:\*\*

\- \*\*Commands executed:\*\*

\- \*\*Errors / failures encountered:\*\*

\- \*\*Resolution applied:\*\*

\- \*\*Commit reference:\*\*



\---



\## Phase 3 — Completion (pending)



\*To be filled in when the VM is booted in VirtualBox and integration work begins.\*



\---



\## Phase 4 — Summary and Video (pending)



\*Final compilation of problems-and-solutions table and project conclusion will be assembled here before being moved into `docs/04-problems-and-solutions.md`.\*

