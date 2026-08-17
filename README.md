# skillpack-account-identity-pivoting

The **Account & identity pivoting** Skill Pack for Vineyard — a text investigation *playbook* the
agent can consult when turning one account or handle into the person's other accounts, without
over-merging strangers who happen to share a username.

A Skill Pack runs no code and requests no permissions of its own; it is guidance the agent follows,
surfaced to it through the `list_skills` / `load_skill` tools. Its only dependency is the Plugin
Pack(s) its steps call, declared in `requires`.

| Field | Value |
| --- | --- |
| Identifier | `run.vineyard.skillpacks.account_identity_pivot` |
| Applies to | `identity.handle`, `identity.account`, `identity.email_address`, `identity.person` |
| Requires | `run.vineyard.pluginpacks.whatsmyname` |
| Sections | `from-handle` · `from-email` · `from-profile` — the three leads you can start from · `discriminate` — the check that would settle an open pair · `corroborate` — judging whether two accounts are one person |

## How it decides that two accounts are one person

Not by counting signals. A threshold like "three weak signals or it stays a candidate" scores
`trustno1` and `imkjd39` identically, when one is a leaked-password staple worn by tens of thousands
and the other is effectively unique — and the pack's own advice elsewhere, and the agent's base
instructions, both say a shared attribute is worth only what its rarity is worth.

So `corroborate` asks for one estimate instead: **if these were two unrelated people, how likely is
everything you are looking at?** The agent judges the crowd behind each attribute from what it knows
about the world, names what the judgement rests on so the analyst can dispute it in two seconds, and
measures instead (a quoted search, the sweep's own hit count) where it cannot name a reason. Then it
*conditions* — a globally known album title is worn by thousands, but worn by someone who is also
Korean and also works in IT security it is worn by a handful — and checks that the axes it is
multiplying came from **different tool results**, since one profile copied wholesale yields a handle,
a display name, an avatar and a bio in a single act, and an impersonator yields them the same way.

A narrow population buys evidence edges, budget, and a stronger sentence in the report. It does not
buy a same-person edge: that still takes a tool result naming both endpoints together, which is the
agent's own rule and not this pack's to relax. Counting survives only as the stated fallback for when
the population can be neither judged nor measured.

## Layout

| Path | Purpose |
| --- | --- |
| `skillpacks/account-pivot.skill.json` | The Skill Pack document (overview + sections) |

## Listing / installing

Listed in the [registry](https://github.com/Vineyard-Intelligence/registry); browsable at
[docs.vineyard.run](https://docs.vineyard.run/). The registry entry pins an immutable commit of this
repo, and the document is served from it via jsDelivr.

## License

MIT
