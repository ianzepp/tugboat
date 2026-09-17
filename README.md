# Tugboat

Lightweight multi-agent operating protocol: one **Mind** routes work, **Hands**
implement, **Auditors** and **Heads** review, **Cadence** advises. The durable
record is [Vivi](https://github.com/ianzepp/vivarium). They go together.
Tugboat is the protocol; Vivi is the board and the CLI. The host starts
processes. Tugboat does not.

This is the protocol the author actually runs. [Fleet](https://github.com/ianzepp/fleet)
is the earlier, heavier runtime (tmux, sensors, cycle-close scripts). Fleet
still exists. Tugboat replaced it for daily use because the coordination
overhead left too little room for product work.

## Start here

- [`SKILL.md`](SKILL.md) — the whole protocol: operating modes (Mind / Direct),
  boot modes, six rules, roles, cadence, board kinds, anti-patterns
- [`scripts/check-task-body.py`](scripts/check-task-body.py) — optional gate
  that a Hand task body is a pointer to one logical change
- [`references/fleet-setup/`](references/fleet-setup/) — one project's worked
  example of the project layer: 21 class-role charters, the shape they share,
  and how to stand up a fleet from them

## Install

Clone and point an agent skill directory at this repo root (the folder that
contains `SKILL.md`):

```sh
git clone https://github.com/ianzepp/tugboat.git
ln -s "$(pwd)/tugboat" ~/.agents/skills/tugboat
```

You also need Vivi. Install the CLI from
[vivarium](https://github.com/ianzepp/vivarium) and point a skill directory at
that repo's [`skills/vivi`](https://github.com/ianzepp/vivarium/tree/main/skills/vivi):

```sh
git clone https://github.com/ianzepp/vivarium.git
ln -s "$(pwd)/vivarium/skills/vivi" ~/.agents/skills/vivi
```

## What Tugboat is not

Tugboat does not name a project's test ladder, checkout isolation, or seat
roster. Those live in the project's own agents/charter docs. Optional
companions (transcript search, model inventory, polish helper, hater skill)
are used when present and skipped when absent.

[`references/fleet-setup/`](references/fleet-setup/) carries one project's
charters as a worked example of that layer. It is illustration, not shipped
law: those charters bind to that project's repos, commands, and lanes, and no
part of them is required to run Tugboat.
