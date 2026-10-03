# Chapter 11: Fluorine Atom Kinetics — Transport and Reaction Models

## Introduction: F-Atoms as the Rate-Limiting Reactant

Chapter 10 established that **inverse ARDE arises from F-atom depletion** in high-aspect-ratio trenches. This chapter provides the quantitative framework for understanding F-atom behavior: where they come from, how they move, and where they disappear.

**Central Question:** Given that we inject CF₄/CHF₃ gas at known rates, what is the steady-state F-atom density as a function of position in the reactor?

**Why It Matters:**
- F-atom density directly determines etch rate: r_etch ∝ n_F
- Spatial F-atom profiles dictate uniformity across wafer
- Transport bottlenecks limit etch performance
- Process optimization requires understanding F-atom flow

This chapter bridges gas chemistry (Chapter 3) and inverse ARDE (Chapter 10).

## Section 11.1: F-Atom Generation — Source Terms

### 11.1.1 Electron-Impact Dissociation of CF₄

**Primary Source:**

```
In the plasma, energetic electrons collide with CF₄ molecules:

e⁻ + CF₄ → e⁻ + CF₃ + F  (electron-impact dissociation)

Cross-section vs. Electron Energy:
σ(E_e) = a × (E_e - E_threshold) × exp(-b × E_e / E_electron)

Where:
- E_e = electron energy (typically 5-100 eV in oxide etch plasma)
- E_threshold ≈ 3-4 eV (energy to break C-F bond)
- σ ≈ 10⁻¹⁶ cm² at 20 eV (small cross-section!)
- a, b = empirical coefficients from gas kinetics databases

Interpretation: Only electrons above ~4 eV can dissociate CF₄
Most electrons in oxide plasma are too slow! Result: Modest dissociation efficiency
```

**Dissociation Rate Calculation:**

```
F-atom generation rate per unit volume:

S_F = ∫ n_e(E_e) × v_e(E_e) × σ(E_e) × n_CF₄ dE_e

Where:
- n_e(E_e) = electron energy distribution (Maxwellian or non-Maxwellian)
- v_e = electron velocity
- n_CF₄ = CF₄ density
- Integration over all electron energies

Typical Result at 100 mTorr, 300W:
S_F ≈ 10¹⁵ F-atoms/(cm³·s)

Meaning: Each cubic centimeter of plasma generates 10¹⁵ F-atoms per second
This seems large! But F-atom diffusion spreads them out quickly
```

### 11.1.2 Electron-Impact Dissociation of CHF₃

**Secondary Source (When Using Gas Mixtures):**

```
CHF₃ dissociation is faster than CF₄:

e⁻ + CHF₃ → products (CF₂, CHF₂, CFH₂, CF₃, etc.) + F

Key differences from CF₄:
- Lower threshold energy (~2-3 eV vs. 3-4 eV)
- Larger cross-section: σ_CHF₃ ≈ 1.5-2× larger than σ_CF₄
- Result: More efficient F-atom production per electron

Why use CHF₃ for high-AR compensation?
- More F-atoms generated per unit RF power
- H-atoms passivate polymer (Chapter 13 mechanism)
- Better etch uniformity in deep trenches

Generation Rate:
S_F (CHF₃) ≈ 2 × S_F (CF₄) for same electron flux
(Factor of 2 improvement!)
```

### 11.1.3 Total F-Atom Source Term

**Combined Generation:**

```
When using CF₄:CHF₃ mixture (example: 60:40):

Total F-atom generation:
S_F_total = 0.60 × S_F(CF₄) + 0.40 × S_F(CHF₃)
          = 0.60 × 10¹⁵ + 0.40 × (2 × 10¹⁵)
          = 10¹⁵ (0.60 + 0.80)
          = 1.4 × 10¹⁵ F-atoms/(cm³·s)

Compared to pure CF₄:
Pure CF₄: S_F = 1.0 × 10¹⁵
60:40 mix: S_F = 1.4 × 10¹⁵
Improvement: +40% F-atom generation!

This explains why CHF₃-rich mixtures improve inverse ARDE:
More F-atoms to supply to deep trenches
```

