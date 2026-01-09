# Client Setup

This guide explains how to configure your smartphone (the client) to connect to your host.

## 1. Mesh VPN Client

The VPN allows your phone to securely talk to your computer over the Internet.

- Install the mobile app for your chosen mesh VPN (e.g., Tailscale)
- Sign in to the same account used on your host machine
- Open the app and confirm you can see your host machine listed as "Online"

## 2. SSH Client

You'll need a terminal app that supports the SSH protocol.

- Install a mobile SSH client (e.g., Termius, Blink, or Prompt)
- Ensure the app supports:
  - SSH Key management (importing and generating keys)
  - Known hosts verification (to prevent man-in-the-middle attacks)
  - FaceID/Passcode locking for the app itself

## 3. Configure the Host Connection

In your SSH client app, create a new "Host" or "Connection" profile with the following details:

- Use the MagicDNS hostname (e.g., `my-laptop.tailnet-name.ts.net`) or the VPN IP address (e.g., `100.x.y.z`)
  - Port: Default is `22`
  - Username: Your host username (or your dedicated `doom` user)
  - Label: Give it a clear name like "Doom Coding - Desktop"

## 4. Authentication Setup

- Import your private key into the app or generate one in the app and add the public portion to your host
- Associate that key with your host connection profile
- Avoid using passwords for authentication to maintain a high security baseline

[← Previous: Host Setup](setup-host.md) | [Next: Workflow →](workflow.md)
