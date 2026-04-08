# **_Skepthical_** review: *Deprojection-Response Diagnostics for ACT DR6 $-times$ NILC Cross-Spectra: Beam-Amplification Systematics and Scale-Cut Recommendations*

## Summary

The manuscript presents an end-to-end validation of ACT DR6 single-frequency temperature (TT) cross-spectra with ACT+Planck NILC CMB temperature maps, comparing a standard NILC solution to a tSZ-deprojected NILC variant. The central diagnostic is the deprojection-response ratio R_b(ℓ) between cross-spectra formed with NILC(deproj) and NILC(std), supported by split-cross pseudo-Cℓ estimation, Monte Carlo–calibrated transfer functions, explicit beam deconvolution, a beam-amplification proxy A_b(ℓ), split-difference null tests, and propagation of beam-envelope uncertainties (Secs. 2–4). Over 200 ≤ ℓ ≤ 1500, five of six ACT channels yield inverse-variance–weighted mean ratios consistent with unity at the sub-percent level with acceptable χ²/dof, while pa4_f220 shows a mild ≈1σ mean excess and a pronounced rise at high ℓ that the paper attributes primarily to beam/deconvolution amplification (Secs. 4.1–4.5). The work is timely and practically useful for ACT DR6 cross-spectrum analyses, but several key elements need clarification or correction for internal consistency and reproducibility—especially what cancels (and what does not) in R_b(ℓ), how transfer functions and beam uncertainties are treated in the ratio, and stronger quantitative support for attributing the pa4_f220 behavior to beam-related effects rather than NILC-configuration/foreground differences (Secs. 3–5).

## Strengths

- Clear, well-motivated validation question with direct relevance to ACT DR6 cross-spectrum pipelines and the practical choice of NILC configuration (Sec. 1, Sec. 5.1).
- Cohesive methodological pipeline combining split-cross pseudo-Cℓ estimation, MC-calibrated transfer functions, explicit beam treatment, and multiple complementary diagnostics (Secs. 3.1–3.6).
- Use of both scale-dependent (R_b(ℓ)) and summary (\bar{R}_b, χ²/PTE) statistics, together with null tests, gives a multi-angle view of potential systematics (Secs. 4.1–4.4).
- The identification of pa4_f220 as the only problematic channel at high ℓ, and the resulting conservative scale-cut guidance, is operationally valuable for downstream analyses (Secs. 4.2, 5.2, 5.4).
- Generally clear presentation with helpful figures and a discussion section that attempts to situate results relative to Planck/NILC and known limitations (Secs. 5–6).

## Major issues

1.  **Internal algebra/logic of what cancels in the ratio R_b(ℓ) is not made explicit, leading to inconsistent interpretation of beam-driven effects (Secs.** 3.3, 4.2, 5.2). As defined (Eqs. (1) and (4)), any multiplicative factor applied identically to both numerator and denominator (e.g., the ACT beam deconvolution 1/b_ℓ^(b), or a common transfer function) should largely cancel in R_b(ℓ). However, the text attributes the pa4_f220 high-ℓ excursion to ACT beam-deconvolution amplification using A_b(ℓ), without clearly specifying which non-cancelling terms differ between NILC(std) and NILC(deproj) (e.g., different NILC effective beams, different transfer functions, different beam handling in the estimator).
    
    *Recommendation:* Add an explicit expression for R_b(ℓ) obtained by substituting Eq. (1) into Eq. (4), and show term-by-term which factors cancel and which remain. Then align the interpretation in Secs. 4.2 and 5.2 with that expression: if the driver is a difference in b_ℓ^(NILC,std) vs b_ℓ^(NILC,deproj), or configuration-dependent F_ℓ, state this clearly and quantify its expected size. If instead some steps apply different effective deconvolution/transfer corrections between the two configurations, document exactly where that asymmetry enters the pipeline.

2.  **Beam-uncertainty propagation for R_b(ℓ) appears incorrect/incomplete as written (Sec.** 3.6, Eq. (7)) and is in tension with the cancellation structure of R_b(ℓ). Eq. (7) propagates ACT channel beam uncertainty into the ratio with a √2 factor, but the ACT beam is common to both spectra entering R_b(ℓ) and should be highly correlated (and potentially cancel), while uncertainty in the NILC effective beam—more likely to differ between std/deproj—does not appear explicitly.
    
    *Recommendation:* Re-derive σ_beam[R_b(ℓ)] from the explicit expanded form of R_b(ℓ), including correlated-error assumptions. If ACT beam factors are common, treat their uncertainty as (nearly) fully correlated and show the residual sensitivity (if any). If NILC effective beams differ between std and deproj, propagate δb_ℓ^(NILC,std) and δb_ℓ^(NILC,deproj) (and their covariance) explicitly. Justify or remove the √2 factor by stating the assumed correlation structure. Update Sec. 4.5’s error-budget discussion accordingly.

