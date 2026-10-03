# Chapter 13: Polymerization and Fluorocarbon Chemistry

## Introduction: The Silent Saboteur

Fluorocarbon polymer is the **"silent killer" of oxide etch process control**. Unlike inverse ARDE (Chapter 10), which manifests as obvious uniformity problems, or selectivity loss (Chapter 12), which shows up in yield data, polymer accumulation creeps silently through every metric:

- Reduces F-atom availability (decreases etch rate uniformly but hard to detect)
- Creates spatially varying deposits (worsens inverse ARDE)
- Blocks trench bottoms (starves deep features)
- Damages device performance (residual polymer in interconnect)
- Requires expensive chamber cleaning (NF₃ cycles, downtime)

**Central Question:** Where does polymer come from, how much deposits where, and how do we manage it?

From Chapter 11: ~15% of generated F-atoms go to polymer formation (not productive etch). This chapter explains that 15%, its consequences, and control strategies beyond NF₃ cleaning.

---

## Section 13.1: Fluorocarbon Formation Mechanisms

### 13.1.1 Gas-Phase Polymerization

**Where Polymer Originates:**

```
Fluorocarbon polymers form in the gas phase and on surfaces through
radical-radical coupling and ion-neutral reactions.

Primary Sources in CF₄ Plasma:

Reaction Chain 1: CF₃ Radical Coupling
CF₄ → CF₃ + F (electron-impact dissociation)
CF₃ + CF₃ → C₂F₆ (dimer formation)
C₂F₆ + CF₃ → C₃F₉ (trimer formation)
C₃F₉ + CF₃ → C₄F₁₂ (continuing growth)

Result: C_nF_(2n+2) oligomers forming in plasma

Reaction Chain 2: CF₂ Radical Coupling
CF₄ + e⁻ → CF₂ + F₂ (electron-impact decomposition)
CF₂ + CF₂ → C₂F₄ (ethylene-like dimer)
C₂F₄ + CF₂ → C₃F₆ (continuing growth)

Result: C_nF_(2n) oligomers forming in plasma

Reaction Chain 3: CFx Radical Addition
Multiple CF_x species (x=1,2,3) combine via free radical addition
→ Complex mixture of C_nF_m oligomers with variable stoichiometry

Key Point: Polymer formation requires INITIATION (creating first radical)
and PROPAGATION (adding monomer units). Both happen readily in plasma.
```

### 13.1.2 Surface Polymerization

**Polymer Grows on Surfaces Too:**

```
Once oligomers form in gas phase, they deposit on surfaces and react further:

Adsorption on Cold Surfaces:
- Oligomers are large molecules (C_nF_m, n=3-10)
- Thermal velocity at 400 K: ~200 m/s
- Surface sticking coefficient: γ_stick ≈ 0.3-0.8 (high!)
- Result: Most oligomers that hit a surface stick

Surface Polymerization on Wafer:

After adsorption:
CF₃(ads) + CF₃(ads) → C₂F₆(ads) (surface coupling)
C₂F₆(ads) + CF(ads) → C₃F₇(ads)
... continuing chain growth ...

Cross-Linking:

High-energy species (ions, energetic neutrals) can cause cross-linking:
(C_nF_m) + Ion → (C_nF_m)−•+ (cation radical)
(C_nF_m)−•+ + (C_pF_q) → [C_(n+p)F_(m+q)]* (cross-linked species)

Result: Densification of polymer film over time
Increasing hardness and resistance to subsequent processes

This is WHY polymer is so hard to remove!
(Not just physisorbed overlayer, but cross-linked network)
```

### 13.1.3 Polymer Composition

**What Is Fluorocarbon Polymer Actually Made Of?**

