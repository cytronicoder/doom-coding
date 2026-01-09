# Overview

At a high level, your phone can simply serve as a remote terminal for your computer.

## Mental Model: Host vs. Client

This setup relies on two primary components:

1. Host: A computer (desktop, laptop, or server) where your code lives, your build tools run, and your dev environment is configured
2. Client: Your phone, which acts as the interface to control the host

## How it Works

The workflow uses three main layers to bridge the gap between your phone and your machine:

- A mesh VPN (e.g., Tailscale) places your phone and computer on a private network without exposing your machine to the public Internet
- SSH provides an encrypted, authenticated remote shell into your computer
- Your editor, build tools, and coding agents run on the computer; you control them from your phone over SSH

_If you can run it in a terminal on your computer, you can "doom code" it from your phone._
