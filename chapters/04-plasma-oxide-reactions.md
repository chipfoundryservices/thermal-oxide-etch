# Chapter 4: Plasma-Oxide Surface Reactions and Ion-Enhanced Chemistry

## Introduction: Where Etch Actually Happens

Chapters 2 and 3 established the thermodynamic and gas-phase foundations for oxide etch. Yet they don't answer the essential question: **What happens when fluorine species reach the oxide surface?**

This chapter focuses on **surface chemistry**—the physical and chemical mechanisms by which F-atoms and ions remove SiO₂ from the wafer. Understanding these mechanisms reveals:

1. **Why selectivity to metal emerges** despite thermodynamically similar driving forces
2. **How ions assist etch** beyond what F-atoms alone could accomplish
3. **Why surface damage is minimal** (compared to silicon or nitride etch)
4. **How etch rate varies** with ion energy, F-atom flux, and temperature
5. **The fundamental limits** on selectivity and process window

This is the bridge between gas-phase chemistry and equipment design.

## Section 4.1: F-Atom Surface Reactions with SiO₂

### 4.1.1 Reaction Mechanism: F-Atom Attack on Si-O Bonds

When an F-atom encounters the SiO₂ surface, a sequence of reactions begins:

#### **Step 1: Chemisorption and Initial Bond Breaking**

```
SiO₂ surface + F⁰ → SiO-F (chemisorbed intermediate)

Reaction time: ~10⁻¹⁴ - 10⁻¹³ seconds (femtoseconds)
Bond energy: Si-O bond (~110 kcal/mol) vs. Si-F bond (~130 kcal/mol)

Result: F-atom **extracts** oxygen from Si-O bond; Si-F is stronger bond
```

**Why F-atoms Prefer Si-O Bonds:**

F has the highest electronegativity of all elements (4.0 vs. O at 3.44). When F approaches:
- Electrons in Si-O bond are pulled toward F
- Si becomes electron-deficient (δ+)
- O leaves as O²⁻ or O-F species
- Si-F bond forms (very strong, ~10% stronger than Si-O)

**Thermodynamic Favorability:**

```
Si-O bond dissociation energy: 110 kcal/mol
Si-F bond dissociation energy: 130 kcal/mol
F-O bond dissociation energy: 64 kcal/mol (weak!)

Net reaction: Si-O + F → Si-F + O
ΔH ≈ 110 - 130 + 64 ≈ 44 kcal/mol (exothermic, favorable)
```

#### **Step 2: SiF₂ or SiF₃ Intermediate Formation**

```
SiO-F + F⁰ → SiF₂ (or continuing attack) → SiF₃
```

Additional F-atoms attack the growing intermediate, replacing remaining oxygens.

#### **Step 3: SiF₄ Formation and Volatilization**

```
SiF₃ + F⁰ → SiF₄ (silicon tetrafluoride)

SiF₄ sublimation temperature: ~32.8°C at 1 atm
At 60°C and 100 mTorr: SiF₄ is **extremely volatile**

Result: SiF₄ immediately desorbs from surface and is pumped away
```

**Key Property of SiF₄:**

| Property | Value | Significance |
|----------|-------|--------------|
| Melting Point | -90.2°C | Solid only at cryogenic temps |
| Boiling Point | 32.8°C | Gas at all practical process temps |
| Vapor Pressure @ 60°C | ~1 atm | Essentially complete volatilization |
| Vapor Pressure @ 20°C | ~0.5 atm | Still highly volatile |

**This is why SiO₂ etches cleanly in fluorine plasma:** The product (SiF₄) is so volatile that it doesn't remain on the surface to form a passivating layer.

### 4.1.2 Etch Rate from F-Atom Flux

The surface etch rate depends on **how many F-atoms reach the surface and react**:

```
Etch Rate = Φ_F × σ_etch × n_sites

Where:
- Φ_F = F-atom flux to surface (atoms/cm²·s)
- σ_etch = reaction cross-section (cm²)
- n_sites = number of reactive sites available
```

