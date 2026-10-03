# Chapter 2: Silicon Dioxide Thermodynamics and Reaction Energetics

## Introduction: Why SiO₂ Thermodynamics Matter for Etch Process Design

Silicon dioxide (SiO₂) is simultaneously the most well-understood and most complex material in semiconductor manufacturing. Its thermodynamic properties determine:

1. **Etch Selectivity:** Why oxide etches 30x faster than aluminum at identical plasma conditions
2. **Temperature Sensitivity:** Why ±2°C precision is required in oxide etch vs. ±5°C for metal etch
3. **Process Windows:** Why certain pressure-temperature-power combinations yield stable etch while others fail catastrophically
4. **Reaction Pathways:** Which fluorine species (F⁰ radicals vs. F⁺ ions) dominate etch at various conditions

This chapter establishes the thermodynamic foundation. Subsequent chapters build process physics on top of this foundation.

### Why Thermodynamics, Not Just Kinetics?

A common misconception in fab engineering is that etch rate depends only on kinetics—reaction speed. In reality:

**Thermodynamics determines WHAT CAN HAPPEN**
- SiO₂ + 6HF → 2H₂O + SiF₄ (highly favorable, ΔG < 0)
- This reaction is thermodynamically favored at all practical process temperatures
- No amount of kinetic optimization can make an unfavored reaction occur

**Kinetics determines HOW FAST it happens**
- If thermodynamically favored but kinetically slow, reactions require:
  - Higher temperature (activate molecules)
  - Higher pressure (increase collision frequency)
  - Ion bombardment (provide energy directly)
  - Catalyst (lower activation energy)

For oxide etch, thermodynamics is NOT limiting—oxide + fluorine reactions are extremely favored. Instead, **kinetics IS limiting**: we must maximize F-atom generation and delivery to the wafer surface.

## Section 2.1: Silicon Dioxide Structure and Phases

### 2.1.1 Amorphous vs. Crystalline SiO₂

Most thermal oxide in semiconductor devices is **amorphous SiO₂** (a-SiO₂):

#### Amorphous SiO₂ Structure
- **Composition:** SiO₂ (silicon dioxide, fully oxidized silicon)
- **Bonding:** Si-O-Si linkages forming random 3D network
- **Coordination:** Each Si surrounded by 4 O atoms (tetrahedral)
- **Density:** 2.20-2.27 g/cm³ (varies with deposition method)
- **Porosity:** ~10-15% void fraction (affects etch rate slightly)

#### Key Advantage for Etch: Lack of Grain Boundaries
- Crystalline phases have grain boundaries → preferential etch sites → rough surfaces
- Amorphous structure → uniform etch rate → smooth surfaces after etch
- This is why plasma-grown oxides (thermally grown at <1100°C) are preferred over sputtered oxides

### 2.1.2 Crystalline Phases (At Process Irrelevant Temperatures, But Useful for Understanding)

SiO₂ exhibits multiple crystalline polymorphs at elevated temperature:

| Crystal Phase | Temperature Range | Crystal System | Density (g/cm³) | Significance |
|---------------|-------------------|-----------------|-----------------|--------------|
| Quartz (α) | <867°C | Trigonal | 2.648 | Most stable at room temp |
| Tridymite (β) | 867-1470°C | Orthorhombic | 2.265 | High-temp meta-stable |
| Cristobalite (γ) | >1470°C | Cubic | 2.27 | Highest temp phase |
| Stishovite | >40 kbar | Tetragonal | 2.8+ | Ultra-high pressure |

**Process Relevance:** None of these crystalline phases form during normal oxide etch (20-100°C, 1 atm). They're mentioned only to understand that SiO₂ **prefers amorphous structure** at process conditions.

### 2.1.3 Refractive Index and Optical Properties

**Importance for Process Monitoring:** Optical endpoint detection relies on refractive index changes

| Parameter | Value | Notes |
|-----------|-------|-------|
| Refractive Index (n) at 550 nm | 1.46 | Visible light (green) |
| Extinction Coefficient (k) | ~10⁻⁸ (negligible) | Minimal absorption |
| Band Gap Energy | 8.9 eV | Large → transparent to visible |
| Reflectance (at normal incidence, air-SiO₂) | ~4% | Low → requires careful OES calibration |

