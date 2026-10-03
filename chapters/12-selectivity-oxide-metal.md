# Chapter 12: Selectivity Engineering — Oxide-to-Metal Ratios

## Introduction: The Most Critical Margin in Oxide Etch

**Selectivity** is the fundamental constraint that makes oxide etch *viable* as a production process. Without selectivity, oxide etch would destroy aluminum metal layers, ruining circuits.

Definition:
```
Selectivity (S) = Etch Rate of SiO₂ / Etch Rate of Al (or Al₂O₃)

Example:
SiO₂ etch rate: 200 nm/min
Al etch rate: 6.7 nm/min
Selectivity = 200 / 6.7 = 30:1

Interpretation: For every 1 nm of Al eroded, 30 nm of SiO₂ is etched
This 30:1 selectivity is the ONLY reason oxide etch can stop at metal layer!
```

**Why Chapter 12 is Critical:**

From earlier chapters:
- Chapter 10: Inverse ARDE requires compensation (pulsing, higher temp, lower power)
- Chapter 11: Higher temperature improves ARDE uniformity
- Contradiction: Higher temperature typically REDUCES selectivity!

**Central Challenge:** Optimize for both ARDE and selectivity simultaneously. Both are non-negotiable for yield.

---

## Section 12.1: The Selectivity Paradox Resolved

### 12.1.1 Why Does Oxide Etch Faster Than Metal?

From Chapter 4, we learned the answer: **Native Al₂O₃ Layer**

```
Aluminum Surface Layer Structure:

Air ↓
↓ Oxygen exposure (hours, factory environment)
↓
─────────────────────────────  ← Al₂O₃ native oxide layer
                               ← Thickness: 20-50 nm (amorphous)
                               ← Extremely stable, hard to etch
─────────────────────────────
║
║ Pure Aluminum (bulk metal)
║
─────────────────────────────

The native oxide is THICKER and HARDER than SiO₂!
But it's also THINNER (20-50 nm vs. 200-500 nm device SiO₂)

Etch Rates:

At 60°C, 100 mTorr, 300W:
- SiO₂ (device layer): 200 nm/min
- Al₂O₃ (native oxide on aluminum): 7 nm/min ← Much slower!
- Al (pure metal, if oxide removed): 1000 nm/min ← Very fast!

So selectivity comes from native oxide acting as barrier!

Key Question: Why is Al₂O₃ so much slower than SiO₂?
(Both are oxides, both contain aluminum!)
```

### 12.1.2 Al₂O₃ vs. SiO₂ Etch Rate Difference

**Root Cause: Crystal Structure and Bonding**

```
SiO₂ Structure (Amorphous):
- Si-O bonds: Si⁴⁺ — O²⁻ (relatively weak)
- Structure: Random, defect-rich
- Open framework: F-atoms can penetrate easily
- Etch mechanism: F-atoms form SiF₄ (volatile)

Al₂O₃ Structure (Amorphous, native oxide):
- Al-O bonds: Al³⁺ — O²⁻ (stronger than Si-O!)
- Structure: More compact, denser packing
- Closed framework: F-atoms penetrate slowly
- Etch mechanism: F-atoms form AlF₃ (less volatile than SiF₄)

Etch Rates (Per Surface F-atom):

At a given F-atom density n_F:

r_SiO₂ ∝ n_F × k_SiO₂
r_Al₂O₃ ∝ n_F × k_Al₂O₃

Where k is reaction rate constant for each oxide:

k_SiO₂ ≈ 200 (high reactivity with F-atoms)
k_Al₂O₃ ≈ 7 (low reactivity with F-atoms)

Ratio: k_SiO₂ / k_Al₂O₃ ≈ 200 / 7 ≈ 28:1

This explains the ~30:1 selectivity!
```

**Why Is Al₂O₃ Less Reactive?**

```
Three contributing factors:

Factor 1: Bond Strength
- Al-O bond energy: ~117 kcal/mol (stronger!)
- Si-O bond energy: ~109 kcal/mol
- Stronger bonds resist F-atom attack

Factor 2: Crystal Density
- Al₂O₃ density: 3.97 g/cm³ (compact)
- SiO₂ density: 2.2-2.6 g/cm³ (more porous)
- Compact structure blocks F-atom penetration

Factor 3: Hydration and Defects
- SiO₂ native oxide: Absorbs water (hygroscopic)
  → Creates defects and weak points
  → Water assists F-atom penetration
- Al₂O₃ native oxide: Hydrophobic (resists water)
  → Fewer defects
  → Slower F-atom penetration
```

