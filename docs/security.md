# Security Baseline

Remote access is powerful. Because you are opening a door into your primary development environment, you must treat it like production access.

## Why This Matters

If your phone is lost or a password is reused or leaked, a poorly secured SSH server can become a fast path to a total account takeover. Using keys and hardening your settings reduces that risk dramatically.

## Least-Privilege Philosophy

Operate with the minimum level of access required to get the job done.

- Consider creating a dedicated "doom-coding" user account on your host
- Keep that user's permissions limited to your development directories
- Do not develop or SSH in as an administrator or root user

## SSH Security & Rationale

### Use SSH Keys, Not Passwords

Passwords are susceptible to brute-force attacks and credential stuffing. SSH keys (Ed25519 preferred) provide much stronger authentication.

- Once you verify your keys work, disable password-based authentication
- Optionally restrict which specific users or IPs are allowed to SSH into the host

### Hardening the Host

- Ensure FileVault (macOS), BitLocker (Windows), or LUKS (Linux) is active on the host
- Keep the host OS, SSH server, and all development tools updated with the latest security patches
- Enable a firewall on the host and only allow traffic from your private VPN network

## Warnings and Recommendations

- Your phone is your key. Use biometric locks or strong passcodes
- Store your private keys in a secure enclave or a password manager that supports SSH key storage
- Periodically check your VPN dashboard to see which devices are connected to your private network