#### **Quantitative Calculation:**

**Typical plasma conditions (100 mTorr, 300W, 60°C):**

```
F-atom density in plasma: [F] = 1.0×10¹¹ cm⁻³
Thermal velocity: v̄_F ≈ 3×10⁴ cm/s (at 60°C)
Flux to surface: Φ_F = 0.25×[F]×v̄_F = 0.25×(1.0×10¹¹)×(3×10⁴)
                     ≈ 7.5×10¹⁴ F-atoms/(cm²·s)

Reaction cross-section: σ_etch ≈ 10⁻¹⁵ cm² (fraction of atomic area)

Reaction probability: σ_etch × 1 ≈ 10⁻¹⁵ cm² (very small!)
Actual F-atoms reacting: Φ_F × σ_etch ≈ 7.5×10¹⁴ × 10⁻¹⁵
                                       ≈ 0.75×10⁰ ≈ 75% of incident flux

Atoms removed per reaction: ~4 (F⁰ + SiO₂ → SiF₄)

Removal rate: 0.75 × (7.5×10¹⁴) / 4 ≈ 1.4×10¹⁴ SiO₂ molecules/(cm²·s)

Convert to etch rate:
- SiO₂ density: 2.2 g/cm³
- Molecular weight: 60 g/mol
- Surface density: n = (2.2 / 60) × 6.02×10²³ / 2.27 ≈ 10¹⁵ molecules/cm²

Etch rate: (1.4×10¹⁴ removed/s) / (1.0×10¹⁵ available/cm²) × (depth per layer)
         ≈ 600-800 Å/min (matches experimental!)
```

**Key Insight:** The calculation shows that etch rate is fundamentally limited by F-atom flux, confirming Chapter 3's conclusion about radical-limited kinetics.

### 4.1.3 Competing Surface Reactions

Not all F-atoms that reach the surface actually etch oxide. Some reactions compete:

#### **Desired Reaction: Oxide Removal**
```
SiO₂ + 4F⁰ → SiF₄↑ + O products
Outcome: Etch (material removed)
Efficiency: ~60-80% of incident F-atoms
```

#### **Competing Reaction 1: Polymerization**
```
SiO₂-CFₓ + F⁰ → SiO₂-CF(x+1) (polymer growth)
Outcome: Passivation layer builds up
Efficiency: ~10-20% of incident F-atoms at 60°C
           ~20-30% of incident F-atoms at 20°C
```

#### **Competing Reaction 2: F₂ Recombination**
```
2F⁰ → F₂ (recombination in gas phase or at surface)
Outcome: F-atoms are "lost" before reacting
Efficiency: ~5-10% loss at medium pressure
           ~20-30% loss at high pressure
```

**Temperature Dependence of Competition:**

```
At Low Temperature (20°C):
- F-atom velocity: Low
- Polymerization rate: High (polymer stable)
- Etch efficiency: ~50-60%
- Net etch rate: Slow (kinetically limited)

At Medium Temperature (60°C, standard):
- F-atom velocity: Moderate
- Polymerization rate: Moderate (polymer thermally unstable)
- Etch efficiency: ~70-80% (good balance)
- Net etch rate: Fast (kinetically optimized)

At High Temperature (100°C):
- F-atom velocity: High
- Polymerization rate: Low (polymer breaks down)
- Etch efficiency: ~80-90% (excellent)
- Net etch rate: Very fast (kinetically enhanced)
- Thermal volatilization: Enhanced
```

This explains why industry standard is 60°C: it's the balance point where etch efficiency is high, polymerization is manageable, and selectivity is maintained.

## Section 4.2: Ion-Assisted Etch Mechanisms

### 4.2.1 Ion-Surface Interactions

While F-atoms dominate (~80-95% of etch), ions contribute through several mechanisms:

#### **Physical Sputtering by Ion Bombardment**

```
Ion (Ar⁺ or F⁺) hits SiO₂ surface with kinetic energy E_ion
        ↓
Collision cascade: ion transfers momentum to surface atoms
        ↓
Surface atoms are dislodged (physically removed)

Sputtering yield: Y = (# removed atoms) / (# incident ions)
```