### 12.1.3 Selectivity Measurement

**Standard Test:**

```
Wafer with SiO₂ layer on Al metal:

Before etch:
SiO₂ thickness: 200 nm (measure with ellipsometry)
Al thickness: 500 nm (known from deposition)

Process:
Etch at standard conditions (60°C, 100 mTorr, 300W) for fixed time T=60 sec

After etch:
SiO₂ remaining: ~80 nm (eroded 120 nm)
Al remaining: ~498 nm (eroded 2 nm)

Calculations:
r_SiO₂ = 120 nm / 60 s = 2.0 nm/s = 120 nm/min
r_Al = 2 nm / 60 s = 0.033 nm/s = 2 nm/min (measured from cross-section SEM)

Wait! This doesn't match earlier statement of 200 nm/min and 6.7 nm/min!

Explanation: Those were rates in *pure* etch, all plasma dedicated to one material
Real process: Plasma etches both SiO₂ and Al simultaneously
→ Competition for F-atoms reduces both rates from theoretical max
→ But SiO₂ preferentially wins competition
→ Result: Actual selectivity measured in production is ~30-40:1
```

---

## Section 12.2: Process Conditions Affecting Selectivity

### 12.2.1 Temperature Effect (CRITICAL TRADEOFF)

**Higher Temperature → WORSE Selectivity**

```
Why? The activation energy for Al₂O₃ etch is HIGHER than SiO₂!

Temperature Coefficient of Etch Rate:

From Arrhenius: r = r₀ × exp(-E_a / kT)

For SiO₂:
E_a,SiO₂ ≈ 25 kcal/mol (moderate activation energy)
Temp coefficient: ~5-7 %/°C increase

For Al₂O₃:
E_a,Al₂O₃ ≈ 40 kcal/mol (HIGHER activation energy!)
Temp coefficient: ~10-12 %/°C increase

Example at baseline (T₀ = 60°C):
r_SiO₂(60°C) = 200 nm/min
r_Al₂O₃(60°C) = 6.7 nm/min
S(60°C) = 200 / 6.7 = 30:1

At elevated temperature (T₁ = 80°C, ΔT = 20°C):
r_SiO₂(80°C) = 200 × (1.06)^20 = 200 × 3.2 = 640 nm/min
              (assuming 6%/°C, simplified)
r_Al₂O₃(80°C) = 6.7 × (1.11)^20 = 6.7 × 7.4 = 50 nm/min
              (assuming 11%/°C, simplified)
S(80°C) = 640 / 50 = 12.8:1

Selectivity DROPPED from 30:1 to 13:1! (57% loss!)
```

**Practical Impact:**

```
Temperature vs. Selectivity Trade-off:

Selectivity (S, ratio)
     35 │  ╲
        │   ╲ Selectivity decreases with T
     30 │    ╲
        │     ╲___
     25 │        ╲___
        │            ╲
     20 │             ╲___
        │                 ╲
     15 └────────────────────
           40   60   80  100 °C
           
Inverse ARDE vs. Selectivity:

ARDE Effect:  ↑ (gets worse with lower T)
              ↓ (improves at higher T)
Selectivity:  ↑ (better at lower T)
              ↓ (worse at higher T)

THE FUNDAMENTAL CONFLICT:
To fix ARDE uniformity, raise temperature
But raising temperature destroys selectivity!

Process Window Squeeze:
Without ARDE constraint: 40-100°C acceptable
With ARDE constraint: 60-75°C is the narrow sweet spot
With selectivity constraint: 55-70°C for adequate margin
Intersection: 60-70°C (very narrow!)
```

### 12.2.2 Pressure Effect

**Higher Pressure → Slightly Reduces Selectivity**