```
Laboratory Analysis (X-ray Photoelectron Spectroscopy + Mass Spec):

Typical Oxide Etch Polymer Composition:

Element Content:
- Carbon: 30-40 at% (forms backbone)
- Fluorine: 50-65 at% (saturates C bonds)
- Oxygen: 2-5 at% (from air exposure + oxide etch products)
- Hydrogen: 1-3 at% (if using CHF₃, introduces H)

Stoichiometry Average:
- Pure CF₄ etch: Polymer ≈ CF₁.₈ (fluorine-deficient compared to CF₄!)
- CF₄/CHF₃ mix: Polymer ≈ CF₁.₆H₀.₃ (more carbon-rich, H-substituted)

Molecular Structure (Estimated from IR Spectroscopy):

- C-F bonds: ~70-80% of total C bonds
- C-C bonds: ~15-25% (backbone, cross-links)
- C=C bonds: ~5-10% (some unsaturation, makes it harder)
- C-H bonds: ~1-5% (if H present from CHF₃)
- O-C bonds: ~1-3% (from oxide surface reactions)

Physical Properties:

Density: ~2.0-2.2 g/cm³ (between SiO₂ 2.2 and SiC 3.2)
Refractive index: n ≈ 1.4-1.5 (similar to SiO₂!)
Hardness: HV ≈ 400-600 (soft, like SiO₂, not like diamond ~7000)
Etch resistance: Very high in F-rich atmosphere (stable C-F bonds)
                 Lower in O-rich atmosphere (C-F bonds break)

Key Insight: Fluorocarbon polymer is NOT protective coating like photoresist
It's a modified surface layer that continues to participate in reactions
```

---

## Section 13.2: Deposition Rates and Spatial Patterns

### 13.2.1 Polymer Deposition Rate Measurement

**How Fast Does Polymer Accumulate?**

```
Experimental Method (Quartz Crystal Microbalance):

Setup:
- Quartz crystal resonator in chamber (measures mass change)
- Frequency shift proportional to deposited mass
- Calibrated to give deposition rate in nm/min

Measurements at Baseline Conditions (60°C, 100 mTorr, 300W):

Open Area (unmasked SiO₂):
- Polymer deposition rate: ~0.1-0.5 nm/min
- Mostly gas-phase deposited oligomers
- Competition with etch: SiO₂ etch 200 nm/min >> polymer 0.3 nm/min
- Net effect: Net consumption (etch wins!)

Trench Bottom (narrow confinement):
- Polymer deposition rate: ~5-10 nm/min (20-100× higher!)
- Why? Cooler location (thermal gradient)
- Ions don't reach (geometry shielding from Chapter 10)
- F-atoms consumed before reaching bottom (Chapter 11)
- Result: Polymer accumulates faster than etch proceeds

Sidewalls (partial confinement):
- Polymer deposition rate: ~2-3 nm/min
- Intermediate between open and trench bottom
- Some ion and F-atom access

Chamber Wall (far from wafer):
- Polymer deposition rate: ~10-20 nm/min
- Coldest location after pump-out
- Polymer very stable here
- Requires NF₃ cleaning to remove (Chapter 8)
```

### 13.2.2 The Spatial Gradient Problem

**Why Does Polymer Accumulate Preferentially in Trenches?**

```
Temperature Gradient (Primary Driver):

Wafer surface (heated electrode): T_wafer ≈ 60°C
Trench bottom (200 nm deep): T_bottom ≈ 50-55°C (cooler!)
Chamber wall (ambient): T_wall ≈ 25-30°C

Why cooler places accumulate more polymer:

Vapor Pressure of Oligomers:

P_vap(T) = P_ref × exp(-ΔH_vap / RT)

At 60°C: P_vap ~ 100 mTorr (oligomers mostly evaporate/dissociate)
At 50°C: P_vap ~ 80 mTorr (some stick)
At 30°C: P_vap ~ 20 mTorr (most stick)

Sticking Probability:

γ_stick(T) = γ_0 × exp(-T / T_ref)

At 60°C: γ_stick ≈ 0.2 (low)
At 50°C: γ_stick ≈ 0.4 (moderate)
At 30°C: γ_stick ≈ 0.8 (high)

Result: Deposition Rate ∝ n_oligomer × γ_stick × (1 - etch_rate_correction)

At trench bottom:
- n_oligomer: High (confined geometry, slower evacuation)
- γ_stick: High (cooler temperature)
- etch_rate: Low (F-atom depletion from Chapter 11)
- Net: Maximum polymer accumulation!

Quantitative:
- Wafer (60°C): 0.2 nm/min polymer net (etch dominates)
- Trench sidewall (55°C): 2 nm/min polymer
- Trench bottom (50°C): 8 nm/min polymer

Over 60-second etch:
- Wafer surface: 12 nm polymer formed + 12,000 nm etched = net etch
- Trench bottom: 480 nm polymer formed + 2,000 nm etched = net etch
                 BUT polymer blocks further etch!
```