## Section 11.2: F-Atom Transport Mechanisms

Three mechanisms transport F-atoms from generation region to wafer surface:

### 11.2.1 Diffusion (Dominant at Higher Pressures)

**Physics:**

```
F-atoms randomly walk due to collisions with neutral molecules.

Diffusivity:
D_F = (3/16) × (√(πmkT)) / (π × d² × n)

Where:
- m = F-atom mass = 19 amu
- k = Boltzmann constant
- T = gas temperature ≈ 300-500 K (plasma temperature)
- d ≈ 3-4 Å (collision diameter)
- n = neutral gas density

At typical oxide etch conditions (100 mTorr, 400 K):
D_F ≈ 100-200 cm²/s

This seems fast! But reactor volumes are large (~1000 cm³)
Diffusion time: τ_diff ~ L² / D_F
For L = 10 cm: τ_diff ≈ (10 cm)² / (150 cm²/s) ≈ 0.67 seconds
Long compared to plasma residence time!
```

**Diffusion Length:**

```
Characteristic length for F-atom diffusion:

L_diff = √(D_F × τ_lifetime)

Where:
- D_F = diffusivity
- τ_lifetime = F-atom lifetime before reacting/recombining

Typical lifetime at 100 mTorr:
τ ≈ 10-100 ms (limited by wall recombination and surface reactions)

Example:
L_diff = √(150 cm²/s × 0.05 s) = √7.5 = 2.7 cm

Interpretation: F-atoms diffuse ~2-3 cm before disappearing
In reactor geometry: sufficiently large that F-atoms reach most regions
In trenches (100-500 nm): trivial compared to diffusion length!
→ Diffusion alone cannot explain F-atom depletion in trenches
```

### 11.2.2 Drift in Electric Field

**Secondary Transport:**

```
Fluorine atoms can ionize to F⁻ (anions) or F⁺ (cations):

Neutral F-atom generation (primary):
e⁻ + CF₄ → F + CF₃

But some F-atoms capture electrons:
F + e⁻ → F⁻ (anion formation)

And some F-atoms lose electrons:
F + ... → F⁺ + e⁻ (cation formation)

If ions form, they drift in plasma electric field:
v_drift = μ_ion × E_field

Where:
- μ_ion ≈ 10²-10³ cm²/(V·s) (ion mobility)
- E_field ≈ 100-500 V/cm (typical plasma field)
- v_drift ≈ 10⁴-10⁵ cm/s (very fast!)

But: Ionization fraction of F-atoms is LOW (~0.1-1%)
Result: Drift contributes <10% of total transport
Primary transport remains diffusion + convection
```

### 11.2.3 Convection (Flow-Driven Transport)

**Practical Importance:**

```
Gas enters reactor at showerhead, flows toward pump-out.
F-atoms move with bulk gas flow.

Convection velocity:
v_conv = Q_gas / A_cross_section

Where:
- Q_gas = gas flow rate (e.g., 200 sccm = 200 cm³/min at STP)
- A_cross_section = reactor cross-sectional area ≈ 100 cm²

v_conv = (200 cm³/min) / (100 cm²) = 2 cm/min = 0.03 cm/s

Convection is SLOW (diffusion is 1000× faster!)

But: Convection direction matters
- F-atoms generated near showerhead
- Convective flow carries them toward wafer
- This is the ONLY directional transport
- Without convection, F-atoms would diffuse isotropically

Result: Convection provides weak "flow" direction
        Diffusion provides strong random transport
        Combined effect: F-atoms slowly drift wafer-ward
```

## Section 11.3: F-Atom Loss Mechanisms

### 11.3.1 Loss on Reactor Walls