```
Pressure affects selectivity less dramatically than temperature:

At 50 mTorr:   S ≈ 33:1
At 100 mTorr:  S ≈ 30:1
At 200 mTorr:  S ≈ 26:1

Why the small effect?

Mechanism 1: F-atom Flux
Higher pressure → More collisions → Lower F-atom mean free path
→ F-atoms diffuse more (less directional)
→ Slightly higher flux to oxide surfaces

Mechanism 2: Plasma Sheath
Higher pressure → Weaker plasma sheath
→ Lower ion energy
→ Ions less effective at removing oxide
→ But ions equally less effective at metal removal
→ Net: Modest selectivity change

Mechanism 3: Gas-Phase Reactions
Higher pressure → More CF₄ fragmentation
→ Different F-species distribution
→ Slight shift in relative reactivities

Result: Pressure effect is ~0.5% per 10 mTorr
(Much smaller than ~6% per °C for temperature)

Implication: Pressure is "tunable" without major selectivity impact
Temperature requires careful balance
```

### 12.2.3 Power Effect

**Higher Power → Complex Effect**

```
Direct Effect: Higher power → More ions → Better ion-assisted etch
But: Ion assistance helps both SiO₂ and Al₂O₃

At low power (150W):
- Ion energy modest
- Ion bombardment helps SiO₂ etch more than Al₂O₃
- S ≈ 35:1

At medium power (300W, baseline):
- Ion energy sufficient for both
- Balanced ion assistance
- S ≈ 30:1

At high power (450W):
- Ion energy very high
- Ion bombardment now helps Al₂O₃ significantly
- S ≈ 22:1

Why higher power helps Al₂O₃ more:
Al₂O₃ is harder → benefits more from sputtering assistance
SiO₂ is softer → already well-etched by F-atoms, ions add little

Result: Selectivity DECREASES with power
(Range: 35:1 at 150W → 22:1 at 450W)

This creates another Process Window Squeeze!
Higher power → Better etch rate but worse selectivity
Lower power → Slower etch but better selectivity
```

---

## Section 12.3: Gas Chemistry and Selectivity

### 12.3.1 CF₄ vs. CHF₃ Selectivity

**Different Gases → Different Selectivity**

```
Pure CF₄ Processing:
- Generates F-atoms efficiently
- F-atoms attack both oxides
- Selectivity: S ≈ 30:1

Pure CHF₃ Processing:
- Generates F-atoms + H-radicals
- H-radicals have different reactivity profile
- H-atoms favor SiO₂ over Al₂O₃ (selectively passivate Al₂O₃)
- Selectivity: S ≈ 45:1 (much better!)

But why use CF₄?
- CHF₃ alone: Slower etch rate (~60% of CF₄)
- Cost: CHF₃ more expensive
- Product: SiF₄ + HF + SiF₃OH species (different product mix)

Gas Mixture Trade-off:
80% CF₄ + 20% CHF₃: S ≈ 32:1 (slight selectivity boost)
60% CF₄ + 40% CHF₃: S ≈ 35:1 (much better selectivity!)
40% CF₄ + 60% CHF₃: S ≈ 40:1 (excellent selectivity)
Pure CHF₃: S ≈ 45:1, but rate drops to 120 nm/min

Choice:
Production use: Typically 70:30 or 80:20 CF₄:CHF₃
- Balances speed (etch rate ~180-190 nm/min)
- With selectivity (S ~32-35:1)
- With cost and product stability
```

### 12.3.2 Adding Modifiers (NF₃, O₂, Ar)

**Advanced Gas Chemistry:**

```
Additive: NF₃ (Nitrogen Trifluoride)
- Already used for chamber cleaning (Chapter 8)
- Can be added to etch gas mixture in small amounts (~5-10%)
- Generates extra F-atoms (3 F per molecule)
- Effect on selectivity: Minimal (S unchanged ~30:1)
- Benefit: Increases F-atom supply → Better etch uniformity

Additive: O₂ (Oxygen)
- Small amounts (~1-2%) passivate damage
- O-atoms react with Al₂O₃ to form stable Al₂O₃•O₂ (very stable)
- But also passivate SiO₂ (less desirable)
- Effect: S ≈ 25:1 (selectivity decreases slightly)
- Use case: Only on certain layers where minimal Al damage acceptable

Additive: Ar (Argon)
- Inert gas, increases momentum transfer
- Enhances ion sputtering component
- Helps deep trench etching
- Effect: S ≈ 28:1 (small degradation)
- Used on advanced nodes for high-AR features

Current State: Most production uses pure CF₄/CHF₃ mixtures
Advanced nodes: Adding NF₃ or Ar becoming more common
Selectivity is maintained, other metrics (uniformity) improved
```

