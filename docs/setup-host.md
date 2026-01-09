# Host Setup

Follow these steps to prepare your computer (the host) for secure remote access.

## 1. Reliability and Power Management

Ensure your host stays online and reachable even when you aren't physically present.

- Configure the machine so it does not sleep while plugged into power
- Use a wired Ethernet connection if possible for maximum stability
- If using a laptop, confirm it remains reachable when the lid is closed. This often requires specific utility settings or OS-level configuration (e.g., "Prevent sleep when display is off")

## 2. Enable the SSH Server

You need a way to log in remotely.

- macOS: Go to System Settings > General > Sharing and enable "Remote Login"
- Linux: Install and enable `openssh-server`
- Windows: Enable the OpenSSH Server feature in Optional Features
- Confirm you can SSH into the machine locally from another device on the same network before attempting remote access

## 3. Configure Your Private Network

Use a mesh VPN to avoid exposing your host to the public Internet.

- Install a tool like Tailscale on the host
- Sign in and confirm the host appears in your private network "tailnet"
- Enable MagicDNS if available; this allows you to use a stable, human-readable hostname instead of an IP address

## 4. SSH Key Setup

Move from password-based login to more secure key-based authentication.

1. Generate an SSH key pair on a trusted computer or directly within your mobile SSH app; use Ed25519 for modern security
2. Append the public key to the file `~/.ssh/authorized_keys` on the host
3. Log in via SSH using the key to ensure it works
4. Once key login is confirmed, edit your `/etc/ssh/sshd_config` to set `PasswordAuthentication no` and restart the SSH service

## 5. (Optional) Dedicated Development User

For improved isolation, create a separate user account.

- Create a user named `doom` or similar
- Restrict SSH access to only this user in the `sshd_config` file using the `AllowUsers` directive
- Ensure this user has the necessary permissions for your development directories but lacks administrative rights

## 6. Install Development Tools

Install the tools you intend to use remotely:

- Language runtimes: Node.js, Python, Rust, Go, etc.
- Build tools: Linters, formatters, and compilers
- Terminal multiplexer: `tmux` or `screen`
- Coding agents: Claude Code, Codex CLI, Aider, etc.
