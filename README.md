# MEA Draft v1.1 — Supporting Numerical Evidence Package

Manuscript: "Reduced-Order Modelling of Magnetically Coupled Engineering Systems" (P. D. Markov)
Prepared for later versioned archiving (GitHub + Zenodo DOI). All values were regenerated from the
notebook code and independently re-verified against the Draft v1.1 text on 2026-08-24.

## Newly generated reviewer-response evidence (this package)

| File | Content |
|---|---|
| case1e_finite_zero_fits.csv | All 12 finite-zero second-order scalar fits (6 perturbations x 2 outputs): K, wn, zeta, tau_z, zero location, |z|/wn, held-out NRMSE, AICc/BIC, optimiser status |
| case1e_finite_zero_comparison.csv | Direct G1/G2/G2z comparison incl. improvements and delta-AICc |
| case1e_finite_zero_summary.json | Acceptance-criterion evaluation per output, incl. gain-sign and left-half-plane zero diagnostics |
| case1b_state_space_identification_rerun.csv | Per-condition identified (A,B), modal quantities, held-out NRMSE (re-run of original export) |
| case1b_models.npz | Identified (A,B) matrices for the six local models |
| case1c_noise_floor_metrics.csv | Noise-floor-normalised held-out errors E_NF per condition |
| case1c_window_sensitivity.csv | Modal topology/quantities for 2/3/5/10 us identification windows (24 combinations) |
| case1f_lopo_predictions.csv | Six-fold leave-one-perturbation-out predictions: NRMSE, E_NF, modal quantities, fold type |
| case1f_lopo_models.npz | Common (A,B) model per LOPO fold |
| case1g_exact_transfer_functions.json | Exact nominal (A0,B0), exact G_theta_u(s) and G_r_u(s) coefficients, zeros, signed DC gains, relative degree, modal values; known-linearisation recovery summary |
| case1g_known_linearisation_recovery.csv | Per-model Frobenius and modal recovery errors vs the exact nominal linearisation |
| case2a_structural_sweep_corrected.csv | Corrected structural ROM sweep (unit-tip exact modal mass m_beam/4), 51 frequencies |
| case2a_summary_corrected.json | Corrected structural constants: m1=9.750e-4 kg, k1=4120.8 N/m, c1=0.08018 N s/m; ROM errors 1.43%/3.94%; tip point-force convention |
| case3c_frf_metrics.csv | Complete-FRF distance metrics: exact vs canonical, exact vs structural, Case1B/LOPO vs structural at zeta_m=0.78 |
| case3d_best_fit_exact.csv | Best-achievable structural damping for exact channels |
| case3d_best_fit_lopo.csv | Best-achievable structural damping per LOPO fold |
| case3d_summary.json | Frozen Case 3C/3D protocol and optimisation summary |

## Pre-existing case evidence (archived separately by the author)
case1_configuration.json, case1_candidate_summary.json, case1_model_fits.csv,
case1_frequency_response.csv, case1_final_characterization.csv, case1b_state_space_identification.csv,
case1b_summary.json, case1d_summary.json, case1d_modal_parameters.csv, case1d_magnetic_coupling.csv,
case2b_summary.json, case2b_stiffness_coupling.csv, case2b_damping_sweep.csv,
case2b_collapse_metric.csv, case2b_plasma_matched_curve.csv, case3a_summary.json,
case3a_cross_domain_curves.csv, case3a_parameter_response_distance.csv,
case3b_full_factorial.csv, case3b_coupling_invariance.csv, case3b_monotonicity.csv,
case3b_unique_damping_comparisons.csv.

## Reproducibility
- Surrogate coefficients, integration settings and seed (20260819) are listed in Table 1 of the manuscript.
- All metrics use the frozen protocols stated in Sections 2.3, 2.6 and 2.7.
- Structural correction in v1.1: exact unit-tip-normalised modal mass m_j = m_beam/4; rounded ROM
  errors are unchanged (median 1.43%, maximum 3.94%).
