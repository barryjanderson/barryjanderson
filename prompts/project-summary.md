# Project summary prompt

Paste the prompt below into a Cursor agent opened at the root of the repo you want to summarize. Fill in the three inputs first. The agent only reads the repo, and it returns one Markdown section plus one JSON line.

To add the result to the profile `README.md`, paste the Markdown section into the Projects list and keep the list ordered by contribution count, highest first. The JSON line is for sorting.

````text
You are helping me write a short, employer-facing product summary of one of my
software projects. The summary will appear in a public profile README, so the
source code and internal details must never be exposed.

## Inputs (I fill these in)

- PROJECT_NAME: <name to show publicly; if blank, infer it from the README or repo name>
- MY_EMAILS: <comma-separated git author emails that are me, e.g. me@example.com, 123+me@users.noreply.github.com>
- SHOW_LIVE_URL: <true | false>

## Rules

This is a read-only task. Do not modify, create, commit, or push anything.

Never output any of the following:
- Source code, code snippets, function or class names, file paths, or file names
- Git remote URLs or any GitHub/GitLab/Bitbucket repo URL
- Secrets, tokens, API keys, internal hostnames, IP addresses, or env var names
- Customer, employer, or third-party names that are not already public in the
  project's own README (if the project looks proprietary or employer-owned,
  stop and ask me before writing anything)

Writing style:
- First person ("I built...", "I designed..."), plain and specific.
- No emojis, no hype words ("revolutionary", "seamless", "cutting-edge"), no filler.
- Do not invent metrics, users, revenue, or outcomes. Only state numbers you can
  verify from the repo. If a claim is your inference rather than something the
  repo states, end that sentence with [VERIFY].
- Describe the product and the user's problem, not the implementation.

## Steps

1. Gather evidence. Read the README and any docs, package/manifest files,
   deployment and CI config, and `git log`. Do not read secrets or .env files.
2. Count my contributions. Count the unique commits across all branches whose
   author email matches any address in MY_EMAILS. Use this command, adding one
   `--author` flag per email (multiple flags are OR'd and commits are deduped):

       git rev-list --all --count --author="<email1>" --author="<email2>"

   Names are unreliable because the same person can appear under several
   names, so match on email only. If a commit author on the repo looks like me
   but is not in MY_EMAILS, list it under NOTES and do not count it.
3. Find the live product URL, if one exists. Look only at the README, the
   repo homepage field, and deployment config. It must be a public product URL
   (not a repo URL, an API endpoint that needs credentials, or localhost). If
   none exists, there is no live URL.
4. Write the section below, using at most 70 words in total across "What it
   is", "Problem it solves", and "Who it's for".

## Output

Return exactly three blocks and nothing else.

Block 1: the Markdown section to paste into the README.

### <PROJECT_NAME>

- **What it is:** <one sentence: what the product does>
- **Problem it solves:** <one or two sentences: the pain, and why it matters>
- **Who it's for:** <the target user, specific rather than "everyone">
- **Stack:** <up to 6 technologies, comma-separated, as named in manifests/config>
- **Live:** <URL>
- **Contributions:** <N> commits

Omit the "Live" line when there is no live URL. When SHOW_LIVE_URL is false and
a live URL exists, replace the line with this HTML comment so I can add it by
hand: `<!-- Live: add URL manually -->`

Block 2: one line of JSON for sorting.

{"project": "<PROJECT_NAME>", "contributions": <N>}

Block 3: NOTES, a short bullet list covering:
- every sentence tagged [VERIFY] and why you inferred it
- any commit author you did not count
- anything in the repo that looked proprietary or sensitive that I should check
- any claim in the repo's docs that disagrees with its config or code
````
