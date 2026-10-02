# Publication governance

## Authority and scope

Christopher Spitzner is the publication authority. This repository holds DONE
WITH AI documentation, the experiment registry, publication records,
retrospectives, recorded metrics, approved source snapshots when appropriate,
and links to canonical project repositories or releases.

Applications, games, experiments, and tools are developed elsewhere. A source
snapshot here never makes this repository its development working tree. Do not
duplicate whole repositories unnecessarily or allow this to become a monorepo.

## Three states

1. **Development:** work in a separately authorized development repository.
   Changes never automatically propagate here.
2. **Publication candidate:** prepare and inspect a local candidate when the
   human identifies a project or milestone for publication. Preparing it does
   not authorize making it public.
3. **Published snapshot:** publish only the exact candidate explicitly approved
   by Christopher. Public history represents intentional milestones.

Work locally, collect changes, validate, show the human, obtain approval, and
perform one coherent publication. Prefer one meaningful commit per operation;
multiple commits must represent distinct logical changes. Never inflate activity
or run an edit/commit/push loop. After publication, stop and report any newly
discovered problem before attempting another change.

`main` is the canonical public branch. Candidates can be reviewed locally; no
additional branch system is required.

## Authorization and change limits

Approval must identify the current publication contents. Approval from another
task and broad instructions such as "continue" or "fix everything" do not
authorize publication. Any change after approval requires a new report and
approval.

Without explicit authorization for the current operation, agents must not push,
merge, publish, upload snapshots, create releases, tags, remote branches,
issues, or pull requests, close issues, modify repository settings, enable
Pages, create Actions, change visibility or licenses, delete remote content,
rewrite history, or force push.

Prefer the smallest coherent change. Before modifying more than 10 files or
creating more than 5 new files, stop and explain why; exceeding those limits
requires explicit approval for that operation. Request approval before deleting,
moving, or renaming any published path.

Initially there are no GitHub Actions, bots, Dependabot configuration, scheduled
jobs, automatic releases, synchronization, documentation generation, auto-merge,
or autonomous agent triggers. Introduce automation only after its behavior is
understood and explicitly approved.

## Identity and records

`registry/projects.json` is the canonical source of identity and status. IDs use
`DWAI-001`, `DWAI-002`, and so on; presentation may use `#001`. Published IDs
never change, and IDs must never be reused or renumbered after cancellation.
Failed and cancelled experiments may remain in the record.

Allowed statuses are `planned`, `development`, `publication-candidate`,
`published`, `paused`, `failed`, and `archived`. Include only known metadata;
documentation must agree with the registry. Do not invent dates, counts, costs,
hours, performance, or other results. Missing historical information is
"Not recorded." and estimates are labeled "Estimate."

## Import and review

Never recursively copy a development tree into this repository. Before import,
prepare a manifest with: source, destination, project ID, publication type,
included paths, excluded paths, license status, asset status, secret scan result,
and human approval status. Use explicit allowlists wherever practical.

Review the complete candidate, including text contents and filenames, for:

- Secrets and credentials: `.env` variants, private keys, certificates, SSH
  material, API/access/OAuth tokens, passwords, cookies, sessions, authentication
  headers, seed phrases, wallets, cloud and service-account credentials.
- Personal and private data: addresses, phone numbers, private correspondence,
  family and financial information, account identifiers, internal notes, private
  configuration, database contents and dumps. Private conversation content is
  not approved public identity information. Publishing private data requires
  explicit approval of that exact data for that exact publication.
- Rights: classify source and assets as `OWNED`, `OPEN-LICENSED`,
  `REDISTRIBUTABLE`, `REFERENCE-ONLY`, `UNKNOWN`, or `PROHIBITED`. Resolve
  `UNKNOWN` before publication. Reference-only and prohibited material must not
  be redistributed. Possession does not establish redistribution rights; review
  third-party code, game assets, music, ROMs, firmware, fonts, commercial SDKs,
  proprietary libraries, and media particularly carefully.
- Unnecessary files: binaries, builds, installers, archives, video, large audio
  and textures, disk images, databases, logs, caches, temporary exports, IDE and
  Godot import caches, dependencies, coverage, and generated output. Normally
  exclude these; exceptions need a clear publication reason. Prefer separately
  approved release hosting for binaries. Do not introduce Git LFS automatically.

Any suspicious item stops publication. Report its file, reason, and recommended
remediation without revealing secret values. The human must review remediation;
never automatically sanitize a secret and then publish.

Keep documentation useful, minimal, factual, and specific. Do not generate
placeholder documents, fake FAQs, roadmaps, changelogs, promotional claims,
badge clutter, or recursive documentation improvements.

## Publication checkpoint

Before any public push, present a report containing every field below. Use
"Not applicable" or "Not recorded." when appropriate; do not fabricate values.

```text
PROJECT:
PROJECT ID:
SOURCE:
TARGET:
FILES ADDED:
FILES MODIFIED:
FILES DELETED:
TOTAL SIZE:
SECRET SCAN:
PERSONAL DATA REVIEW:
LICENSE REVIEW:
ASSET REVIEW:
BINARY REVIEW:
TEST STATUS:
DOCUMENTATION STATUS:
KNOWN ISSUES:
EXACT COMMIT MESSAGE:
EXACT REMOTE:
EXACT BRANCH:

PUBLICATION STATUS: AWAITING HUMAN APPROVAL
```

Stop without pushing. Valid approval explicitly refers to the reviewed candidate,
for example "Approve this publication report and push it." Changed contents
invalidate approval.

After a successful approved push, report the repository, branch, commit SHA,
files changed, publication/project ID, and remote URL. Then stop: no cleanup
commit, additional publication, or new project.
