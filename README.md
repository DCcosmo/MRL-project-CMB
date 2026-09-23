# MRL-project-CMB

Data products, posterior chains, and Jupyter notebooks associated with the paper

**The Primordial power spectrum from the largest to smallest CMB scales**

Debabrata Chandra, Dhiraj Kumar Hazra, Arman Shafieloo, and Tarun Souradeep

- arXiv: [2608.24413](https://arxiv.org/abs/2608.24413)
- INSPIRE: [literature/3195743](https://inspirehep.net/literature/3195743)

---

## Overview

This repository contains the numerical products and analysis chains associated with our reconstruction of the primordial power spectrum (PPS) from CMB observations spanning the largest to the smallest scales currently accessible with Planck, ACT, and SPT.

The analysis uses two complementary approaches:

1. **Free-form reconstruction** of the primordial power spectrum using the Modified Richardson--Lucy (MRL) deconvolution algorithm, including Gaussian, diffusive, and total-variation regularization.

2. **Parametric Bayesian reconstruction** using a double-tilt primordial power spectrum, with posterior sampling to constrain the model parameters.

The repository contains:

- reconstructed primordial power spectra from the observed CMB data;
- reconstruction products obtained from simulations used in the statistical-significance analysis;
- posterior chains from the parametric analyses;
- Cobaya input and updated configuration files;
- PolyChord evidence outputs where applicable;
- Jupyter notebooks used to generate the figures presented in the paper.

The original Planck, ACT, and SPT observational data and likelihood packages are **not redistributed here**. They are publicly available from the respective collaborations and are described and cited in the paper.

---

## CMB datasets

The analysis uses:

### Planck PR4 CamSpec-NPIPE

Planck PR4 CamSpec-NPIPE temperature and polarization spectra are used both independently and in combination with the ground-based datasets.

### ACT DR6

ACT DR6 temperature and polarization measurements are used for the reconstruction and parametric analyses.

Public ACT DR6 products are available from NASA LAMBDA:

https://lambda.gsfc.nasa.gov/product/act/act_dr6.02/

### SPT-3G D1

SPT-3G D1 temperature and polarization measurements are used for the free-form reconstruction and consistency analyses.

Public SPT-3G D1 products are available from NASA LAMBDA:

https://lambda.gsfc.nasa.gov/product/spt/spt_3gd1/

Please refer to the paper for the precise multipole ranges, dataset combinations, foreground treatment, background cosmologies, and likelihood choices used in each analysis.

---

## Repository structure

```text
MRL-project-CMB/
│
├── ACT/
│   ├── coadded_act_data_n_act_background/
│   ├── coadded_act_data_n_planck18_background/
│   └── coadded_act_data_n_camspec12.6v_background/
│
├── SPT/
│   ├── spt_data_n_spt_background/
│   ├── spt_data_n_planck18_background/
│   └── spt_data_n_camspec12.6v_background/
│
├── CamSpec12_6v/
│
├── CamSpec12_6v_n_ACT/
│
├── CamSpec12_6v_n_SPT/
│
├── chains/
│
├── Posterior_plots/
│
├── Power_spectrum_confidence_interval/
│
├── .gitattributes
└── README.md
```

### `CamSpec12_6v/`

Free-form MRL reconstruction using Planck PR4 CamSpec-NPIPE data and the corresponding Planck PR4 best-fit background cosmology.

The directory contains:

- `real/` — reconstructions obtained from the observed data;
- `simulation/` — reconstructions from simulated power-law CMB realizations used to estimate confidence intervals;
- `Figure 2_n_3.ipynb` — notebook used for Figs. 2 and 3.

### `ACT/`

Free-form reconstructions of the PPS from ACT DR6 data using different fixed background cosmologies.

The three subdirectories correspond to:

- `coadded_act_data_n_act_background/`  
  ACT data reconstructed using the ACT DR6 best-fit background cosmology.

- `coadded_act_data_n_planck18_background/`  
  ACT data reconstructed using the Planck PR3 best-fit background cosmology.

- `coadded_act_data_n_camspec12.6v_background/`  
  ACT data reconstructed using the Planck PR4 CamSpec-NPIPE best-fit background cosmology.

Each directory contains reconstruction products from the observed data, simulation products where applicable, and the corresponding figure notebook.

### `SPT/`

Free-form reconstructions of the PPS from SPT-3G D1 data using different fixed background cosmologies.

The three subdirectories correspond to:

- `spt_data_n_spt_background/`  
  SPT data reconstructed using the SPT best-fit background cosmology.

- `spt_data_n_planck18_background/`  
  SPT data reconstructed using the Planck PR3 best-fit background cosmology.

- `spt_data_n_camspec12.6v_background/`  
  SPT data reconstructed using the Planck PR4 CamSpec-NPIPE best-fit background cosmology.

### `CamSpec12_6v_n_ACT/`

Free-form reconstruction using the combined Planck PR4 CamSpec-NPIPE and ACT DR6 data.

The plotting notebook is:

```text
CamSpec12_6v_n_ACT/Figure 18.ipynb
```

### `CamSpec12_6v_n_SPT/`

Free-form reconstruction using the combined Planck PR4 CamSpec-NPIPE and SPT-3G D1 data.

The plotting notebook is:

```text
CamSpec12_6v_n_SPT/Figure 19.ipynb
```

### `chains/`

Posterior chains and associated configuration/output files for the parametric double-tilt analyses.

Depending on the run, the directory contains:

```text
*.1.txt, *.2.txt, ...
```

posterior samples,

```text
*.input.yaml
```

input configurations,

```text
*.updated.yaml
```

the corresponding updated Cobaya configurations, and

```text
*.logZ
```

PolyChord Bayesian-evidence outputs where applicable.

The chain filenames encode the dataset combination and analysis assumptions, including quantities such as

- Planck PR3 versus Planck PR4/CamSpec;
- ACT-only versus Planck+ACT;
- TT-only versus TTTEEE;
- free or fixed break scale;
- multipole cuts;
- fixed versus varied nuisance parameters.

### `Posterior_plots/`

Contains

```text
Cobaya_run_plot_ns1_vs_ns2.ipynb
```

used to generate the posterior-distribution plots for the parametric double-tilt analyses.

### `Power_spectrum_confidence_interval/`

Contains

```text
Power_spec_fgivenx.ipynb
```

used to generate primordial-power-spectrum posterior confidence intervals from the Bayesian chains.

## Free-form reconstruction products

For the main MRL reconstruction directories, the stored numerical products include the primordial wavenumber grid, baseline power-law spectrum, and reconstructed spectra obtained using the different regularization prescriptions.

Typical filenames include

```text
k_grid_...
base_pk_...
rec_pks_MRL_...
rec_pks_smthMRL_...
rec_pks_regMRL_...
rec_pks_MRLTV_...
```

where the different reconstruction labels correspond to the methods discussed in the paper.

Simulation directories contain analogous products reconstructed from power-law CMB realizations, for example

```text
rec_pks_mock_base_regMRL_...
rec_pks_mock_base_MRLTV_...
```

These simulations are used to assess the statistical significance of structures appearing in the PPS reconstructed from the real data.

---

## Figure reproduction guide

The notebooks and numerical products correspond to the figures in the accompanying paper as follows.

| Figure | Content | Notebook / repository location |
|---|---|---|
| **Fig. 1** | CMB radiative-transfer kernels \(\mathcal{G}_{\ell k}^{XY}\) | Generated using CAMB code |
| **Figs. 2–3** | Planck PR4 CamSpec-NPIPE MRL reconstruction and simulation-based confidence intervals | `CamSpec12_6v/Figure 2_n_3.ipynb` |
| **Figs. 4–5** | ACT DR6 reconstruction using the ACT best-fit background cosmology | `ACT/coadded_act_data_n_act_background/Figure 4_n_5.ipynb` |
| **Figs. 6–7** | ACT DR6 reconstruction using the Planck PR3 best-fit background cosmology | `ACT/coadded_act_data_n_planck18_background/Figure 6_n_7.ipynb` |
| **Figs. 8–9** | ACT DR6 reconstruction using the Planck PR4 CamSpec-NPIPE best-fit background cosmology | `ACT/coadded_act_data_n_camspec12.6v_background/Figure 8_n_9.ipynb` |
| **Figs. 10–11** | SPT-3G D1 reconstruction using the SPT best-fit background cosmology | `SPT/spt_data_n_spt_background/Figure 10_n_11.ipynb` |
| **Figs. 12–13** | SPT-3G D1 reconstruction using the Planck PR3 best-fit background cosmology | `SPT/spt_data_n_planck18_background/Figure 12_n_13.ipynb` |
| **Figs. 14–15** | SPT-3G D1 reconstruction using the Planck PR4 CamSpec-NPIPE best-fit background cosmology | `SPT/spt_data_n_camspec12.6v_background/Figure 14_n_15.ipynb` |
| **Fig. 16** | Comparison of the CamSpec, ACT and SPT MRL-DR and MRL-TVR reconstructed primordial spectra | Uses products in `CamSpec12_6v/`, `ACT/coadded_act_data_n_act_background/`, and `SPT/spt_data_n_spt_background/`; no dedicated notebook currently included |
| **Fig. 17** | Null distributions of the weighted Pearson correlations between reconstructed CamSpec, ACT and SPT spectra | Uses the observed and simulated reconstruction products in the corresponding CamSpec/ACT/SPT directories; no dedicated notebook currently included |
| **Fig. 18** | Combined Planck PR4 CamSpec-NPIPE + ACT DR6 reconstruction | `CamSpec12_6v_n_ACT/Figure 18.ipynb` |
| **Fig. 19** | Combined Planck PR4 CamSpec-NPIPE + SPT-3G D1 reconstruction | `CamSpec12_6v_n_SPT/Figure 19.ipynb` |
| **Fig. 20** | Double-tilt analysis of P18-TT + ACT-TT with the broad \(k_{\rm break}\) prior | `Posterior_plots/Cobaya_run_plot_ns1_vs_ns2.ipynb`, `Power_spectum_confidence_interval/Power_spec_fgivenx.ipynb`, and chain prefix `double_tilt_planckcut_actdr6mflike_lmin_lmax_custom_tt_only_PC_25D_CC` |
| **Fig. 21** | P18 + ACT analysis with restricted \(k_{\rm break}\), for TT and TTTEEE combinations | Posterior and PPS notebooks; corresponding `kbreak_lower_bound_0.1` chains in `chains/` |
| **Fig. 22** | Double-tilt P18 + ACT TTTEEE analysis with the broad \(k_{\rm break}\) prior | Posterior and PPS notebooks; chain prefix `double_tilt_planckcut_actdr6mflike_lmin_lmax_custom_PC_25D_CC` |
| **Fig. 23** | \(n_{s1}\)-\(n_{s2}\) constraints for fixed \(k_{\rm break}=0.165\,{\rm Mpc}^{-1}\) for different likelihood/nuisance choices | `Posterior_plots/Cobaya_run_plot_ns1_vs_ns2.ipynb`; corresponding `kbreak_fix_0.165` chains |
| **Fig. 24** | Double-tilt PPS confidence intervals for the Planck PR3/PR4 + ACT combinations at fixed \(k_{\rm break}=0.165\,{\rm Mpc}^{-1}\) | `Power_spectum_confidence_interval/Power_spec_fgivenx.ipynb`; corresponding `planckcut` and `npipecut` chains |
| **Fig. 25** | ACT-only double-tilt constraints and PPS confidence intervals for TT and TTTEEE | Posterior and PPS notebooks; `double_tilt_actdr6mflike_*lmax_4810*` chains |
| **Fig. 26** | ACT TTTEEE analysis with \(k_{\rm break}=0.30\,{\rm Mpc}^{-1}\) and nuisance parameters fixed at their baseline best-fit values | `Posterior_plots/Cobaya_run_plot_ns1_vs_ns2.ipynb`; chain prefix `double_tilt_actdr6mflike_lmax_4810_tausroll2prior_kbreak_fix_0.3_all_nui_params_fixed_at_bf_CC` |

---

## Parametric chain naming

Some frequently occurring terms in the chain filenames are:

```text
planckcut
```

Planck PR3 + ACT analysis,

```text
npipecut
```

Planck PR4 CamSpec-NPIPE + ACT analysis,

```text
actdr6mflike
```

ACT DR6 likelihood,

```text
tt_only
```

temperature-only analysis,

```text
kbreak_fix_0.165
```

fixed break scale \(k_{\rm break}=0.165\,{\rm Mpc}^{-1}\),

```text
kbreak_fix_0.3
```

fixed break scale \(k_{\rm break}=0.30\,{\rm Mpc}^{-1}\),

and

```text
all_nui_params_fixed_at_bf
```

Planck (PR3 and PR4) and ACT nuisance parameters fixed to their baseline best-fit values.

For the exact priors and likelihood combinations associated with each chain, consult the corresponding `.input.yaml` and `.updated.yaml` files together with the analysis description in the paper.

---

## Git Large File Storage

Large numerical products, posterior chains, and Jupyter notebooks in this repository are tracked using **Git Large File Storage (Git LFS)**.

Git LFS must therefore be installed when cloning the repository. Otherwise, Git may retrieve only small LFS pointer files rather than the actual data.

### Clone the repository

```bash
git lfs install
git clone https://github.com/DCcosmo/MRL-project-CMB.git
cd MRL-project-CMB
git lfs pull
```

Git LFS documentation is available at:

https://git-lfs.com/

---

## Using the notebooks

After cloning the repository with Git LFS enabled, the Jupyter notebooks can be opened in the usual way, for example

```bash
jupyter lab
```

or

```bash
jupyter notebook
```

and then navigating to the relevant notebook listed in the figure-reproduction table above.

The notebooks use stored numerical reconstruction products or posterior chains to generate the corresponding figures.

The repository is intended primarily to make the **derived numerical results and paper figures reproducible**. It should not be interpreted as a packaged implementation of the complete analysis pipeline used to generate every reconstruction or likelihood chain from the original observational likelihoods.

For methodology, likelihood definitions, priors, reconstruction settings, regularization parameters, simulation procedure, multipole cuts, and background cosmologies, please consult the accompanying paper.

---

## Data availability

The observational CMB data used in this work are publicly available from the respective Planck, ACT, and SPT data releases described and cited in the paper.

The derived numerical products used in the analysis, the MCMC and PolyChord posterior-sampling chains for the parametric analyses, and the Jupyter notebooks used to reproduce the figures are provided in this repository.

No proprietary observational data are used in this work.

---

## Citation

If you use the results, chains, or numerical products from this repository, please cite the accompanying paper:

```bibtex
@article{Chandra:2026byw,
    author = "Chandra, Debabrata and Hazra, Dhiraj Kumar and Shafieloo, Arman and Souradeep, Tarun",
    title = "{The Primordial power spectrum from the largest to smallest CMB scales}",
    eprint = "2608.24413",
    archivePrefix = "arXiv",
    primaryClass = "astro-ph.CO",
    month = "8",
    year = "2026"
}
```

The bibliographic information can be updated with the journal reference and DOI after publication.

---

## Contact

For questions concerning the analysis or the material in this repository, please contact the authors of the accompanying paper.

Corresponding author information is provided in the paper.

---

## Notes on reproducibility

The repository records the numerical products associated with the version of the analysis described in arXiv:2608.24413.

For long-term reproducibility, users should refer to a tagged release corresponding to the published version of the paper when such a release is available.
