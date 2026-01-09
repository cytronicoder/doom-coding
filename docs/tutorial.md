# Step-by-Step Setup Tutorial

This guide provides a complete, command-line-first walkthrough for setting up your doom coding environment.

## Part 1: Prepare the Host (Your Computer)

### 1. Enable SSH

You must have a way to receive connections.

macOS:
Open Terminal and run:

```bash
sudo systemsetup -setremotelogin on
```

Linux (Ubuntu/Debian):

```bash
sudo apt update
sudo apt install openssh-server -y
sudo systemctl enable ssh
sudo systemctl start ssh
```

### 2. Networking (Tailscale)

We use Tailscale to create a secure tunnel without opening router ports.

Install on macOS:
Download from the [App Store](https://apps.apple.com/us/app/tailscale/id1475387142) or use Homebrew:

```bash
brew install tailscale
```

Install on Linux:

```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

Get your IP and Hostname:

```bash
tailscale ip -4
tailscale status
```

_Tip: Copy the IPv4 address (starts with 100.x.y.z) or the full MagicDNS name (found in `tailscale status`) for your phone setup later._

### 3. Generate SSH Keys

Do this on the device you'll use to log in, OR generate it on the host and move the public key. For this tutorial, we will generate it on the host to get the `authorized_keys` ready.

```bash
# Create the directory if it doesn't exist
mkdir -p ~/.ssh
chmod 700 ~/.ssh

# Generate a modern Ed25519 key
ssh-keygen -t ed25519 -f ~/.ssh/doom_key -C "doom-coding-mobile"

# Add it to authorized_keys
cat ~/.ssh/doom_key.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys

# Output the PRIVATE key so you can copy it to your phone
cat ~/.ssh/doom_key
```

CRITICAL: The `cat ~/.ssh/doom_key` command will print a block of text starting with `-----BEGIN OPENSSH PRIVATE KEY-----` and ending with `-----END OPENSSH PRIVATE KEY-----`. Copy this entire block to your phone via a secure method (e.g., a secure note, encrypted chat to yourself, or shared clipboard).

### 4. Hardening (Optional but Recommended)

Disable password logins so only your key works.

```bash
# Edit the config (you will need sudo/root)
sudo nano /etc/ssh/sshd_config
```

Search for these lines and set them:

```text
PasswordAuthentication no
PubkeyAuthentication yes
PermitEmptyPasswords no
```

_Save (Ctrl+O) and Exit (Ctrl+X)._

Restart SSH:

```bash
# macOS
sudo launchctl unload /System/Library/LaunchDaemons/ssh.plist
sudo launchctl load -w /System/Library/LaunchDaemons/ssh.plist

# Linux
sudo systemctl restart ssh
```

## Part 2: Prepare the Client (Your Phone)

### 1. Install Apps

1. Tailscale: Download from App Store/Play Store and sign in.
2. Termius/Blink/Prompt: Install your preferred terminal.

### 2. Configure VPN

1. Open the Tailscale app.
2. Switch the toggle to ON.
3. Ensure your host computer appears in the list.

### 3. Add the Connection in your SSH App

1. Import the Key:
   - In your app (e.g., Termius), go to Keychain or Keys.
   - Select Add Key or New Key.
   - Choose Paste Private Key (don't try to type it manually!).
   - Paste the `-----BEGIN OPENSSH PRIVATE KEY-----` block you copied earlier.
   - Give it a name like "Doom Laptop Key".
2. Setup the Host:
   - Go to Hosts > New Host.
   - Address: Your Tailscale IP (starts with `100.x`) or your MagicDNS name (e.g., `laptop.tailxxxx.ts.net`).
     - _Note: MagicDNS is preferred because it's easier to remember, but IPs are more reliable if DNS isn't resolving on your phone yet._
   - Username: Your laptop username (run `whoami` on your laptop to check).
   - Password: Leave blank.
   - Key: Select the "Doom Laptop Key" you just imported.
   - Port: 22.

## Part 3: Connect and Persistent Sessions

### 1. First Login

Tap the host in your phone app. Accept the host key fingerprint. You are now in!

### 2. Launch tmux

Never work in a raw shell. If your 5G drops, your process will die. Use `tmux`.

```bash
# Install (macOS)
brew install tmux

# Install (Linux)
sudo apt install tmux -y

# Start/Attach a session
tmux attach || tmux new
```

---

## Tips for Success

- Mobile State:
  - Android: Exclude Tailscale and your SSH app from "Battery Optimization."
  - iOS: Enable "Background App Refresh" for both apps to prevent the tunnel from collapsing in the background.
- If you are running a web app on port 3000, access it on your phone browser via `http://[tailscale-ip]:3000`.
- Use a mechanical keyboard via Bluetooth or a "hacker's keyboard" app with a Ctrl key to make terminal navigation easier.
- Keep a `DEVLOG.md` file. Before you close your phone, write one sentence on what you were doing.

[← Back to Overview](overview.md) | [Back to README →](../README.md)
