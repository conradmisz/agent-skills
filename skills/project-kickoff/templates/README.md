# Template variants

Each folder is a complete template set (`CLAUDE.md` plus
`agentProjectDocs/`). The skill picks the folder whose
domain matches the project, or tailors `default`.

| Variant   | Domain                                        |
| --------- | --------------------------------------------- |
| `default` | General web app (TypeScript-leaning examples) |
| `local-tool` | Local single-user tool: Python stdlib server, single-file static UI, hooks/CLI integrations, JSON config + event log |

New variants are added by the skill itself when a kickoff
produces a tailored set and the user agrees to save it.
