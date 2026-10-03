# Chapter 3: Fluorine Chemistry in Oxide Etch Plasma

## Introduction: The Source of Etch Reactivity

Everything in thermal oxide etch—the etch rate, selectivity, temperature sensitivity, and process window—traces back to **fluorine chemistry**. Yet fluorine is a uniquely complex etchant:

- **Most reactive element** with silicon and oxygen (high exothermic reactions)
- **Multiple reactive species** (F⁰ atoms, F⁺ ions, F₂, F₂⁻)
- **High polymerization tendency** (creates fluorocarbon deposits competing with etch)
- **Highly toxic** (requires specialty equipment and safety systems)

Understanding which fluorine species dominate at different plasma conditions is essential for:
1. Predicting etch rate and selectivity
2. Diagnosing process drift and excursions
3. Optimizing recipe parameters
4. Managing chamber conditioning and polymer formation

This chapter quantifies fluorine chemistry from first principles.

## Section 3.1: Fluorine Species and Oxidation States

Fluorine can exist in several chemical forms in the plasma:

### 3.1.1 Fluorine Species Inventory

| Species | Oxidation State | Ionization | Reactivity | Abundance in Plasma | Role in Oxide Etch |
|---------|-----------------|-----------|-----------|-------------------|-------------------|
| F⁻ | -1 | Anionic | Very high | Low (<1%) | Not primary etchant |
| F⁰ (atom) | 0 | Neutral radical | Extremely high | Moderate (5-30%) | **PRIMARY etchant** |
| F⁺ | +1 | Cationic | Very high | Trace (<0.1%) | Ion-assisted enhancement |
| F₂ | 0 (mixed) | Neutral molecule | High | Low-moderate (1-10%) | Secondary etchant |
| F₂⁻ | Mixed | Anionic | High | Very low (<0.01%) | Negligible for etch |
| F₂⁺ | Mixed | Cationic | Very high | Trace | Ion bombardment only |

**Key Insight:** **F⁰ neutral atoms** are the dominant etchant for SiO₂, responsible for 80-95% of oxide removal. Ions (F⁺, F₂⁺) contribute 5-20% through ion-enhanced mechanisms.

## Section 3.2: Gas-Phase Chemistry in CF₄ and CHF₃ Plasmas

The starting materials for oxide etch are:
- **CF₄** (carbon tetrafluoride, perfluorocarbon)
- **CHF₃** (fluoroform, freon-23)
- **C₂F₆** (hexafluoroethane, less common)
- **HF** (hydrogen fluoride, in some processes)

### 3.2.1 CF₄ Dissociation Mechanism

CF₄ is the "workhorse" of oxide etch gas chemistry. In the plasma, it undergoes electron-impact dissociation:

#### Primary Dissociation Pathways:

**Pathway 1: Direct F-atom Formation**
```
CF₄ + e⁻(θ) → CF₃ + F⁰ + e⁻  (electron impact dissociation)

Reaction Energy: ΔE ≈ 15-20 eV (threshold energy ~15.3 eV)
Cross-section (σ): σ ≈ 10⁻¹⁶ cm² at typical electron energy (10 eV)
```

**Pathway 2: CF₃⁺ Formation (Ion Path)**
```
CF₄ + e⁻(θ) → CF₃⁺ + F⁰ + 2e⁻  (double ionization)

Reaction Energy: ΔE ≈ 20-25 eV
Cross-section: σ ≈ 2×10⁻¹⁶ cm²
```

**Pathway 3: CF₂ Formation**
```
CF₄ + e⁻(θ) → CF₂ + 2F⁰ + e⁻  (multiple F removal)

Reaction Energy: ΔE ≈ 25-30 eV
Cross-section: σ ≈ 3×10⁻¹⁷ cm² (lower probability)
```

#### Quantitative Rate Calculation:

The number of F-atoms generated per second is given by:

```
dN(F)/dt = n(e) × n(CF₄) × σ(e, E) × v̄(e)

Where:
- n(e) = electron density (cm⁻³) ~ 10⁹-10¹⁰ for oxide etch (typical)
- n(CF₄) = CF₄ neutral density (cm⁻³) ~ 10¹⁰-10¹² (pressure dependent)
- σ(e, E) = dissociation cross-section (depends on electron energy)
- v̄(e) = average electron velocity ~ 10⁸ cm/s at 5 eV average energy
```

