# Investigating Evidence for Dark Matter Using Galactic Rotation Curves

## Overview

This project compares observed galaxy rotation velocities with predictions from the gas and stellar components to investigate whether visible matter alone explains the observations. A mismatch is consistent with additional gravitating matter, often modelled as dark matter, but this analysis does not prove dark matter is the unique explanation.

## Research question

**Can the observed rotation speeds of galaxies be explained by visible matter alone, or do the data indicate a discrepancy consistent with additional unseen mass?**

## Galaxies studied

- **NGC 3198** — primary case study.
- **NGC 2683** — comparison galaxy.
- **DDO 154** — comparison galaxy.

The galaxies have different radial coverage and sampling, so their outermost points should not be treated as equivalent-radius comparisons.

## Method

The notebook loads SPARC-format rotation-curve data and calculates the baryonic rotation velocity:

V_bar(R) = sqrt(V_gas(R) * |V_gas(R)| + Υ_disk * V_disk(R)^2 + Υ_bul * V_bul(R)^2)

The adopted mass-to-light ratios are Υ_disk = 0.5 and Υ_bul = 0.7. These are assumptions used in the model, not universal values.

The notebook calculates:

- Velocity discrepancy: ΔV = V_obs - V_bar
- Velocity ratio: R_V = V_obs / V_bar

It plots observed and baryonic-predicted rotation curves, examines the discrepancy, and compares the three galaxies.

## Project files

The project contains the following files:

```text
dark-matter-rotation-curves/
├── README.md
├── dark_matter_rotation_curves.ipynb
├── NGC3198_rotmod.dat
├── NGC2683_rotmod.dat
└── DDO154_rotmod.dat
```

Make sure the notebook filename matches the actual file you upload. The three `.dat` files are the input data files used by the notebook.

## Data files

The notebook expects these files:

```text
NGC3198_rotmod.dat
NGC2683_rotmod.dat
DDO154_rotmod.dat
```

Expected whitespace-separated columns:

| Column | Meaning | Unit |
|---|---|---|
| `Rad` | Radius from the galactic centre | kpc |
| `Vobs` | Observed rotation velocity | km/s |
| `errV` | Observed-velocity uncertainty | km/s |
| `Vgas` | Gas contribution | km/s |
| `Vdisk` | Stellar disk contribution | km/s |
| `Vbul` | Bulge contribution | km/s |
| `SBdisk` | Disk surface brightness | Dataset-dependent |
| `SBbul` | Bulge surface brightness | Dataset-dependent |

Cite the exact source and version of the data files included with the project. Keep the Zenodo reference below only if it is the record from which the included files were obtained.

## Requirements

This project is designed to run in **Google Colab**, so you do not need to install Jupyter Notebook on your computer.

- A Google account to access Google Colab
- Python 3 (provided by the Colab runtime)
- NumPy
- pandas
- Matplotlib

These libraries are generally available in Colab. If a library is missing, run this in a notebook code cell:

```python
%pip install numpy pandas matplotlib
```

## How to run in Google Colab

1. Upload `dark_matter_rotation_curves.ipynb` to Google Drive, or open it directly in Google Colab.
2. In Colab, choose **File → Upload notebook** if you are opening the notebook from your computer. If it is stored in Google Drive, open it with Google Colab.
3. Upload the three `.dat` files using the **Files** panel on the left of Colab, or place them in Google Drive and update the paths in the notebook accordingly.
4. Check that the filenames in the notebook's data-loading code exactly match the uploaded filenames.
5. Run the notebook cells in order, or choose **Runtime → Run all**.
6. Check that the data load correctly and that all plots and summary outputs appear.

**Important:** Files uploaded directly to a Colab runtime are temporary and may disappear when the runtime is reset or disconnected. For a more persistent setup, keep the notebook and data files in Google Drive and load them from their Drive folder, or upload the data files to the runtime again when needed.

If you see `FileNotFoundError`, check that the `.dat` files are present in the current Colab runtime and that the file paths and filenames match exactly.

## Interpretation and limitations

A positive discrepancy means observed velocity exceeds the prediction from the adopted baryonic model at that radius. It is a model discrepancy, not a direct measurement of dark-matter mass.

Limitations include fixed mass-to-light ratios, observational errors, uncertainty in the baryonic model, and possible effects of galaxy distance and inclination. The `errV` error bars do not represent every source of model uncertainty. This is a small case study, not a statistical survey of all galaxies.

## References

1. Lelli, F., McGaugh, S. S., & Schombert, J. M. (2016). “SPARC: Mass Models for 175 Disk Galaxies with Spitzer Photometry and Accurate Rotation Curves.” *The Astronomical Journal*, 152, 157. https://doi.org/10.3847/0004-6256/152/6/157
2. SPARC database — Spitzer Photometry and Accurate Rotation Curves. https://astroweb.case.edu/SPARC/
3. Dataset record used for this project, if applicable: https://zenodo.org/records/16284118

## Reproducibility note

The notebook contains the analysis code; the `.dat` files contain the input measurements. Include the notebook and the exact data files used when sharing the repository.