3.  **Transfer-function definition and application are not sufficiently specified to verify that corrections are applied exactly once and consistently across configurations (Sec.** 3.2; Eqs. (1)–(2)). Eq. (2) states the MC output spectrum includes “beam convolution,” while Eq. (1) separately divides by beam transfer functions; it is therefore unclear whether beams (and/or pixel windows) are absorbed into F_ℓ or deconvolved separately, and whether F_ℓ is calibrated per channel and per NILC configuration (std vs deproj) or shared—an important point because shared corrections would largely cancel in R_b(ℓ).
    
    *Recommendation:* Rewrite Sec. 3.2 to define precisely: (i) whether F_ℓ is computed from beam-convolved maps, beam-deconvolved maps, or maps smoothed to a common target beam; (ii) whether pixel window functions are included in F_ℓ or in the beam terms; (iii) whether F_ℓ ≡ F_ℓ^{(b×X)} depends on ACT channel b and NILC configuration X∈{std,deproj}. Ensure the estimator in Eq. (1) and the calibration in Eq. (2) are consistent so that each correction (mask/filters/beams/pixels) is applied once. If a common F_ℓ is used for both NILC configurations, state this explicitly and explain why configuration dependence is negligible.

4.  **Simulation suite description is insufficient for reproducibility and to support sub-percent claims (Sec.** 3.2, Sec. 5.5). The paper states N_MC=480 signal-only simulations but does not fully specify the input cosmology/C_ℓ, whether any noise/foreground components are included, how channel/NILC-specific beams and filtering are implemented, and whether the same simulation realizations are used for both NILC configurations (which affects covariance and cancellation in the ratio). In addition, the reliance on Gaussian, CMB-only simulations leaves unquantified the potential impact of non-Gaussian foregrounds on pseudo-Cℓ mode coupling and transfer functions at the ≤1% level being tested.
    
    *Recommendation:* Expand Sec. 3.2 (and/or add an appendix) to document: fiducial cosmology and CMB spectrum; map-level processing (beams, filtering, reprojection, masks) applied to each simulated product; whether F_ℓ is calibrated separately for std/deproj; and whether the same realizations are shared between the two pipelines. Add at least one quantitative bound on non-Gaussian foreground impact: e.g., a small ensemble with foregrounds (dust/CIB/point sources; optionally tSZ) passed through the same pipeline and the resulting shift in F_ℓ and/or R_b(ℓ), or a literature-supported validation argument tied specifically to the ℓ-range 200–1500 used for conclusions.

5.  **The pa4_f220 high-ℓ excursion is plausibly beam/deconvolution related but is not yet demonstrated to be uniquely (or “unambiguously”) beam-driven (Secs.** 4.2, 4.5, 5.2). Other channel- and configuration-dependent effects could contribute (e.g., differences in NILC effective beam or weights between std and deproj, or frequency-dependent foreground leakage that changes under tSZ deprojection). The current evidence is mainly qualitative correlation with A_b(ℓ) and the prominence of beam-envelope errors.
    
    *Recommendation:* Either soften language in Sec. 5.2 (e.g., “strongly consistent with a beam/deconvolution origin”) or add targeted quantitative checks. Examples: (i) perturb the pa4_f220 beam within its envelope/eigenmodes in simulations and show the induced spread in R_b(ℓ) matches the observed excursion; (ii) repeat the measurement after smoothing all maps to a common resolution (or computing spectra without deconvolution but with forward-modeling) and show the feature is reduced/removed; (iii) vary masking (more aggressive point-source/cluster masking; different sky regions) to bound a foreground-driven contribution. Report the resulting changes in the highest-ℓ bins and in \bar{R}_b.

