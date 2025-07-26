# Synthetic Load Duration Curve Analysis: Data Centers and Virtual Power Plants (VPPs)

A very simple notebook that explores how the addition of inflexible data center loads and flexible Virtual Power Plant (VPP) resources affect the shape of a regional power system’s Load Duration Curve (LDC). It uses synthetic hourly load data to illustrate how VPPs can shift demand away from peak hours, potentially mitigating capacity strain from new constant loads such as data centers.

---

## What This Script Does

1. **Generates synthetic baseline load** data for a full year (8760 hours) using a normal distribution.
2. Simulates three load scenarios:
   - **Data Center Load Only**: Adds a constant 6 GW to the baseline.
   - **VPP Flexibility Only**: Simulates 6 GW of flexible demand shifting from high-load to low-load hours.
   - **Both Combined**: Adds 6 GW of inflexible load and 6 GW of VPP shifting.
3. Constructs and plots **Load Duration Curves (LDCs)** for each scenario, sorted from highest to lowest hourly load.
4. Overlays an example **available capacity line** to show how each scenario approaches system limits.

---

## Scenarios Modeled

| Scenario | Description |
|----------|-------------|
| **Original Load** | Baseline synthetic hourly demand |
| **+6 GW Data Centers** | Uniformly adds inflexible 6 GW across all hours |
| **+6 GW VPPs** | Shifts 6 GW from top 15% peak hours to bottom 15% valley hours |
| **+6 GW Data Centers + 6 GW VPPs** | Combined case with added inflexible load and active VPP shifting |

---

## Key Assumptions

- **Baseline Load**: Normally distributed with mean = 75 GW and standard deviation = 10 GW, clipped at a minimum of 40 GW.
- **Data Center Load**: Treated as constant (not responsive to price or load conditions).
- **VPP Behavior**: Peak shaving (subtracting load at highest 15% of hours) and valley filling (adding load at lowest 15% of hours).
- **Available Capacity**: Fixed at 120 GW to illustrate headroom constraints.

---

## 🛠 Dependencies

An environment file `env.txt` is included in the repo. The script uses very basic libraries:

- `numpy`
- `matplotlib`