### 13.2.3 Polymer Buildup Over Time

**How Process Changes as Polymer Accumulates:**

```
Time Evolution in Single Etch Step:

Time = 0 sec (Fresh Chamber):
- No polymer yet
- Maximum F-atom supply to trenches
- ARDE Index: 35%
- Etch rate (deep): 90 nm/min

Time = 20 sec:
- Polymer thickness: ~100 nm in deep trenches
- F-atom path blocked partially
- Etch rate (deep): Drops to 75 nm/min (-17%)
- ARDE Index: 42% (worsening!)

Time = 40 sec:
- Polymer thickness: ~250 nm in deep trenches
- Significant blockage
- Etch rate (deep): Drops to 45 nm/min (-50%!)
- ARDE Index: 55% (severe!)
- Deep features falling significantly behind shallow

Time = 60 sec:
- Polymer thickness: ~400 nm in deep trenches
- Nearly complete blockage
- Etch rate (deep): Drops to 15 nm/min (-83%!)
- ARDE Index: 80% (catastrophic!)
- Shallow features etched 1.5× deeper than deep features

The Process Deteriorates Over the Single Etch Cycle!

This is why pulsed etch (Chapter 10) helps so much:
OFF periods allow polymer to decompose slightly,
recovery of F-atom access to bottom of trenches
```

---

## Section 13.3: Polymer Effects on Process Performance

### 13.3.1 Etch Rate Degradation

**How Much Does Polymer Reduce Etch Rate?**

```
Mechanism 1: F-Atom Depletion (From Chapter 11)

Polymer-coated surface has higher reaction rate constant k_surf
Result: F-atoms consumed at polymer surface before reaching SiO₂
→ Effective F-atom supply to oxide reduced

Quantification:
- Fresh oxide: Available F-atoms = n_F,bulk
- With polymer: Available F-atoms = n_F,bulk × (1 - f_blocked)
  where f_blocked ≈ 20-50% (fraction blocked by polymer)

Etch rate reduction: ΔR / R ≈ -25% to -35% per wafer lot after cleaning

Mechanism 2: Surface Passivation

Polymer can form stable fluorocarbon layers that resist further etch:

F + SiO₂ → (reacts, contributes to etch)
F + C_nF_m → (reacts, forms new polymer, consumes F but no etch!)

As polymer builds up, more F-atoms go to polymer growth than to oxide etch
Result: Effective etch rate reduction

Mechanism 3: Ion Access Reduction

Polymer can partially block ion access to underlying oxide
Fewer ions → Reduced ion-assisted etch component
→ 10-15% additional rate reduction

Total Etch Rate Reduction (After 20 Wafers):

Fresh chamber: r_etch = 200 nm/min
After 5 wafers: r_etch = 190 nm/min (-5%)
After 10 wafers: r_etch = 175 nm/min (-12%)
After 15 wafers: r_etch = 160 nm/min (-20%)
After 20 wafers: r_etch = 145 nm/min (-27%)
After 25 wafers: MUST CLEAN! r_etch would drop below 120 nm/min

This dictates NF₃ cleaning frequency: Every 20-25 wafers (Chapter 8)
```

### 13.3.2 Selectivity Impact