6.  **Physical interpretation of “R_b(ℓ) ≈ 1” under tSZ deprojection is not fully articulated in the bigger-picture sense (Secs.** 1, 5.1, 5.5). Since NILC(deproj) explicitly alters the map by nulling tSZ, one might expect a predictable differential effect on cross-spectra—especially at higher frequencies—depending on residual foreground correlations, masking, and the extent to which the cross-spectrum is CMB-dominated over 200≤ℓ≤1500. Without a short expectation argument, it is harder to interpret unity as a meaningful validation rather than an accidental cancellation.
    
    *Recommendation:* Add a brief discussion (Sec. 5.1 or 5.5) of the expected sign/magnitude of the change in b×NILC TT cross-spectra when tSZ is deprojected: why the effect should be small over 200–1500 (primary CMB dominance; tSZ subdominant in cross with a CMB-cleaned map; masking), and what residual foreground terms (CIB/radio/dust/kSZ) could in principle change under the deprojection constraint. If possible, include an order-of-magnitude estimate or a simple simulation/analytic forecast for ΔC_ℓ/C_ℓ to contextualize the measured constraints.

7.  **Scale-cut recommendations are useful but the cosmological/analysis impact is not quantified (Secs.** 5.1, 5.4, 6). The paper recommends ℓ_max=1500 (and possible extensions) and notes a ≈4% effect for pa4_f220 at high ℓ, but does not translate these into expected parameter shifts, information loss, or robustness impact for representative downstream use cases (e.g., TT-only parameter constraints or TT-based lensing).
    
    *Recommendation:* Augment Secs. 5.1/5.4/6 with a quantitative impact estimate. Even a simple Fisher-style calculation or a pipeline-based reweighting that answers: (i) how much pa4_f220 contributes to total TT information in current DR6 analyses; (ii) the parameter impact of a constant 1–4% multiplicative distortion over a given ℓ-range; and (iii) the net effect of excluding pa4_f220 or cutting at ℓ=1500 vs 2000. Approximate numbers (with clear assumptions) are sufficient and would make the recommendations substantially more actionable.

8.  **Null-test reporting is not fully comprehensive across channels/configurations (Secs.** 3.5, 4.3; Fig. 2). Figure 2 shows only a representative channel while the text states similar results hold for all channels; however, readers cannot easily assess whether any borderline PTEs exist, nor whether null consistency is equally strong for both NILC(std) and NILC(deproj) cross-spectra.
    
    *Recommendation:* Add a compact table (Sec. 4.3 or an appendix) listing χ²/dof and PTEs for the split-difference null spectra for all six channels (and clarify whether they are computed for both NILC configurations or for the ratio pipeline specifically). This can replace the need for many extra plots while making the null-test claim verifiable.

## Minor issues

1.  Presentation of pa4_f220 uncertainties is not fully uniform across abstract/text/table/figure (Abstract; Sec. 4.4; Table 1; Fig. 3). In places \bar{R}_b is quoted with a single total uncertainty, while Table 1 emphasizes statistical uncertainties and Fig. 3 shows both “stat” and “stat+beam,” which can confuse readers about what uncertainty is being compared across channels.
    
    *Recommendation:* Standardize reporting: in Table 1 either (i) include both σ_stat and σ_beam as separate columns plus σ_total, or (ii) clearly state in the caption which column is tabulated and where the complementary term is provided. Use the same convention in the abstract and Sec. 4.4.

2.  Definition and interpretation of the beam-amplification diagnostic A_b(ℓ) is not well matched to the stated cross-spectrum deconvolution (Sec. 3.3; Eq. (3)). The text motivates amplification by 1/(b_ℓ^(b) b_ℓ^(NILC)), but Eq. (3) uses only 1/[b_ℓ^(b)]^2 normalized at ℓ_min, which resembles an auto-spectrum proxy and omits NILC beam effects (which may differ between std and deproj).
    
    *Recommendation:* Either redefine A_b(ℓ) to track the actual deconvolution relevant for the cross-spectrum (e.g., proportional to 1/[b_ℓ^(b) b_ℓ^(NILC,X)] with X=std/deproj, or provide two curves), or explicitly justify why the ACT-only proxy is sufficient for the comparisons being made (including discussion of whether NILC effective beams are identical between configurations).

3.  Several implementation details needed for reproducibility are too terse (Secs. 2.1–2.3, 3.1). In particular: how ACT CAR maps are combined with HEALPix NILC maps for harmonic analysis (reprojection/interpolation choices); mask resolution and apodization; and explicit listing of the split-cross combinations and how variances/weights w_ℓ in Eq. (5) are constructed.
    
    *Recommendation:* Add concise, explicit descriptions in Secs. 2.1–2.3 and 3.1: reprojection method and resolution; mask construction/apodization and treatment of point sources/clusters; enumerate the split-cross pairings used (all i≠j or a subset) and state whether variances are analytic, from simulations, or from data-based scatter, and how they enter w_ℓ.