**Wall Recombination:**

```
F-atoms hitting chamber walls recombine:

F + F (wall) → F₂ (desorbs from surface)

Or:

2F (wall) → F₂

Sticking coefficient:
γ_wall ≈ 0.1-0.3 (10-30% of F-atoms that hit wall stick and recombine)

Wall loss rate:
L_wall = γ_wall × n_F × (v_thermal / 4) × S_wall / V_reactor

Where:
- v_thermal = thermal velocity of F-atom ≈ 300-400 m/s
- S_wall = wall surface area ≈ 500 cm² (typical reactor)
- V_reactor ≈ 1000 cm³

Typical loss time:
τ_wall ≈ 20-50 ms

Lifetime Budget:
At 100 mTorr: τ_total ≈ 30-100 ms
Wall loss: τ_wall ≈ 20-50 ms
→ Wall loss accounts for 50-80% of F-atom disappearance!
```

**Importance for Oxide Etch:**

```
Wall loss is NOT wasteful if walls are clean!
Lost F-atoms formed F₂ (stable molecule) that cannot etch SiO₂
Better to lose F-atoms on walls than have them form unwanted species

But: Polymer-coated walls change kinetics
- Polymer reduces sticking coefficient (γ ↓)
- F-atoms that hit polymer may not recombine
- Instead: Partially reflected, can participate in etch again
- Result: Polymer buildup extends F-atom lifetime in reactor!

This is why polymer management (Chapter 8) affects etch performance:
More polymer → F-atoms live longer → higher bulk F-atom density
But: Polymer also blocks access to wafer (negative effect)
Net: Competing effects! Balance is critical.
```

### 11.3.2 Loss on Wafer Surface (Productive Consumption)

**Main Etch Reaction:**

```
F + SiO₂ (wafer) → SiF₄ (desorbs) + products

This is PRODUCTIVE loss:
- F-atom consumed in etch
- Contributes to desired reaction
- Directly affects etch rate

Reaction probability:
γ_etch ≈ 0.5-0.8 (50-80% of F-atoms hitting wafer surface participate in etch)

Wafer loss rate:
L_wafer = γ_etch × n_F × (v_thermal / 4) × A_wafer

Where:
- A_wafer ≈ 100-300 cm² (300mm wafer)

Typical loss time:
τ_wafer ≈ 50-100 ms

Competition with Wall Loss:
τ_wall ≈ 20-50 ms (wall)
τ_wafer ≈ 50-100 ms (wafer)
Ratio: Wall loss is 2-5× faster!

This explains low etch efficiency:
For every 1 F-atom that reacts at wafer,
2-5 F-atoms recombine on walls!
→ Only 20-33% etch efficiency from F-atoms
→ Requires high F-atom generation to compensate
```

### 11.3.3 Loss in Gas-Phase Reactions

**Fluorocarbon Formation:**

```
From Chapter 3 & 8: Fluorocarbon polymerization competes with etch

F-atoms can combine with hydrocarbon fragments to form polymers:

F + CFx → CFxF (more fluorinated species)
Multiple reactions → High-order fluorocarbons (polymers)

This is UNPRODUCTIVE loss:
- F-atoms consumed but don't etch
- Deposited as polymer layer
- Competes directly with etch reaction

Polymer formation efficiency:
η_polymer ≈ 0.1-0.2 (10-20% of F-atoms go to polymers)

Example at 100 mTorr, 300W:
F-atom generation: S_F = 10¹⁵ cm⁻³s⁻¹
Wall loss: ~50% (nonproductive)
Polymer: ~15% (nonproductive)
Etch: ~35% (productive!)

Result: Only 1/3 of generated F-atoms actually etch!
(35% / (35% + 50% + 15%) = 35% / 100%)

This is why power efficiency matters:
Need high RF power to generate enough F-atoms to overcome parasitic losses
```

## Section 11.4: Steady-State F-Atom Density

