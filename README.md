# skillpack-account-identity-pivoting

The **Account & identity pivoting** Skill Pack for Vineyard: a text investigation playbook that turns one account, handle, email address, or profile into the accounts behind the same person, without merging strangers who happen to share a name.

| Field | Value |
| --- | --- |
| Identifier | `run.vineyard.skillpacks.account_identity_pivot` |
| Version | `3.3.1` |
| Applies to | `identity.handle`, `identity.account`, `identity.email_address`, `identity.person` |
| Requires | `run.vineyard.pluginpacks.whatsmyname` |

## When to use
- The analyst has a username, email address, or profile and asks where else this person is.
- You need to expand a lead into other accounts, handles, addresses, or profile fields.
- You need to decide whether two accounts are one person or two people who share a name.

Do not use it for one fact about one account, or for an infrastructure question. Hand infrastructure off to "Infrastructure pivoting".

## Requirements
- The `run.vineyard.pluginpacks.whatsmyname` plugin pack for the handle sweep. This pack declares it in `requires`; the skill is not offered when the pack cannot run in the project. WhatsMyName is desktop-only, so the skill is not available in the web build.
- Graph write access to stage accounts, handles, and edges.
- Platform, PGP, image, archive, or document plugins for the checks you take. Where one is missing, name the check you cannot run.
- `challenge_claim` for the pre-merge challenge.

## Structure
The `overview` is the top-level Markdown card. Load one section for the lead you are holding; each section body is a self-contained Markdown document with its own `#` title and `##` headings.

| Section | Use it for |
| --- | --- |
| `from-handle` | Spread one username across platforms and stage each hit as a candidate. |
| `from-email` | Turn one address into the handles, keys, documents, and accounts behind it. |
| `from-profile` | Mine one profile page for every field that gives an independent pivot. |
| `discriminate` | Turn a candidate pair with a gap into a decision. |
| `corroborate` | Decide whether two accounts are one person: estimate the population, check independence, then decide. |

## How it decides that two accounts are one person

Not by counting signals. A shared attribute is worth only what its rarity is worth.

`corroborate` asks for one estimate: **if these were two unrelated people, how likely is everything you are looking at?** The agent judges the crowd behind each attribute, names what the judgement rests on so the analyst can dispute it, and measures instead (a quoted search, the sweep's own hit count) where it cannot name a reason. It multiplies only axes that came from **different tool results**, since one copied profile yields a handle, display name, avatar, and bio in a single act.

A narrow population buys evidence edges, budget, and a stronger sentence in the report. It does not buy a same-person edge: that still takes a tool result naming both endpoints together. Counting is only the fallback for when the population can be neither judged nor measured.

## Layout

| Path | Purpose |
| --- | --- |
| `skillpacks/account-pivot.skill.json` | The Skill Pack document (overview + sections + starters) |
| `.github/workflows/validate.yml` | CI validation |

## Listing / installing

Listed in the [registry](https://github.com/Vineyard-Intelligence/registry); browsable at [docs.vineyard.run](https://docs.vineyard.run/). The registry entry pins an immutable commit of this repo, and the document is served from it via jsDelivr.

## License

MIT
