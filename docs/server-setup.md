# Homelab Server Setup

Sep 27, 2026 · @Rabie

Ubuntu Server, fresh install, hardened before installing Docker.

1. **Non-root user** — confirmed `whoami` wasn't `root`; added a sudo user with `adduser` + `usermod -aG sudo`.
2. **System update** — `sudo apt update && sudo apt upgrade -y`.
3. **Static IP** — set a DHCP reservation on the router so the server's LAN IP never changes.
4. **SSH hardening** — key-based login only; `PasswordAuthentication no` and `PermitRootLogin no` in `/etc/ssh/sshd_config`.
5. **Firewall (UFW)** — `sudo ufw allow OpenSSH` before `sudo ufw enable`, to avoid locking out the current SSH session.
6. **fail2ban** — installed to auto-ban IPs after repeated failed SSH login attempts.
7. **Tailscale** — installed on the server and on admin devices, for SSH access from outside the home network without opening any port to the public internet.
