## 0. Jitter filter research

- **Type:** research task. Its deliverable is a document with a recommendation, not code.
- **Depends on:** a real take processed through P3 (`mocap-extract` body), so the
  jitter can be measured instead of guessed
- **Contract:**
  - In: 3D body and hand trajectories from real takes (static T-pose, slow
    motion, fast motion), at the take's constant FPS
  - Requires:
    - measure the jitter: spectrum of bone-end positions on the static and slow
      takes, so the jitter band can be told apart from the motion band
    - compare the filters used for markerless mocap: zero-phase Butterworth
      (`filtfilt`), One Euro, Savitzky–Golay, Kalman + RTS smoother, and
      bone-length-constrained smoothing. Check each for phase lag, how it
      treats fast motion (no "rubber" lag on a punch), and how it behaves at gaps
    - Rafael's target (2026-10-12): bones don't visibly jitter. 1–3 mm of
      residual is acceptable, and the character models get enough fluidity
      that what remains reads as natural
    - every library used must have a license that allows commercial use
  - Delivers: `docs/filtering-research.md`: measured jitter band per joint
    group (body, hands), the recommended filter(s) and parameters per group,
    and how to measure residual jitter. It feeds task 1's filter choice
- **Pre-work:** a processed real take (blocked on the capture initiative gate)
- **Out of scope:** implementing the filter (task 1)
- **Tests:** — (research). The numbers in the document must come from takes,
  with the script used kept under `tools/`
