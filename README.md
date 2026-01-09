# Doom Coding

Inspired by [@rberg27's original guide](https://github.com/rberg27/doom-coding), this is an upgraded, secure, and tool-agnostic approach to "doom coding."

Doom coding is the practice of developing software entirely from your smartphone by using it as a remote terminal. By leveraging a private mesh VPN and SSH, you can access your powerful host machine's environment, build tools, and coding agents from anywhere, turning your phone into a portable engineering workstation.

## How it Works

At a high level, your phone serves as a remote terminal for your computer:

1. A mesh VPN places your phone and computer on a private network, hidden from the public Internet
2. SSH provides a secure tunnel into your computer's terminal
3. Your editor, build tools, and coding agents run on the computer; you control them from your phone

Explore the detailed guides below to set up your environment:

1. [**Quick Start Tutorial**](docs/tutorial.md) - **Start here!**
2. [Overview](docs/overview.md)
3. [Requirements](docs/requirements.md)
3. [Host Setup](docs/setup-host.md)
4. [Client Setup](docs/setup-client.md)
5. [Workflow](docs/workflow.md)
6. [Best Practices](docs/best-practices.md)
7. [Troubleshooting](docs/troubleshooting.md)
8. [Contributing](docs/contributing.md)

> [!IMPORTANT]
> Before getting started, you must read the [security baseline](docs/security.md). Remote access is powerful; treat your mobile connection with the same rigor as production access.
