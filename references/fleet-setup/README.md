# Fleet setup — a worked example

Tugboat's protocol is [`SKILL.md`](../../SKILL.md). It deliberately does not
name a project's seat roster, test ladder, or checkout isolation — those are
project law. This directory is one project's answer to that layer: the class-role
charters of the `faberlang` fleet, kept as a worked example for a Mind standing
up a new fleet.

Copy the **shape**, not the tokens. Several charters here are bound to that
project's repos, commands, and lanes; they are included because an abstract
description of a lane charter is worth less than one that is actually run.

## Provenance

| | |
| --- | --- |
| Source mailspace | `~/work/faberlang` |
| Extracted | 2026-09-17 |
| Method | `vivi role charter show <role> --project ~/work/faberlang` |
| Vivi | 8.1.0 |
| Files | 21 charters, ~169 KB |

Extraction was read-only. Three files (`release.md`, `verification.md`,
`website.md`) gain a trailing newline from the CLI; their content is otherwise
byte-identical to the mailspace source.

## The charter shape

Every charter here follows the same three-part form, and that form is the most
transferable thing in this directory:

1. **A one-paragraph spawn pointer.** First line, no heading: what the seat is,
   its one job, and what it must not do. This is the text a Mind pastes into a
   spawn, and it is the whole opening prompt in the protocol's
   [handoff example](../../SKILL.md#handoff-example).
2. **`Standing law:`** — the durable rules the seat enforces on itself without
   asking. Self-enforcing law is why these charters work on small models: the
   seat does not need the Mind present to know what it may not do.
3. **Role sections and dated amendments.** Identity, job, do-not, report
   contract. Later corrections are appended with a date rather than rewritten,
   so the file accumulates the fleet's operating history.

Use the last part with care in a new fleet: the amendments carry *this* fleet's
history (a specific escalation trigger, a specific repeat failure, one
operator's ruling dated 2026-09-16), and only the general rule inside them
travels.

## The roster

`Band` is the row from the protocol's model table. "Portable" means the charter
reads as role law for any project; "project-bound" means it names surfaces that
only exist here.

| Charter | Seat | Band | Portable? | What a new fleet must rewrite |
| --- | --- | --- | --- | --- |
| `mind.md` | mind | `P0-S2` | — | Only 397 bytes: a pointer to the protocol plus this fleet's packet tool. The real Mind law is `SKILL.md`. |
| `hand.md` | hand | `P2-S0` | shape | Packets (`scripta/hand-packet`), the `$faber` skill requirement, the merge-debt rule |
| `planner.md` | planner | `P1-S2` | yes | Goal-forge phases, evidence discipline, and handoff labels read as role law anywhere |
| `auditor.md` | auditor | `P1-S1` | yes | Freeze → packet → lenses → validate → challenge → severity sequence; report schema |
| `cadence.md` | cadence | `P4-S0` | partly | Keep `A tick`, `Mail body`, `Refuse`; the process catalog, kill list, and four dated amendments are this fleet's operations |
| `head-ceo.md` | head-ceo | `P1-S2` | yes | Strategist lens; growth/standby/dormant posture dial |
| `head-cto.md` | head-cto | `P1-S2` | yes | Correctness and gate honesty; adds a decision-routing section naming this fleet's design standard |
| `head-cxo.md` | head-cxo | `P1-S2` | yes | Complexity / purity lens |
| `head-cpo.md` | head-cpo | `P1-S2` | yes | Product lens (lazy) |
| `head-cmo.md` | head-cmo | `P1-S2` | yes | Positioning lens (lazy) |
| `head-cso.md` | head-cso | `P1-S2` | yes | Security / privacy lens |
| `test.md` | test | `P2-S0` | no | The ladder itself: `radix/scripta/test` stages 3–4, lane graph, cargo-target law |
| `lint.md` | lint | `P3-S0` | no | This project's stages 1–2 gate |
| `merge.md` | merge | `P2-S0` | shape | Lane names and the ahead-of-main warning tool |
| `release.md` | release | `P2-S0` | mostly | The install script and release manifest; the "dispatch is the decision" law is portable |
| `docs.md` | docs | `P3-S0` | shape | Which repos carry docs |
| `website.md` | website | `P3-S0` | no | The site, its generator, its deploy boundary |
| `canary.md` | canary | `P2-S0` | shape | The canary surface |
| `e2e-rust.md` | e2e-<surface> | `P2-S0` | no | The command (`./scripta/e2e rust`) and the lane token |
| `triage.md` | triage | — | mostly | The report scratch directory (currently a dated folder) |
| `verification.md` | verification | — | yes | One named bounded surface, verdict, stop |

`triage` and `verification` are lanes this fleet runs that the protocol's band
table does not name; a new fleet can skip them.

## Standing up a new fleet

1. **Create the class roles in Vivi**, one per seat, with the band from the
   protocol's model table. Class roles only — the mailspace here carries 137
   roles because every unit got a numbered instance (`hand-1` … `hand-38`,
   `planner-1` … `planner-40`); those are retired, and the class charter is what
   replaced them.
2. **Adapt a charter per role**, keeping the three-part shape. Bind it to the
   project by naming the packet tool, the ladder command, and the lanes.
3. **Factor the shared layer.** Five of the six Heads here carry a byte-identical
   190-line persona block (`head-ceo`, `head-cxo`, `head-cpo`, `head-cmo`,
   `head-cso`; `head-cto` is the same block plus 27 lines). That is ~950
   duplicated lines. A new fleet should keep it in one file and have each Head
   charter reference it.
4. **Spawn by pointer.** The spawn prompt is the charter's first paragraph plus
   one handle — not the whole file.
5. **Let amendments accumulate**, dated, which is how these reached their present
   quality.

## Known warts in this set

- **Head duplication**, as above.
- **The e2e lanes are one template.** Eight surfaces (`go`, `gpu`, `llvm`,
  `runner`, `rust`, `swift`, `ts`, `wasm`) differ by 8 lines each — the lane
  token. Only `e2e-rust.md` is kept here, as the pattern.
- **`triage.md` names a dated scratch directory** (`.tugboat/cleanup-20260912/`)
  from the cleanup that produced it.
- **Hater has no class charter.** The mailspace has only `hater-1`, whose
  charter file is the `$hater` skill body. If a new fleet wants a Hater seat,
  the protocol names it but this set does not charter it.

## Not included

The human identity (`operator`), product- and bot-specific seats that carry no
role pattern (`faber-web`, `grok-pr`, `polish-analyzer`, `benchmark`, `lab-*`,
`codex`), and the retired numbered instances.
