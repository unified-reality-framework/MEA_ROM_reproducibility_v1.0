# MEA ROM Reproducibility Archive v1.0
## Reduced-Order Modelling of Magnetically Coupled Engineering Systems
**Author:** Paul D. Markov  
**Research programme:** Harmony Research Initiative  
**Repository version:** 1.0  
**Manuscript:** *Reduced-Order Modelling of Magnetically Coupled Engineering Systems*
This repository contains the numerical code, machine-readable evidence,
supporting data, and publication-figure materials for the manuscript
*Reduced-Order Modelling of Magnetically Coupled Engineering Systems*.
The study evaluates a hierarchical cross-domain reduced-order modelling
procedure using two deliberately dissimilar numerical systems: a controlled
stochastic plasma-inspired surrogate and an Euler--Bernoulli structural
benchmark. Domain-specific reduced models are first assessed independently,
after which pole-derived modal correspondence is tested and then subjected to
the stronger requirement of complete input--output transfer-function
correspondence.
The principal methodological result is that similarity in shared pole-derived
modal coordinates can identify candidate cross-domain correspondence but does
not establish complete input--output correspondence when transfer-function
zeros, relative degree, gain, phase, residues, or input/output participation
remain incompatible.
## Scope
The plasma component is a controlled nonlinear stochastic numerical surrogate.
It is not an experimentally validated, kinetic, fluid, or PIC--MCC plasma
model. Plasma-side verification in this repository therefore concerns
identification, prediction, tangent-linearisation recovery, and robustness
within the stated surrogate operating range.
The structural component is an analytical Euler--Bernoulli cantilever
benchmark. The first-mode reduced model is assessed against a four-mode
analytical reference using a transverse point force applied at the free tip.
It is not presented as experimental validation of a specific magnetic
actuator or material system.
## Repository Structure
```text
MEA_ROM_reproducibility_v1.0/
├── README.md
├── CITATION.cff
├── LICENSE
├── MANIFEST_SHA256.txt
├── code/
├── data/
├── figures/
└── supplementary/

* code/ — numerical notebooks/scripts used for Cases 1–3 and supporting
    analyses.
* data/ — machine-readable numerical evidence and summary records.
* figures/ — publication figures and/or figure-generation outputs.
* supplementary/ — convenience audit records assembled from the primary
    machine-readable evidence.

Numerical Reproduction Order

The principal analysis sequence is:

1. Case 1 — Plasma surrogate and reduced-model identification
2. Case 2 — Structural reduced-order benchmark
3. Case 3 — Cross-domain canonical and complete-FRF comparison

The fixed stochastic seed for the plasma simulations is:

20260819

The primary Savitzky–Golay preprocessing setting is:

window_length = 101
polyorder = 3

Case 1H additionally evaluates preprocessing sensitivity over:

window_length = {51, 101, 151}
polyorder     = {2, 3, 4}

for a total of 54 local state-space identifications. All 54 retain stable
complex-conjugate modal topology.

Evidence Map

Analysis	Primary evidence
Scalar finite-zero model selection	case1e_finite_zero_fits.csv, case1e_finite_zero_comparison.csv, case1e_finite_zero_summary.json
Local coupled state-space identification	case1b_state_space_identification_rerun.csv, case1b_models.npz
Noise-floor verification	case1c_noise_floor_metrics.csv
Identification-window sensitivity	case1c_window_sensitivity.csv
Leave-one-perturbation-out verification	case1f_lopo_predictions.csv, case1f_lopo_models.npz
Nominal tangent-linearisation recovery	case1g_exact_transfer_functions.json, case1g_known_linearisation_recovery.csv
Savitzky–Golay preprocessing sensitivity	case1h_savgol_sensitivity_all_fits.csv, case1h_savgol_sensitivity_summary.csv
Corrected structural benchmark	case2a_structural_sweep_corrected.csv, case2a_summary_corrected.json
Complete input–output FRF comparison	case3c_frf_metrics.csv
Best-achievable structural damping	case3d_best_fit_exact.csv, case3d_best_fit_lopo.csv, case3d_summary.json
Fold-wise reviewer audit	supplementary/lopo_foldwise_audit_summary.csv

Reviewer-Response and Verification Evidence

Case 1E — Finite-Zero Scalar Models

case1e_finite_zero_fits.csv

Contains all 12 finite-zero second-order scalar fits across six magnetic
perturbations and two outputs, including fitted gain, natural frequency,
damping ratio, zero time scale, zero location, normalised zero location,
held-out NRMSE, AICc/BIC, and optimiser status.

case1e_finite_zero_comparison.csv

Provides direct comparison of the first-order, zero-free second-order, and
finite-zero second-order candidates, including held-out prediction improvement
and descriptive AICc differences.

case1e_finite_zero_summary.json

Contains output-specific evaluation against the pre-specified scalar
acceptance criteria and diagnostics for gain sign and zero half-plane.

The finite-zero model family is structurally capable of representing the
nominal tangent-linear scalar channels. Failure of the pre-specified criterion
for the temperature-like output is therefore interpreted as an empirical
finite-amplitude identification/acceptance result rather than structural
insufficiency of the finite-zero model family.

Case 1B/1C — Coupled State-Space Verification

case1b_state_space_identification_rerun.csv

Contains the six locally identified state-space models and associated modal
and held-out predictive quantities.

case1b_models.npz

Contains the corresponding identified A and B matrices.

case1c_noise_floor_metrics.csv

Contains held-out deterministic prediction errors normalised by the
realisation-to-realisation stochastic spread.

case1c_window_sensitivity.csv

Contains modal topology and quantities for 2, 3, 5, and 10 microsecond
identification windows across all six perturbations.

Case 1F — Leave-One-Perturbation-Out Verification

case1f_lopo_predictions.csv

Contains the six LOPO folds, including omitted perturbation, interpolation or
edge-extrapolation classification, NRMSE, noise-floor-normalised errors, and
modal quantities.

case1f_lopo_models.npz

Contains the common A and B model identified in each LOPO fold.

supplementary/lopo_foldwise_audit_summary.csv

Provides a six-row convenience audit linking each omitted perturbation to its
predictive metrics, modal quantities, complete-FRF discrepancies, and
best-achievable structural damping results.

Case 1G — Nominal Tangent-Linearisation Recovery

case1g_exact_transfer_functions.json

Contains the analytically derived nominal tangent matrices A0 and B0,
exact scalar transfer-function coefficients, poles, finite zeros, signed DC
gains, relative degrees, and nominal modal quantities.

case1g_known_linearisation_recovery.csv

Contains the historical analysis output comparing identified models with the
nominal tangent reference. The filename predates the manuscript terminology
change from “known linearisation recovery” to “nominal tangent-linearisation
recovery” and is retained unchanged for provenance.

The tangent reference is exact only for infinitesimal deterministic
perturbations about the nominal equilibrium. Finite-amplitude stochastic
identifications may additionally contain nonlinear, stochastic-averaging,
preprocessing, and estimation effects.

Case 1H — Savitzky–Golay Preprocessing Sensitivity

case1h_savgol_sensitivity_all_fits.csv

Contains all 54 local state-space identifications over the 3 x 3
Savitzky–Golay preprocessing grid and six magnetic perturbations.

case1h_savgol_sensitivity_summary.csv

Contains setting-level topology, modal estimates, tangent-reference recovery
errors, and deviations from the primary 101-sample, third-order setting.

All 54 fits retain stable complex-conjugate topology. Damping remains
comparatively stable across the evaluated grid, while the longest,
lowest-order smoothing setting produces the largest characteristic-frequency
and matrix-recovery deviations.

Case 2A — Corrected Structural Benchmark

case2a_structural_sweep_corrected.csv

Contains the corrected first-mode versus four-mode structural sweep.

case2a_summary_corrected.json

Contains the corrected structural constants based on the exact
unit-tip-normalised modal mass,

m1 = 9.750e-4 kg
k1 = 4120.8 N/m
c1 = 0.08018 N s/m

together with the transverse free-tip point-force convention. The corrected
median and maximum first-mode ROM errors remain approximately 1.43% and
3.94%, respectively.

Case 3C — Complete Input–Output FRF Comparison

case3c_frf_metrics.csv

Contains the complete-FRF comparisons for the exact nominal plasma channels,
their denominator-only canonical projections, locally identified models, and
LOPO models.

The complex quantity reported in the manuscript as (D^{(c)}) is a
plasma-reference relative complex-response discrepancy, not a symmetric
metric. The plasma response supplies the normalising norm in all reported
plasma–structural comparisons.

Case 3D — Best-Achievable Structural Correspondence

case3d_best_fit_exact.csv

Contains the best-achievable structural damping results for the exact plasma
channels.

case3d_best_fit_lopo.csv

Contains the corresponding optimisation for each LOPO model and output.

case3d_summary.json

Contains the frozen Case 3C/3D comparison and optimisation protocol and
summary results.

Pre-Existing Case Evidence

The repository also retains earlier case outputs used during development and
cross-checking, including:

case1_configuration.json
case1_candidate_summary.json
case1_model_fits.csv
case1_frequency_response.csv
case1_final_characterization.csv
case1b_state_space_identification.csv
case1b_summary.json
case1d_summary.json
case1d_modal_parameters.csv
case1d_magnetic_coupling.csv
case2b_summary.json
case2b_stiffness_coupling.csv
case2b_damping_sweep.csv
case2b_collapse_metric.csv
case2b_plasma_matched_curve.csv
case3a_summary.json
case3a_cross_domain_curves.csv
case3a_parameter_response_distance.csv
case3b_full_factorial.csv
case3b_coupling_invariance.csv
case3b_monotonicity.csv
case3b_unique_damping_comparisons.csv

These historical files are retained for provenance. Where terminology or
numerical definitions were subsequently refined, the reviewer-response and
corrected evidence listed above should be treated as the publication-release
evidence.

Metric Conventions

NRMSE

Held-out NRMSE uses the standard deviation of the held-out ensemble-mean
trajectory over the same post-step interval as its normalising scale. A
response-range fallback is used only if that standard deviation is
numerically vanishing.

Noise-Floor-Normalised Error

For each retained state, the pointwise sample standard deviation is calculated
across the 15 offset-corrected held-out realisations and RMS-aggregated over
the post-step interval. (E_{\mathrm{NF}}<1) therefore indicates that the
deterministic ROM discrepancy from the held-out ensemble mean is smaller than
the RMS stochastic realisation spread over the same interval.

Information Criteria

AICc and BIC are used as comparative descriptive model-selection diagnostics.
Because residual samples along each transient are temporally correlated, they
are not interpreted as formal independent-sample likelihood tests.

Complete Complex Response

The complete-FRF complex discrepancy is reference dependent:

plasma response = reference norm
structural response = comparison response

It is therefore described as a plasma-reference relative complex-response
discrepancy rather than a symmetric response distance.

Reproducibility Notes

* Fixed plasma stochastic seed: 20260819.
* Six magnetic perturbations are evaluated.
* Fifty stochastic realisations are generated per perturbation.
* Thirty-five realisations are used for identification and fifteen for
    held-out assessment.
* Primary Savitzky–Golay preprocessing: window length 101, polynomial order
* Case 1H preprocessing sensitivity: window lengths 51, 101, 151;
    polynomial orders 2, 3, 4.
* Complete FRF comparisons use 1001 uniformly spaced points over
    05 <= Omega <= 2.5.
* No post hoc output selection, fitted phase correction, peak normalisation,
    residue fitting, or frequency-window selection is used in the complete-FRF
    comparison.
* The corrected structural benchmark uses the exact unit-tip-normalised
    first-mode mass m_beam/4 and a transverse free-tip point force.

Integrity and Provenance

MANIFEST_SHA256.txt contains SHA-256 hashes for the frozen release
artifacts. The manifest should be regenerated whenever the release contents
change.

Historical filenames are retained where practical to preserve provenance,
even when manuscript terminology has subsequently been refined.

Citation

Citation metadata are provided in CITATION.cff.

A DOI-backed archival citation will be added following publication of the
versioned repository release.

Licence

See LICENSE for the licence applying to the repository materials.
