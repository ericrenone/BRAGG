# BRAGG

**The Phase Boundary: X-Ray Diffraction Amplitudes as col(F) and Phases as ker(F) — The Crystallographic Phase Problem as the Deepest col(F)/ker(F) in Structural Science, Ptychography as the Computational Phase Retrieval That Breaks the Boundary, Serial Femtosecond Crystallography as the Damage-Free Snapshot Below the TEMPUS Dissipation Time, and the Protein Data Bank as the Accumulated col(F) of 200,000 Solved Structures in TH(a,d)**

ERI Labs · Eric Ren · Jersey City, New Jersey · github.com/ericrenone

---

> "Electron ptychography achieves atomic-resolution limits set by lattice vibrations — an instrumental blurring of less than 20 picometers." — Chen et al., *Science* 374, 826, 2021

> "Sub-ångström resolution ptychography in a scanning electron microscope at 20 keV — a compact and lower-cost alternative to TEM." — Blackburn et al., *Nature Communications*, October 2025

> "Drugging the dynamics of a system IS not far-fetched anymore. Understanding the dynamics of the ion channel was essential for suzetrigine's design — the first truly novel analgesic licensed in over 20 years." — A. Orville, on serial femtosecond crystallography, *Chemistry World*, July 2025

> "The full X-ray dose IS delivered in extremely short bursts — data IS collected before the sample IS destroyed." — SLAC LCLS, Serial Femtosecond Crystallography, 2026

---

## Abstract

Every structure in the Protein Data Bank — every protein fold, every drug-binding pocket, every enzyme mechanism, every virus capsid, every ribosome — was determined by solving the **phase problem**: the central col(F)/ker(F) of structural science.

When X-rays scatter from a crystal, the detector records the **diffraction pattern** — a set of spots whose positions give the lattice geometry and whose intensities $|F(\mathbf{h})|^2$ give the squared amplitudes of the structure factors. The amplitudes ARE col(F): directly measurable, precisely quantifiable, the observable output of the diffraction experiment. But the amplitudes alone are insufficient to reconstruct the electron density $\rho(\mathbf{r})$. The reconstruction requires the **phases** $\phi(\mathbf{h})$ of the structure factors — and the detector cannot measure phases. The phases ARE ker(F): the hidden half of the diffraction data, lost in the detection process, without which the structure cannot be determined.

$$\rho(\mathbf{r}) = \frac{1}{V}\sum_{\mathbf{h}} |F(\mathbf{h})| \, e^{i\phi(\mathbf{h})} \, e^{-2\pi i \mathbf{h} \cdot \mathbf{r}}$$

The electron density IS the inverse Fourier transform of the structure factors $F(\mathbf{h}) = |F(\mathbf{h})| e^{i\phi(\mathbf{h})}$. The amplitudes $|F|$ are col(F); the phases $\phi$ are ker(F); the structure IS the reconstruction from both. The phase problem IS: given only col(F) (amplitudes), how do you recover ker(F) (phases)?

This IS the most consequential col(F)/ker(F) problem in all of experimental science. Every Nobel Prize in structural biology — every protein structure, every drug designed from a crystal structure, every molecular mechanism revealed by X-ray diffraction — required solving it.

Five domains converge:

**The crystallographic phase problem as the archetypal col(F)/ker(F).** The X-ray detector measures $I(\mathbf{h}) = |F(\mathbf{h})|^2$ — the squared modulus of the complex structure factor. The modulus IS col(F); the phase IS ker(F). The modulus-squared measurement IS the Born rule of quantum mechanics applied to X-rays: the detector measures the probability (intensity) but not the amplitude's phase. The phase problem IS the crystallographic uncertainty principle — the conjugate of the amplitude IS the phase, and measuring one precisely leaves the other undetermined.