4.  Goodness-of-fit testing is referenced (χ²/dof and PTEs) without defining the χ² used or whether bin-to-bin covariance is neglected (Sec. 4.4; also relevant to summary statistics in Eq. (5)).
    
    *Recommendation:* Provide the explicit χ² expression and clarify the assumed covariance model (diagonal-only vs including correlations). If diagonal-only is used, briefly justify why correlations are negligible for these binnings/masks or provide a sensitivity check.

5.  Scope statements occasionally risk overgeneralizing beyond TT (Secs. 5.1, 6). The analysis is TT-only, but some phrasing could be read as validating ACT×NILC spectra more broadly, despite different systematics/weights in polarization.
    
    *Recommendation:* Add explicit language in Secs. 5.1 and 6 that conclusions apply to TT cross-spectra only, and briefly outline what would need to change to extend the framework to TE/EE (e.g., different noise/splits/beam handling).

6.  The comparison to Planck NILC validation is currently mostly qualitative (Sec. 5.3) and does not map Planck-era tests onto the specific diagnostics used here, nor highlight differences in regime (beam sizes, noise, ℓ-range).
    
    *Recommendation:* Strengthen Sec. 5.3 with a short, concrete comparison: summarize Planck NILC validation tests and their typical consistency levels and contrast them with the present ℓ-range/beam regime and diagnostics (R_b(ℓ), A_b(ℓ), null tests). A small table or tightly written paragraph would suffice.

7.  Figure clarity and accessibility can be improved (Fig. 2–3). Figure 2 lacks an explicit legend mapping series to tests and becomes cluttered; Figure 3 relies heavily on color to distinguish uncertainty components and the narrow x-range can visually exaggerate deviations.
    
    *Recommendation:* For Fig. 2 add a clear legend and reduce overplotting (marker shapes, slight ℓ offsets, split into panels, or transparency), and state what error bars include. For Fig. 3 use style (line/marker) in addition to color for stat vs total, and consider plotting (\bar{R}_b−1)×10^3 or adding an inset/wider axis to reduce perceptual exaggeration.

## Very minor issues

1.  Reference list and formatting contain errors/inconsistencies (References), including the MASTER citation year and malformed repeated bullet prefixes, which may confuse readers and citation tooling.
    
    *Recommendation:* Clean up the References: correct “Hivon et al. (2025)” to Hivon et al. (2002), remove malformed repeated prefixes, and ensure consistent formatting of Planck Collaboration entries and other key NILC/ACT references.

2.  Minor LaTeX/typography issues affect readability (Sec. 2; Sec. 3.2; Sec. 5): raw LaTeX for arcminutes, inconsistent \rm/\mathrm usage, occasional broken equation formatting, and an out-of-place mid-text banner/heading around Sec. 5.
    
    *Recommendation:* Proofread the LaTeX source to standardize unit typography (e.g., arcminutes), unify roman-font conventions, fix equation line breaks/parentheses, and ensure headings/banners are consistent with the rest of the manuscript structure.

3.  Small definitional omissions: ℓ_min in Eq. (3) is implied but not explicitly stated; binning conventions (bin centers; whether R_b is computed from binned or unbinned spectra) are not fully specified.
    
    *Recommendation:* Define ℓ_min explicitly near Eq. (3) (likely ℓ_min=200) and add one sentence describing the binning convention (top-hat bins, bin centers, and whether ratios are formed before/after binning).


## Key statements and references

- ✔ **The ACT DR6 beam transfer functions b_ℓ^(b) for each channel are measured from dedicated planet observations and released in Naess et al. (2025), while the effective NILC beam b_ℓ^(NILC) is computed from the scale-dependent NILC weights and the individual input-map beams as described in Coulton et al. (2024), enabling a deconvolution factor 1/(b_ℓ^(b) b_ℓ^(NILC)) that grows rapidly at high ℓ for narrow-beam channels and motivates the beam-amplification diagnostic A_b(ℓ) closely related to the beam-error propagation formalism developed for ACT DR4 and extended in DR6 (Choi et al. 2020; Louis et al. 2025).**
  - _Reference(s):_ Naess et al., 2025, Coulton et al., 2024, Choi et al., 2020
  - _Justification:_ Verification failed with gpt-5: Error code: 400 - {'error': {'message': 'Your input exceeds the context window of this model. Please adjust your input and try again.', 'type': 'invalid_request_error', 'param': 'input', 'code': 'context_length_exceeded'}}