**How Does Polymer Affect Oxide-to-Metal Selectivity?**

```
Polymer reduces F-atom availability globally (Chapter 11 effect)
This affects BOTH oxide and metal etch rates:

Fresh Oxide Etch (No Polymer):
r_SiO₂ = 200 nm/min
r_Al₂O₃ = 6.7 nm/min
S = 200 / 6.7 = 30:1

After Polymer Buildup (20% F-atom reduction):
r_SiO₂ = 200 × (1 - 0.20) = 160 nm/min
r_Al₂O₃ = 6.7 × (1 - 0.20) = 5.4 nm/min
S = 160 / 5.4 = 29.6:1

Selectivity UNCHANGED! (Polymer affects both equally)

But Al erosion during etch INCREASES because of longer process time:

Fresh chamber: Etch 200 nm SiO₂ in 60 sec → Al eroded: 2 nm
After polymer: Etch 200 nm SiO₂ in 72 sec (+20% longer) → Al eroded: 2.4 nm (+20%)

This is the REAL selectivity impact:
Polymer doesn't change selectivity ratio, but extends etch time
→ More over-etch → More Al damage

Process margin at end of chamber life: NARROWER than at start!
```

### 13.3.3 Uniformity and ARDE Degradation

**Polymer Worsens Inverse ARDE:**

```
From Section 13.2.3, ARDE Index worsens over time:

Fresh chamber (after NF₃ clean): ARDE Index = 35%
Mid-chamber (12 wafers): ARDE Index = 50%
End-of-chamber (24 wafers): ARDE Index = 65%

Why? Polymer accumulates preferentially in high-AR trenches
→ Deep features increasingly blocked
→ Deep features fall behind shallow features
→ ARDE Index increases

This means: Uniformity DEGRADES over chamber lifetime

Impact on Yield:

Start of chamber: CD variation on wafer: ±2 nm
Mid-chamber: CD variation: ±4 nm (due to ARDE increase)
End of chamber: CD variation: ±6 nm (severe!)

Device Impact:
- Timing margins compress over chamber life
- Yield drift downward as chamber ages
- Forced to clean more frequently to maintain yield spec
```

---

## Section 13.4: Polymer Control Strategies

### 13.4.1 Strategy 1: Temperature Increase

**Higher Wafer Temperature → Less Polymer**

```
Temperature Effect on Polymer Deposition:

Polymer deposition rate: r_poly ∝ P_vap(T) × γ_stick(T)

At 50°C: r_poly = 1.0 (baseline)
At 60°C: r_poly ≈ 0.4 (60% reduction!)
At 70°C: r_poly ≈ 0.15 (85% reduction!!)
At 80°C: r_poly ≈ 0.05 (95% reduction!!!)

Mechanism: Higher temperature increases vapor pressure
→ Oligomers evaporate instead of depositing
→ Sticking probability decreases exponentially

Trade-offs:
- Benefit: Polymer buildup reduced, longer chamber life
- Cost: Etch rate slightly reduced (200→180 nm/min)
- Cost: Selectivity reduced 30:1 → 23:1 (Chapter 12 activation energy effect)
- Net: Usually worth it for advanced nodes (manage selectivity separately)

Practical Approach:
- Conservative fab: Keep T = 60°C (baseline)
- Aggressive fab (advanced nodes): T = 70-75°C (trade selectivity for polymer control)
- Very aggressive (5nm+): T = 75-80°C with CHF₃-rich gas (manage both)
```

### 13.4.2 Strategy 2: O₂ Additive

**Oxygen Passivates Polymer Growth:**

