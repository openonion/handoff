<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/banner-dark.png">
    <img src="assets/banner-light.png" alt="handoff: hand your Claude Code session to a teammate's Codex. Redacted first, end-to-end encrypted." width="100%">
  </picture>
</p>

<h2 align="center">Hand your Claude Code session to a teammate's Codex.<br>Redacted first, end-to-end encrypted.</h2>

<p align="center">
  <a href="#install"><img alt="npx skills add openonion/handoff" src="https://img.shields.io/badge/npx_skills_add-openonion%2Fhandoff-0b8a3c?style=flat-square"></a>
  <a href="LICENSE"><img alt="Apache-2.0" src="https://img.shields.io/badge/Apache--2.0-0d1b14?style=flat-square"></a>
  <a href="https://discord.gg/4xfD9k8AUF"><img alt="Discord" src="https://img.shields.io/badge/Discord-0b8a3c?style=flat-square"></a>
</p>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/handoff-dark.webp">
    <img src="assets/handoff-light.webp" alt="Real Codex on two laptops: Aaron types $handoff this to bob; his own Codex takes the dentist sentence out; he says yes; Bob pastes one line into his Codex, which picks up Aaron's conversation, finishes the work and sends it back; Aaron's Codex applies it" width="100%">
  </picture>
  <br><sub><a href="assets/handoff.mp4">Watch it with sound</a> · recorded in real Codex with two test accounts on co 1.9.2b30; the waiting is fast-forwarded</sub>
</p>

<p align="center"><sub>HAND OFF A SESSION FROM</sub></p>

<p align="center">
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/agents/codex-dark.png"><img src="assets/agents/codex-light.png" alt="Codex" width="96"></picture>
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/agents/claude-code-dark.png"><img src="assets/agents/claude-code-light.png" alt="Claude Code" width="96"></picture>
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/agents/gemini-cli-dark.png"><img src="assets/agents/gemini-cli-light.png" alt="Gemini CLI" width="96"></picture>
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/agents/cursor-dark.png"><img src="assets/agents/cursor-light.png" alt="Cursor" width="96"></picture>
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/agents/opencode-dark.png"><img src="assets/agents/opencode-light.png" alt="opencode" width="96"></picture>
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/agents/droid-dark.png"><img src="assets/agents/droid-light.png" alt="droid" width="96"></picture>
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/agents/grok-dark.png"><img src="assets/agents/grok-light.png" alt="Grok" width="96"></picture>
</p>

<p align="center"><sub>Codex and Claude Code, tested end to end. Gemini CLI, Cursor, opencode, droid and Grok sessions are new in this preview.</sub></p>

## Install

```bash
# the skill
npx skills add openonion/handoff

# the co CLI it runs
pip install --upgrade --pre connectonion
```

Then tell your agent: **"Hand this to Bob."**

<p align="center">
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/features/1-dark.png"><img src="assets/features/1-light.png" alt="1. Hand off the whole session: every message you wrote and where the code is, to a teammate or to yourself on another machine" width="100%"></picture>
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/features/2-dark.png"><img src="assets/features/2-light.png" alt="2. Private sentences filtered out: your own agent reads every message first and removes health, family, money and other people's details" width="100%"></picture>
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/features/3-dark.png"><img src="assets/features/3-light.png" alt="3. Only what you approve leaves: you see the exact text first, secrets stop the send, nothing goes without your yes" width="100%"></picture>
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/features/4-dark.png"><img src="assets/features/4-light.png" alt="4. It flows back by itself: their agent picks up, asks yours when unsure, and sends the work back as a patch" width="100%"></picture>
  <picture><source media="(prefers-color-scheme: dark)" srcset="assets/features/5-dark.png"><img src="assets/features/5-light.png" alt="5. End-to-end encrypted, in the next release: sealed on your machine, opened only by their agent" width="100%"></picture>
</p>

## More

<details>
<summary><b>From the terminal</b></summary>

```bash
co handoff send bob@example.com "the slugify rules"           # preview: exactly what will leave
co handoff send bob@example.com --draft ho-1a2b3c4d --yes     # send it
co handoff status ho-1a2b3c4d --wait                          # accepted, questions, done
co handoff withdraw ho-1a2b3c4d                               # take it back
```

