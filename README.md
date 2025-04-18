# IOC-File
This Bash script performs automated daily security checks and IoC (Indicator of Compromise) validation on a Linux host. It requires three command-line arguments: an HTTPS URL for the IoC file source, a remote upload server address, and a user identity name for SSH/rsync.



This script automates crucial daily security tasks on a Linux system:

- Securely downloads and verifies daily Indicators of Compromise (IoCs) via HTTPS and GPG signatures.
- Validates the integrity of critical analysis tools using hashes from the IoC file.
- Performs system checks: listening ports, firewall rules, critical binary integrity (dpkg -V), recent file changes, SUID/GID files.
- Scans specified directories for files matching IoC hashes or containing specific strings.
- Ensures specified web directories are non-executable.
- Generates detailed logs, archives them securely (tgz + GPG signature + SHA256 checksum), and uploads them via rsync over SSH.
- Creates a concise pass/fail summary (ioc_summary.txt) ideal for automated email reporting via cron and msmtp.
- Requires: 3 arguments (IoC URL, Remote Server, User ID), sudo, specific directories, standard Linux utilities (curl, gpg, etc.).
