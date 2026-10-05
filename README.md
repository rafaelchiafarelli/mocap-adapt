# mocap-adapt

P4, **on the processing PC**: turns the raw 3D motion from `mocap-extract`
into clean animation data. It puts everything on one timeline, smooths the
jitter, locks the feet to the floor during ground contact, and exports the
`MocapTake` that Blender reads.

## Where it sits in the architecture

```
mocap-extract ──extract/index.json──▶ mocap-adapt ──adapt/mocap_take.json──▶ mocap-blender
```

- **Timeline (4.1):** loads the extraction index and puts body and hands on
  one timeline, with gaps marked, never filled in silently
- **Smoothing (4.2):** a configurable filter (Butterworth / One Euro)
- **Ground contact (4.3):** detects foot contact and locks the feet
- **Export (4.4):** `adapt/mocap_take.json` (`MocapTake`, defined in
  `mocap-contracts`), in metres, Z up

Body and hands only in the baseline. The face and emotion fields of
`MocapTake` exist but stay empty (phase 2).

## Status

Planned, no code yet. It's off the critical path to the camera decision.
Plan: [`initiatives/baseline/`](initiatives/baseline/baseline.md). Architecture:
`mocap-studio/HANDOFF.md`.