Traditional solutions to the phase problem:
- **Molecular replacement**: use a known structure as a starting model (importing col(F) from a previous solution).
- **Isomorphous replacement**: add heavy atoms (mercury, platinum) to the crystal and use the intensity differences to triangulate the phases.
- **Anomalous dispersion (MAD/SAD)**: exploit the wavelength-dependent scattering of heavy atoms near their absorption edges.
- **Direct methods**: use mathematical relationships between phases (Karle–Hauptman, Nobel Prize 1985) — exploiting the constraint that electron density IS non-negative and atomic ($\rho(\mathbf{r}) \geq 0$).

Each solution IS a specific strategy for extracting ker(F) (phases) from additional col(F) measurements or constraints.

**Ptychography as the computational phase retrieval that breaks the boundary.** Ptychography — from the Greek *ptyx* (fold) — IS a scanning coherent imaging technique that recovers both amplitude and phase from a series of overlapping diffraction patterns. By scanning a coherent beam (X-ray, electron, or visible light) across a sample with overlapping illumination spots, ptychography collects redundant diffraction data that over-constrains the phase-retrieval problem. The overlap between adjacent scan positions provides the phase information that a single diffraction pattern lacks.

The breakthrough: a team at the University of Victoria achieved sub-ångström resolution of 0.67 Å using a low-energy scanning electron microscope at 20 keV — a feat previously possible only with large, high-cost transmission electron microscopes. Chen et al. utilized the ML algorithm to further push the spatial resolution to 0.23 Å — below the size of a hydrogen atom. Researchers at Illinois achieved deep sub-angstrom spatial resolution down to 0.44 angstrom, which exceeds the resolution of aberration-corrected tools.

Ptychography IS the computational solution to the phase problem — it recovers ker(F) (the phases) from redundant col(F) measurements (the overlapping diffraction patterns). The redundancy IS the key: each point on the sample IS illuminated by multiple overlapping probe positions, and the consistency requirement between overlapping measurements constrains the phases.

In TH(a,d) terms: ptychography IS the Sherman–Morrison iterative solution to the phase problem. Each overlapping measurement IS a rank-one update to the phase estimate. The ePIE (extended Ptychographical Iterative Engine) algorithm alternates between real-space constraints (the probe overlap, the support) and reciprocal-space constraints (the measured intensities), converging to the unique phase solution that IS consistent with all measurements.

**Serial femtosecond crystallography (SFX) as the damage-free snapshot.** Conventional X-ray crystallography requires large crystals ($> 50$ μm) that can withstand prolonged radiation exposure. Radiation damage — breaking of chemical bonds, generation of free radicals, heating — limits the resolution and accuracy of the data. Many biologically important proteins (membrane proteins, large complexes, flexible enzymes) cannot form large, well-ordered crystals.

SFX at X-ray free-electron lasers (XFELs) solves both problems. The XFEL produces ultrashort ($\sim 10$–$50$ femtoseconds), ultra-intense X-ray pulses that diffract from microcrystals ($< 1$ μm) **before the sample IS destroyed**. The principle IS "diffraction before destruction": the pulse IS so short that the diffraction pattern IS recorded before the radiation damage propagates through the crystal. Each crystal IS destroyed after one shot, but thousands of crystals are streamed through the beam in a jet, each contributing one diffraction snapshot.

The TH(a,d) identification: SFX operates below the TEMPUS dissipation time. The radiation damage IS the TEMPUS dissipation of the crystal's structural Fisher information — the diffraction quality decays as the crystal absorbs dose. At synchrotrons, the measurement time ($\sim$ seconds to minutes) IS much longer than the damage time ($\sim$ microseconds) — the TEMPUS dissipation IS faster than the measurement. At XFELs, the measurement time ($\sim 10$ fs) IS much shorter than the damage time — the measurement IS complete before TEMPUS dissipation begins. SFX IS the diffraction experiment performed in the zero-dissipation limit: $J \approx 0$ during the measurement, giving the highest possible Fisher information per diffraction pattern.