### 11.4.1 Rate Equation Approach

**Balance Equation:**

```
At steady state, F-atom generation = F-atom loss:

∂n_F/∂t = 0 (steady state)

0 = S_F (generation) - L_wall - L_wafer - L_polymer - L_diffusion_div

Simplified 0D model (uniform throughout reactor):

S_F = k_wall × n_F + k_wafer × n_F + k_polymer × n_F + ...

Where k_wall, k_wafer, etc. are loss rate constants

Solving for steady-state density:

n_F,ss = S_F / (k_wall + k_wafer + k_polymer + ...)

Typical values at 100 mTorr, 300W:
S_F ≈ 10¹⁵ cm⁻³s⁻¹
k_total ≈ 10⁴ s⁻¹ (all loss mechanisms combined)

n_F,ss = 10¹⁵ / 10⁴ = 10¹¹ cm⁻³

This matches measurements!
(Chapter 3 stated n_F ≈ 10¹⁴ atoms/cm³/s was generation rate)
(Steady-state density ~10¹¹ cm⁻³)
```

### 11.4.2 1D Transport Model (Showerhead to Wafer)

**Spatial Variation:**

```
More realistic: F-atom density varies with position z (distance from showerhead)

Governing equation (diffusion-convection):

∂n_F/∂t + v_z × ∂n_F/∂z = D × ∂²n_F/∂z² - n_F/τ + S_F(z)

Where:
- v_z = convective velocity (small, ~0.03 cm/s)
- D = diffusivity (~150 cm²/s)
- τ = F-atom lifetime (~50 ms)
- S_F(z) = generation (localized near plasma region)

At steady state (∂n_F/∂t = 0):

v_z × ∂n_F/∂z ≈ D × ∂²n_F/∂z² - n_F/τ + S_F(z)

Diffusion-dominated regime (when D >> v_z × L):

D × ∂²n_F/∂z² - n_F/τ + S_F(z) = 0

Solution in bulk plasma (without generation):

n_F(z) = A × exp(-z/L_diff) + B × exp(z/L_diff)

Where L_diff = √(D × τ) ≈ √(150 × 0.05) ≈ 2.7 cm
```

**Expected Profile:**

```
F-atom density as function of height in reactor:

n_F(z) (arbitrary units)
    1.0 │ ┌─ High density near showerhead
        │ │   (plasma generation region)
    0.8 │ │
        │ │╲
    0.6 │ │ ╲ Exponential decay
        │ │  ╲ with L_diff ≈ 2.7 cm
    0.4 │ │   ╲
        │ │    ╲
    0.2 │ │     ╲___
        │ │         ╲___  → Wafer
    0.0 └─┴──────────────
        0    5    10   15  (height, cm)

Wafer sees ~30-40% of peak F-atom density
(Compared to showerhead region)

This explains pressure dependence:
- Higher P: More collisions → Shorter L_diff → Steeper gradient
- Lower P: Fewer collisions → Longer L_diff → Gentler gradient
```

## Section 11.5: F-Atom Depletion in Trenches

### 11.5.1 Why Bulk Transport Models Fail for Trenches

**Scale Mismatch:**

```
Trench dimensions:
- Width: 10-100 nm
- Depth: 50-500 nm

F-atom diffusion length:
L_diff ≈ 2.7 cm = 2.7 × 10⁷ nm

Ratio: L_diff / Trench_depth ≈ 10⁷ (10 million times larger!)

Implication: From purely diffusive transport, F-atoms would be uniform
in trenches (no depletion possible!)

Then why does inverse ARDE exist?

Answer: Must include CONSUMPTION of F-atoms in etch reaction
        Surface reactions remove F-atoms as fast as diffusion brings them in
        In narrow trenches, this bottleneck matters
```

### 11.5.2 1D Trench Model (Depth Dependence)

**Governing Equation Inside Trench:**

