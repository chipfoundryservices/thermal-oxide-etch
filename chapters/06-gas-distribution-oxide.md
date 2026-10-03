# Chapter 6: Gas Distribution Systems for Uniform Etch

## Introduction: Gas Delivery is the Etch Rate Bottleneck

Chapter 3 established that **F-atom supply is the rate-limiting factor** in oxide etch. Chapter 5 addressed **thermal transport** to maintain temperature. This chapter focuses on **gas distribution**—ensuring F-atoms reach every point on the wafer uniformly.

The fundamental challenge: **deliver fluorine species uniformly across 300mm diameter while maintaining process window**.

Unlike prior etch processes:
- **Silicon etch (Books 11-15):** Ion-limited regime; gas distribution less critical (excess radicals)
- **Metal etch (Book 16):** Moderate uniformity challenge; can tolerate 5-10% variation
- **Oxide etch:** **Radical-limited regime**; even 5% gas flow variation creates 15-20% etch rate variation (due to 8-10%/°C coefficient combined with local heating effects)

This chapter details how equipment engineers achieve the uniformity required.

## Section 6.1: Fundamental Gas Flow Principles

### 6.1.1 Knudsen Number and Flow Regimes

The **Knudsen number (Kn)** determines which flow physics applies:

```
Kn = λ / L

Where:
- λ = mean free path (distance between collisions)
- L = characteristic chamber dimension (e.g., showerhead hole diameter)
```

#### **Flow Regime Classification:**

| Regime | Kn Range | Pressure | Physics | Oxide Etch? |
|--------|----------|----------|---------|------------|
| Continuum | <0.01 | High (atm) | Fluid dynamics, Navier-Stokes | No |
| Transition | 0.01-10 | 0.1-100 Torr | Mixed molecular/continuum | **YES (typical)** |
| Molecular | >10 | Ultra-high vacuum | Individual molecule trajectories | No |
| Free Molecular | >>10 | UHV | Individual collisions only | No |

**For oxide etch at 100 mTorr in a chamber with 20cm dimensions:**
```
Mean free path: λ ≈ kT / (√2 π d² P) ≈ 1-10 μm
Showerhead hole diameter: L ≈ 0.5-2 mm
Kn ≈ (5 μm) / (1 mm) ≈ 0.005 (borderline continuum!)
```

**Implication:** Oxide etch operates at the **boundary between continuum and molecular flow**, creating complex nonlinear behavior in gas distribution.

### 6.1.2 Residence Time and Radical Transport

Once CF₄/CHF₃ is injected, how long do gas molecules spend in the chamber before exiting?

```
Residence Time Calculation:

τ = V / (Pumping Rate)

Where:
- V = chamber volume (~100 L typical for oxide etch)
- Pumping rate = (Pressure × Pump speed) / (at STP)

Example:
At 100 mTorr, pump speed = 500 L/s (typical diffusion pump):
Pumping rate = (100/760 atm) × 500 L/s ≈ 66 L/s

Residence time: τ = 100 L / 66 L/s ≈ 1.5 seconds
```

**Critical Insight:** Radical residence time (1-2 seconds) is SHORT, meaning:
1. Gas molecules must dissociate QUICKLY to produce F-atoms
2. F-atoms must reach the wafer DURING their residence time
3. Late-arriving F-atoms get pumped away unutilized

### 6.1.3 Distribution Uniformity Metric

How do engineers quantify gas distribution uniformity?

```
Standard Metric: Relative Standard Deviation (RSD)

RSD = (σ / mean) × 100%

Where:
- σ = standard deviation of local etch rates
- mean = average etch rate

Interpretation:
- RSD < 3%: Excellent (target for advanced nodes)
- RSD 3-5%: Good (acceptable for 7nm and above)
- RSD 5-10%: Fair (not recommended for <7nm)
- RSD > 10%: Poor (process not viable)

Example from real fab data:
9 sites measured across 300mm wafer:
Etch rates: 580, 600, 620, 610, 630, 615, 590, 625, 605 Å/min
Mean: 609 Å/min
σ: 17 Å/min
RSD = 17/609 × 100% = 2.8% ✓ (excellent)
```

## Section 6.2: Showerhead Design

### 6.2.1 Showerhead Geometry and Hole Pattern

The showerhead is the critical gas distribution component. It must:
1. Mix gases uniformly
2. Distribute flow evenly across wafer area
3. Minimize polymer deposition on showerhead
4. Withstand F-atom erosion and corrosion

#### **Typical Showerhead Design:**

```
Side View:
┌─────────────────────────────┐
│  Gas Inlet Manifold         │
│  (CF₄, CHF₃, Ar mixing)     │
└────────┬────────────────────┘
         │ (Pressure drop)
    ┌────▼─────────────────┐
    │  Showerhead Plate    │
    │  (Stainless Steel)   │ ~20mm thick
    │  1000-2000 holes     │
    │  (0.5-2mm diameter)  │
    └────┬─────────────────┘
         │ (Gas spray)
    ┌────▼──────────────────┐
    │  Wafer Surface        │
    │  (receiving gas)      │
    └──────────────────────┘
```