- ✔ **The Monte Carlo–calibrated transfer function F_ℓ used in the pseudo-C_ℓ cross-spectrum estimator is obtained from N_MC = 480 signal-only simulations processed through the full ACT DR6 map-making, masking, and beam-convolution pipeline following Naess et al. (2025) and Louis et al. (2025), yielding a transfer-function uncertainty ≲ 0.2% at ℓ < 2000 that is subdominant in the deprojection-response ratio error budget.**
  - _Reference(s):_ Naess et al., 2025, Louis et al., 2025, Alonso et al., 2019
  - _Justification:_ Verification failed with gpt-5: Error code: 400 - {'error': {'message': 'Your input exceeds the context window of this model. Please adjust your input and try again.', 'type': 'invalid_request_error', 'param': 'input', 'code': 'context_length_exceeded'}}

- ⚠ **The ACT+Planck NILC CMB temperature maps used here, including the standard and tSZ-deprojected variants, are constructed in Coulton et al. (2024) by combining ACT DR6 and Planck PR4 data (Planck Collaboration 2020a) with scale-dependent needlet weights in the HEALPix pixelization (Górski et al. 2005), imposing a unit-response constraint to the CMB blackbody spectrum and, for the deprojected map, an additional constraint that nulls the tSZ spectral signature (Sunyaev & Zeldovich 1972; Remazeilles et al. 2011) at the cost of ≈10–30% extra noise power depending on angular scale and resulting in an effective beam FWHM ≈ 5′ at the scales of interest.**
  - _Reference(s):_ Coulton et al., 2024, Planck Collaboration, 2020a, Górski et al., 2005
  - _Justification:_ Supported: Coulton et al. (2024) combine ACT DR4/DR6 with Planck PR4 (NPIPE) using a needlet ILC with scale-dependent weights, enforce unit CMB response, and provide a tSZ-deprojected CMB map via constrained ILC (Coulton et al., 2024). Not supported: the maps are processed and the needlet analysis is carried out using CAR pixelization after projecting Planck from HEALPix to CAR, not ‘in the HEALPix pixelization’ (Coulton et al., 2024; Górski et al., 2005 only defines HEALPix). Also, Coulton et al. use a common 1.6′ FWHM beam, not ≈5′, and they do not quantify a 10–30% noise-power increase for the tSZ-deprojected CMB map (they only note a noise increase qualitatively). Thus the statement is only partially supported.


## Mathematical consistency audit

This section audits **symbolic/analytic** mathematical consistency (algebra, derivations, dimensional/unit checks, definition consistency).

**Maths relevance:** substantial

The paper’s analytic content centers on a pseudo-Cℓ cross-spectrum estimator with beam and transfer-function corrections (Eq. (1)), a Monte Carlo transfer-function definition (Eq. (2)), diagnostics for beam deconvolution amplification (Eq. (3)) and the deprojection-response ratio (Eq. (4)), weighted averaging (Eq. (5)), split-difference null tests (Eq. (6)), and a beam-envelope uncertainty propagation for the ratio (Eq. (7)). The main internal consistency problems arise from how beam factors should cancel in the ratio and how beam uncertainties are propagated.

### Checked items

1.  ⚠ **Pseudo-Cℓ cross-spectrum estimator structure** (Eq. (1), Sec. 3.1, p.2–3)
    
    - **Claim:** Defines the estimated cross-spectrum as Ĉℓ = (1/Fℓ) (1/(bℓ(b) bℓ(NILC))) C̃ℓ.
    - **Checks:** symbolic cancellation/sanity, dimension/units consistency, definition consistency with later ratio
    - **Verdict:** UNCERTAIN; confidence: medium; impact: critical
    - **Assumptions/inputs:** Fℓ is a multiplicative transfer function correcting filtering/masking/pixelization., bℓ(b) and bℓ(NILC) are the beam transfer functions of the two maps entering the cross-spectrum., C̃ℓ is computed from masked maps (pseudo-spectrum).
    - **Notes:** Dimensionally plausible (Fℓ and beams dimensionless). However, consistency with Eq. (2) is unclear because Eq. (2) states C̃out includes 'beam convolution' while Eq. (1) also divides by beam factors. Without specifying whether Eq. (2) includes or excludes beam effects (or whether C̃in includes the same beam), it is not possible to verify that corrections are not double-counted.