```
Inside a trench, F-atoms diffuse inward, react at surface:

D × ∂²n_F/∂z² = k_surf × n_F

Where:
- z = depth into trench
- k_surf = surface reaction rate constant
- Assumes: F-atoms consumed by surface reaction

Boundary conditions:
- z = 0 (trench opening): n_F = n_F,bulk (F-atoms from bulk plasma)
- z = ∞ (infinite depth): n_F → 0 (depleted)

Solution:

n_F(z) = n_F,bulk × exp(-z/L_trench)

Where:

L_trench = √(D / k_surf)

Interpretation:
- Large D (high diffusivity): Larger L_trench (less depletion)
- Large k_surf (fast etch): Smaller L_trench (severe depletion)

Numerical Example:
D ≈ 150 cm²/s = 1.5 × 10⁻³ cm²/ms
k_surf ≈ 10⁴ s⁻¹ = 10 ms⁻¹

L_trench = √(1.5 × 10⁻³ / 10) = √(1.5 × 10⁻⁴) ≈ 0.012 cm = 120 μm

Result: For 200 nm trench depth:
n_F(200 nm) / n_F(0) = exp(-200 nm / 120 μm)
                      = exp(-0.0017)
                      ≈ 0.998 (virtually no depletion!)

This still contradicts Chapter 10 observations!
Something is missing...
```

### 11.5.3 The Polymer Effect: Reducing Diffusivity

**Key Missing Mechanism:**

```
Chapter 8 showed polymer accumulates preferentially in deep trenches
Polymer blocks F-atom transport!

Effective diffusivity with polymer:

D_eff ≈ D_vacuum × (1 - f_polymer)

Where:
- D_vacuum = bare diffusivity ≈ 150 cm²/s
- f_polymer = fraction of trench cross-section blocked by polymer

With heavy polymer buildup:
f_polymer ≈ 0.3-0.5 (30-50% blockage)

D_eff ≈ 150 × (1 - 0.4) = 90 cm²/s (40% reduction!)

More importantly: Polymer surface has HIGH k_surf value
(F-atoms react with polymer readily)

New governing equation:

D_eff × ∂²n_F/∂z² = k_polymer × n_F

Where:
k_polymer >> k_etch (polymer reaction faster than oxide etch!)

New depletion length:

L_trench = √(D_eff / k_polymer)
         = √(90 / 10⁵)
         = √(9 × 10⁻⁴)
         ≈ 0.03 mm = 30 μm

Still too large! For 200 nm trench:
n_F(200 nm) / n_F(0) = exp(-200 nm / 30 μm)
                      = exp(-0.0067)
                      ≈ 0.993 (still minimal depletion)

Even WITH polymer, standard 1D model predicts small depletion!
```

### 11.5.4 The Geometry Effect: 2D/3D Transport

**Why 1D Models Underestimate Depletion:**

```
Real situation: Trenches are NARROW features in a field of features

F-atoms entering trench opening must traverse:
1. Shrinking cross-section (trench walls)
2. Only limited width to receive F-atoms from bulk

Analogy: Water flowing into a narrow drain
- 1D model: Ignore that drain opening is small
- Reality: Limited water can enter because opening is small

Mathematical treatment requires 2D or 3D transport:

∂n_F/∂t = D(∇²n_F) - k_surf × n_F

Full 2D solution:

n_F(x,z) varies in both horizontal (x, across trench width)
         and vertical (z, depth) directions

Edge effects:
- Near sidewalls: n_F ↓ (sidewall consumes F-atoms)
- At bottom: n_F ↓↓↓ (deep + confined geometry)

Result: 2D model predicts 30-50% depletion at 200nm depth
        (Matches Chapter 10 experimental observations!)
```

## Section 11.6: Process Condition Effects on F-Atom Behavior

### 11.6.1 Pressure Dependence

