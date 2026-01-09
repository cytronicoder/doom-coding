# Requirements

To get started with doom coding, you'll need a few pieces of hardware and software. The goal is to keep this setup tool-agnostic so you can use what works best for your OS and workflow.

## Hardware / Access

1. Host computer: A machine you control that can stay online reliably (desktop, laptop, home server, or cloud VM)
2. Mobile client: A smartphone with a stable Internet connection
3. Stable network: A reliable network connection on the host (Ethernet preferred; strong Wi-Fi acceptable)

## Accounts / Software

1. A method to connect your devices securely
    - *Recommended*: Tailscale or an equivalent zero-config mesh VPN
2. A terminal application for your phone
    - *Examples*: Termius, Prompt, Blink, JuiceSSH, or any SSH-capable terminal app
3. The host must have an SSH server enabled
    - *macOS*: Remote Login
    - *Linux*: OpenSSH server
    - *Windows*: OpenSSH Server
4. (Optional) A terminal-based agent installed on the host to assist with coding
    - *Examples*: Claude Code, Codex CLI, Aider, Cursor CLI workflows, etc.

## Optional Quality-of-Life Tools (Highly Recommended)

- `tmux` or `screen` on the host for session persistence
- `git` and a clean repository workflow
- A tool (1Password, Bitwarden, Keychain, etc.) to manage your credentials securely