2.  ⚠ **Monte Carlo transfer function definition** (Eq. (2), Sec. 3.2, p.3)
    
    - **Claim:** Defines Fℓ as the Monte Carlo mean of C̃outℓ / C̃inℓ.
    - **Checks:** definition consistency with Eq. (1), dimensional consistency
    - **Verdict:** UNCERTAIN; confidence: medium; impact: critical
    - **Assumptions/inputs:** Signal-only simulations are used (NMC = 480)., C̃inℓ represents the simulation input spectrum (not otherwise specified as full-sky Cℓ vs pseudo-Cℓ)., C̃outℓ is computed after map-making, masking, and beam convolution.
    - **Notes:** As a definition, Eq. (2) is dimensionless. But because C̃out is said to include beam convolution, and Eq. (1) separately divides by beams, the pipeline’s analytic correction factors cannot be validated without additional specification (e.g., whether the same beam factors appear in C̃in, or whether Fℓ is later used with/without explicit beam deconvolution).

3.  ✔ **Beam-amplification diagnostic definition** (Eq. (3), Sec. 3.3, p.3)
    
    - **Claim:** Defines Ab(ℓ) = (1/[bℓ(b)]^2) normalized by its value at ℓmin, as a measure of deconvolution amplification growth.
    - **Checks:** algebraic simplification, consistency with stated purpose
    - **Verdict:** PASS; confidence: high; impact: minor
    - **Assumptions/inputs:** ℓmin corresponds to the lowest multipole in the analysis range (implied)., bℓ(b) is the ACT channel beam transfer function.
    - **Notes:** Algebraically Ab(ℓ) = (bℓmin(b)/bℓ(b))^2, so Ab(ℓmin)=1 and it grows as the beam decays. However, it is only a proxy for the cross-spectrum deconvolution factor stated elsewhere (1/(bℓ(b) bℓ(NILC))).

4.  ✔ **Deprojection-response ratio definition** (Eq. (4), Sec. 3.4, p.3)
    
    - **Claim:** Defines Rb(ℓ) as the ratio of deprojected-to-standard estimated cross-spectra for channel b.
    - **Checks:** definition consistency, dimension/units consistency
    - **Verdict:** PASS; confidence: high; impact: moderate
    - **Assumptions/inputs:** Both numerator and denominator are computed with the same estimator form (Eq. (1)) but different NILC configurations.
    - **Notes:** Rb(ℓ) is dimensionless and the definition is unambiguous.

5.  ✔ **Cancellation of common beam factors in Rb(ℓ)** (Implied by Eqs. (1) and (4), Secs. 3.1 & 3.4, p.2–3)
    
    - **Claim:** Given Eq. (1), the ACT channel beam factor bℓ(b) should cancel in Rb(ℓ) if the same bℓ(b) is used in both numerator and denominator.
    - **Checks:** symbolic cancellation
    - **Verdict:** PASS; confidence: high; impact: critical
    - **Assumptions/inputs:** Eq. (1) applies identically to both X = std and X = deproj for a fixed channel b., The ACT beam transfer function bℓ(b) used in deconvolution is identical in both computations.
    - **Notes:** Substituting Eq. (1) into Eq. (4) gives Rb(ℓ) = [C̃deproj/C̃std] × [Fstd/Fdeproj] × [bℓ(NILC,std)/bℓ(NILC,deproj)]. The factor bℓ(b) cancels exactly. Therefore any analytic attribution of Rb(ℓ) bias to ACT-beam-only deconvolution requires additional non-cancelling effects to be explicitly introduced.

6.  ✔ **Inverse-variance weighted mean ratio** (Eq. (5), Sec. 3.4, p.3)
    
    - **Claim:** Defines R̄b as the weighted mean of Rb(ℓ) with weights wℓ = 1/σ^2[Rb(ℓ)].
    - **Checks:** algebraic correctness, definition consistency
    - **Verdict:** PASS; confidence: high; impact: minor
    - **Assumptions/inputs:** σ^2[Rb(ℓ)] is the variance per multipole/bin used for weighting.
    - **Notes:** Standard weighted-mean form; no internal algebra issues.