#### **Hole Pattern Optimization:**

Gas must be distributed radially, not just perpendicularly:

```
Poor Distribution (Uniform Radial):
o o o o o o o o
o o o o o o o o
o o o [W] o o o    — Wafer (W) in center
o o o o o o o o    — Gets excess gas

Better Distribution (Radial Compensation):
o   o   o   o      — Fewer holes at center
  o   o   o   o
o   o   o [W] o o  — More holes at edge
  o   o   o   o

Result: Gas density becomes uniform across surface
```

#### **Hole Size and Pressure Drop:**

```
Pressure Drop Through Showerhead:
ΔP = (128 × μ × L × Q) / (π × d⁴ × N)

Where:
- μ = gas viscosity
- L = hole length (showerhead thickness)
- Q = volume flow rate
- d = hole diameter
- N = number of holes

Trade-off:
- Larger holes (d ↑): Lower ΔP, but less mixing
- Smaller holes (d ↓): Higher ΔP, better uniformity, but flow resistance

Typical design: d ≈ 1mm, ΔP ≈ 10-50 mbar (small, to minimize power loss)
```

### 6.2.2 Pre-Mixing Chamber Design

Gas mixing must occur BEFORE reaching showerhead:

```
Gas Inlet Architecture:

CF₄ inlet ─┐
CHF₃ inlet ─┼─→ [Premix Chamber] ─→ [Showerhead] ─→ [Wafer]
Ar inlet  ─┘

Premix Chamber Function:
1. Turbulent mixing (ensures homogeneous composition)
2. Pressure equalization (all species at same pressure before showerhead)
3. Temperature stabilization (gas heats to chamber temperature)
4. Particle filtering (remove dust that could contaminate wafer)

Chamber Volume Target: 1-2 L (large enough for good mixing, small enough to minimize holdup)

Residence Time in Premix: ~0.1-0.2 seconds (long enough for diffusional mixing)
```

## Section 6.3: Flow Rate Optimization

### 6.3.1 Mass Flow Controller (MFC) Principles

Modern oxide etch chambers use MFCs to precisely control gas flow:

```
MFC Principle:

Gas Inlet
    ↓
Laminar Flow Element (restriction)
    ↓
    ├─→ Pressure Drop Sensor (ΔP)
    │
    └─→ Temperature Sensor (T)
        ↓
    Flow = f(ΔP, T, Gas Properties)
        ↓
Bypass Valve (adjusts to maintain setpoint)
    ↓
Gas Outlet

Control Loop:
Setpoint (SCCM) → Error Signal → Valve Position → Actual Flow → Feedback
```

#### **Accuracy Specification:**

```
Typical MFC Performance:
- Accuracy: ±2% of setpoint (good)
- Repeatability: ±0.5% (excellent)
- Response time: <500 milliseconds (adequate)
- Turndown ratio: 100:1 (can set 1-100 SCCM with same MFC)

Example: 50 SCCM setpoint
Actual flow varies: 49-51 SCCM (±2% of 50)
This translates to: ±2% etch rate variation
With 8-10%/°C sensitivity: Equivalent to ±0.2-0.25°C (within control window!)
```

### 6.3.2 Gas Flow Rate Selection for Oxide Etch

**Typical Gas Flows at 100 mTorr:**

```
Gas Species | Flow Rate (SCCM) | Reason for Selection
─────────────────────────────────────────────────────
CF₄         | 10-20           | Primary F-atom source
CHF₃        | 15-30           | Secondary F-source + selectivity
Ar          | 10-30           | Ion generation, sputtering assist
─────────────────────────────────────────────────────
TOTAL       | 35-80           | Typical recipe: 50-60 SCCM

Residence time at 50 SCCM total flow:
V = 100 L, Flow = 50 SCCM = 0.833 L/s
τ = 100 L / 0.833 L/s ≈ 120 seconds (much longer than 1.5 sec calculated earlier!)

Reconciliation: Pumping rate dominates residence time (residence = V/pump rate, not V/inlet rate)
```

### 6.3.3 Flow Rate Effects on Etch Rate and Selectivity

**Etch Rate Dependence on Gas Flow:**