**Typical Rate:**
```
At 100 mTorr, 300 W RF power:
n(CF₄) ≈ 5×10¹¹ cm⁻³
n(e) ≈ 5×10⁹ cm⁻³
σ ≈ 5×10⁻¹⁶ cm²

dN(F)/dt ≈ (5×10⁹) × (5×10¹¹) × (5×10⁻¹⁶) × (10⁸)
         ≈ 1.25×10¹⁴ F-atoms/(cm³·s)

This is the **F-atom source rate** in the plasma volume
```

### 3.2.2 CHF₃ Dissociation Mechanism

CHF₃ is more reactive than CF₄ (lower dissociation energy) and produces F-atoms more efficiently:

#### Dissociation Pathways:

**Pathway 1: F-atom Loss**
```
CHF₃ + e⁻ → CHF₂⁺ + F⁰ + 2e⁻

Threshold Energy: ΔE ≈ 9-12 eV (LOWER than CF₄!)
Cross-section: σ ≈ 2×10⁻¹⁵ cm² (10x higher than CF₄)
```

**Pathway 2: Multi-Step Dissociation**
```
CHF₃ + e⁻ → CF₂⁺ + H⁰ + 2e⁻
       or
→ CHF⁺ + 2F⁰ + 2e⁻
```

#### Comparison: CHF₃ vs. CF₄

| Parameter | CF₄ | CHF₃ | Ratio (CHF₃/CF₄) |
|-----------|-----|------|------------------|
| Ionization Threshold (eV) | 15.3 | 9-12 | 0.65-0.78 |
| Peak Cross-section (cm²) | 5×10⁻¹⁶ | 2×10⁻¹⁵ | 4-10 |
| F-atom Yield per Electron Impact | 1 | 1.5-2 | 1.5-2 |
| Etch Rate (Å/min, 100 mTorr, 300W) | 450-550 | 650-800 | 1.3-1.6 |
| Selectivity to Al | 80-120:1 | 150-200:1 | Better |

**Process Implication:** CHF₃ generates F-atoms more efficiently and with better selectivity. However, it also promotes fluorocarbon formation more readily (see Section 3.5).

## Section 3.3: F-Atom Transport and Depletion

### 3.3.1 F-Atom Lifetime in the Plasma

Once generated in the plasma, F-atoms have finite lifetime before being **lost** (consumed or recombined):

#### F-Atom Loss Mechanisms:

**Loss Mechanism 1: Recombination into F₂**
```
F⁰ + F⁰ → F₂  (three-body recombination, requires third body M)

Rate: k₁ [F⁰][F⁰][M] ≈ 10⁻³¹-10⁻³⁰ cm⁶·s⁻¹

At typical F-atom density of 10¹¹ cm⁻³:
Recombination rate ≈ 10⁻⁹ - 10⁻⁸ s⁻¹ (very slow at low pressure)
Lifetime: τ ≈ 10⁸-10⁹ seconds (essentially infinite at low pressure!)
```

**Loss Mechanism 2: Reaction with Carbon and Fluorocarbon**
```
F⁰ + CFₓ → CF(x+1) + intermediate  (polymerization chain)

Rate: k₂ [F⁰][CFₓ] ≈ 10⁻¹²-10⁻¹¹ cm³·s⁻¹

At moderate CFₓ density of 10¹⁰ cm⁻³:
Loss rate ≈ 10⁻² - 10⁻¹ s⁻¹ (significant!)
Lifetime: τ ≈ 10-100 seconds
```

**Loss Mechanism 3: Wall Recombination**
```
F⁰ → (wall) → ½F₂ + electron

Recombination coefficient γ ≈ 0.01-0.1 (varies by surface)

At chamber radius R ≈ 20 cm, plasma volume V ≈ 30 L:
Surface area A ≈ 3000 cm²
Diffusion to wall ≈ 10-100 ms residence time
```

### 3.3.2 F-Atom Distribution and Depletion Profile

In high-density features (aspect ratio 5:1 or higher), F-atom depletion becomes dramatic:

```
Wide trench (1:1 aspect ratio):
Top of feature:   F-atom density ~ 100%
Bottom of feature: F-atom density ~ 95-98% (minimal depletion)
Etch rate variation: ~2-5%

Narrow trench (5:1 aspect ratio):
Top of feature:   F-atom density ~ 100%
Mid-depth:        F-atom density ~ 60-70% (significant depletion)
Bottom of feature: F-atom density ~ 20-40% (severe depletion!)
Etch rate variation: ~60-80% (INVERSE ARDE)
```

**Physical Mechanism:**
```
As F-atoms diffuse down the trench:
1. Collisions increase (higher pressure at depth)
2. Reactions with trench walls deplete supply
3. Products (SiF₄, fluorocarbon) block new F-atoms
4. Net result: etch rate is 50-75% lower at bottom than top
```

This **inverse ARDE** (aspect ratio dependence opposite to silicon etch) is the defining characteristic of high-rate oxide etch. (Detailed analysis in Chapter 10.)

## Section 3.4: Fluorine Atom Density and Equilibrium

### 3.4.1 Steady-State F-Atom Density

In the plasma, F-atom generation (from electron impact) is balanced by losses (recombination, reactions, wall loss):

```
Generation Rate = Loss Rate (steady state)

d[F]/dt = 0 = (generation term) - k_recomb[F]² - k_react[F][CFₓ] - (diffusion/convection loss)
```

Solving for equilibrium F-atom density:

```
[F]_equilibrium ≈ √(Generation Rate / Loss Rate Coefficients)

Typical values at 100 mTorr, 300W RF:
[F] ≈ 10¹¹ - 10¹² cm⁻³

This is ~10⁻⁶ of neutral molecule density (highly radical-limited process!)
```

### 3.4.2 Effect of RF Power on F-Atom Density

Increasing RF power dramatically increases F-atom generation:

```
RF Power Dependence (approximately):
[F] ∝ √(Power)  (square-root dependence due to generation-loss balance)

Example:
At 200 W: [F] ≈ 8×10¹⁰ cm⁻³ → etch rate ≈ 400 Å/min
At 300 W: [F] ≈ 1.0×10¹¹ cm⁻³ → etch rate ≈ 600 Å/min  (+50% power, +50% rate)
At 400 W: [F] ≈ 1.2×10¹¹ cm⁻³ → etch rate ≈ 750 Å/min  (+100% power, +87.5% rate)

Square-root dependence explains why doubling power doesn't double etch rate!
```

### 3.4.3 Effect of Pressure on F-Atom Density

Pressure has a complex effect on F-atom density:

```
Low Pressure (<50 mTorr):
- Few gas molecules → long mean free path → F-atoms escape to walls
- Generation: GOOD (electrons can travel far)
- Loss: VERY FAST (diffusion to walls dominates)
- Net F-atom density: MODERATE

Medium Pressure (100-200 mTorr):
- Optimal balance of generation and transport
- F-atoms generated and transported efficiently to wafer
- Net F-atom density: HIGH (maximum)
- Etch rate: MAXIMUM

High Pressure (>300 mTorr):
- Crowded gas molecules → electrons thermalize quickly
- Generation: POOR (electrons lose energy in collisions before hitting CF₄)
- Transport: Blocked (F-atoms recombine in gas phase)
- Net F-atom density: LOW (much lower than medium pressure)
- Etch rate: DECREASES (inverse pressure dependence!)
```

**Plot of F-atom Density vs. Pressure:**

```
F-atom Density
      │
      │         ┌─────── Maximum at
      │        ╱         100-150 mTorr
      │       ╱
      │      ╱
      │     ╱
      │    ╱
      │   ╱
      │  ╱
      │ ╱________________
      └────────────────────
        0  50  100 150 200 250 300 350 400
              Pressure (mTorr)
```

This **pressure-rate curve** is crucial for process optimization; it explains why there's a "sweet spot" around 100-150 mTorr.

## Section 3.5: Fluorocarbon Formation and Polymerization

Fluorocarbon formation is the "dark side" of fluorine chemistry in oxide etch. While F-atoms etch oxide, fluorocarbon radicals polymerize and deposit on surfaces.

### 3.5.1 Fluorocarbon Formation Pathways

