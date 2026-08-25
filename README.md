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
