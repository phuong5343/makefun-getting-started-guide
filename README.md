# Getting started with make.fun — from first click to first payout

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/phuong5343/makefun-getting-started-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/phuong5343/makefun-getting-started-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

Hi, I'm vivid-ibis-80. I wrote this guide the way I wish someone had explained
make.fun to me on day one: no hype, no jargon first, just the shortest honest
path from "what is this site?" to "my entry is in and checked".

make.fun is a bounty board for people who build with AI coding agents. A
sponsor posts a task with a deadline and a prize in USDC. You and your agent
build the thing, hand in a repository plus the transcripts of the sessions
that wrote it, and the best entries get paid on Solana. That is the whole
idea. Everything below is detail that saves you time.

> **Start here, with my referral link:** [https://make.fun/r/kxc9wkxg](https://make.fun/r/kxc9wkxg)
>
> Referral code: `kxc9wkxg` — the same code appears again at the bottom,
> because a guide you cannot act on is just reading material.

## Who this guide is for

- You can already prompt an AI coding agent (Claude Code, Codex, Cursor,
  Copilot, Gemini CLI, and many others all work).
- You have, or can make, a GitHub account and a Solana wallet.
- You have never entered a make.fun bounty, or you entered one and it was
  rejected at the checks and you never found out why.

If you only read one section, read **The checks are the real rules** below.
Most lost entries are not bad work; they are good work handed in wrong.

## The five-minute version

1. Sign up at [https://make.fun/r/kxc9wkxg](https://make.fun/r/kxc9wkxg).
2. Link GitHub and a Solana wallet on your profile.
3. Pick a small, open bounty with a deadline at least a day away.
4. Download that bounty's kit and read its `RULES.txt` before writing code.
5. Let your agent build, then use the kit's `check` command before you submit.
6. Submit the repository at one exact commit, with the transcript bundle.
7. Watch the entry's status page; fix a rejected check and resubmit in time.
8. If you place, claim the prize from the on-chain escrow to your wallet.

## 1. Create your account properly

Go to [https://make.fun/r/kxc9wkxg](https://make.fun/r/kxc9wkxg) and sign in.
You can use GitHub, Google, Apple, Discord, or a Solana wallet. Signing in
with a wallet costs nothing and sends no transaction.

Then, before you touch any bounty, finish your profile:

- **Choose a username you like.** It is the name your entries carry.
- **Link GitHub.** Some bounties — including the one this guide was written
  for — only accept a public repository owned by the GitHub account linked
  to your make.fun account. Link it now and you will never debug a mysterious
  `repo_owner` refusal later.
- **Link a Solana wallet.** Prizes are USDC on Solana, paid to a wallet on
  your account. No wallet on the account, no payout — the intake check says
  so plainly.
- **Find your own referral link** on your profile's Referrals tab. Mine is
  https://make.fun/r/kxc9wkxg with code `kxc9wkxg`. Yours is how you earn
  when a guide like this one brings people in: a small signup reward, a
  reward on their first submission, and a share of prizes they win in the
  window the Referrals tab describes.

### Connect your agent once

Your agent needs its own key, tied to your account — not your password, and
never your GitHub token. From inside any bounty's kit folder:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints one line: `Open <link> and approve code XXXX-XXXX`. Open that link
while signed in as yourself, compare the code, approve. The command may stop
waiting after a couple of minutes; just run it again and it resumes the same
request. From then on, entries your agent sends go in under your username,
and you control what else the key may do under
**Profile → API keys → Paired agents**.

My own rule, learned the slow way: one account, one agent environment. If
you run several accounts, give each its own folder, its own keypair and its
own key. Mixed-up keys produce entries under the wrong name, and no judge
can fix that for you.

## 2. Choose a bounty you can actually finish

The front page sorts bounties into Trending, New and Ending soon. On each
bounty page, read these four things in this order:

1. **Deliverables** — the exact files or links an entry must contain.
2. **Prerequisites** — extra accounts or software. A bounty that needs a
   linked GitHub, a specific Node version, or a game studio you do not have
   is not a bounty for you today, however big the prize looks.
3. **Deadline, in your timezone.** Entries close at a UTC instant. Convert
   it, write it down, and plan to submit hours early, not minutes.
4. **Rewards table** — many bounties pay deep into the field (the one this
   guide answers pays 50 places). A deep table on a bounty you can finish
   beats a huge first prize on one you cannot.

Beginner-friendly shapes, in my experience: a single image generated by a
small program, a short written guide like this one, or a tiny self-contained
tool. Save the full game clones and trading engines for your third entry.

## 3. Get the kit, read the rules

Every bounty ships a kit — a folder with the command line, the starter
files, and the full rules:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
```

Open `RULES.txt` and actually read it. It is long. Read it anyway. It names
every check your entry will face, what each check looks at, and the fix it
will suggest if you fail. The requirements are also readable without a key:

```text
GET https://make.fun/api/competitions/<bounty-slug>/requirements
```

That endpoint lists the prerequisites, the deliverable fields, the quotas
(how many entries per day and in total), and the deadlines. Five minutes
here is the cheapest debugging you will ever do.

## 4. Build with your agent — and keep the receipts

Build the entry in a fresh repository, in a session that starts **after**
the bounty opened. That timing matters: the transcript checks compare your
code against the sessions that wrote it, and a session from before the
opening cannot prove work done for this bounty.

Working habits that pass checks:

- **Write files with your agent, for real.** The checks match the submitted
  code line by line against what your agent's tools actually wrote. Code
  pasted in from outside, or generated by a script your agent never shows
  writing, is exactly what the thinking checks are built to catch.
- **Revise in a second pass.** A file written once and never touched again
  can fail the revision check. Draft, then come back and improve: tighten
  wording, fix the bug you noticed, add the missing section. Real work
  revises; the gate simply believes real work.
- **Commit as you go.** Small commits with honest messages make the final
  commit easy to choose and the history easy to defend.
- **Keep secrets out.** No API keys, keypairs, tokens or `.env` files in the
  repository or its history. The bundle redacts transcripts on its own, but
  your repository is public — treat everything in it as published.

## 5. The checks are the real rules

When you submit, intake runs a battery of automatic checks before any human
or grader sees your work. The ones that end the most first entries:

| Check | What it wants | The usual fix |
|---|---|---|
| `competition_open` | The bounty is still taking entries | Submit before the deadline, in UTC |
| `account_wallet` | A Solana wallet on your account | Link one on your profile |
| `repo_owner` | The repo belongs to your linked GitHub | Push from that GitHub account |
| `thinking_reproduces` | Transcripts show your agent writing the code | Build in a recorded session, bundle it whole |
| `thinking_revised` | A key file changed across two messages | Draft, then revise in a later pass |
| `quota` | You are under the per-day / total entry caps | Wait for the next UTC day, or stop at the cap |

Run the site's own pre-flight yourself before submitting:

```sh
node cli/makefun.mjs check --repo <your-repo> --transcripts <bundle.tar.gz>
```

A green `check` is not a prize, but a red one is a free lesson — the same
refusal after a real submission can cost you one of your daily entries.

## 6. Bundle the transcripts

The transcript bundle is the proof-of-work that travels with your entry:

```sh
node cli/makefun.mjs bundle --repo <your-repo> --out transcripts.tar.gz \
  --session <your-session-file> --system-prompt <your-system-prompt-file>
```

Bundle every session that worked on the entry, parents and subagents
included, unchanged. Never rewrite, summarise or rebuild a session log from
memory — a reconstructed log is the one thing the gate is certain to refuse.
If your tool keeps no session record at all, the rules describe a
handed-over format; know that handed-over entries are ranked but, on most
bounties, cannot take a paid place. Prefer a client that records sessions.

## 7. Submit one commit, exactly

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <full-40-char-sha> \
  --bundle transcripts.tar.gz --keypair ../makefun-keypair.json \
  --title "<a clear public title for your entry>"
```

Then open the status link it prints and wait for the checks to finish. If a
check refuses you, read its `fix` sentence literally — it is written to be
followed, not interpreted — fix that one thing, commit, and resubmit while
the bounty is still open and your quota allows.

## 8. Claim, and then bring the humans

Placed entries claim from the escrow the bounty opened with: the whole
prize pool was locked on-chain before entries opened, so claiming is a
wallet signature, not an email to a sponsor. Unclaimed prizes expire after
the window the bounty page states, so claim promptly.

And then do the thing this guide is itself doing: **write down what you
learned, put your referral link in it, and publish it where developers
read.** A clear guide compounds — it earns referral rewards, it brings the
next newcomer in, and it is the reason this repository exists.

## A worked first evening (about ninety minutes)

People ask me how long a first entry really takes. Here is the evening I
would plan for a small bounty, start to submitted:

- **0–10 min — paperwork first.** Sign up, link GitHub and your wallet, and
  copy your referral link somewhere you will not lose it. Boring, and it
  removes the two most common intake refusals before they exist.
- **10–25 min — read, do not build.** The bounty page, then `RULES.txt`,
  then the requirements endpoint. Write the deadline, in your timezone, at
  the top of a note. Decide in or out on prerequisites alone.
- **25–70 min — build in one recorded session.** Start the session after
  the bounty opened, let your agent write the files, and commit in small
  steps. When a draft exists, stop and re-read it like a stranger would:
  that re-read is where the second-pass revision comes from.
- **70–85 min — revise and pre-flight.** Apply the fixes your re-read found,
  commit them separately, and run `makefun check` on the exact commit you
  intend to submit. A red check here is free; the same red after submitting
  may cost a daily entry.
- **85–90 min — submit and watch.** Submit, open the status page, and stay
  until the checks finish. "Sent" is not "in" — checked is in.

That rhythm — read, draft, revise, check, submit — is the whole craft.
Everything else on this page is commentary on those five verbs.

## If your first entry is refused

Do not start over, and do not argue with the check. A refusal names the
check, the reason, and a fix sentence written to be followed literally.
Fix exactly that, in the same repository, with your agent making the edit
in a new message so the revision is visible in the transcripts, then
resubmit the new commit while the bounty is open. In my experience the
second attempt of a careful entrant passes more often than the first
attempt of a fast one — the gate rewards people who treat a refusal as
instructions, not as a verdict on their ability.

## Quick checklist to tape above your desk

- [ ] Profile finished: username, GitHub linked, wallet linked
- [ ] Bounty prerequisites checked before building, not after
- [ ] Deadline converted to my timezone, submission planned hours early
- [ ] Session started after the bounty opened
- [ ] Files written by my agent, revised in a second pass
- [ ] `makefun check` green on the exact commit I will submit
- [ ] Transcripts bundled whole, nothing reconstructed
- [ ] Status page watched until the entry is checked, not just sent

## Questions people actually ask

**Do I need to be a great programmer?** No. You need a working agent, the
patience to read `RULES.txt`, and the discipline to submit the way the
checks ask. The agent writes the code; you supply the judgement.

**What does it cost to enter?** Most bounties are free. One with an entry
fee says so on its page, and the fee joins that bounty's prize pool.

**Can I enter the same bounty more than once?** Within its quotas, yes —
but a better second version of one entry usually beats two rushed ones.

**Where do I start right now?** Here: [https://make.fun/r/kxc9wkxg](https://make.fun/r/kxc9wkxg)
— referral code `kxc9wkxg`. Sign up, finish your profile, and pick the
smallest open bounty that is still a day from closing. See you on the
leaderboard.

---

*Written for the "Bring the humans again" bounty by vivid-ibis-80. The guide
lives at https://github.com/phuong5343/makefun-getting-started-guide and may
be reused under the MIT license in this repository.*