```
Increasing Pressure → WORSE Depletion

Why? Collisions increase, diffusivity decreases:

D(P) = D₀ × (P_ref / P)

At 50 mTorr: D ≈ 300 cm²/s (high)
At 100 mTorr: D ≈ 150 cm²/s (medium)
At 200 mTorr: D ≈ 75 cm²/s (low)

With lower D, depletion length shrinks:

L_trench(P) = √(D(P) / k_surf) ∝ √P

At 50 mTorr: L_trench ≈ 50 μm, ARDE Index ≈ 20%
At 100 mTorr: L_trench ≈ 35 μm, ARDE Index ≈ 35%
At 200 mTorr: L_trench ≈ 25 μm, ARDE Index ≈ 50%

Counterintuitive result: Higher pressure WORSENS inverse ARDE!

Fab practice: Keep pressure 100-150 mTorr (compromise point)
- Not so high that ARDE becomes severe (bad uniformity)
- Not so low that etch rate collapses (low throughput)
```

### 11.6.2 Temperature Dependence

```
Increasing Temperature → BETTER (Reduced Depletion)

Multiple mechanisms:

Mechanism 1: Temperature ↑ → D ↑ (faster diffusion)
D ∝ T^1.5 (kinetic theory)

At 40°C (313 K): D₁
At 60°C (333 K): D ≈ 1.06 × D₁ (+6%)
At 80°C (353 K): D ≈ 1.13 × D₁ (+13%)

Mechanism 2: Temperature ↑ → Polymer volatilization ↑
More polymer escapes from surface
Result: k_surf (polymer reaction) DECREASES
→ L_trench increases
→ Less depletion!

Mechanism 3: Temperature ↑ → F-atom lifetime ↑
Fewer F-atoms lost in gas-phase reactions
→ Higher bulk n_F
→ Better supply to trenches

Combined effect:
At 40°C: ARDE Index ≈ 45%
At 60°C: ARDE Index ≈ 35%
At 80°C: ARDE Index ≈ 20%

Temperature 40→80°C gives 2.25× improvement in ARDE!
(This justifies thermal control emphasis in Chapter 5)
```

### 11.6.3 Power Dependence

```
Increasing Power → HIGHER n_F (Bulk F-atom Density Increases)

From S_F ∝ P and n_F,ss = S_F / k_loss:

n_F ∝ P

Example:
At 200W: n_F ≈ 0.67 × 10¹¹ cm⁻³
At 300W: n_F ≈ 1.0 × 10¹¹ cm⁻³ (higher bulk density)
At 400W: n_F ≈ 1.33 × 10¹¹ cm⁻³

But: Higher power also increases POLYMER GENERATION!

At higher power:
- More F-atoms generated ✓
- But more polymer formed ✗ (70-80% of F goes to polymer)
- Polymer increases k_surf ✗
- Polymer decreases D_eff ✗

Net result: Competing effects!
Bulk F-atom density ↑ (favors etch)
Depletion severity ↑ (hurts deep features)

Practical observation:
At 200W: Moderate etch, good uniformity
At 300W: Fast etch, moderate ARDE
At 400W: Very fast etch, SEVERE ARDE

This explains Chapter 10's finding:
"Higher power WORSENS inverse ARDE"
(Not because of physics, but because polymer effects dominate)
```

## Section 11.7: Advanced Topic — Multi-Species Transport Models

**Beyond Simple F-Atoms:**

```
Real oxide etch plasma contains multiple fluorine species:

F (neutral atom)
F⁻ (anion, rare)
F⁺ (cation, rare)
CF₃ (fluorine-containing radical)
CF₂ (partially fluorinated species)
etc.

Each species has:
- Different diffusivity
- Different reactivity with surfaces
- Different contribution to etch

Full transport model requires solving coupled equations:

∂n_F/∂t = D_F × ∇²n_F - k_F × n_F + S_F
∂n_CF₃/∂t = D_CF₃ × ∇²n_CF₃ - k_CF₃ × n_CF₃ + S_CF₃
etc.

Etch rate becomes:

r_etch = k₁ × n_F + k₂ × n_CF₃ + ...

Different species contribute to etch with different weights!

State of practice:
- Lab: Full multi-species models run on supercomputers
- Production fabs: 1-2 species simplified models
- Advanced nodes: 5-10 species models becoming standard
```