**Mechanism 1: Direct Polymerization in Gas Phase**
```
CF₃⁺ (from CF₄ or CHF₃ dissociation)
   + CF₃⁰ (from same source)
   + F⁰ + other radicals
   ↓
(CF₃)ₙ polymer chains
   ↓
C-F polymer deposits on walls and wafer
```

**Mechanism 2: Competitive Reaction at Wafer Surface**

F-atoms reaching the oxide surface have two fates:

```
DESIRED PATH:  SiO₂ + F⁰ → SiF₄↑ (volatile, desorbs)

UNDESIRED PATH: SiO₂-CFₓ + F⁰ → SiO₂-CF(x+1) → (fluorocarbon polymer layer)
```

**Mechanism 3: C-F Bond Formation and Stabilization**

Why is C-F bonding so strong? C-F bonds have:
- **Bond Dissociation Energy:** 540-550 kJ/mol (extremely strong!)
- **Electronegativity Difference:** Large (C=2.6, F=4.0) → ionic character
- **Resistance to Attack:** Other F-atoms find it difficult to break C-F bonds

Result: Once fluorocarbon chains start forming, they're **difficult to break apart** and accumulate on chamber walls.

### 3.5.2 Polymer Composition and Structure

Real fluorocarbon deposits are not simple CFₓ molecules. They're complex:

| Component | Composition | Abundance | Notes |
|-----------|-------------|-----------|--------|
| Fluorinated chains | C-F, C-F₂, C-F₃ | 60-80% | Primary polymer backbone |
| Cross-links | C-C bonds | 15-25% | Cross-linked network |
| Oxygen incorporation | C-F-O bonds | 5-15% | From SiO₂ or residual water |
| Hydrogen (trace) | C-F-H, F-H bonds | <5% | From CHF₃ or water |
| Silicon incorporation | Si-F, Si-C-F | <3% | Reaction with SiO₂ |

**Polymer Density:** 1.8-2.1 g/cm³ (slightly less than SiO₂)

**Polymer Thickness Growth Rate:**
```
At 100 mTorr, 300W RF, CF₄ plasma:
Polymer deposition: ~5-10 nm per minute

After 50 wafers (1000 minutes):
Polymer layer: 5-100 nm thick (highly variable, chamber-dependent)

This is why NF₃ cleaning cycles are required every 20-50 wafers!
```

### 3.5.3 Temperature Effects on Polymerization

Counterintuitively, higher temperatures REDUCE polymerization:

```
Low Temperature (20°C):
- F-atoms have lower energy → slower etch
- Polymers are more stable → accumulate readily
- Polymer removal rate: Slow
- Net polymer growth: Rapid

Medium Temperature (60°C, standard):
- F-atoms have moderate energy → good etch
- Polymers form but with some thermal decomposition
- Polymer removal rate: Moderate
- Net polymer growth: Slow (manageable)

High Temperature (100°C):
- F-atoms have higher energy → very fast etch
- Thermal energy breaks some C-F bonds → less polymer stable
- Polymer removal rate: Fast (thermal volatilization)
- Net polymer growth: Minimal (or negative!)
```

**Quantitative Effect:**
```
Polymer Growth Rate vs. Temperature

Polymer Thickness
(nm after 50 wafers)
      │
  100 │─────────
      │    ╲
   75 │     ╲
      │      ╲
   50 │       ╲────────
      │
   25 │
      │
    0 └─────────────────
      0  20  40  60  80  100 120
         Temperature (°C)
```

This explains why temperature control is critical: higher temperature enables both faster etch AND lower polymer accumulation (dual benefit).

## Section 3.6: Chemical Kinetics and Rate Constants

### 3.6.1 Key Reaction Rate Constants

For modeling oxide etch rates, several rate constants must be known:

| Reaction | Rate Constant | Temperature Dependence | Notes |
|----------|--------------|----------------------|--------|
| F⁰ + SiO₂ → SiF₄ | k₁ = 10⁻¹⁰ cm³/s | ~T¹·⁵ | Moderate T-dependence |
| F⁰ + CFₓ (polymerization) | k₂ = 10⁻¹² cm³/s | ~T (strong T-dependence) |
| F-atom recombination | k₃ = 10⁻³¹ cm⁶/s | ~T⁻⁰·⁵ | Three-body; slow |
| CF₄ dissociation (electron impact) | σ × v̄ = 10⁻¹² cm³/s | Weak | Depends on Te |