**Sputtering Yield for Common Ions:**

| Ion | Target | Ion Energy (eV) | Yield (atoms/ion) | Notes |
|-----|--------|-----------------|------------------|--------|
| Ar⁺ | SiO₂ | 100 | 0.5-1.0 | Physical sputtering dominant |
| Ar⁺ | SiO₂ | 500 | 1.5-2.5 | Energy-dependent |
| F⁺ | SiO₂ | 100 | 1.0-2.0 | Chemical + physical hybrid |
| F⁺ | SiO₂ | 500 | 2.5-4.0 | Synergistic chemistry |

#### **Ion-Enhanced Chemical Etch**

```
Mechanism: Ion bombardment doesn't just physically remove atoms; it:
1. Creates reactive sites (dangling bonds, defects)
2. Provides activation energy for reactions
3. Drives reactions that would be kinetically slow otherwise

Example: With F-atoms alone, etch rate at room temperature ≈ 100 Å/min
         With F-atoms + low-energy ions, etch rate at room temp ≈ 300 Å/min
         Enhancement factor: ~3x from ion-assist
```

#### **Subsurface Damage**

```
High-energy ion (>500 eV) creates displacement cascade:
- Primary knock-on atom (PKA) travels ~50-200 Å into surface
- Leaves trail of defects (vacancies, interstitials)
- Creates amorphous layer below surface

Depth of damage: ~2-10 nm for typical oxide etch conditions
Consequence: Surface becomes more reactive; defect-rich layer etches faster
```

### 4.2.2 Ion Energy Control and Selectivity

The kinetic energy of ions (E_ion) directly affects selectivity to metal:

#### **Low Ion Energy Regime (<50 eV)**

```
Characteristics:
- Physical sputtering negligible
- Ion-assist is minimal
- Chemical etch (F-atoms) dominates
- Selectivity to Al: Very high (100-150:1)
- Selectivity trade-off: Etch rate lower (~400 Å/min)
```

#### **Medium Ion Energy Regime (50-150 eV)**

```
Characteristics:
- Physical sputtering modest but present
- Ion-assist becomes significant
- Mixed chemical + physical etch
- Selectivity to Al: Good (50-100:1)
- Selectivity trade-off: Good etch rate (600-800 Å/min)
- Process window: WIDEST (most forgiving)
```

#### **High Ion Energy Regime (>200 eV)**

```
Characteristics:
- Physical sputtering dominates
- Oxide AND aluminum both sputter effectively
- Chemical selectivity advantages lost
- Selectivity to Al: Poor (10-30:1)
- Etch rate: Very high (>1000 Å/min)
- Process window: NARROW (easily over-etch)
```

**Process Decision:**

Industry operates in the **medium ion energy regime** (50-150 eV) because it optimizes the selectivity-rate tradeoff. Self-bias voltage in typical CCP systems naturally falls into this range:

```
Self-bias voltage: V_bias = √(Power × Pressure) / (constant)

For typical oxide etch (300W, 100 mTorr):
V_bias ≈ 50-100 V
Ion energy ≈ 50-100 eV (desirable!)
```

### 4.2.3 Synergistic Ion-Radical Chemistry

Perhaps the most important insight: ions and radicals work **synergistically**, not independently.

#### **Synergy Example: F⁺ Ion + F⁰ Radical**

```
Scenario 1: F-atoms alone
4 F⁰ + SiO₂ → SiF₄↑ (slow at low temperature)
Reaction cross-section: σ ≈ 10⁻¹⁵ cm²

Scenario 2: F⁺ ion prepares surface, then F-atoms attack
Step 1: F⁺ ion hits SiO₂ → creates dangling Si bonds (reactive sites)
Step 2: F⁰ atom hits prepared site → reaction is faster
        Reaction cross-section: σ ≈ 10⁻¹⁴ cm² (10x larger!)
        Rate-limiting step changes from chemical reaction to F-atom arrival

Result: Same number of F-atoms, but 3-5x higher etch rate due to synergy
```