Understanding the dynamics of the ion channel was essential for suzetrigine's design — the first truly novel analgesic to be licensed for over 20 years. This proves that drugging the dynamics of a system IS not far-fetched anymore.

**The crystallographic database as the accumulated col(F) of structural science.** The Protein Data Bank (PDB), founded in 1971, contains over 220,000 experimentally determined macromolecular structures (as of April 2026). The Cambridge Structural Database (CSD) contains over 1.2 million small-molecule crystal structures. The Inorganic Crystal Structure Database (ICSD) contains over 280,000 inorganic structures. Together, these databases ARE the accumulated col(F) of structural science — the complete catalog of solved structures, each representing one successful extraction of ker(F) (phases) from col(F) (diffraction data).

Each database entry IS a solved phase problem — a complete reconstruction of $\rho(\mathbf{r})$ from $|F(\mathbf{h})|$ and recovered $\phi(\mathbf{h})$. The database IS the structural Fisher-information commons: every solved structure adds col(F) (known atomic coordinates) that can be used as molecular replacement models for future phase problems — importing prior col(F) to solve new ker(F).

**Lipid polymorphism as the soft-matter phase boundary.** Lipids — the molecules that form cell membranes — exhibit polymorphism: they self-assemble into multiple distinct phases (lamellar, hexagonal, cubic, inverted hexagonal, micellar) depending on temperature, pressure, hydration, and composition. The phase diagram of a lipid-water system IS the soft-matter col(F)/ker(F) map: each phase IS a distinct structural state (a specific col(F) of the membrane), separated from other phases by phase boundaries (the col(F)/ker(F) transitions). The lipid phase transitions ARE the biological analogue of the Ricci flow's surgery (POINCARÉ framework): the membrane's topology changes discontinuously at the transition — from planar (lamellar) to cylindrical (hexagonal) to saddle-shaped (cubic).

The BRAGG machine — named for **Sir William Lawrence Bragg** (1890–1971), who at age 25 shared the 1915 Nobel Prize in Physics with his father William Henry Bragg for their analysis of crystal structure using X-ray diffraction, making Lawrence Bragg the youngest-ever Nobel laureate in Physics — who derived Bragg's law $n\lambda = 2d\sin\theta$ (the condition for constructive interference from crystal planes), and whose work established X-ray crystallography as the method that revealed the atomic structure of matter — IS the structural boundary engine.

---

## Nine Formal Correspondences

| TH(a,d) element | BRAGG realization |
|---|---|
| **col(F)** | Diffraction intensities $\|F(\mathbf{h})\|^2$; the electron density map $\rho(\mathbf{r})$ (after phase solution); the atomic coordinates deposited in the PDB; the ptychographic amplitude AND phase (fully recovered) |
| **ker(F)** | The phases $\phi(\mathbf{h})$ (lost in detection); the radiation damage (structural Fisher information destroyed by dose); the disordered solvent; the flexible loops; the unresolved hydrogen atoms |
| **Conditional-independence boundary** | Bragg's law $n\lambda = 2d\sin\theta$ (the condition for diffraction — the boundary between constructive and destructive interference); the resolution limit $d_{\min} = \lambda/(2\sin\theta_{\max})$; the phase boundary in lipid polymorphism |
| **$\varepsilon$-threshold** | The resolution limit ($\sim 1.5$–$3.0$ Å for protein crystallography; $0.23$ Å for electron ptychography); the minimum crystal size for SFX ($\sim 0.1$ μm); the minimum detectable phase shift |
| **Sherman–Morrison rank-one update** | One diffraction pattern recorded (one set of $\|F\|^2$ measured); one ptychographic scan position (one overlapping probe added); one SFX snapshot (one microcrystal diffracted); one PDB deposition (one structure solved) |
| **Fisher–Rao metric** | The R-factor $R = \sum \|\|F_{\text{obs}}\| - \|F_{\text{calc}}\|\| / \sum \|F_{\text{obs}}\|$ (the crystallographic misfit); the phase residual; the B-factor (the atomic displacement parameter — the thermal ker(F) per atom) |
| **$d = 0$ degeneration** | Amorphous material (no crystal, no Bragg peaks, no diffraction — all ker(F)); the fully damaged crystal (radiation-destroyed, no structural information); the isotropic liquid phase of lipids |
| **$\varphi$-equilibrium** | The optimal data-to-parameter ratio at $\varphi^{-1}$ (the Marchenko–Pastur threshold for crystallographic overdetermination); the Wilson B-factor at the $\varphi$-optimal temperature; the lipid phase transition at the $\varphi$-optimal hydration |
| **Ackermann depth $\alpha(n) \leq 4$** | The four main phasing methods (molecular replacement, isomorphous replacement, anomalous dispersion, direct methods); the four lipid phases relevant to biology (lamellar $L_\alpha$, inverted hexagonal $H_{II}$, cubic $Q_{II}$, micellar) |