```
How O₂ Works:

When small amounts of O₂ added to CF₄/CHF₃ mixture (~0.5-2%):

O⁻ radicals and ions generated in plasma:
CF₄ + e⁻ → CF₃ + F⁻
O₂ + e⁻ → O⁻ + e⁻ (or fragmented)

O-radicals attack fluorocarbon oligomers:

C_nF_m + O → C_nF_(m-1)O + F (oxidative fragmentation!)

Result: Oligomers broken apart instead of polymerizing
Polymer deposition rate reduced 50-70%

Example:
Pure CF₄: r_poly = 8 nm/min in deep trench
CF₄ + 1% O₂: r_poly = 2-3 nm/min (70% reduction!)

Trade-offs:
- Benefit: Dramatically reduced polymer accumulation
- Benefit: Chamber lifetime extended 2-3×
- Cost: O-atoms also attack SiO₂ surface slightly
  → Etch rate reduced ~10%
  → Selectivity REDUCED (O helps Al₂O₃ too!)
  → S: 30:1 → 25:1

Use Case: O₂ addition good for maintaining chamber life on 7-14nm nodes
Not recommended for 5nm and below (selectivity margin too tight)
```

### 13.4.3 Strategy 3: Pulsed Etch Waveform

**OFF Periods Allow Polymer Decomposition:**

```
From Chapter 10, pulsed etch structure:

Power ON (20 ms):
- Plasma active, etch proceeds
- Oligomers form and deposit
- Polymer: +0.5 nm accumulated

Power OFF (20 ms):
- Plasma quenches, deposition stops
- Temperature maintained (electrode has thermal mass)
- Oligomers still present but not depositing
- Polymer decomposition begins:
  
  C_nF_m → C_(n-1)F_m + CF (partial fragmentation)
  
  Decomposition rate: ~0.2 nm in 20 ms
- Net during OFF: -0.2 nm polymer (slight removal!)

Cycle Result (40 ms total):
Continuous 40 ms: +1.0 nm polymer
Pulsed 40 ms: +0.3 nm net polymer (70% reduction!)

Cumulative Effect (60-second etch):

Continuous etch, 60 sec:
- Polymer accumulation: 400 nm (severe blockage)
- ARDE degrades significantly
- Deep features etched much slower

Pulsed etch, 60 sec (50% duty cycle):
- Polymer accumulation: 120 nm (3× less!)
- ARDE remains stable
- Deep features stay relatively uniform with shallow

This is CRITICAL reason why pulsed etch is standard on advanced nodes
```

### 13.4.4 Strategy 4: Multi-Step Etch Sequences

**Different Recipe for Different Stages:**

```
Single-Step Traditional Etch (risky):
Step 1 (0-60 sec): CF₄/CHF₃ 80:20, T=60°C, 300W
- Result: Rapid polymer buildup, ARDE degrades, uniformity suffers

Advanced Multi-Step Approach:

Step 1 - Bulk Etch (0-30 sec):
- Recipe: CF₄:CHF₃ 90:10, T=60°C, 350W
- Purpose: Fast etch of thick oxide, get majority depth quickly
- Polymer: Moderate (only 30 sec)
- Etch depth: ~150 nm

Step 2 - Uniform Etch (30-50 sec):
- Recipe: CF₄:CHF₃ 50:50, T=70°C, 250W, PULSED
- Purpose: Finishing etch, uniform deep and shallow
- Polymer: Minimal (pulsed + higher T)
- Etch depth: ~50 nm (additional)

Step 3 - Fine Etch (50-60 sec):
- Recipe: CHF₃ 100%, T=60°C, 150W, PULSED
- Purpose: Final depth control, stop on barrier
- Polymer: Negligible (high T, pure CHF₃)
- Etch depth: ~10 nm (additional)

Total: 210 nm etched with excellent uniformity
Polymer at end: ~100 nm (vs 400 nm in single-step)

Cost: 60 sec recipe vs. 60 sec continuous (same time!)
Benefit: 
- Better uniformity (ARDE 35% → 25%)
- Lower polymer burden (less frequent cleaning needed)
- Better selectivity control (Step 2 compensates for ARDE)
```

---

## Section 13.5: Advanced Polymer Management

### 13.5.1 In-Situ Polymer Monitoring

**Detecting Polymer Buildup in Real-Time:**

