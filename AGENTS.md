# liao-info-site — agent instructions

Scope: registry entry `liao-info-site` in `hamlet-archer/atlas` — resolve it with
`atlas.py field liao-info-site scope`; this file does not restate it.

<!-- atlas:pointer:start — verbatim from hamlet-archer/atlas template/AGENTS.md
     (ADR 0023); reconcile's pointer/verbatim flags drift. Edit it there, not here. -->
## Workspace

`hamlet-archer/atlas` (clone: `~/Repo/atlas`) is the workspace registry. Before
asking Kelvin a workspace-shaped question, look there:

- **Which project owns this?** `registry/projects.yaml` — resolve there, never
  guess.
- **Machines and what runs where:** `registry/hosts.yaml`.
- **Credentials:** `registry/platform.yaml` (`credentials:`) ledgers every
  machine credential. Values live in 1Password vault `AI`, and that grant is
  standing authorization for agent sessions to *use* them — pipe a value into
  its consumer; never display or commit it (atlas ADR 0019). Check
  `op item list --vault AI` before claiming a step needs Kelvin: his boundary
  is billing consent and the `Finance` vault, not use and not minting.
- **A credential that does not exist yet is minted in atlas, never here.**
  `python3 scripts/mint.py` there mints from a reviewed scope profile, proves
  the scope both ways, and prints the ledger entry — so a token cannot exist
  unregistered (atlas ADR 0030). `mint.py --vendors` says which vendors it can
  mint for and, for the ones it cannot, why and what to do instead. Rotation
  is `mint.py rotate <item-id>`.
- **Tickets and workflow:** `docs/workflow.md`. **Live rules:**
  `python3 scripts/atlas.py decisions` — one sentence each.
<!-- atlas:pointer:end -->