The mail goes from your own Gmail or Outlook, so it arrives from someone they know.
</details>

<details>
<summary><b>What Bob sees</b></summary>

<p align="center">
  <img src="assets/viewer-desktop.png" width="68%" alt="The handoff page: who passed the task, one button to copy it into Codex, and what was discussed">
  <img src="assets/viewer-phone.png" width="24%" alt="The same page on a phone">
</p>

A short note from you with a link to this page, and one button that copies a single line. He pastes it into Codex or Claude Code, in the folder where he wants the code. His agent installs co if it's missing, accepts the handoff and gets to work.
</details>

<details>
<summary><b>How it works</b></summary>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/flow-dark.png">
    <img src="assets/flow-light.png" alt="1 you say hand this to Bob; 2 your agent shows you the exact text; 3 a short note goes to Bob from your own mailbox; 4 Bob pastes one line; 5 his agent asks what the session doesn't say; 6 your agent answers from the session; 7 his agent sends the result back; 8 you see bob finished it and the git apply to run" width="100%">
  </picture>
</p>
</details>

<details>
<summary><b>What leaves your machine</b></summary>

- **Nothing goes until you approve.** You see the exact text in the preview first.
- **Secrets stop the send.** That covers anything credential-shaped (API keys, tokens, private keys) and the values of your secret environment variables.
- **Private sentences come out.** Your own agent reads every message and removes health, family, money, travel and other people's details. The preview lists each removal, and `--edit` puts any back.
- **Other people stay out.** Their email addresses, phone numbers and IPs are masked, and so are the names of the people in your [co rem](https://github.com/openonion/corem) notebook.
- **Only the conversation goes.** The commands your agent ran, and their output, stay on your machine.
- **One person picks it up.** The first agent to accept a handoff holds it, and anyone else with a forwarded link is told it's taken. A handoff nobody accepts expires after a week.
- **You can take it back.** `co handoff withdraw <id>` removes the page and the pickup.
</details>

<details>
<summary><b>Where it goes in between</b></summary>

The handoff waits on ConnectOnion's backend, so Bob can pick it up while you're offline. One nobody accepts expires after 7 days. Once accepted it's kept for 30, and `co handoff withdraw <id>` removes it sooner. End-to-end encryption for the handoff itself lands in the next release; direct agent-to-agent connections are already sealed. The note to Bob goes from your own Gmail or Outlook when you've connected one (`co auth google` or `co auth microsoft`), and otherwise from your agent's mailbox. The preview tells you which.
</details>

<details>
<summary><b>Does Bob need an account or any setup first?</b></summary>

No. The line he pastes tells his agent to install co if it's missing, then to accept the handoff. He needs Codex or Claude Code, and network access for that one install.
</details>

<details>
<summary><b>Which agents work?</b></summary>

You can send from a Claude Code or Codex session, both tested end to end. This preview also reads Gemini CLI, Cursor, opencode, droid and Grok sessions. Bob can receive in Codex or Claude Code. The skill itself installs into any agent that `npx skills` supports.
</details>

<details>
<summary><b>Can I send one session to several people?</b></summary>

Send one handoff per person. Each handoff is picked up by one agent, so every person gets their own, and you see each one's progress separately in `co handoff status`.
</details>

<details>
<summary><b>What if Bob is offline, or never opens it?</b></summary>

The handoff waits for him. One nobody accepts expires after a week, and you can take it down sooner with `co handoff withdraw <id>`. While his agent works, `co handoff status <id> --wait` on your side answers his questions from the session.
</details>

<details>
<summary><b>Copy the skill by hand</b></summary>

```bash
git clone https://github.com/openonion/handoff
cp -r handoff/skills/handoff ~/.claude/skills/     # Claude Code
cp -r handoff/skills/handoff ~/.codex/skills/      # Codex
```
</details>

<p align="center"><sub><a href="https://github.com/openonion/connectonion/blob/main/docs/cli/handoff.md">Guide</a> · <a href="https://github.com/openonion/connectonion">Code</a> · <a href="https://discord.gg/4xfD9k8AUF">Discord</a><br>Built by <a href="https://github.com/openonion/connectonion">ConnectOnion</a>. If handoff saved you a long explanation, a ⭐ helps other people find it.</sub></p>