## Section 11.8: Measurement and Validation

### 11.8.1 Diagnostic Techniques

```
How do engineers verify F-atom density models?

Technique 1: Laser-Induced Fluorescence (LIF)
- Shine laser tuned to F-atom absorption line
- Fluorescence emission indicates F-atom density
- Spatial resolution: mm scale
- Advantage: Direct F-atom measurement
- Limitation: Expensive, lab-only
- Result: Validates 0D/1D models to ±20%

Technique 2: Mass Spectrometry of Exhaust
- Measure ion/neutral species in vacuum system
- Infer upstream densities using transport modeling
- Advantage: Production-compatible diagnostic
- Limitation: Indirect (requires modeling)
- Result: Cross-check on average F-atom density

Technique 3: Etch Rate Metrology
- Standard wafers with test trenches
- Measure etch depth vs. aspect ratio
- Infer F-atom profiles from rate measurements
- Advantage: Production-standard measurement
- Limitation: Convolves etch dynamics
- Result: Practical process control metric
```

### 11.8.2 Model Validation

```
Good model should predict:
✓ n_F ≈ 10¹¹ cm⁻³ (matches LIF observations)
✓ Etch rate ∝ n_F (linear with F-atom density)
✓ Pressure effect: Higher P → Lower n_F (diffusivity drop)
✓ Temperature effect: Higher T → Higher n_F (polymer loss ↓)
✓ Power effect: Higher P → Higher n_F (but with polymer competition)
✓ Spatial variation: ~30% density drop showerhead to wafer
✓ Trench depletion: ~40% drop at 200nm depth, 10:1 aspect ratio

State of models:
- 0D uniform models: Predict ~30% of effects
- 1D spatial models: Predict ~60% of effects
- 2D/3D transport: Predict ~90% of effects
- Full multi-species 3D: Predict ~95% of effects

Most fabs use 1D models (balance of accuracy vs. compute time)
```

## Section 11.9: Summary and Connection Forward

**Key Takeaways:**

1. **F-atom generation is the source** — electron-impact dissociation of CF₄/CHF₃
2. **Multiple loss mechanisms compete** — walls (50%), polymer (15%), etch (35%)
3. **Steady-state density is ~10¹¹ cm⁻³** — balance of generation and loss
4. **Transport is diffusion-dominated** — slow but thorough mixing
5. **Depletion in trenches is real** — 2D/3D geometry effects matter
6. **Pressure, temperature, power all affect n_F** — process optimization requires tuning all three
7. **Polymer presence is critical** — reduces effective diffusivity, increases k_surf

**Why F-Atom Kinetics Matters:**

Chapters 10-12 form the core physics of oxide etch:
- **Ch 10 (ARDE):** Observes that deep trenches etch slower
- **Ch 11 (F-kinetics):** Explains *why* — F-atom depletion from complex transport
- **Ch 12 (Selectivity):** Shows how F-atom availability affects selectivity margins

**Forward References:**

- **Chapter 12 (Selectivity):** F-atom density directly determines selectivity ratio (F to oxide vs. F to metal)
- **Chapter 13 (Polymerization):** Polymer formation competes with F-atom etch reactions
- **Chapter 14 (Temperature Control):** Temperature affects both D (diffusivity) and polymer, making control complex

---

**PART III DEEPENING: From Observations to First Principles**

Chapter 11 translates Chapter 10's empirical observations into quantitative transport theory. The next chapters (Selectivity, Polymerization) apply this F-atom framework to explain other oxide etch phenomena.
