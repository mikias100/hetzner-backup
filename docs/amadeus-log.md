\# Amadeus — Work Log



\*\*Member:\*\* Amadeus

\*\*Role:\*\* Lead Server Architect \& Integration Engineer (Group Leader)

\*\*Project:\*\* Hetzner Cloud Server Alienable Backup



This document is Amadeus's personal real-time audit log, parallel to `member-a-log.md`. Compiled by Member A based on technical updates provided by Amadeus.



\---



\## Phase 1 — Environment Architecture \& Cryptographic Access



\### Repository Initialization \& Workflow Standards



The repository has been initialized with a standardized `main` branch to comply with collaborative development tracking and project auditing requirements. All subsequent architectural changes, environment discoveries, and technical implementations are mapped via explicit, atomic commits to maintain a clean engineering audit trail.



\### Local Administration Environment — WSL Integration



To bridge the gap between production cloud infrastructure and the local Windows-based workstation, Amadeus deployed \*\*Windows Subsystem for Linux (WSL)\*\* running Ubuntu.



\*\*Rationale:\*\* Operating within a native WSL environment ensures that standard POSIX utilities — the OpenSSH client suite, cryptographic permission masking (`chmod`), and standard input/output block streams (`dd`, `gzip`) — operate natively and reliably without requiring Windows-native translation wrappers or PowerShell formatting workarounds.



\### Secure Host Verification \& Key Authentication



Remote administrative access to the staging environment (`wordpress.multinomial.se`) was established using an asymmetric ED25519 private key payload (`private\_openssh`).



During the initial handshake phase, the local OpenSSH client intercepted the remote host's public key cryptographic fingerprint:ED25519 key fingerprint is SHA256:BLQSBiQczsi8AE+NnGyx16svBDeJIRyWWJ/4QDQCpMI



The fingerprint was validated against the infrastructure provider's expectations to confirm host authenticity. Upon validation, the record was permanently appended to `\~/.ssh/known\_hosts` to mitigate potential Man-In-The-Middle (MITM) attack vectors before initiating the interactive root shell session.



\### Phase 1 status — Amadeus's deliverables



\- WSL Ubuntu environment configured on workstation

\- SSH client toolchain verified functional

\- Server host fingerprint validated and trusted

\- Root SSH access to `wordpress.multinomial.se` confirmed working



Ready to begin Phase 2 (Implementation) — block-level imaging procedure.



