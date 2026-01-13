## Generic engineering prompt

Assume you are a senior process engineer designing a hybrid first-principles + ML model for an industrial unit operation.

### Step 1 – Define the unit operation

- Identify the conserved quantities (mass, energy, momentum, species).
- List manipulated variables, disturbances, and measured outputs.
- Define operating envelopes and known failure / degradation modes.

### Step 2 – Build the first-principles backbone

- Write the governing balances and constitutive relationships.
- Identify parameters that degrade, drift, or are uncertain over time.
- Explicitly state physical constraints the system must never violate.

### Step 3 – Generate synthetic operating scenarios

- Simulate normal, stressed, and off-design conditions.
- Include slow degradation, maintenance events, and mode transitions.
- Inject realistic sensor noise, bias, and sampling effects.

### Step 4 – Blend with historian data

- Align synthetic data with real tags and timestamps.
- Use real data to anchor ranges, correlations, and noise statistics.
- Reject synthetic scenarios that contradict plant reality.

### Step 5 – Train a constrained ML model

- Train ML only on residuals, nonlinearities, or unmodeled effects.
- Enforce conservation laws and operating limits during training.
- Ensure predictions remain explainable and auditable.

### Step 6 – Define engineering-grade outputs

- Health or degradation indices.
- Early warning indicators.
- Sensitivity to operating conditions.
- Actionable recommendations (not raw predictions).

### Step 7 – Validate like an engineer

- Test extrapolation to new operating regimes.
- Check physical plausibility, not just accuracy metrics.
- Confirm failure modes are detected before alarms trip.
