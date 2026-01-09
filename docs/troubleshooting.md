# Troubleshooting

If you encounter issues while doom coding, use this guide to diagnose and resolve them.

## Cannot Connect to the Host

### Symptom: Connection Timeout or "Host Unreachable"

1. Diagnosis: Is the host online?
    - Fix: Check that the computer is powered on and connected to a network. If it is a laptop, ensure it hasn't slept because the lid was closed
2. Diagnosis: Is the VPN active?
    - Fix: Open your VPN app (e.g., Tailscale) on your phone and ensure it is "Connected." Check the list to see if the host also shows as "Online"
3. Diagnosis: Is SSH running?
    - Fix: Try to SSH into the machine from another local device or check the system settings on the host to verify "Remote Login" or the SSH service is active
4. Diagnosis: Is the firewall blocking access?
    - Fix: Ensure the host firewall allows incoming connections on the SSH port (default 22) specifically from the VPN interface

### Symptom: "Permission Denied (publickey)"

1. Diagnosis: Are you using the correct key?
    - Fix: Verify that the private key selected in your mobile SSH app matches the identity you intended to use
2. Diagnosis: Is the public key registered?
    - Fix: Ensure the corresponding public key is present in the `~/.ssh/authorized_keys` file for the user you are trying to log in as
3. Diagnosis: Are file permissions too open?
    - Fix: SSH requires strict permissions. On the host, ensure `~/.ssh` is `700` and `authorized_keys` is `600`

## Connection is Slow or Unreliable

### Symptom: Type Lag or Stuttering

1. Diagnosis: Poor Network Connection
    - Fix: Move to a stronger Wi-Fi or cellular signal. If possible, plug the host machine into Ethernet
2. Diagnosis: Large Console Output
    - Fix: Avoid running commands that flood the terminal with logs, as these are painful to render over mobile data

### Symptom: Connection Drops Frequently

1. Diagnosis: Aggressive Mobile Battery Management
    - Fix: Disable battery optimization or "Low Power Mode" for your VPN and SSH apps to prevent the OS from killing the background connection
2. Diagnosis: Host Power Management
    - Fix: Double-check that your host computer isn't entering a low-power state or disconnecting the network adapter after a period of inactivity

## Session State is Lost

### Symptom: Reconnecting starts a fresh terminal shell

1. Diagnosis: Not using a multiplexer
    - Fix: Always start your sessions by attaching to `tmux` (e.g., `tmux attach || tmux new`). This ensures that if the connection drops, your processes continue running
2. Diagnosis: Server Reboot
    - Fix: If the host machine rebooted, your tmux sessions are gone unless you use a persistence plugin like `tmux-resurrect`