```
Challenge: How do you know polymer is accumulating if you can't see inside chamber?

Approach 1: Optical Emission Spectroscopy

Plasma emits specific wavelengths for different species:
- CF₃ radical: 290 nm (strong line, indicates fresh gas)
- C₂F₃ dimer: 420 nm (weak, indicates oligomer formation)
- F atom: 702 nm (indicator of F-atom availability)

As polymer builds up:
- Oligomer concentration ↑ (420 nm intensity increases)
- F-atom concentration ↓ (702 nm intensity decreases)
- Trend: Increasing 420 nm / decreasing 702 nm = time to clean

Advantages:
- Non-invasive optical measurement
- Real-time feedback
- Can trigger automatic NF₃ clean cycle

Disadvantages:
- Requires expensive spectrometer ($30-50k)
- Calibration needed to correlate spectrum to actual polymer thickness
- Limited production deployment (still emerging tech)

Approach 2: Impedance Monitoring

RF matching network impedance changes as polymer deposits:
- Fresh chamber: Z ≈ 10 Ω (stable)
- With polymer buildup: Z drifts (polymer is dielectric)

Monitoring Z drift:
- Normal drift: < 1 Ω per wafer
- Excessive drift: > 2 Ω per wafer → Indicates heavy polymer
- Trigger: Z drift > 3 Ω → Recommend NF₃ clean

Advantages:
- Uses existing RF matching network (no extra cost)
- Already monitored on most production tools

Disadvantages:
- Less direct signal (affected by other factors too)
- Coarse indicator, not precise thickness measurement
```

### 13.5.2 Automated Chamber Management

**Future: Self-Regulating Chambers**

```
Emerging Concept: Adaptive Gas Chemistry

System Components:
- Real-time polymer monitoring (optical or impedance)
- Feedback controller with multi-line gas system
- Pulsing frequency dynamically adjusted
- NF₃ clean automatically triggered

Operation Example:

Wafer 1-10: Standard recipe
- Polymer accumulating normally
- Optical signal increasing ~5% per wafer

Wafer 11-15: Recipe adjusts automatically
- System detects polymer trend
- Switches to O₂-added recipe (-1% O₂)
- Pulsing frequency increases 5% (longer OFF periods)
- Polymer accumulation slowed

Wafer 16-20: Further adjustment
- Switches to higher temperature (+3°C)
- Maintains etch rate with adjusted power
- Polymer accumulation further reduced

Wafer 21: NF₃ Clean Triggered
- System predicts polymer will exceed safe limit by wafer 25
- Triggers automatic NF₃ sequence
- Chamber cleaned, baseline reset

Benefit: Extends chamber life 30-50% through optimization
Cost: $50-100k investment in additional control systems
Timeline: Likely standard on 3-5nm nodes within 5 years

Current Status: IMEC and leading tool makers testing
Production deployment: Starting 2027-2028
```

---

## Section 13.6: Polymer Residue After Etch

### 13.6.1 Device Impact of Residual Polymer

**When Polymer Is Left on Wafer:**

```
In perfect world: All polymer removed before device use

In reality: Residual polymer sometimes remains

Causes of Residual Polymer:
1. Incomplete NF₃ cleaning (2-5% residue always remains)
2. Polymer in deep features survives cleaning better
3. Low-energy tail of etch damage spectrum leaves trace fluorocarbon
4. Ash/descum step (if needed) uses energetic process that can redeposit polymer

Typical Residue:

After standard NF₃ clean: 1-3 nm residual fluorocarbon on wafer
After aggressive clean: <0.5 nm residual
On device features: 5-20 nm residual (in deep trenches, hard to access)

Device Consequences:

Electrical:
- Residual fluorocarbon is insulator (high resistivity)
- Creates parasitic capacitance in interconnect
- Can increase RC delay: Δt ≈ +0.5-2% (depends on residue thickness)

Mechanical:
- Fluorocarbon is soft (density ~2.0 g/cm³)
- Can cause via fill problems (via material doesn't flow into polymer-filled voids)
- May cause incomplete metal deposition in fine features

Thermal:
- Fluorocarbon has low thermal conductivity
- In extreme case (thick residue), can limit heat dissipation
- Impact: Minimal for most devices, critical for high-power circuits

Yield Impact:
- Residue <1 nm: No yield impact
- Residue 1-5 nm: Can cause <1% yield loss (timing skew, via fill)
- Residue 5-20 nm: Can cause 5-15% yield loss
- Residue >20 nm: Major defect, likely device failure

Modern fabs manage this through:
- Automatic ash step after oxide etch to remove residue
- Precleaning step on cluster tool
- Tight control of NF₃ clean chemistry and endpoint
```