```
Etch Rate vs. Total Gas Flow

Etch Rate (Å/min)
        900 │       ╱──────── Saturation
            │      ╱          (F-atom supply excess)
        700 │     ╱
            │    ╱
        500 │   ╱  Linear region
            │  ╱   (radical-limited)
        300 │ ╱
            │╱
        100 └──────────────────
            0  20  40  60  80  100
            Total Gas Flow (SCCM)

Interpretation:
- Low flow (<30 SCCM): Linear increase (radical-limited, F-atom supply limiting)
- Medium flow (30-60 SCCM): Mostly linear with slight saturation
- High flow (>60 SCCM): Saturation regime (F-atom flux is no longer limiting)

Process Window: Typically operated at 40-60 SCCM (linear regime, predictable)
```

**Selectivity Dependence on Gas Mixture:**

```
Oxide-to-Metal Selectivity vs. CHF₃ Fraction

Selectivity (to Al)
        200 │
            │       CHF₃-rich (better selectivity)
        150 │    ╱──╲
            │   ╱    ╲
        100 │  ╱      ╲
            │ ╱        ╲  CF₄-rich (faster, worse selectivity)
         50 │╱
            │
          0 └──────────────────
            0%  25% 50% 75% 100%
            CHF₃ Fraction in CF₄/CHF₃ Mix

Typical Operating Point: 40-60% CHF₃ (balance of rate and selectivity)
```

## Section 6.4: Pressure Uniformity Challenges

### 6.4.1 Radial Pressure Gradient Effects

In oxide etch chambers, pressure is not uniform radially:

```
Pressure Profile During Etch:

Typical 300mm chamber:
─ Center of showerhead: 105 mbar (slightly higher)
─ Near wafer center: 100 mbar (target setpoint)
─ Edge regions: 95-98 mbar (lower)
─ Exhaust port: 80-90 mbar (vacuum pump reduces pressure)

ΔP_radial ≈ 5-10 mbar (5-10% variation)

Effect on F-atom Production:
From Chapter 3: F-atom density is pressure-dependent
[F] ∝ P (in linear regime)

If pressure varies ±10%:
[F] varies ±10% → etch rate varies ±10% (potentially!)

BUT: Temperature coefficient is 8-10%/°C
10% etch rate variation ≈ 1-1.25°C equivalent
Unacceptable for ±2°C process window!
```

### 6.4.2 Pressure Control Strategies

**Strategy 1: Exhaust Port Geometry**

```
Pump inlet location affects pressure distribution

Poor Design (Single port at edge):
┌─────────────────┐
│     Chamber     │
│ [W = wafer]     │  Pump
│                 ├──→ ↓
└─────────────────┘      Fast exhaust at edge
                         Pressure high at center

Better Design (Central exhaust):
┌─────────────────┐
│     Chamber     │
│   [W]     ↓     │  Pump
│        Pump     │ ↓
└─────────────────┘ More uniform

Best Design (Multiple exhaust ports):
┌─────────────────┐
│ [W]     ↓    ↓  │  Pump
│   ↓        ↓    │ ↓↓↓ (multiple ports)
└─────────────────┘ Excellent uniformity
```

**Strategy 2: Pressure Regulation**

```
Pressure setpoint maintained via throttle valve:

Throttle Valve → controls pumping conductance
Spring-loaded valve maintains constant pressure upstream

Accuracy: ±0.5% (one of the best controls in system)

Example: 100 mbar setpoint
±0.5% accuracy = ±0.5 mbar (excellent!)
```

## Section 6.5: Gas Composition Effects

### 6.5.1 CF₄ vs. CHF₃ Distribution

Different gases have different molecular weights and thermal properties:

```
Gas Properties:
                CF₄         CHF₃        Ar
Molecular Wt    88 g/mol    86 g/mol    40 g/mol
Thermal Cond    15 mW/m·K   20 mW/m·K   22 mW/m·K
Viscosity       20 μPa·s    18 μPa·s    21 μPa·s

Effect: Slight differences in diffusion and flow behavior
        CF₄ and CHF₃ mix well (similar properties)
        Ar mixes readily due to higher thermal conductivity

Result: Gas composition uniformity is generally not a major issue
        (pressure uniformity matters more than composition uniformity)
```

### 6.5.2 Mixing Dynamics in Premix Chamber

```
Mixing Time Scale:

Diffusional mixing time: τ_mix = L² / D
Where D ≈ diffusivity ≈ 0.01 cm²/s for gas mixtures at 100 mTorr

For L ≈ 10 cm (premix chamber dimension):
τ_mix ≈ (10 cm)² / (0.01 cm²/s) ≈ 10,000 seconds (TOO SLOW!)

Turbulent mixing is required instead:
Turbulence develops when Reynolds number Re > 2300

Re = ρ × v × D / μ

At typical inlet velocities (v ≈ 1-10 m/s):
Re ≈ 5000-50,000 (turbulent! Good mixing)

Turbulent mixing time: τ_turb ≈ 0.1-0.3 seconds (much faster!)
```

## Section 6.6: Polymer Deposition on Showerhead

### 6.6.1 Fluorocarbon Accumulation Pattern