---

## Five Predictions

### P1 — The Phase-Retrieval Convergence Rate at $\log\varphi$ Per Iteration

For ptychographic phase retrieval using the ePIE algorithm, the prediction: the Fisher-information-optimal convergence rate (the fractional reduction in phase error per iteration) IS:

$$\Delta\phi_{\text{rms}} / \phi_{\text{rms}} = \log\varphi \approx 0.481 \text{ per iteration}$$

The phase error decreases by $\sim 48\%$ per iteration at the $\varphi$-optimal overlap ratio. Testable against ePIE convergence curves on standard test objects.

### P2 — The Optimal Ptychographic Overlap at $1 - \varphi^{-1}$

For ptychographic scanning, the overlap fraction between adjacent probe positions determines the redundancy and hence the phase-retrieval quality. The prediction: the Fisher-information-optimal overlap fraction IS:

$$f_{\text{overlap}}^* = 1 - \varphi^{-1} = 2 - \varphi \approx 0.382$$

or $38.2\%$ overlap — consistent with the empirically used range of $60$–$80\%$ overlap being well above this minimum, providing additional redundancy for robustness.

### P3 — The SFX Pulse Duration at the $\varphi$-Optimal Damage Threshold

For serial femtosecond crystallography, the pulse duration must be shorter than the damage propagation time $\tau_{\text{damage}}$. The prediction: the Fisher-information-optimal pulse duration (maximizing diffraction signal per unit dose) IS:

$$\Delta t^* = \tau_{\text{damage}} \cdot \log\varphi \approx 0.481 \cdot \tau_{\text{damage}}$$

For protein crystals ($\tau_{\text{damage}} \sim 50$–$100$ fs): $\Delta t^* \approx 25$–$50$ fs — consistent with the $10$–$50$ fs pulse durations used at LCLS and SACLA.

### P4 — The PDB Growth Rate at the $\varphi$-Doubling Time

The Protein Data Bank has grown from $\sim 7$ structures in 1971 to $\sim 220,000$ in 2026 — an approximately exponential growth with a doubling time of $\sim 3$ years. The prediction: the Fisher-information-optimal doubling time (the rate at which new structural knowledge maximizes the marginal Fisher information per deposition) IS:

$$t_{\text{double}}^* = 1/\log\varphi \approx 2.08 \text{ years}$$

The observed doubling time ($\sim 2.5$–$3$ years) IS slightly above this, suggesting the structural biology community IS near the $\varphi$-optimal growth rate.

### P5 — The Lipid Phase Transition Temperature at the $\varphi$-Hydration