---

## Section 12.4: Selectivity Margin Analysis

### 12.4.1 Process Window Definition

**What Is Process Margin?**

```
Selectivity Margin = Actual Selectivity - Minimum Acceptable Selectivity

Example:

Aluminum Metal Thickness: 100 nm
Maximum Acceptable Al Etch Loss: 5 nm (5% max erosion, device specs)

Over-etch requirement (from process):
SiO₂ etch depth needed: 200 nm
Over-etch time: 20% extra (to guarantee SiO₂ fully etched)
Extra SiO₂ etched: 40 nm (safety factor)
Total etch time: Equivalent to 240 nm of SiO₂

During this time, Al etch:
Time for 240 nm SiO₂ = 240 nm / (etch rate) = 2.4 minutes at 100 nm/min

If S = 30:1:
Al eroded = 240 nm / 30 = 8 nm (EXCEEDS 5nm spec by 60%! FAIL!)

If S = 50:1:
Al eroded = 240 nm / 50 = 4.8 nm (Within 5 nm spec! OK!)

Minimum Selectivity Required: S_min = 240 nm / 5 nm = 48:1

But actual selectivity: S_actual ≈ 30:1

PROBLEM: Actual selectivity (30:1) < Required selectivity (48:1)!
Margin = 30:1 - 48:1 = -18:1 (NEGATIVE margin = FAILURE!)

Solution: Reduce over-etch from 20% to 10%
Total etch depth: 220 nm → Al eroded: 220/30 = 7.3 nm (STILL FAILS!)

Solution 2: Use CHF₃-rich mixture to raise selectivity to 40:1
Al eroded = 240 nm / 40 = 6 nm (CLOSE to 5nm spec)
Margin = 40:1 - 48:1 = -8:1 (Still tight!)

Solution 3: Do ALL of above:
- CHF₃-rich mixture: S = 40:1
- Lower over-etch: 10%
- Total etch: 210 nm
- Al eroded: 210 / 40 = 5.25 nm (Still marginal!)

FUNDAMENTAL TENSION: Modern devices are SO THIN,
selectivity margins are continuously eroding!
```

### 12.4.2 Selectivity Margin vs. Advanced Nodes

**Node Scaling Crisis:**

```
Technology Node Progression:

2014 (28 nm node):
- Al thickness: 200 nm
- SiO₂ thickness: 300 nm
- Required over-etch: 15%
- Minimum S needed: 20:1
- Actual S available: 30:1
- Margin: +10:1 (comfortable)

2018 (14 nm node):
- Al thickness: 150 nm
- SiO₂ thickness: 250 nm
- Required over-etch: 20% (tighter control needed)
- Minimum S needed: 33:1
- Actual S available: 30:1 (with current recipe)
- Margin: -3:1 (NEGATIVE! Must improve S!)

2022 (5 nm node):
- Al thickness: 80 nm
- SiO₂ thickness: 150 nm
- Required over-etch: 25% (very tight)
- Minimum S needed: 47:1
- Actual S available: 30:1 (baseline) or 40:1 (with CHF₃ richness)
- Margin: -17:1 to -7:1 (SEVERE challenge!)

2025-2026 (3 nm node):
- Al thickness: 50 nm (thinner!)
- SiO₂ thickness: 100 nm
- Required over-etch: 30% (extremely tight)
- Minimum S needed: 60:1
- Actual S available: 40:1 (even with aggressive CHF₃)
- Margin: -20:1 (CANNOT ACHIEVE with conventional oxide etch!)

Current Status: 5 nm node is at absolute limit of oxide etch selectivity
Advanced alternative technologies emerging:
- Directional etch (IBE, ion beam etching)
- Plasma beam etching
- Selective wet etch processes
- Atomic layer etching (ALE)
```

---

## Section 12.5: Selectivity and Inverse ARDE Conflict

### 12.5.1 The Central Dilemma

**Revisiting Process Optimization Constraints:**