Fluorocarbon polymer deposits preferentially on cool surfaces (opposite to wafer which is hot):

```
Temperature Profile in Chamber:

Wafer:              60°C (hot, inhibits polymer deposition)
Electrode:          60°C (coupled to wafer)
Chamber wall:       30-40°C (cooler)
Showerhead (inlet): 25°C (coldest! POLYMER DEPOSITS HERE)

Deposition Rate:
On showerhead:     5-10 nm/minute (fast)
On wafer:          0-1 nm/minute (minimal due to high temperature)
On chamber wall:   2-5 nm/minute (moderate)

Result: Showerhead accumulates thick polymer layer quickly!
```

### 6.6.2 Showerhead Conditioning and Cleaning

```
Polymer Buildup Effect:

Time (wafers)    Polymer Thickness    Hole Diameter Change
0                0 nm                 1.000 mm (nominal)
100              100 nm               0.998 mm (-0.2%)
500              500 nm               0.990 mm (-1%)
1000             1000 nm              0.980 mm (-2%)

Effect on Gas Distribution:
As holes get smaller:
- Flow resistance increases
- Pressure drop increases
- Radial flow distribution changes
- Gas uniformity DEGRADES

Result: Etch rate uniformity drifts over 500-1000 wafers
```

### 6.6.3 NF₃ Cleaning Protocol

```
Standard NF₃ Cleaning Cycle:

Every 100 wafers (or weekly):

1. Cool chamber to room temperature (30 min)
2. Pump out process gas
3. Introduce NF₃ at 100 SCCM
4. Apply 100W RF power (lower than process power)
5. Duration: 10-15 minutes
6. Polymer reaction: C-F polymers + NF₃ → products + CO₂, etc.
7. Products pump away

Polymer Removal Efficiency:
First clean: 80-90% removal
Repeat clean: 60-70% removal

Practical result: After 10-15 cleans, must replace showerhead

Maintenance Cycle:
- Weekly NF₃ clean during production
- Quarterly deep clean (8 hours)
- Every 12-18 months: Replace showerhead and upstream components
```

## Section 6.7: Advanced Gas Distribution Concepts

### 6.7.1 Adaptive Gas Flow Control

Emerging concept: Adjust gas flow in real-time based on etch rate feedback:

```
Closed-Loop Gas Flow Control:

Measure: Etch rate via OES (Optical Emission Spectroscopy)
Feedback: If etch rate dropping due to polymer, increase flow
Adjustment: MFC setpoint increases 5-10%

Example:
Nominal setpoint: 50 SCCM
OES signal drops 10%: etch rate drifting down
System increases flow to 52-55 SCCM
OES signal recovers to nominal
Result: Constant etch rate despite polymer buildup!

Trade-off:
- Benefit: Extends cleaning cycles (more production time)
- Cost: Complex feedback algorithm, risk of overcorrection
```

### 6.7.2 Azimuthal Gas Modulation

Emerging technique: Use multiple gas inlets at different azimuthal positions:

```
Multi-Inlet Showerhead:

Traditional single inlet:
CF₄ inlet → [Premix] → [Showerhead] → Uniform distribution (theoretically)

Multi-inlet design:
CF₄ inlet at 0° ─┐
CHF₃ inlet at 90° ├─→ [Azimuthal Distribution]
Ar inlet at 180° │   Better control of radial composition
At 270° ────────┘

Benefit: Can tune composition at different radii
Example: More CHF₃ at edge (needs better selectivity), more CF₄ at center

Current status: Being studied for advanced node implementation
```

## Section 6.8: Summary and Connection Forward

### Key Takeaways:

1. **Gas distribution is critical bottleneck** in radical-limited oxide etch
2. **Showerhead design dominates uniformity** — hole pattern, size, spacing are optimization variables
3. **Residence time is very short** (1-2 seconds) — must design accordingly
4. **Pressure uniformity is essential** — 5-10% pressure variation creates unacceptable etch rate drift
5. **Polymer accumulation degrades distribution** over hundreds of wafers
6. **NF₃ cleaning must be frequent** (every 100 wafers typical)
7. **Gas flow rate operates in radical-limited regime** — straightforward proportionality to etch rate
8. **Temperature of showerhead dominates polymer deposition** — coolest surfaces accumulate fastest

### Forward References:

- **Chapter 7 (Pressure-Temperature-Power Phase Space):** Pressure uniformity limits achievable process windows
- **Chapter 13 (Polymerization & Fluorocarbon):** Polymer buildup dynamics affect gas distribution over time
- **Chapter 15 (Cluster Integration):** Gas distribution in cluster tools adds complexity (shared exhaust, cross-chamber effects)

---

**Next Chapter:** Chapter 7 maps the pressure-temperature-power phase space, defining the actual achievable process windows given the constraints from thermal (Ch 5) and gas distribution (Ch 6) systems.