#### **Quantitative Synergy Model:**

```
Total etch rate = k_F × [F] + k_ion × I_ion + k_synergy × [F] × I_ion

Where:
- k_F [F] = etch from F-atoms alone
- k_ion I_ion = etch from ions alone
- k_synergy [F] × I_ion = synergistic enhancement (non-linear term)

Typical contributions:
- F-atom term: 70-80% of total etch rate
- Ion term: 10-20% of total etch rate
- Synergy term: 5-15% of total etch rate
```

## Section 4.3: Why Selectivity to Metal Emerges

### 4.3.1 The Selectivity Paradox

**Question:** If both SiO₂ + F and Al + F are thermodynamically favorable, why is selectivity only ~30:1?

**Answer:** It's not a thermodynamic issue—it's a **surface chemistry and kinetics issue**.

### 4.3.2 Al₂O₃ Native Oxide as Selectivity Layer

This is the critical insight: **Aluminum doesn't etch directly. Its protective native oxide (Al₂O₃) etches much slower than SiO₂.**

#### **Etch Rate Comparison:**

| Material | Etch Rate (Å/min) | Selectivity vs. SiO₂ |
|----------|------------------|-------------------| 
| SiO₂ (thermal) | 600-800 | 1.0× (reference) |
| Al₂O₃ (native) | 20-40 | 20-30:1 |
| SiO₂ (porous) | 700-900 | 0.9-1.1× |
| SiO₃N₄ (Si₃N₄) | 50-150 | 5-10:1 |
| Cu | 2-5 | 150-300:1 (extremely slow) |

**Why Al₂O₃ Etches Slower Than SiO₂:**

```
Physical Reason 1: Different Bond Strengths
- Al-O bond energy: ~115 kcal/mol (vs. Si-O at 110)
- Al-F bond energy: ~125 kcal/mol (vs. Si-F at 130)
- Slight advantage for Al (bonds are stronger), BUT...

Physical Reason 2: Product Stability
- AlF₃: Melting point 1291°C, sublimation temperature ~1000°C
  (NOT volatile at oxide etch temperatures!)
- AlF₄⁻ (in hydrolytic solution): Can form stable complex
- Results: AlF₃ deposits on surface, passivates further etch

Physical Reason 3: Surface Reconstruction
- Al₂O₃ surface can reconstruct during etch
- Al-F bonds are strong → difficult to break
- Creates more stable surface than SiO₂
```

#### **Quantitative Selectivity Model:**

```
Selectivity = (Etch Rate SiO₂) / (Etch Rate Al₂O₃)
            = (k₁[F]_SiO₂ + k₂I_ion) / (k₁[F]_Al₂O₃ + k₂I_ion)

Since [F-atom flux and ion current are identical to both surfaces]:
            = k_SiO₂ / k_Al₂O₃
            ≈ 30-50 (for optimized conditions)

The selectivity comes from ~20-30:1 difference in surface reaction 
rate constants (k_SiO₂ >> k_Al₂O₃), NOT from F-atom availability difference.
```

### 4.3.3 Temperature Effects on Selectivity

Higher temperature increases BOTH oxide and aluminum etch rates, but oxide increases more:

```
Temperature Effect on Rate Constants (Arrhenius):
k(T) = A × exp(-Eₐ/RT)

For SiO₂:  Eₐ ≈ 0.9 eV
For Al₂O₃: Eₐ ≈ 0.6 eV (LOWER activation energy!)

Result: At low T, Al₂O₃ is "frozen" (kinetically slow)
        At high T, Al₂O₃ becomes more reactive
        Selectivity DECREASES at higher temperature!

Example:
At 20°C: SiO₂ rate ≈ 200 Å/min, Al₂O₃ ≈ 5 Å/min → 40:1 selectivity
At 60°C: SiO₂ rate ≈ 600 Å/min, Al₂O₃ ≈ 20 Å/min → 30:1 selectivity
At 100°C: SiO₂ rate ≈ 1500 Å/min, Al₂O₃ ≈ 60 Å/min → 25:1 selectivity
```

