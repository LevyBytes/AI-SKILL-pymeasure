# PyMeasure Instrument-Control Reference

This is the `pymeasure` skill for Agent Kaizen: an original-prose reference package derived from the PyMeasure documentation, with API identifiers, class names, parameter names, resource strings, and numeric values preserved exactly.

## What this skill covers

PyMeasure is the Python library for scientific measurement, instrument control, and experiment automation, built on PyVISA. This skill covers the `Instrument`/`Channel` base classes and dynamic properties, instrument drivers organized by manufacturer (Keithley, Agilent/Keysight, HP, Lake Shore, SRS, Tektronix, Rohde & Schwarz, and more), and the Adapters that handle VISA, serial, Prologix, and TCP connections. It also covers the `Procedure`/`Experiment`/`Worker` automation framework, `Results` storage, plotting/display, and the end-to-end measurement workflow. It is not for the Python standard library, raw PyVISA, or other instrument-control libraries.

## What's inside

- `SKILL.md` - the skill entry point: trigger description, workflow, and pointers into the reference set.
- `references/` - all depth, one subject per file, plus `INDEX.md` for browsing and `topics.json` for metadata-driven lookup.
- `GOTCHA.md` - recurring failure modes, including exact identifier handling, PyVISA backend requirements, and version-sensitive drivers.

## Use it

The published skill lives at `<devroot>\SKILLS\skills\pymeasure` and is linked into each agent surface as a per-skill junction. Edit the store copy directly; do not copy it through `.agents` or `.claude`.

## Status

The reference prose has been recontextualized into original AGPL-licensable wording. Upstream identifiers are intentionally preserved verbatim.

## Reducing idle context cost (skill invocation policy)

Every installed skill costs a little context on every session: the agent sees each skill's name and description before you ever use it. If you rarely use this skill in a given project, you can keep it installed and still explicitly invocable while hiding it from the model's automatic listing.

Doing so does **not** modify this skill's source repo — the policy lives in your local agent settings. The Agent Kaizen **[skill-drafting](https://github.com/DirectorGunner/AI-skill-drafting)** repo ships a manager, `scripts/skill_policy.py`, that sets this for all your skills at once:

```bash
python skill_policy.py audit     # list every skill + its current policy + idle cost
python skill_policy.py plan      # write a decision file with recommendations (nothing applied)
# edit that decision file: set selected_policy + approved:true for the skills you choose
python skill_policy.py preview   # show the exact change
python skill_policy.py apply     # apply ONLY what you approved (backup + rollback recorded)
python skill_policy.py restore   # roll back
```

- **Claude Code (works today):** writes `skillOverrides: { "<skill>": "user-invocable-only" }` to `.claude/settings.local.json` — zero idle listing cost, still available from the `/skills` menu. Start a new session for it to take effect; invoke it any time via `/skills`.
- **Codex (currently unreliable):** explicit-only Codex skills are affected by an open bug ([openai/codex#23454](https://github.com/openai/codex/issues/23454)) where `$skill` invocation of an explicit-only local skill can fail. Until it's fixed, leave Codex skills implicit, or fully disable rarely-used ones with `[[skills.config]] enabled = false` in `config.toml`. The manager audits Codex but does not change Codex policy.