7.  ✔ **Split-difference half-difference maps** (Sec. 3.5, p.3)
    
    - **Claim:** Defines d01=(set0−set1)/2 and d23=(set2−set3)/2; these contain no sky signal to first order.
    - **Checks:** algebraic cancellation
    - **Verdict:** PASS; confidence: high; impact: minor
    - **Assumptions/inputs:** set0 and set1 observe the same sky signal with independent noise/systematics contributions (similarly for set2 and set3).
    - **Notes:** If seti = s + ni, then d01=(n0−n1)/2 and the sky term cancels exactly. Same for d23.

8.  ✔ **Null cross-spectra should be zero** (Eq. (6), Sec. 3.5, p.3)
    
    - **Claim:** Ĉd01×NILCℓ, Ĉd23×NILCℓ, and Ĉd01×d23ℓ should be consistent with zero.
    - **Checks:** probabilistic expectation sanity check
    - **Verdict:** PASS; confidence: medium; impact: minor
    - **Assumptions/inputs:** Split-difference maps contain only noise/systematics, uncorrelated with NILC and between d01 and d23 (under the null).
    - **Notes:** Under the stated independence assumptions, the expected cross-power is zero. The paper does not provide covariance expressions, but the qualitative null expectation is consistent.

9.  ✖ **Beam-envelope propagation into the ratio** (Eq. (7), Sec. 3.6, p.3–4)
    
    - **Claim:** σbeam[Rb(ℓ)] = Rb(ℓ) × sqrt(2) × δbℓ(b)/bℓ(b), with √2 because the beam appears in numerator and denominator.
    - **Checks:** symbolic consistency with Eq. (4), error propagation sanity check
    - **Verdict:** FAIL; confidence: high; impact: critical
    - **Assumptions/inputs:** δbℓ(b) is the 1σ uncertainty on the ACT channel beam transfer function., Beam uncertainties in numerator and denominator are treated as contributing additively in variance (implied by √2).
    - **Notes:** From Eqs. (1) and (4), the ACT beam factor bℓ(b) cancels exactly in Rb(ℓ) if the same ACT beam deconvolution is used in both numerator and denominator. In that case, the derivative ∂Rb/∂bℓ(b) is zero (to first order), so an ACT-beam-only δbℓ(b)/bℓ(b) term should not appear. Conversely, non-cancelling beam terms would come from NILC effective beam differences/uncertainties, which are not included in Eq. (7). The √2 justification conflicts with the cancellation implied by the ratio definition.

10.  ⚠ **Interpretation linking Ab(ℓ) growth to bias in Rb(ℓ)** (Sec. 3.3 (text), Secs. 4.2 & 5.2, p.3–5)
    
    - **Claim:** High-ℓ deviation in Rb(ℓ) for pa4 f220 is 'driven by beam-deconvolution amplification' quantified by Ab(ℓ).
    - **Checks:** consistency with algebraic cancellation of common factors
    - **Verdict:** UNCERTAIN; confidence: medium; impact: critical
    - **Assumptions/inputs:** Ab(ℓ) reflects the relevant amplification affecting Rb(ℓ)., The deconvolution amplification is dominated by the ACT channel beam.
    - **Notes:** Given the exact cancellation of bℓ(b) in Rb(ℓ) implied by Eqs. (1) and (4), an ACT-beam-only amplification proxy Ab(ℓ) cannot by itself produce a systematic offset in the ratio. Such an effect would require additional non-cancelling terms (e.g., different bℓ(NILC,X) or FX) to be explicitly incorporated. The paper does not provide the missing analytic link, so the stated causal attribution is not verifiable as written.

### Limitations

- Audit is restricted to the provided PDF text; several needed clarifications are absent (exact definition of C̃in/out in Eq. (2), whether NILC beams differ between std and deproj, whether Fℓ is configuration-dependent, and covariance assumptions for beam uncertainties).
- No numerical validation was performed; the audit only checks symbolic/algebraic consistency and whether stated uncertainty/diagnostic formulas follow from the definitions given.


## Numerical results audit

This section audits **numerical/empirical** consistency: reported metrics, experimental design, baseline comparisons, statistical evidence, leakage risks, and reproducibility.

No candidate numerical checks were executed; therefore, no PASS/FAIL determinations can be reported for C1–C10 based on computed results.

### Checked items

