# WH Auto v0.3 — Auto Probe rationale

Observed on the vehicle with v0.2:
- `bridge.Charge.loader = OK`
- `bridge.Energy.loader = OK`
- `bridge.Charge = NO_CURSOR`
- `bridge.Energy = NO_CURSOR`

Interpretation:
- DiCarServer classes are loadable by the app.
- The failure is specifically in the provider route returning no Cursor.
- Therefore v0.3 probes several read-only ContentProvider access shapes automatically.

The app remains read-only. It does not invoke vehicle-control setters.