```
From earlier chapters:

To Fix Inverse ARDE:
✓ Raise temperature (from 60→80°C reduces ARDE Index from 35% → 20%)
✓ Use pulsed power
✓ Add CHF₃ to gas (increases F-atoms)
✓ Lower pressure

But Selectivity Consequences:

✓ Raise temperature → S drops 30:1 → 13:1 (60% loss!) ✗
✓ Use pulsed power → Minimal effect on S
✓ Add CHF₃ → S improves 30:1 → 35:1 (small gain) ✓
✓ Lower pressure → S improves 26:1 → 30:1 (small gain) ✓

The MOST effective ARDE fix (temperature) is the WORST for selectivity!

Practical Resolution:

Multi-Objective Optimization:

Baseline (60°C, 100 mTorr, CF₄/CHF₃ 80:20):
- ARDE Index: 35%
- Selectivity: 30:1
- Etch Rate: 180 nm/min
- All metrics: ACCEPTABLE

Advanced Recipe (65°C, 120 mTorr, CF₄/CHF₃ 60:40, pulsed):
- ARDE Index: 22% (improved by 37%)
- Selectivity: 33:1 (improved by 10%)
- Etch Rate: 170 nm/min (slightly reduced)
- Trade-off: Better ARDE uniformity, acceptable selectivity, small rate loss

Optimization achieved by combining multiple strategies:
- Temperature increase: 5°C (modest, not extreme)
- Pressure increase: 20 mTorr (provides selectivity boost)
- Gas mix: More CHF₃ (improves selectivity + provides extra F-atoms)
- Pulse modulation: Reduces polymer (helps both ARDE and selectivity)
- Over-etch reduction: 20% → 15% (from better uniformity)

Result: Balanced solution that manages both ARDE and selectivity
Without pushing either to extreme
```

### 12.5.2 Advanced Temperature Modulation Strategy

**Dynamic Temperature Control:**

```
From Chapter 14 (Temperature Control), advanced approach:

Phase 1 (0-20 sec): T = 60°C
- Objective: Fast etch rate, good selectivity
- ARDE Index: 35% (moderate)
- S: 30:1 (excellent)
- Etch rate: 200 nm/min (fast)

Phase 2 (20-40 sec): T = 70°C
- Objective: Improve deep trench uniformity
- ARDE Index: 25% (improving)
- S: 23:1 (degrading but acceptable)
- Etch rate: 210 nm/min (slightly faster)

Phase 3 (40-60 sec): T = 62°C
- Objective: Recovery to baseline selectivity
- ARDE Index: 34% (near baseline)
- S: 29:1 (recovered)
- Etch rate: 195 nm/min

Net Result:
- Deep features: Etched during phase 2 when T higher (caught up uniformity)
- Shallow features: Average rate similar to baseline
- Selectivity: Maintained at near-baseline average
- ARDE Index: Effectively reduced by ~15% through dynamic control

This is FUTURE DIRECTION for advanced nodes:
Temperature not constant, but programmed profile
Optimized for both uniformity AND selectivity
Requires sophisticated thermal control (Chapter 5 systems)
```

---

## Section 12.6: Selectivity in Device Layers

### 12.6.1 Inter-Layer Selectivity Challenges

**Multi-Layer Stacks:**

```
Real device structure (interconnect):

SiO₂ Dielectric
         ↓ etch
─────────────────  ← Stop on TiN barrier
TiN Barrier (10 nm)
         ↓ no etch desired!
─────────────────  ← Stop on Al
Al Metal
         ↓ no etch desired!

Selectivity Requirements:

SiO₂ / TiN Selectivity: ~100:1 or better
(TiN is refractory, much harder to etch than SiO₂)
Easy to achieve with CF₄/CHF₃

TiN / Al Selectivity: ~10:1
(Al much easier to etch than TiN)
Easy to achieve

SiO₂ / Al Selectivity: ~30:1
(From this chapter)
Just barely adequate

Key Issue: Process must maintain selectivity to Al
while fully removing SiO₂ to TiN

Strategy: Over-etch enough to reach TiN
but not so much as to erode Al excessively

Typical:
Target SiO₂ depth: 200 nm
Over-etch time: 20 sec (equivalent to 40 nm more SiO₂)
Total etch: 240 nm equivalent
Al erosion: 240 / 30 = 8 nm (must be within device specs!)
```

### 12.6.2 Barrier Layer Selectivity

**Advanced Node Challenge:**

