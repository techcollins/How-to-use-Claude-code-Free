🚀 Claude Code for Free with OpenCode Zen

This guide shows how I configured Claude Code to work with OpenCode Zen at no cost, and how the setup can be used as part of a workflow for security research and bug-bounty programs such as HackerOne.

## 📺 Full Video / Walkthrough

[![Claude Code Free with OpenCode Zen](https://img.youtube.com/vi/LIHGui4NYQE/maxresdefault.jpg)](https://youtu.be/LIHGui4NYQE)

**▶️ Click the thumbnail to watch the complete guide on YouTube**

---

⚠️ Disclaimer

This guide is intended for authorized security research, learning, and bug-bounty programs.

Only test systems where you have explicit permission to do so. Always follow the rules and scope of the specific bug-bounty program.

---

📋 What You'll Set Up

By following this guide, you will:

- Install Claude Code
- Install OpenCode
- Configure OpenCode Zen
- Connect Claude Code to your OpenCode Zen setup
- Verify that the configuration works
- Run Claude Code using the configured model

---

🛠️ Requirements

Before starting, make sure you have:

- WSL installed on Windows
- Internet access
- An OpenCode Zen API key
- Basic knowledge of the Linux terminal
- A GitHub account if you want to clone the configuration repository

---

1️⃣ Install Claude Code

Open your WSL terminal and run:

curl -fsSL https://claude.ai/install.sh | bash

You can find the official Claude Code documentation here:

👉 https://code.claude.com/docs/en/overview

---

2️⃣ Install OpenCode

Go to:

👉 https://opencode.ai/

Or install OpenCode directly from your WSL terminal:

curl -fsSL https://opencode.ai/install | bash

---

3️⃣ Configure Your Model

Start OpenCode and use:

/model

Then press:

Ctrl + A

Select/configure the model you want to use.

---

4️⃣ Claude Code + OpenCode Zen

Clone the configuration repository:

git clone https://github.com/Itsme23476/claude-zen

Enter the repository:

cd claude-zen

Before continuing, read the repository's README carefully.

Run the installation script:

./install.sh

When prompted, provide your OpenCode Zen API key.

«Never commit your real API key to GitHub.»

Use a placeholder such as:

YOUR-API-KEY

---

5️⃣ Verify the Installation

Run the full verification:

./verify.sh --full

The verification should complete successfully before you consider the setup ready.

If something fails:

1. Read the error message.
2. Fix the problem.
3. Run the verification again.

./verify.sh --full

Do not assume the configuration works until the verification passes end-to-end.

---

🤖 Prompt Used

I used the following prompt with Claude Code to automate the setup:

Set up Claude Code on this machine to run YOUR-MODEL-NAME for free through
OpenCode Zen.

Repo: https://github.com/Itsme23476/claude-zen

My OpenCode Zen API key: YOUR-API-KEY

Steps:
1. Clone the repo somewhere sensible and read its README first.
2. Run ./install.sh and give it my key when it asks.
3. Run ./verify.sh --full and paste me the full output.
4. Tell me the exact command to start it.

Rules:
- Do NOT rewrite or "improve" zen-proxy.mjs. The repo copy is correct. Two
  parts of it are load-bearing and break in non-obvious ways if touched:
  the reasoning_content cache with its stub retry, and the tool-schema filter.

- Check ~/.claude/settings.json for pinned ANTHROPIC_*_MODEL values. If any
  exist, tell me — they override env vars and will silently break the launcher.

- If a step fails, debug and fix it, then re-run verify.sh.

- Do not tell me it works until verify.sh passes end to end.

---

🔍 Important Configuration Check

Claude Code may have model settings stored in:

~/.claude/settings.json

Check the file:

cat ~/.claude/settings.json

Look specifically for:

ANTHROPIC_*_MODEL

Pinned model values can override environment variables and cause the launcher configuration to behave unexpectedly.

---

⚠️ Do Not Modify "zen-proxy.mjs"

If you're using the referenced "claude-zen" repository, do not casually rewrite or "improve" "zen-proxy.mjs".

Two important components are load-bearing:

1. "reasoning_content" cache

This works together with the stub retry mechanism.

2. Tool-schema filter

This handles tool-schema compatibility.

Changing these components can cause failures that aren't immediately obvious.

---

▶️ Starting Claude Code

After the installation and verification have completed successfully, use the exact startup command provided by the installation.

For example:

# Use the startup command provided by the installer

«Don't substitute a different command unless you understand how the launcher was configured.»

---

📚 References

Claude Code

https://code.claude.com/docs/en/overview

OpenCode

https://opencode.ai/

Claude Zen Repository

https://github.com/Itsme23476/claude-zen

HackerOne

https://www.hackerone.com/

---

⭐ Support

If this guide helped you, consider:

- ⭐ Starring this repository
- 🍴 Forking the project
- 📺 Watching the full video walkthrough
- 🐛 Opening an issue if you discover a problem

---

📺 Full Video Guide

YouTube:
https://youtu.be/LIHGui4NYQE?si=EDuw3gCQ9vatxSvG

---

🔐 Security Reminder

Never publish:

YOUR-API-KEY

with your real API key.

If you accidentally expose an API key, revoke/rotate it immediately.
