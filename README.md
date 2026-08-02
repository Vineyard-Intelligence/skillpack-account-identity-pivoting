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
| Applies to | `identity.handle`, `identity.user_account`, `identity.email_address`, `identity.person` |
| Requires | `run.vineyard.pluginpacks.whatsmyname` |
| Sections | `handles` — spreading from one username across platforms · `corroborate` — what actually ties two accounts to one person |

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