```
For 5 nm node with 50 nm Al:

Process Step: Etch SiO₂, stop on Ta/TiN barrier

Initial TiN thickness: 5-10 nm
Acceptable TiN loss: 1-2 nm maximum

While etching 200 nm SiO₂ with 20% over-etch (240 nm equivalent):

If SiO₂ / TiN selectivity = 50:1 (excellent):
TiN erosion = 240 / 50 = 4.8 nm
FAILS (only 5-10 nm TiN available, losing 4.8 nm is SEVERE!)

If SiO₂ / TiN selectivity = 100:1 (extraordinary):
TiN erosion = 240 / 100 = 2.4 nm
OK but very tight margin

Solution: REDUCE SiO₂ etch depth requirement
by improving uniformity (Chapter 10 fix → Chapter 12 selectivity margin)
OR use pulsed oxide etch with endpoint detection (Chapter 16)
to eliminate over-etch

Current industry status:
Basic selectivity available: 30-40:1 to metal
Barrier selectivity: 50-100:1 to TiN
Advanced nodes: Hitting limits, driving new technologies
```

---

## Section 12.7: Selectivity Measurement and Control

### 12.7.1 Production Metrology

**How Selectivity Is Monitored:**

```
Test Vehicle on Production Wafer:

Pattern 1: SiO₂ / Al metal bilayer
Pattern 2: SiO₂ / TiN barrier bilayer
Pattern 3: Isolated SiO₂ features (reference)

After etch:
- Measure SiO₂ thickness remaining (ellipsometry)
- Cross-section al and Ti/TiN to measure erosion depth (SEM)
- Calculate actual selectivity ratios

Feedback:
IF Selectivity decreasing (trending toward limits):
  → Reduce etch time, improve uniformity
  → Adjust gas mix toward more CHF₃
  → Evaluate temperature adjustment
  → Consider recipe change for next wafer lot

IF Selectivity excellent (well above minimum):
  → Process is stable, continue as-is

Frequency: Every wafer lot (~25 wafers)
Cost: ~$100 per measurement (expensive! But critical)
Time: 2-4 hours (offline, not real-time)
```

### 12.7.2 In-Situ Selectivity Monitoring

**Emerging Technology:**

```
Goal: Real-time selectivity monitoring without breaking wafer

Approach: Emission Spectroscopy
- Monitor plasma light emissions
- Specific wavelengths indicate which reactions active
- Over time, trace changes in F-atom density and ion energy
- Correlate changes to selectivity shift

Challenges:
- Calibration requires offline validation measurements
- Optical window fogging from polymer deposition
- Interpretation requires complex plasma modeling

Current Status:
- Lab demonstrations show ±10% accuracy
- Limited production deployment
- Requires $50-100k investment in additional instrumentation

Future: 5 nm and below will likely mandate in-situ selectivity control
Justifies high cost through yield improvement
```

---

## Section 12.8: Advanced Selectivity Engineering

### 12.8.1 Plasma Composition Control

**Future Direction: Active Selectivity Tuning**

```
Emerging Concept: Electronically controlled gas chemistry

System:
- Multiple gas feed lines (CF₄, CHF₃, NF₃, Ar, O₂)
- Mass flow controllers with millisecond response time
- Real-time plasma diagnostics (optical emission spec)
- Feedback algorithm adjusting gas mixture every pulse cycle

Implementation:
- Pulse 1 (ON): High F-atom generation (CF₄ rich)
- Pulse 2 (OFF): Plasma quenches, polymer decomposes
- Pulse 3 (ON): Different gas mix for selectivity control

Result: Can adjust selectivity in real-time
without changing chamber temperature (which is slow)

Example Selectivity Control:
Over-etch phase 1: CF₄ dominant (fast etch, S = 25:1)
Fine etch phase 2: CHF₃ dominant (slow etch, S = 40:1)
Recovery phase 3: Ar additive to enhance selectivity to TiN

Advantage: Decouples uniformity (ARDE), rate, and selectivity control
Each optimized independently
Achieves better overall performance

Current Status: Lab demonstrations only
Timeline: Likely production implementation 3-5 nm node era
```

### 12.8.2 Atomic Layer Etching (ALE) Approach

**Beyond Continuous Plasma Etch:**