### 13.6.2 Prevention Strategies

**How to Minimize Residual Polymer:**

```
Strategy 1: In-Situ Stripping (During Etch)

Concept: Use two-gas mode during final moments of etch

Final 20 sec of 60-sec recipe:
- Regular recipe (CF₄:CHF₃) for first 40 sec
- Switch to O₂ + Ar mode for last 20 sec
  (O₂ removes polymer, Ar provides ion sputtering)

Effect:
- SiO₂ etch continues (O₂ doesn't stop etch completely)
- Polymer on wafer surface oxidized and sputtered away
- Residue reduced from 3 nm → 0.5 nm

Trade-off: Selectivity slightly worse during final stage (O₂ helps Al)
Solution: Reduce final power (150W instead of 300W) to maintain selectivity

Strategy 2: Post-Etch Ash Step

Immediately after oxide etch, while wafer still in chamber:

Option A - O₂ Plasma Ash:
- Switch to pure O₂ plasma (no etching gas)
- O-radicals oxidize fluorocarbon → CO₂, CO (volatile products)
- 30-60 sec ash removes residual polymer

Option B - Ar+ Ion Sputtering:
- Switch to Ar plasma, bias substrate
- Ar ions sputter polymer from surface
- Gentler than O₂ (doesn't damage underlying oxide)

Current Practice: Most production tools do O₂ ash (5-10 sec, low power)

Strategy 3: Cluster Tool Precleaning

On cluster tools (Chapter 15), use dedicated cleaning chamber:

Between etch chamber and next process:
1. Strip chamber cleans any residual polymer
2. Precook chamber at high temperature (~200°C, brief)
3. Optional UV treatment to cross-link any remaining polymer

Effect: Residue on wafer reduced to <0.1 nm (negligible)

Current Status: Standard on advanced node cluster tools
Advanced nodes: Some fabs adding dedicated precleaning chambers
Timeline: Becoming standard for 5nm and below
```

---

## Section 13.7: Polymer Chemistry Advanced Topics

### 13.7.1 Compositional Evolution

**How Polymer Composition Changes During Chamber Life:**

```
Fresh Chamber (Wafer 1):
- Composition: CF₁.₈ (fluorine-poor due to partial dissociation)
- Cross-linking: Minimal (linear chains)
- Density: ~1.9 g/cm³
- Etch resistance: Moderate

Mid-Chamber (Wafer 15):
- Composition: CF₁.₅ (more carbon-rich as F consumed by etch)
- Cross-linking: Increasing (some 3D network forming)
- Density: ~2.0 g/cm³
- Etch resistance: Higher (more cross-linked)

End-of-Chamber (Wafer 25):
- Composition: CF₁.₂ (mostly carbon, highly fluorine-depleted)
- Cross-linking: Extensive (3D network, hard polymer)
- Density: ~2.1 g/cm³
- Etch resistance: Very high (resistant even to NF₃)

This is WHY old polymer is harder to clean than fresh polymer!
(Over-cross-linked, more stable network, fewer fluorine removal sites)

Solution: More aggressive NF₃ cleaning at chamber end-of-life
(Higher temperature, longer soak, may require 90+ min vs. 60 min baseline)
```

### 13.7.2 Polymer and Selectivity Interactions

**How Polymer Affects Selectivity Control:**

