## 1. Configurable filter

- **Depends on:** timeline
- **Contract:**
  - In: TakeData
  - Requires: Butterworth (body) and One Euro (hands); can be turned off, since FreeMoCap already filters
  - Delivers: `smooth(data, cfg)`
- **Pre-work:** none
- **Out of scope:** —
- **Tests:** synthetic noise reduced with no phase lag (filtfilt)
