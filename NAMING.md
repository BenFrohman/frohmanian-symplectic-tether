# Naming glossary

This file follows the naming standard in [`BenFrohman/Clay-` `NAMING.md`](https://github.com/BenFrohman/Clay-/blob/main/NAMING.md).
**Nothing in this file is proved. The canonical open statement is OPEN.**

## Canonical names

| Role | Canonical name | Status |
|---|---|---|
| Core object | **Frohmanian Tether** (𝔉𝕋) | definition |
| Open statement | **Frohmanian Tether Hypothesis** (FT), parts (A) and (B) | **open** |
| Result, once proved | **Frohmanian Tether Theorem** | *reserved*: not used, because FT is not proved |

FT (A): the bending strain $(I-\tau\otimes\tau)S\tau$, with $\tau=\omega/|\omega|$, stays bounded where $|\omega|$ is large on $[0,T^*)$.
FT (B): that bound gives a $\tfrac12$-Hölder vorticity direction. Both parts are open; their Lean forms live in
[`periodic-ns-classical-continuation`](https://github.com/BenFrohman/periodic-ns-classical-continuation).

## Rules

- An open statement is called a **Hypothesis**. It is never called a "Law" or a "Theorem" in a paper or README.
  It becomes a Theorem only once it is proved.
- A Lean declaration written `theorem` is a kernel-checked implication from its stated hypotheses. When those
  hypotheses are open, the result is **conditional**, and the text says so.
- Code names in this repository are kept as historical records; this file maps them to the canonical names.
- Navier–Stokes global regularity remains open. Nothing here is a certificate.

## This repository

- `frohmanian_symplectic_tether_theorem`, `routeA_determines_kappa`, the uniqueness results and the 9-term Jacobi
  expansion are **proved** algebraic statements about 𝔗_F. They are not the Frohmanian Tether Hypothesis.
- `global_regularity`, `global_regularity_logloss`, `frohmanian_symplectic_tether_theorem_global` are **conditional**
  (on the named `Prop` inputs in the README) and concern only the modified, cubically damped model.
- κ is a free parameter here. The value κ = 3/2 used in some earlier drafts is a **modelling / normalization choice**,
  not a derived or sourced constant. (The coefficients 3/2 and 3i/8 in the field-level Jacobi test are computed
  Fourier coefficients, unrelated to that choice.)

## Related repository: `frohmanian-symplectic-tether-regularity`

The older [`frohmanian-symplectic-tether-regularity`](https://github.com/BenFrohman/frohmanian-symplectic-tether-regularity)
uses other code names. Its record is:

- `tethered_jacobi_identity_conditional` takes the Jacobi identity (`hident`, `hvanish`) as **hypotheses**; it does
  not prove Jacobi for the tethered bracket.
- Condition C2 for the ψ-slot `TetherKernel` is **false** in general: Lean shows it fails on an explicit two-mode
  shear (value −3/4 κπ), commit `a52c6af` (`C2Analysis.lean`). It holds only when δH/δω ∥ u (Beltrami).
- The velocity-slot `TetherKernelVel` satisfies C2 (`tetherKernelVel_C2`) and is the model to use; it is the one
  that matches 𝔗_F here.