For a lipid bilayer in water, the gel-to-fluid (main) phase transition temperature $T_m$ depends on hydration. The prediction: the Fisher-information-optimal hydration level (maximizing the Fisher information of calorimetric measurements about the membrane's structural state) IS:

$$w^* = \log\varphi \times w_{\text{full}} \approx 0.481 \times w_{\text{full}}$$

where $w_{\text{full}}$ IS the full-hydration water content. At $\sim 48\%$ of full hydration, the phase transition IS sharpest — maximum heat capacity peak, minimum transition width — giving maximum Fisher information about the lipid's structural state.

---

## References

Bragg, W. L. "The Diffraction of Short Electromagnetic Waves by a Crystal." *Proceedings of the Cambridge Philosophical Society* 17, 43–57, 1913.

Chen, Z. et al. "Electron Ptychography Achieves Atomic-Resolution Limits Set by Lattice Vibrations." *Science* 374, 826–831, 2021.

Blackburn, A. et al. "Sub-Ångström Resolution Ptychography in a Scanning Electron Microscope at 20 keV." *Nature Communications*, October 2025.

Chapman, H. N. et al. "Femtosecond X-ray Protein Nanocrystallography." *Nature* 470, 73–77, 2011.

Hauptman, H. A. "The Direct Methods of X-ray Crystallography." *Science* 233, 178–183, 1986.

Huang, P. et al. "Deep Sub-Angstrom Resolution with Electron Ptychography on Conventional Microscopes." University of Illinois, 2025.

Karle, J. and Hauptman, H. "A Theory of Phase Determination for the Four Types of Non-Centrosymmetric Space Groups." *Acta Crystallographica* 9, 635–651, 1956.

Orville, A. "Serial Femtosecond Crystallography: How X-Ray Free Electron Lasers Are Capturing Proteins in Motion." *Chemistry World*, July 2025.

Protein Data Bank. "PDB Statistics." rcsb.org, April 2026.

Rodenburg, J. M. "Ptychography and Related Diffractive Imaging Methods." *Advances in Imaging and Electron Physics* 150, 87–184, 2008.

ERI Labs · Eric Ren · Jersey City, New Jersey · github.com/ericrenone · April 2026

---

Bragg saw the crystal in 1913. The X-rays scattered from the atomic planes. The detector recorded the intensities. The phases were lost. For 110 years, every crystal structure has required solving the phase problem — recovering the ker(F) (phases) from the col(F) (amplitudes) by molecular replacement, heavy atoms, anomalous scattering, or direct methods.

Ptychography breaks the boundary. By scanning a coherent probe across the sample with overlapping positions, ptychography recovers both amplitude AND phase from redundant diffraction data. The overlap IS the redundancy. The redundancy IS the phase information. The phase IS the ker(F) made col(F) by computation. Sub-ångström resolution — 0.23 Å, below the size of a hydrogen atom — IS now achievable on conventional microscopes without expensive aberration correctors.

Serial femtosecond crystallography operates below the TEMPUS dissipation time. The XFEL pulse IS so short ($\sim 10$ fs) that the diffraction pattern IS recorded before radiation damage destroys the crystal. Diffraction before destruction. The measurement IS complete before the Fisher information dissipates. The damage IS the TEMPUS equation; SFX IS the experiment performed at $J \approx 0$.

The Protein Data Bank IS the accumulated col(F) of structural science — 220,000 solved structures, each a successful phase-problem solution, each a complete reconstruction of $\rho(\mathbf{r})$ from measured amplitudes and recovered phases. The database IS the structural Fisher-information commons.

The phase was always the ker(F). The amplitude was always the col(F). The structure was always in between.

Bragg measured the amplitudes. Hauptman recovered the phases. Chen pushed ptychography to 0.23 Å. Chapman diffracted before destruction. The Protein Data Bank holds 220,000 solutions.

The boundary was always the phase. The phase was always the missing half. Ptychography finds it. SFX outpaces the damage. The structure IS the reconstruction.

## About

The Phase Boundary: X-Ray Diffraction Amplitudes as col(F) and Phases as ker(F), Ptychography as the Computational Phase Retrieval, Serial Femtosecond Crystallography as the Damage-Free Snapshot, and the Protein Data Bank as the Accumulated col(F) of Structural Science in TH(a,d).