**Process Consequence:** Higher temperature improves etch rate but reduces selectivity margin. This is why process windows exist: there's a "sweet spot" balancing rate, selectivity, and uniformity.

## Section 4.4: Etch Profile Evolution

### 4.4.1 Reaction Layer Model

As etch progresses, a **reactive layer** at the surface becomes the active etch front:

```
Time T=0 (Fresh oxide):
   Clean SiO₂ surface
   Reactivity: Maximum
   Etch rate: Maximum

Time T=1 min (Early etch):
   SiO₂-CFₓ polymer layer forms (5-20 nm)
   This layer etches SLOWER than bulk
   Etch rate: Decreasing

Time T=10 min (Steady state):
   Polymer layer reaches equilibrium thickness
   Layer etches at same rate as formation
   Steady-state polymer thickness: 10-50 nm
   Etch rate: Constant (steady state)

Time T=99.9% done (Near endpoint):
   Approaching underlying metal
   Metal surface begins to affect field
   Plasma properties change
   Etch rate: Changes (EPD signal)
```

### 4.4.2 Sidewall Chemistry During Aspect Ratio Etch

In high-aspect trenches, sidewalls etch differently from bottom:

```
Bottom of trench (feature interior):
- High local radical density
- High ion bombardment
- High etch rate
- Aggressive chemistry

Sidewalls (vertical surfaces):
- Lower radical arrival rate (diffusion limited)
- Lower ion energy to sidewalls (field geometry)
- Lower etch rate
- Profile develops anisotropy
```

**Profile Development:**

```
Early etch (T << T_complete):
┌─────┐  (approximately vertical)
│     │
│     │
│     │
└─────┘

Mid-etch (T ~ 0.5 × T_complete):
╱─────╲  (slight notching at top)
│     │  (slower sidewall etch creates profile)
│     │
╲─────╱

Late etch (T ~ 0.9 × T_complete):
╱─────╲
│     │  (notching is severe)
│     │  (sidewalls lag bottom)
│     │
└─────┘  (bottom reaches metal)
```

**This creates the "undercut" defect** if sidewall etch continues after bottom reaches metal. Selectivity becomes critical: metal must etch much slower than oxide to prevent undercut.

## Section 4.5: Surface Analytical Understanding

### 4.5.1 Reaction Mechanisms from X-Ray Photoelectron Spectroscopy (XPS)

XPS reveals the actual chemical species at the surface during etch:

```
Binding Energy (eV):
Si 2p: 103-105 eV (Si-O bonds)
Si 2p: 99-101 eV (Si-F bonds, shifted lower)
Si 2p: 95-97 eV (metallic Si, if breakthrough)

F 1s: 687-689 eV (Si-F bonds)

O 1s: 532-534 eV (Si-O bonds)
O 1s: 530-532 eV (Si-F-O intermediates)
```

**XPS Depth Profile During Etch:**

```
Surface (0-1 nm):     Si-F, C-F (polymer-rich)
Near-surface (1-5 nm): Mixed Si-O, Si-F (reaction layer)
Bulk (5+ nm):         Si-O (unreacted oxide)
```

**Interpretation:** The surface maintains Si-F richness due to continuous F-atom bombardment. The reaction layer thickness (~5-10 nm) represents the depth to which F-atoms penetrate and react before returning to bulk oxide.

### 4.5.2 Time-Resolved Surface Chemistry (Molecular Dynamics Insights)

Recent molecular dynamics (MD) simulations reveal the atomic-scale mechanism:

