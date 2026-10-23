# Template variants

Each folder is a complete template set (`CLAUDE.md` plus
`agentProjectDocs/`). The skill picks the folder whose
domain matches the project, or tailors `default`.

| Variant   | Domain                                        |
| --------- | --------------------------------------------- |
| `default` | General web app (TypeScript-leaning examples) |

New variants are added by the skill itself when a kickoff
produces a tailored set and the user agrees to save it.