```
Fundamental Limitation of Continuous Etch:
Cannot independently control:
- Adsorption (F-atoms arrive at surface)
- Reaction (F-atoms break bonds)
- Desorption (products leave surface)

All three happen simultaneously → Limited selectivity control

ALE (Atomic Layer Etching) Concept:

Step 1: ADSORPTION
- Stop etch plasma
- Fluorine layer adsorbs on both SiO₂ and Al₂O₃
- Exposure: ~1 second (monolayer coverage)

Step 2: PULSE DESORPTION
- Turn on inert ion beam (Ar⁺, low energy)
- Ions preferentially sputter weakly-bonded adsorbed F on metal
- F on oxide (more strongly bonded) remains
- Remove ~0.1 nm of oxide + preferential metal F-removal

Step 3: REPEAT
- Cycle steps 1-2 many times
- Each cycle removes 0.1-0.3 nm of oxide
- Selectivity becomes ATOMIC (not just 30:1, but ~infinite!)

Process Time Trade-off:
- Continuous oxide etch: 200 nm in 2 minutes
- ALE approach: 200 nm in 20 minutes (10× slower)
  But selectivity is perfect!

Current Status: Research phase
- University labs: Demonstrated on small areas
- Challenges: Wafer-scale uniformity, throughput, cost
- Timeline: Production viability uncertain, likely 5+ years away
- Justification: For 3 nm and below, normal selectivity not adequate
```

---

## Section 12.9: Summary and Connection Forward

**Key Takeaways:**

1. **Selectivity ~30:1 comes from Al₂O₃ native oxide** acting as barrier, not from SiO₂ thermodynamic advantage
2. **Temperature is critical double-edged sword** — fixes ARDE but destroys selectivity
3. **Higher temperature increases Al₂O₃ etch rate 2× faster than SiO₂** due to higher activation energy
4. **Gas chemistry (CHF₃ addition) improves selectivity** by ~15-30% with modest etch rate cost
5. **Process margin is eroding with technology scaling** — 5nm node close to selectivity limit
6. **Multi-parameter optimization required** — temperature, pressure, gas mix, pulsing all matter
7. **Dynamic temperature profiling emerging** as solution to balance ARDE and selectivity
8. **Advanced nodes may require ALE or new technologies** because conventional selectivity insufficient

**The Selectivity-ARDE Trade-off Summary:**

```
Process Optimization Space:

                  Selectivity ↑
                      │
                      │ GOOD (S > 35:1)
       High Temp ──→  │ ╱ (Low ARDE, Poor S)
                      │╱
       ────────────────┼──────── Temperature
                      │╲
       Low Temp ──→   │ ╲ (High ARDE, Excellent S)
                      │  GOOD (S > 25:1)
                      ▼ ARDE ↓

Sweet Spot: 60-70°C with 60:40 CF₄:CHF₃, pulsed
Achieves: ARDE ~25%, S ~32:1, Rate ~170 nm/min
Viable for 7-14 nm nodes, marginal for 5nm
```

**Why This Matters for Yield:**

- Low selectivity → Al erosion → Increased resistance → Device timing fails → Yield loss
- High ARDE → CD variation → Timing skew → Device performance variable → Yield loss
- Both must be managed simultaneously
- Both have fundamental physical limits
- Advanced nodes operating near both limits simultaneously
- Future requires new approaches (ALE, IBE, wet etch) for sub-3nm

**Forward References:**

- **Chapter 13 (Polymerization):** Polymer affects both F-atom availability (selectivity) and surface reactions (uniformity)
- **Chapter 14 (Temperature Control):** Temperature control systems determine selectivity margin available
- **Chapter 15 (Cluster Integration):** Temperature uniformity across cluster affects selectivity uniformity across wafer
- **Chapter 16 (Endpoint & Yield):** Endpoint detection enables reduced over-etch, improving selectivity margin

---

**SELECTIVITY: THE ULTIMATE CONSTRAINT**

Oxide etch is viable only because Al₂O₃ is difficult to etch. This chapter quantifies that fundamental advantage: 30:1 at best. Everything else (ARDE, uniformity, temperature control, gas chemistry) is optimization around this single immutable constraint. Advanced nodes are exhausting this constraint. Future technologies will emerge because oxide etch selectivity is running out of margin.
