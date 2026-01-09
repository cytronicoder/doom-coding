# Workflow

Once you are set up, your daily "doom coding" routine should focuses on efficiency and persistence.

## 1. Connect and Code

Follow these steps to start a session:

1. Turn on your VPN connection on your phone
2. Open your SSH client app and select your host profile
3. Navigate to your project directory

    ```bash
    cd path/to/project
    ```

## 2. Session Persistence with tmux

Mobile connections can be interrupted by phone calls, signal drops, or app switching. Using a terminal multiplexer like `tmux` is essential.

- Always run your work inside a tmux session

  ```bash
  tmux attach || tmux new
  ```

- If your SSH connection drops, your processes (tests, builds, agents) keep running on the host. You simply reconnect and pick up exactly where you left off

## 3. Using Coding Agents

This workflow is highly compatible with terminal-based coding agents:

- Claude Code/Aider/Codex CLI: Because these tools run in the terminal, they are native to the SSH experience
- Workflow Pattern: Use one tmux window for the coding agent and another for manual commands or logs

## 4. General Workflow Patterns

- Doom coding is often done in short intervals. Focus on small, atomic tasks that can be completed or summarized quickly
- Remember that if it works in the host terminal, it works from your phone; this includes:
  - Language servers and linters
  - Test runners and build systems
  - Git operations
  - Database CLIs