**Practical Implication:** Small changes in oxide thickness create measurable reflectance changes, enabling endpoint detection via ellipsometry or OES (Optical Emission Spectroscopy).

## Section 2.2: Native Oxide and Surface Chemistry

### 2.2.1 Native Oxide Formation on Silicon and Aluminum

One of the most important concepts in oxide etch is that SiO₂ **forms spontaneously** on silicon and aluminum surfaces exposed to air or water.

#### On Silicon Surfaces:
```
Si (bulk) → Si-OH (surface hydroxyl, first reaction)
        ↓
Si-O-Si network growth (linear propagation)
        ↓
Steady state: ~15-20 Å native oxide thickness
Formation rate: ~1-2 nm/minute in humid air
```

**Thermodynamic Driver:**
```
ΔG° (Si oxidation) ≈ -900 kJ/mol SiO₂ (at 298 K)

This is a HIGHLY favorable reaction—essentially irreversible under ambient conditions
```

#### On Aluminum Surfaces:
```
Al (bulk) → Al-O-H (rapid chemisorption of water/oxygen)
        ↓
Al₂O₃ formation (3-5 nm in minutes)
        ↓
Steady state: ~50-100 Å native aluminum oxide
Formation rate: Very rapid (milliseconds in moist air)
```

**Key Difference:** Aluminum oxide (Al₂O₃) is MORE stable thermodynamically than SiO₂. This creates a critical challenge for oxide etch selectivity: we must etch SiO₂ rapidly while protecting the underlying Al₂O₃ surface.

### 2.2.2 Kinetics of Native Oxide Growth (Deals-Grove Model)

The classic **Deals-Grove model** describes thermal oxidation kinetics:

```
dX/dt = B / (2X + C)

Where:
- X = oxide thickness
- B = parabolic rate constant (depends on temperature, orientation, pressure)
- C = linear rate constant
- t = time
```

**Physical Interpretation:**
- **Early stage (X small):** Linear growth (surface reaction limited)
- **Late stage (X large):** Parabolic growth (diffusion limited—O₂ must diffuse through existing oxide)
- **Practical consequence:** Oxide growth slows dramatically after ~100 nm

**Temperature Dependence (Arrhenius-type):**
```
B ∝ exp(-Eₐ/kT)

Activation energy for oxidation: Eₐ ≈ 1.2-1.5 eV

Example: Silicon oxidation rate at 1000°C is ~100x faster than at 700°C
```

**Relevance to Oxide Etch:** The same kinetic principles that govern oxidation (temperature-dependent diffusion and reaction) affect etch rate control. Temperature precision is critical because oxide etch rate exhibits similar exponential temperature dependence.

## Section 2.3: SiO₂ Film Quality and Etch Rate Variation

### 2.3.1 How Deposition Method Affects Etch Rate

Not all SiO₂ films etch at identical rates. Subtle differences in structure create **etch rate variations of 10-30%**:

| Deposition Method | Density (g/cm³) | Porosity | Water Content (ppm) | Etch Rate Relative to TEOS | Notes |
|------------------|-----------------|----------|---------------------|---------------------------|--------|
| Thermal Oxide (1000°C, dry O₂) | 2.27 | 0% | 0-10 ppm | 1.0× | Reference standard; highest quality |
| TEOS (Tetraethyl orthosilicate) | 2.18 | 2-3% | 50-200 ppm | 0.95-1.05× | Most common; well-controlled |
| Silane (SiH₄ + O₂ CVD) | 2.15 | 5-8% | 100-300 ppm | 1.1-1.3× | More porous; etches faster |
| Sputtered SiO₂ | 2.12 | 8-12% | 200-500 ppm | 1.3-1.6× | Least dense; highly variable |

**Physical Explanation:**
- **Water incorporation:** H₂O in amorphous SiO₂ weakens Si-O bonds → faster etch
- **Porosity:** More void volume → higher F-atom penetration → faster removal
- **Defect density:** Si dangling bonds at pores → higher etch rate

**Manufacturing Consequence:** Recipe must account for film type. A recipe optimized for TEOS oxide may over-etch (undercut metal) if applied to thermal oxide, or under-etch if applied to silane oxide.

### 2.3.2 Etch Rate vs. Oxide Age (Aging Effects)

SiO₂ films etch **slower if aged** at room temperature in humid air:

**Mechanism:**
```
Fresh TEOS oxide
  ↓ (exposure to humidity over hours/days)
Water diffusion into oxide network
  ↓
Formation of Si-OH and H-bonding networks
  ↓
More stable oxide structure
  ↓
Slower etch rate (~10-15% reduction after 24 hrs in humid air)
```

**Process Implication:** Oxide etch recipes should account for wafer storage time. Wafers stored for >1 week in humid environment will etch 10-20% slower than freshly processed wafers.

## Section 2.4: Thermodynamic Stability and Free Energy Analysis

### 2.4.1 SiO₂ Stability Against Fluorine Attack

The fundamental question: **Why does SiO₂ etch in fluorine plasma?**

The answer lies in **Gibbs Free Energy (ΔG)**—the driving force for chemical reactions:

#### Relevant Reactions:

**Reaction 1: SiO₂ + 4F· → SiF₄↑ + O²⁻**
```
ΔG° ≈ -850 kJ/mol at 298 K

This is HIGHLY favorable (ΔG << 0)
```

**Reaction 2: SiO₂ + 6HF(aq) → SiF₄↑ + 2H₂O**
```
ΔG° ≈ -320 kJ/mol at 298 K

Also highly favorable, though less so than F-atom reaction
```

**Reaction 3 (Unwanted): Al + 1.5 O₂ → Al₂O₃**
```
ΔG° ≈ -1600 kJ/mol at 298 K

MORE favorable than oxide etch! This is why pure Al is at risk during oxide etch
```

#### Interpretation:
- **ΔG < -100 kJ/mol:** Reaction proceeds essentially to completion
- **-100 < ΔG < 0:** Reaction proceeds but may reach equilibrium with significant products remaining
- **ΔG > 0:** Reaction does not proceed spontaneously

All oxide etch reactions of interest have ΔG << 0, meaning they are **thermodynamically unstoppable**. The etch process is limited only by **kinetics** (how fast reactants are supplied).

### 2.4.2 Temperature Dependence of ΔG (Van 't Hoff Analysis)

Free energy varies with temperature according to:

```
ΔG(T) = ΔH - TΔS

Where:
- ΔH = enthalpy (heat of reaction)
- ΔS = entropy (disorder increase)
- T = absolute temperature (K)
```

**For Oxide Etch Reaction:** SiO₂ + 4F· → SiF₄↑ + O²⁻

```
ΔH ≈ -1100 kJ/mol (large negative; reaction releases heat)
ΔS ≈ +50 J/(mol·K) (moderate positive; products are more disordered)

ΔG(298K) = -1100 - (298)(0.050) ≈ -1115 kJ/mol

ΔG(400K) = -1100 - (400)(0.050) ≈ -1120 kJ/mol

Conclusion: ΔG becomes MORE negative at higher temperature
           (Reaction is MORE favorable at elevated temperature)
```

**Process Consequence:** Higher temperature → thermodynamically stronger driving force for etch. This explains why etch rate increases with temperature, even at the modest rates observed in oxide etch (20-100°C).

## Section 2.5: Reaction Energetics and Activation Barriers

### 2.5.1 Activation Energy for Key Reactions

Although oxide + fluorine reactions are thermodynamically favorable, they don't proceed instantaneously. An **activation barrier** (Eₐ) must be overcome:

```
Reactants + Eₐ → Transition State → Products

The higher the barrier, the slower the reaction (at fixed temperature)
```

#### Activation Energies for Oxide Etch Reactions:

| Reaction | Eₐ (eV) | Eₐ (kJ/mol) | Process Control | Notes |
|----------|---------|------------|-----------------|--------|
| SiO₂ + F⁰ → products | 0.8-1.2 | 77-116 | Temperature | F-atom attack dominant |
| F-atom generation (RF dissociation) | 1.5-2.0 | 145-193 | RF power | Limits F-atom availability |
| Polymerization (C₂F₆ + radicals) | 0.3-0.5 | 29-48 | Temperature, Chemistry | Competes with etch |

### 2.5.2 Arrhenius Relationship: Etch Rate vs. Temperature

The **Arrhenius equation** quantifies rate dependence on temperature:

```
k(T) = A × exp(-Eₐ/RT)

Where:
- k(T) = reaction rate constant
- A = pre-exponential factor
- Eₐ = activation energy (eV or kJ/mol)
- R = gas constant (8.314 J/(mol·K))
- T = absolute temperature (K)
```

#### Practical Application:

For oxide etch with Eₐ ≈ 1.0 eV ≈ 96 kJ/mol:

**Temperature Coefficient (% change per °C):**
```
Coefficient = (1/ln(10)) × (Eₐ/RT²) × 100%

At T = 60°C (333 K):
Coefficient = (0.434) × (96,000 / (8.314 × 333²)) × 100%
           ≈ 8.5% per °C

At T = 100°C (373 K):
Coefficient ≈ 6.5% per °C

At T = 20°C (293 K):
Coefficient ≈ 10.2% per °C
```

**Real-World Consequence:**
```
If nominal etch rate at 60°C = 600 Å/min

Then:
- At 58°C (2°C lower):  600 × (1-0.085) ≈ 549 Å/min (-8.5%)
- At 62°C (2°C higher): 600 × (1+0.085) ≈ 651 Å/min (+8.5%)

±2°C temperature variation → ±8-10% etch rate variation
```

This is why **thermal control at ±2°C precision is non-negotiable** for advanced-node oxide etch.

## Section 2.6: SiO₂ Properties and Etch Rate Prediction

### 2.6.1 Optical and Thermal Properties Affecting Etch

#### Thermal Properties:

| Property | Value | Significance |
|----------|-------|--------------|
| Thermal Conductivity | 1.4 W/(m·K) at 25°C | Low → oxide is thermal insulator |
| | 0.8 W/(m·K) at 200°C | Decreases at elevated temperature |
| Specific Heat (Cp) | 750 J/(kg·K) | Moderate heat capacity |
| Linear CTE | 0.5 ppm/°C | Very low thermal expansion |
| Melting Point | ~1710°C | Far above any oxide etch condition |

**Process Implication:** Oxide's low thermal conductivity means:
- Heat generated during plasma etch (ion bombardment, chemistry) concentrates at wafer surface
- Wafer temperature rises above electrode temperature
- Active cooling required to maintain target temperature

#### Optical Properties (Critical for Endpoint Detection):

| Property | Value | Notes |
|----------|-------|--------|
| Refractive Index (n) @ 550nm | 1.460 | Green light; used in OES endpoint detection |
| Refractive Index (n) @ 632nm | 1.456 | Red light; used in ellipsometry |
| Extinction Coefficient (k) | ~10⁻⁸ | Essentially transparent; minimal absorption |
| Reflectance (n-Si interface) | ~30% | Significant change allows monitoring |

**Optical Advantage:** As oxide thickness decreases during etch, reflectance and OES signal change predictably, enabling **real-time thickness monitoring**.

## Summary and Connection to Subsequent Chapters

### Key Takeaways:

1. **Thermodynamics guarantees oxide etch is favorable** (ΔG << 0), but thermodynamics alone don't determine rate
2. **Kinetics is the limiting factor** — F-atom generation, transport, and surface reaction are all rate-limiting at different conditions
3. **Temperature sensitivity is extreme** (~8-10%/°C) due to activation energy of F-atom reactions
4. **Pressure-rate relationship is inverse** — higher pressure reduces F-atom availability
5. **Selectivity is thermodynamically limited** to ~30-50:1; cannot be improved further through chemistry alone
6. **Film quality matters** — water content, porosity, and deposition method affect etch rate by 10-30%

### How This Connects to Subsequent Chapters:

- **Chapter 3 (Fluorine Chemistry):** Explores F-atom generation mechanisms in plasma, quantifying rate constants and reaction pathways
- **Chapter 4 (Plasma-Oxide Reactions):** Details surface reaction mechanisms and how ions enhance etch beyond pure thermodynamic prediction
- **Chapter 5 (Thermal Systems):** Explains why ±2°C thermal control is mandatory, given 8-10%/°C temperature sensitivity
- **Chapter 10 (Inverse ARDE):** Shows how F-atom depletion at high density features creates inverse aspect ratio dependence
- **Chapter 14 (Temperature Control):** Develops feedback control systems to manage thermal sensitivity discovered here

---

**Next Chapter:** Chapter 3 explores fluorine chemistry and the mechanisms by which CF₄ and CHF₃ generate reactive F-atoms in the plasma
