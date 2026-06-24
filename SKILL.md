---
name: pymeasure
description: Use when working with PyMeasure - the Python library for scientific measurement, instrument control, and experiment automation (built on PyVISA): the Instrument/Channel base classes and dynamic properties, instrument drivers by manufacturer (Keithley, Agilent/Keysight, HP, Lake Shore, SRS, Tektronix, Rohde & Schwarz, ...), Adapters (VISA/serial/Prologix/TCP), the Procedure/Experiment/Worker framework, Results, plotting/display, and the measurement workflow. from pymeasure.instruments import ... Not for the Python stdlib, raw PyVISA, or other instrument-control libraries.
---

# PyMeasure Reference

Original-prose reference for PyMeasure, split into one focused file per subject across 109 reference files.
Identifiers (API/type/function names, flags, paths, enums, numbers) are preserved verbatim.

## When to use this

Use this skill when the task involves the PyMeasure library - instrument drivers by manufacturer, the Instrument/Channel base classes and dynamic instrument properties, Adapters (VISA/serial/Prologix/TCP), the Procedure/Experiment/Worker automation framework, Results storage, plotting/display, and the end-to-end measurement workflow.

## Workflow

1. Open `references/INDEX.md` (or `references/topics.json`) and pick the one file that matches.
2. Read only that file; open another only if the task spans subjects. Grep across files when needed: `rg -n "PATTERN" references/*.md`.
3. Treat every identifier as an exact reference fact - never invent or paraphrase.

## Gotchas

Recurring failure modes and what to do instead live in the sibling [GOTCHA.md](GOTCHA.md).

## References

All depth lives in `references/` - start at `references/INDEX.md`, metadata in `references/topics.json`. One subject per file.

## Source

Adapted from the upstream PyMeasure documentation into original prose for local reference. Identifiers remain verbatim. Upstream: https://pymeasure.readthedocs.io/en/latest/

## Verification

```powershell
python D:\dev\SKILLS\skills\skill-drafting\scripts\validate_skill_package.py D:\dev\SKILLS\skills\pymeasure
```