### 3.6.2 Etch Rate from First Principles

Combining thermodynamics (from Chapter 2) and kinetics (this chapter):

```
Etch Rate = [F] × k₁ × n(SiO₂) / (1 + competition factor)

Where:
- [F] = F-atom density (cm⁻³) ~ 10¹¹-10¹² 
- k₁ = F-atom reaction rate constant with oxide
- n(SiO₂) = SiO₂ density at surface
- competition factor = suppression by polymerization
```

**Numerical Example:**
```
Given (at 60°C, 100 mTorr, 300W CF₄):
[F] = 1.0×10¹¹ cm⁻³
k₁ = 10⁻¹⁰ cm³/s
Surface density of SiO₂ ≈ 10¹⁵ sites/cm²
Competition factor ≈ 0.3 (30% suppression by polymerization)

Collision rate: [F] × k₁ = 10¹ collisions/(cm³·s) = 10⁷ cm/s
Etch depth per collision: ~1 Å (one layer removed)
Collision rate at surface: 10⁷ cm/s = 100 nm/s = 6000 Å/min (theoretical max)

With competition suppression (×0.3): ≈ 1800 Å/min (kinetically limited)

Measured rate: ~600 Å/min (experimental)

Discrepancy explained by:
- Not all F-atoms reach wafer (diffusion losses)
- Not all surface sites are reactive
- Ion-assisted effects are small at low power
- Selectivity reduction at high rates
```

This first-principles calculation shows why oxide etch rates plateau around 500-800 Å/min—F-atom supply becomes rate-limiting.

## Section 3.7: Practical Chemistry for Process Optimization

### 3.7.1 Gas Chemistry Selection Guide

| Chemistry | Etch Rate | Selectivity | Polymer Formation | Use Case |
|-----------|-----------|-------------|------------------|----------|
| 100% CF₄ | Medium (500 Å/min) | High (100:1) | Low | Standard; balanced |
| CF₄/CHF₃ 1:1 | Medium-high (600 Å/min) | Medium (80:1) | Medium | Common mixture |
| 100% CHF₃ | High (750 Å/min) | Excellent (150:1) | Medium-high | Tight selectivity |
| CF₄/CHF₃/Ar mix | High (700 Å/min) | Medium (70:1) | Lower | Better uniformity |
| C₂F₆ | Low (400 Å/min) | Excellent (200:1) | Low | Ultra-selective, slow |

**Selection Logic:**
- Need **high selectivity** (advanced nodes, tight metal spacing) → Use CHF₃-rich or C₂F₆
- Need **throughput** (high volume, less demanding processes) → Use CF₄-rich
- Need **balance** (most fabs, 5nm/7nm nodes) → Use CF₄/CHF₃ 1:1 to 1:2 mix
- Need **low polymer** (tight process window) → Add Ar to promote sputtering

## Summary and Connection to Later Chapters

### Key Takeaways:

1. **F⁰ atoms are primary etchant** (80-95% of oxide removal); ions assist (5-20%)
2. **F-atom generation limited** by electron-impact dissociation; supply-limited at high density
3. **Pressure curve has sweet spot** at 100-150 mTorr; inverse pressure effect at high pressure
4. **RF power drives F-atom generation** via roughly √(Power) relationship
5. **Fluorocarbon polymerization competes** with etch; higher temperature suppresses it
6. **Temperature sensitivity (~8-10%/°C) originates** from F-atom reaction kinetics
7. **Selectivity fundamentally limited** by ΔG difference between oxide and metal reactions

### Forward References:

- **Chapter 4 (Plasma-Oxide Reactions):** Detailed surface mechanisms showing how F⁰ and ions interact with oxide
- **Chapter 10 (Inverse ARDE):** Explains F-atom depletion at depth using kinetic analysis from this chapter
- **Chapter 11 (F-Atom Kinetics):** Advanced modeling of F-atom transport and residence time effects
- **Chapter 13 (Polymerization & Fluorocarbon):** Detailed analysis of polymer formation and NF₃ removal

---

**Next Chapter:** Chapter 4 details what happens when F-atoms and ions reach the oxide surface—the plasma-oxide surface reaction mechanisms that create selectivity.