```
MD Simulation of Single F-Atom Impact on SiO₂:

1. F-atom approaches Si-O bond (separation ~ 2-3 Å)
   Time: 0 fs (femtoseconds)

2. F-atom trajectory bends toward bond (Coulomb attraction)
   Time: 50 fs

3. F-atom collides, breaking Si-O bond
   Time: 100 fs
   Result: Si-F + O-side species formed

4. Secondary F-atoms encounter newly exposed Si
   Time: 200-500 fs
   Result: Further F-incorporation

5. SiF₃/SiF₄ becomes mobile, desorbs
   Time: 1000 fs (1 picosecond)
```

**Activation Barriers from MD:**

- Si-O bond breaking in presence of F: Eₐ ≈ 0.8-1.0 eV (matches Arrhenius!)
- Si-F bond formation: Spontaneous (highly exothermic)
- SiF₄ desorption: Spontaneous at oxide etch temperatures

## Section 4.6: Practical Implications for Process Design

### 4.6.1 Recipe Window Determination

Given understanding of surface reactions, how do process engineers set recipe windows?

#### **Selectivity Margin Calculation:**

```
Safe Operating Window:
- Target selectivity: 30:1 (oxide/metal)
- Acceptable variation: ±20% due to drift
- Required minimum: 30:1 × (1 - 0.2) = 24:1

Example recipe:
- Pressure: 100 ± 10 mTorr (±10% tolerance)
- Temperature: 60 ± 2°C (±2°C; critical!)
- Power: 300 ± 20 W (±7% tolerance)
- Gas: CF₄/CHF₃ 1:1

Process margin: Can absorb these variations without losing selectivity
Process yield: >95% in-spec
```

#### **Temperature as Primary Control:**

```
Given temperature coefficient of 8-10%/°C:
±2°C precision → ±17-20% etch rate control

This allows:
- Feedback control of etch rate
- Recipe tuning for slight variations in wafer lot
- Thermal drift compensation
```

### 4.6.2 Endpoint Detection Strategy

Based on surface chemistry understanding:

```
F-atom arrival rate at surface ∝ OES signal intensity
As oxide thickness decreases → F-atom density (and OES) changes

When oxide completely removed:
- F-atoms reach Al₂O₃ surface
- Different reaction rate
- SiF₄ production drops dramatically
- OES intensity drops
- This is the "endpoint" signal
```

**Challenges:**
- Polymer layer can mask signal
- Need frequent NF₃ cleaning cycles (every 20-50 wafers)
- Signal-to-noise ratio becomes critical

## Section 4.7: Summary and Connection Forward

### Key Takeaways:

1. **F-atom surface reactions are thermodynamically driven** (ΔH < -100 kcal/mol) but kinetically controlled by F-atom arrival rate
2. **SiF₄ volatility is essential** — it's the most volatile etch product in semiconductor processing, enabling clean etch
3. **Ions assist etch** through physical sputtering and ion-enhanced chemistry, contributing 15-30% of total etch rate
4. **Selectivity emerges from Al₂O₃ slower etch**, not from SiO₂ selectivity to Al — it's a surface chemistry difference
5. **Temperature sensitivity** comes from F-atom reaction kinetics (activation energy ~1 eV) with additional effects from Al₂O₃ temperature dependence
6. **Polymer layer forms immediately** and reaches equilibrium; steady-state etch rate reflects this layer presence
7. **Undercut during metal etch** results from sidewall-to-bottom selectivity loss when oxide completely removed

### Forward References:

- **Chapter 5 (Electrode Thermal Systems):** Thermal management required due to high heat from F-atom reactions (exothermic)
- **Chapter 10 (Inverse ARDE):** Shows how F-atom depletion in trenches reduces etch rate at depth, causing inverse aspect ratio dependence
- **Chapter 12 (Selectivity Oxide-to-Metal):** Expands selectivity framework and quantifies margins for advanced nodes
- **Chapter 13 (Polymerization):** Detailed analysis of polymer layer formation and its effects on etch rate and uniformity
- **Chapter 14 (Temperature Control):** Explains thermal feedback control systems needed due to temperature-sensitive etch rate

---

**Next Chapter:** Chapter 5 transitions from surface chemistry to equipment engineering, focusing on thermal management systems required to maintain ±2°C precision during high-rate oxide etch.
