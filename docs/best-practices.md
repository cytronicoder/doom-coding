# Best Practices

These practices help maintain productivity and security while coding from a mobile device.

## 1. Handoff Files

Create a lightweight scratchpad in each repository (e.g., `CLAUDE.md`, `NOTES.md`, or `DEVLOG.md`). At the end of every session, spend 30 seconds updating it with:

- What changed in this session
- What you were in the middle of doing
- The exact commands needed to resume
- Specific thoughts on next steps

This dramatically reduces context loss when switching between several short mobile sessions.

## 2. Session Persistence

- One session per project; keep dedicated `tmux` sessions for different projects
- Use tabs or windows for specific tasks (e.g., Window 1 for code, Window 2 for tests, Window 3 for the coding agent)

## 3. Previewing Web Apps

When developing web applications, you likely need to see what you're building.

- Run your development server on the host machine
- Access the preview from your phone's browser using the host's VPN IP and the application port (e.g., `http://100.x.y.z:3000`)
- Make sure that your dev server binds to `0.0.0.0` or the VPN interface, rather than just `localhost`, so it is reachable over the private network

## 4. Database Access

Managing databases on mobile can be tricky.

- Use a dedicated mobile database viewer app that supports SSH tunneling
- Use SSH port forwarding (if your client app supports it) to map the remote database port to your phone
- When in doubt, stick to `psql`, `sqlite3`, or `mysql` directly within your SSH session

## 5. Secrets Management

- Store SSH keys in your phone's secure enclave or a trusted password manager
- Never copy API keys, tokens, or passwords into standard notes apps
- Use `.env` files or a secrets manager on the host machine to handle credentials

## 6. Safe Execution Posture

When using coding agents remotely, adopt a cautious approach:

- Always review output from agents before running destructive commands (e.g., `rm -rf` or database migrations)
- Commit your work often so you can revert easily if a remote session goes sideways
- Avoid running any development tasks as administrative or root users

[← Previous: Workflow](workflow.md) | [Next: Troubleshooting →](troubleshooting.md)