```
Paradox from Chapter 12: Polymer reduces F-atom availability equally
to SiO₂ and Al₂O₃, so selectivity ratio unchanged.

But deeper interaction exists:

Polymer Preferentially Protects Al₂O₃!

Why? Al₂O₃ surface is naturally more reactive with polymer:
- Al₂O₃ lacks C (more hydrophilic reactive surface)
- Fluorocarbon deposits more readily on Al₂O₃ than SiO₂
- Polymer layer on Al₂O₃: Thicker and more protective

Example:
- Wafer surface (SiO₂): 2 nm polymer residue
- Metal area (Al₂O₃ native oxide): 5 nm polymer residue

If polymer blocks both equally:
- SiO₂ etch rate reduced: 200 → 160 nm/min (-20%)
- Al₂O₃ etch rate reduced: 6.7 → 5.4 nm/min (-20%)
- Selectivity: 160/5.4 = 29.6:1 (unchanged from 200/6.7 = 30:1)

But if polymer on Al₂O₃ is thicker → blocks more:
- SiO₂ etch rate reduced: 200 → 160 nm/min (-20%)
- Al₂O₃ etch rate reduced: 6.7 → 3.0 nm/min (-55%!)
- Selectivity: 160/3.0 = 53:1 (IMPROVED from 30:1!)

Implication: Old chambers (more polymer) have BETTER selectivity!

Production Consequence:
- Early in chamber life: Selectivity = 30:1 (tight!)
- End of chamber life: Selectivity = 40:1 (comfortable!)
- But: ARDE gets worse! (Polymer blocks deep features more)

This is another manifestation of the fundamental conflict:
Polymer helps selectivity but hurts uniformity!
```

---

## Section 13.8: Summary and Connection Forward

**Key Takeaways:**

1. **Polymer is inevitable** — 15% of F-atoms go to polymer in every CF₄/CHF₃ process
2. **Accumulation is spatially non-uniform** — trenches get 20-100× more polymer than open areas
3. **Polymer worsens inverse ARDE** — preferentially blocks deep features
4. **Temperature is the simplest control** — 10°C increase reduces polymer 75%
5. **Pulsed etch is critical** — OFF periods allow polymer decomposition
6. **Multi-step recipes** — optimize each stage for different needs (bulk, uniform, fine)
7. **Chamber lifetime limited by polymer** — forces NF₃ cleaning every 20-25 wafers
8. **Residual polymer can impact yield** — in-situ stripping or post-etch ash required
9. **Polymer composition evolves** — becomes harder, more cross-linked over time
10. **Polymer paradox** — improves selectivity but worsens uniformity

**Why Polymer Management Is Critical:**

- Most labs spend 15-20% of chamber time on NF₃ cleaning (downtime cost)
- Polymer buildup forces frequent recipe adjustments to maintain uniformity
- Residual polymer on device can cause timing skew and via fill problems
- Advanced nodes at technology limits can't afford either option:
  - Can't accept polymer-induced ARDE drift (uniformity margins too tight)
  - Can't accept O₂ additives (selectivity margins too tight)
  - Must use complex multi-step recipes or pulsed etch

**Forward References:**

- **Chapter 14 (Temperature Control):** Temperature control directly impacts polymer — optimization required
- **Chapter 15 (Cluster Integration):** Multi-chamber clusters use thermal and chemical management to reduce polymer burden
- **Chapter 16 (Endpoint & Yield):** Endpoint detection with polymer compensation strategies

---

**POLYMER: THE SECONDARY CHALLENGE**

Oxide etch has two fundamental challenges: ARDE (primary) and Polymer (secondary). ARDE is fixed by plasma physics and geometry. Polymer can be managed but never eliminated. Advanced process engineering focuses on optimizing both simultaneously through temperature control, pulsing, gas chemistry, and multi-step sequences. As technology scales to 3nm and below, managing this polymer-ARDE-selectivity triangle becomes the central constraint on production feasibility.