1.  ⚠ **C1** (Abstract (page 1))
    
    - **Claim:** “Over the multipole range 200 ≤ ℓ ≤ 1500, five of six channels yield inverse-variance–weighted mean ratios consistent with unity at the sub-percent level (|R̄b − 1| < 0.005). The remaining channel, pa4 f220, exhibits a mild ∼ 1σ excess (R̄b = 1.042 ± 0.040).”
    - **Checks:** cross-check repeated summary vs Table 1; compute |R̄b-1| for the five channels; check pa4 f220 combined uncertainty matches ±0.040
    - **Verdict:** UNCERTAIN
    - **Notes:** Check not executed due to execution error; no computed comparison available.

2.  ⚠ **C2** (Results §4.4 (page 4) vs Table 1 (page 6) vs Conclusions bullet (page 7))
    
    - **Claim:** “pa4 f220 channel gives R̄b = 1.042 ± 0.018 (stat) ± 0.035 (beam)” and Conclusions also report “R̄b = 1.042 ± 0.040” for pa4 f220.
    - **Checks:** quadrature combination and rounding consistency
    - **Verdict:** UNCERTAIN
    - **Notes:** Check not executed due to execution error; no computed comparison available.

3.  ⚠ **C3** (Results §4.5 (page 4))
    
    - **Claim:** “for pa4 f220 the beam envelope is the dominant uncertainty source (σbeam = 0.035 versus σstat = 0.018)”
    - **Checks:** inequality/dominance check
    - **Verdict:** UNCERTAIN
    - **Notes:** Check not executed due to execution error; no computed comparison available.

4.  ⚠ **C4** (Methods §3.2 (page 3) and Limitations §5.5 (page 6))
    
    - **Claim:** “NMC = 480” simulations; “transfer-function uncertainty … ≲ 0.2% at ℓ < 2000” and again “≲ 0.2% at all scales below ℓ = 2000”
    - **Checks:** repeated-constant consistency check
    - **Verdict:** UNCERTAIN
    - **Notes:** Check not executed due to execution error; no computed comparison available.

5.  ⚠ **C5** (Methods §3.1 (page 3))
    
    - **Claim:** “We use split-cross spectra—averaging over the six independent pairs from the four time splits…”
    - **Checks:** combinatorics check
    - **Verdict:** UNCERTAIN
    - **Notes:** Check not executed due to execution error; no computed comparison available.

6.  ⚠ **C6** (Methods §3.5 (page 3))
    
    - **Claim:** “Define the half-differences d01 = (set0 − set1)/2 and d23 = (set2 − set3)/2.”
    - **Checks:** algebraic scaling check (half-difference definition)
    - **Verdict:** UNCERTAIN
    - **Notes:** Check not executed due to execution error; no computed comparison available.

7.  ⚠ **C7** (Data §2.2 (page 2))
    
    - **Claim:** “tSZ-deprojected variant adds a second constraint … at the cost of ∼ 10–30% additional noise power depending on angular scale.”
    - **Checks:** range sanity check
    - **Verdict:** UNCERTAIN
    - **Notes:** Check not executed due to execution error; no computed comparison available.

8.  ⚠ **C8** (Data §2.1 (page 2))
    
    - **Claim:** “The beam full-width at half-maximum (FWHM) ranges from ≈ 2.1′ at 90 GHz to ≈ 1.0′ at 220 GHz.”
    - **Checks:** monotonicity check of stated range endpoints
    - **Verdict:** UNCERTAIN
    - **Notes:** Check not executed due to execution error; no computed comparison available.

9.  ⚠ **C9** (Data §2.3 (page 2))
    
    - **Claim:** “The resulting sky fraction is fsky ≈ 0.40.”
    - **Checks:** probability range check
    - **Verdict:** UNCERTAIN
    - **Notes:** Check not executed due to execution error; no computed comparison available.

10.  ⚠ **C10** (Methods §3.1 (page 3))
    
    - **Claim:** “The binned estimator averages Ĉℓ into bandpowers of width Δℓ = 40.”
    - **Checks:** positive-integer check
    - **Verdict:** UNCERTAIN
    - **Notes:** Check not executed due to execution error; no computed comparison available.

### Limitations

- Only the provided parsed text of the PDF was used; no external datasets, code, or beam/spectrum arrays are available for recomputation-heavy checks.
- Figure-based numerical claims (e.g., Rb at specific ℓ, Ab thresholds) cannot be verified without underlying data; plot-pixel extraction is explicitly avoided.
- Several statements reference per-ℓ uncertainties, transfer functions, and beam envelopes that are not numerically specified in the text, limiting verification to algebraic/consistency and simple recombinations.
- Execution errors prevented running any checks: Sandbox policy violation: from-import of 'typing' is not allowed
