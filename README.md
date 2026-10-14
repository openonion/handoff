# co handoff

**Hand your Claude Code or Codex session to someone else's AI, and get the work back.**

You spent the afternoon working something out with your coding agent, and now someone else should carry it on. `co handoff` sends them the session itself:
- every message you wrote, word for word;
- your AI's replies;
- where the code is.

They paste one line into Codex or Claude Code, and their agent picks up where yours stopped. When the session doesn't answer something, their agent asks yours. When the work is done, it comes back to you as a patch.

<p align="center">
  <img src="assets/viewer-desktop.png" width="68%" alt="A handoff page: who passed you the task, one button to copy it into Codex, and what was discussed">
  <img src="assets/viewer-phone.png" width="24%" alt="The same page on a phone">
</p>
<p align="center"><sub>An example handoff page. The person you send it to reads this before installing anything.</sub></p>

## Send one

```bash
pip install --upgrade --pre connectonion            # co handoff ships in the 1.9.2 preview
co handoff send bob@example.com "the slugify rules"  # preview: exactly what will leave
co handoff send bob@example.com --draft ho-1a2b3c4d --yes
```

- Run it in the folder where you worked; it finds the session there.
- The preview prints everything that will leave your machine, and nothing goes until you add `--yes`.
- The mail goes from your own Gmail or Outlook (`co auth google` or `co auth microsoft`), so it arrives from someone they know.

## What they get

1. **A short note from you**, in your language, with a link to a page like the one above and one line to paste.
2. **One paste.** They open a new Codex or Claude Code conversation and paste the line. Their agent:
   - installs co if it's missing;
   - accepts the handoff;
   - reads what you discussed, decided and left open;
   - starts working in that folder.
3. **Questions go to your agent, not to you.** Anything the session doesn't cover, their agent asks. While `co handoff status --wait` runs on your side, your agent answers from the session, and only a question that needs your decision comes to you.
4. **The result comes back.** Their agent sends it with `co handoff done … --file result.patch`. Your status line reads "bob finished it · their file saved" and gives you the `git apply` to run.

In our own test on a small task, the person receiving it did one thing: trust the folder in Codex, with "Approve for me" on. From the paste, the patch was back in under four minutes.

## Follow along

```bash
co handoff status ho-1a2b3c4d          # accepted, questions, done
co handoff status ho-1a2b3c4d --wait   # run in the background; returns when there is news
co handoff answer ho-1a2b3c4d "…"      # a question only you can answer
co handoff withdraw ho-1a2b3c4d        # take the page down
```

## The skill

`handoff` is a plain `SKILL.md`, the format Claude Code and Codex load. With it installed, you just ask:

> "Hand this to Bob."
> "Pass the login task to priya@example.com."
> "交给 Bob。"

Your agent:
1. prepares the handoff;
2. shows you the exact text;
3. sends it only after you say yes.

On the receiving side, the same skill tells the agent what to do with a pasted handoff: accept it, do the work, ask when unsure, and report back when done.

```bash
git clone https://github.com/openonion/handoff
cp -r handoff/skills/handoff ~/.claude/skills/     # Claude Code
cp -r handoff/skills/handoff ~/.codex/skills/      # Codex
```

## You decide what leaves

- **Nothing goes until you approve.** You see the exact text in the preview first.
- **Secrets stop the send.** That covers anything credential-shaped (API keys, tokens, private keys) and the values of your secret environment variables.
- **Other people stay out.** Their email addresses, phone numbers and IPs are masked, and so are the names of the people in your [co rem](https://github.com/openonion/corem) notebook.
- **Only the conversation goes.** The commands your agent ran, and their output, stay on your machine.
- **One person picks it up.** The first agent to accept a handoff holds it. Anyone else with a forwarded link is told it's taken. A handoff nobody accepts expires after a week.
- **You can take it back.** `co handoff withdraw <id>` removes the page and the pickup.

## Learn more

- Guide: [docs/cli/handoff.md](https://github.com/openonion/connectonion/blob/main/docs/cli/handoff.md)
- Code: [openonion/connectonion](https://github.com/openonion/connectonion) (handoff lives in `connectonion/handoff/`)
- Community: [Discord](https://discord.gg/4xfD9k8AUF)
