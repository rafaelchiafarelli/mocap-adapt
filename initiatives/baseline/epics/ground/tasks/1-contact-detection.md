## 1. Contact detection

- **Depends on:** filtering
- **Contract:**
  - In: 3D feet + plane
  - Requires: height and velocity below a threshold, with hysteresis and minimum duration
  - Delivers: `detect_contacts(data) -> foot_contact[frames]`
- **Pre-work:** none
- **Out of scope:** —
- **Tests:** synthetic walk
