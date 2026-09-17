# PyHC Package Evaluation: SWVO

**Package**: SWVO  
**Version Evaluated**: 1.2.7 (`main` at commit `9bf8200`, 2026-09-15)  
**Repository**: https://github.com/GFZ/SWVO  
**Date**: 2026-09-16  
**Evaluator**: Claude Fable 5.1  

## Standards Compliance Summary

| Standard | Grade | Status |
|----------|-------|--------|
| Community | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Public GitHub development, contribution guide, and Contributor Covenant code of conduct all present |
| Documentation | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | Read the Docs site with numpydoc API reference, but roughly a third of public functions/classes lack docstrings and almost none include examples |
| Testing | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | 700+ pytest tests, integration tests, 83% Coveralls coverage, CI matrix across Python 3.11–3.14 |
| Software Maturity | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Installable, on PyPI with regular semver releases, ruff/ty enforced; Windows untested, dev tools in runtime deps, heavy test data in repo |
| PHEP 3 | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | Python 3.11–3.14 supported, but numpy/scipy/xarray minimum pins drop feature series still inside the 24‑month window |
| License | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Apache‑2.0, permissive and OSI‑approved, REUSE‑compliant |

## Executive Summary

**SWVO** (Space Weather Virtual Observatory, GFZ Helmholtz Centre for Geosciences) demonstrates strong overall compliance with PyHC standards, meeting every "must" in four of the six categories. The package excels in testing and engineering hygiene: 713 pytest tests including cross‑source integration tests, 83% measured coverage, ruff and ty type checking enforced in CI and pre‑commit, and a steady cadence of semver releases to PyPI. The most significant gaps are incomplete docstring coverage (29 of 59 modules and 37 of 127 public functions lack docstrings; only 2 functions have examples) and overly aggressive minimum dependency pins on numpy, scipy, and xarray that fail the PyHC PHEP 3 compliance checker. SWVO fills a genuine niche by unifying access to Kp, Hp, Dst, F10.7, SuperMAG, OMNI, real‑time L1 solar wind, and GFZ ensemble forecast products behind a single reader interface. To reach full compliance, the primary focus should be completing docstrings across the `RBMDataSet` subpackage and relaxing the numpy, scipy, and xarray lower bounds to the PHEP 3‑suggested versions.

## Detailed Assessment

### 1. Community ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

All required community sub‑standards are met: the code is developed openly on GitHub with a contribution guide and a Contributor Covenant code of conduct. Some functionality overlaps with other ecosystem tools, but the GFZ forecast products are unique.

- **Open Development**\*: ✅ Developed publicly at https://github.com/GFZ/SWVO since June 2025 with 84 pull requests (76 merged), 53 issues (50 closed), and external contributors (`DoctorRabbit55`, `Simon060899`, `Parvathy-jani`, `DmitriiGurev`, `xandrd`) alongside the core GFZ team.
- **Duplication**: ✅ SWVO is not a fork and reuses upstream clients where they exist (e.g., the MIDL reader wraps the official `csem-midl` package). Index and archival coverage overlaps substantially with GeospaceLAB, whose datahub already downloads GFZ Kp/ap (including the nowcast), GFZ Hpo (Hp30/Hp60), GFZ SN/F10.7, WDC Dst/AE/ASY‑SYM, and SuperMAG indices, and more loosely with PySPEDAS (`noaa_load_kp`, Kyoto Dst/AE, OMNI, ACE, DSCOVR), SpacePy (`spacepy.omni`), and HAPI clients. What is not available elsewhere in PyHC is the GFZ‑specific forecast and model products (Kp/Hp ensemble forecasts, SWIFT and ENLIL ensemble solar wind, PAGER plasmasphere, IMAP nowcast, MIDL merged L1 record) and the unified `BaseIO` reader interface.
- **Collaboration**\*: ✅ `CONTRIBUTING.md` (mirrored in the docs as a Contributing Guide) covers forking, branching, ruff/ty requirements, running tests, PR expectations, and states that ruff failures must be resolved and at least one maintainer must approve before merging. No issue or PR templates exist in `.github/`.
- **Code of Conduct**\*: ✅ `CODE_OF_CONDUCT.md` is the Contributor Covenant 2.x text with GFZ‑specific contact details.

### 2. Documentation ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

High‑level documentation is solid and published on Read the Docs with a numpydoc‑rendered API reference, but docstring coverage and content fall short of the "all functions, classes, and modules" requirement.

- **Docstrings**\*: ⚠️ AST analysis of `swvo/` finds docstrings on 30 of 59 modules, 37 of 52 public classes, and 90 of 127 public functions/methods. Gaps are concentrated in `swvo/io/RBMDataSet/` (e.g., `bin_and_interpolate_to_model_grid`, `identify_orbits`, `linearize_trajectories`, `interp_flux`, every enum in `custom_enums.py`) plus `swvo/io/exceptions.py`, `swvo/io/utils.py`, and `swvo/logger.py`.
- **Docstring Content**\*: ⚠️ Of the 90 documented public functions, 67 have a `Parameters` section and 62 have a `Returns` section, but only 2 (`swvo/io/omni/variables.py:180`, `swvo/io/sme/supermag.py:313`) include an `Examples` section. The standard requires examples. Some docstrings also drift from their signatures: `PlasmaspherePredictionReader` (`swvo/io/plasmasphere/read_plasmasphere.py:130`) documents a `folder : str` parameter, but the constructor takes `data_dir: Optional[Path]`, and the documented exceptions omit the `ValueError` raised when the environment variable is unset.
- **Docstring Standards**\*: ✅ Existing docstrings consistently follow numpydoc conventions (see `swvo/io/base.py`, `swvo/io/kp/omni.py`), and `docs/conf.py` loads the `numpydoc` and `napoleon` Sphinx extensions.
- **High-Level Documentation**\*: ✅ `docs/index.rst` provides a README‑based overview, an autosummary API reference, a solar wind tutorial notebook, reference pages for OMNI variables and SuperMAG indices/substorm catalogues, a changelog, and the contributing guide. Only one tutorial exists; the README's per‑index reader table partly compensates.
- **Documentation Accessibility**\*: ✅ Documentation lives in `docs/` under version control and is built by `.readthedocs.yaml` at https://swvo.readthedocs.io/en/latest/ (confirmed live).

### 3. Testing ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Testing is a clear strength: a large pytest suite with unit and integration tests, measured coverage, and CI across four Python versions. Some network‑dependent tests are flaky, which the project openly acknowledges.

- **Unit Tests**\*: ✅ 713 test functions across 38 test modules in `tests/`, one per reader (e.g., `test_kp_omni.py`, `test_wdc.py`, `test_omni_high_res.py`, `test_RBMDataset.py`), using fixture data and `pytest-mock`. A local offline run of the kp/dst/f10_7/hp/omni subsets gave 326 passed, 13 skipped, 1 xfailed.
- **Integration Tests**\*: ✅ The `read_*_from_multiple_models` test modules (87 tests total, 41 in `tests/io/solar_wind/test_read_solar_wind_from_multiple_models.py`) exercise fallback and ensemble combination across several readers, and `tests/io/omni/test_derived_compatibility.py` tests derived‑variable interplay.
- **Test Coverage**: ✅ Coverage is measured with `coverage` in `.github/workflows/tests.yml` and reported to Coveralls; the badge currently reads 83%. Note that `[tool.coverage.report] exclude_lines` in `pyproject.toml` excludes all `raise` and `logger.error` lines, which inflates the figure somewhat.
- **Automated Testing**: ✅ `tests.yml` runs ruff, ty, and pytest on Python 3.11, 3.12, 3.13, and 3.14 for every push and PR to `main`; `apptainer.yml` additionally runs the suite inside a container image. Four of the last ten `main` runs failed, all on live‑download tests (an IMAP row‑count assertion in `test_imap.py` and a `kp.gfz.de` connection timeout in `test_kp_niemegk.py`), reflecting the network flakiness noted in `CONTRIBUTING.md`.
- **System/Acceptance Testing**: ⚠️ Opt‑in live smoke tests exist (gated by `SWVO_RUN_LIVE_TESTS=1`, marked `@pytest.mark.network`), and the Apptainer workflow acts as an end‑to‑end deployment test, but there is no formal acceptance test suite.

### 4. Software Maturity ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

All "must" sub‑standards are met, with modern packaging, PyPI releases, and enforced linting/type checking. Windows support, dependency hygiene, and repository weight are the main areas for improvement.

- **Packaging**\*: ✅ PEP 621 `pyproject.toml` with a setuptools backend; `pip install swvo` and `uv pip install swvo` both work, and the package ships `py.typed`.
- **Releases**: ✅ **PyPI**: yes, 12 stable releases from 1.0.0 (2025‑08‑22) to 1.2.7 (2026‑09‑04), published automatically by `publish_pypi.yml` on GitHub releases, with release candidates (`1.2.7rc0`, `rc1`) tested first. **Conda**: no, `conda-forge/swvo` returns 404. Version is ≥1.0, consistent with the stable API.
- **Semantic Versioning**: ✅ `bumpver` is configured with `MAJOR.MINOR.PATCH[PYTAGNUM]`, and all git tags conform to that pattern.
- **OS Support**: ⚠️ Classifiers list only POSIX, Unix, and macOS; the CI matrix runs only on `ubuntu-latest`. The code uses `pathlib` throughout with no obvious POSIX‑only calls, so Windows may work, but it is neither claimed nor tested. On macOS 26.6 with Python 3.14, the ENLIL live-download test (`tests/io/solar_wind/test_enlil.py`) hung indefinitely: three forked `richpool` worker processes sat blocked on pipe reads for over seven minutes with no output and had to be killed. The `fork` start method combined with macOS system-proxy and DNS lookups in workers is a known fragility, so macOS is only partially validated.
- **Version Control**\*: ✅ Git on GitHub with 900+ commits, protected‑branch PR workflow, and Dependabot for pre‑commit hooks.
- **Coding Style**\*: ✅ `ruff check .` and `ruff format --check .` both pass cleanly on the evaluated commit (104 files), enforcing pycodestyle/pyflakes/isort rules at a 120‑character line length.
- **Static Analysis**: ✅ ruff and the `ty` type checker run in CI (`tests.yml`) and in `.pre-commit-config.yaml`, along with REUSE license‑header linting.
- **Dependencies**: ⚠️ The runtime dependency list in `pyproject.toml` bundles development tools (`pytest`, `pytest-mock`, `ruff`, `ty`, `pre-commit`, `reuseify`) and includes a package that is never imported (`wget`) and debugging aids (`icecream`, `ipython`). These should move to optional extras or be removed.
- **Binaries**: ⚠️ `tests/` holds 137 MB of fixture data including a 28 MB NetCDF file (`tests/io/RBMDataSet/data/ARASE/...T89.nc`) and dozens of 2–3 MB OMNI CSVs; git history also contains several 31 MB CSVs under a former `.swvo/` directory, giving a 256 MB `.git`. A Jupyter notebook is committed at `docs/examples/solar_wind_example.ipynb`, which the standard discourages. The fixtures are also shipped in the PyPI sdist, which is 59.7 MB versus a 0.2 MB wheel.

### 5. PHEP 3 (Python & Upstream Package Support) ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

Python version support is fully compliant and new upstream versions are adopted promptly, but the PyHC PHEP 3 Compliance Checker reports four errors, three of which are genuine: minimum pins on numpy, scipy, and xarray exclude feature series released within the last 24 months. See [PHEP 3](https://doi.org/10.5281/zenodo.17794207) for full policy details.

- **Python Version Support**: ✅ `requires-python = ">=3.11"` with classifiers and a CI matrix for 3.11, 3.12, 3.13, and 3.14, covering every minor release in the 36‑month window (3.12 through 3.14). The checker notes 3.11 may now be dropped but this is not a violation.
- **Upstream Package Support**: ❌ Running the [PHEP 3 Compliance Checker](https://github.com/heliophysicsPy/pyhc-actions) against `pyproject.toml` fails with 4 errors. Three are genuine policy violations: `numpy>=2.4.2` drops the numpy 2.2 (Dec 2024) and 2.3 feature series; `scipy>=1.17.0` drops scipy 1.15 (Jan 2025) and 1.16; `xarray>=2025.1.0` drops xarray 2024.10 and 2024.11. The fourth, `matplotlib>=3.10.8`, is a checker false positive: PHEP 3 is defined in terms of feature releases, and the 3.10 feature series is still permitted, so only the patch floor is excluded. The checker suggests `numpy>=2.2`, `scipy>=1.15`, `xarray>=2024.10`, and (to silence the tool) `matplotlib>=3.10`. To confirm the relaxed floors are viable, the full test suite was run locally on Python 3.12 with numpy 2.2.6, scipy 1.15.3, xarray 2024.10.0, matplotlib 3.10.0, and pandas 2.3.3 installed; the result was 900 passed, 19 skipped, 1 xfailed, 1 xpassed, and 1 network test deselected, identical to the outcome on the current locked versions. `astropy>=7.2.0` (Nov 2025) and `sunpy>=7.0.5` (Mar 2026) are similarly aggressive though not core packages.
- **New Version Adoption**: ✅ No upper bounds are set, and `uv.lock` (used by CI via `uv sync --locked`) already resolves to numpy 2.5.2, scipy 1.18.1, pandas 3.0.5, matplotlib 3.11.1, xarray 2026.7.0, and astropy 8.0.1, all released within the past six months.

### 6. License ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The project uses the permissive, OSI‑approved Apache‑2.0 license with full REUSE/SPDX compliance.

- **License Exists**\*: ✅ `LICENSES/Apache-2.0.txt` is present, declared via `license = "Apache-2.0"` and `license-files` in `pyproject.toml`, and every source file carries an SPDX header checked by `reuse_compliance.yml`. GitHub's license detector does not recognize the `LICENSES/` layout (the API reports `licenseInfo: null`), so a root‑level `LICENSE` copy would improve discoverability.
- **License Type**: ✅ Apache‑2.0 is a permissive license suitable for open source scientific software (PyHC's examples are BSD variants, but Apache‑2.0 is equally permissive and adds an explicit patent grant).
- **OSI Approved**: ✅ Apache License 2.0 is OSI‑approved.

*(\* = "must")*

## Recommendations

### 🔴 "Musts"
*These must be addressed to meet minimum PyHC standards*

1. **Complete docstring coverage**: Add numpydoc docstrings to the 29 undocumented modules, 15 undocumented public classes, and 37 undocumented public functions/methods, prioritizing `swvo/io/RBMDataSet/` (`bin_and_interpolate_to_model_grid.py`, `identify_orbits.py`, `linearize_trajectories.py`, `interp_functions.py`, `custom_enums.py`), `swvo/io/exceptions.py`, and `swvo/io/utils.py`.
   - Add one‑line module docstrings to the `__init__.py` files and the `read_*_from_multiple_models.py` modules so the autosummary pages have descriptions.
2. **Add examples and complete sections in existing docstrings**: Include an `Examples` section (a short `>>>` snippet) in the public `read()` and `download_and_process()` methods of every reader class, and fill in the missing `Parameters`/`Returns` sections in the 23–28 functions that currently omit them.

### 🟡 "Shoulds"
*Important for package quality but not blocking compliance*

1. **Relax core dependency lower bounds to satisfy PHEP 3**: Change to `numpy>=2.2`, `scipy>=1.15`, and `xarray>=2024.10` (or later pins that still fall inside the 24‑month window); `matplotlib>=3.10` is optional and only needed to satisfy the checker. Consider similar relaxation for `astropy` and `sunpy`. Add a CI job that installs these minimum versions so the range stays tested. Add the `heliophysicsPy/pyhc-actions/phep3-compliance@v1` action to CI so future pins are checked automatically.
2. **Separate development dependencies from runtime dependencies**: Move `pytest`, `pytest-mock`, `ruff`, `ty`, `pre-commit`, and `reuseify` into a `[project.optional-dependencies] dev` extra or a `[dependency-groups]` table; remove `wget`, which is never imported, and evaluate whether `icecream` and `ipython` are needed at runtime.
3. **Fix the macOS forked-worker hang and add Windows/macOS to CI**: Switch the ENLIL download pool to the `spawn` start method or a thread pool so system-proxy and DNS lookups do not run in forked children on macOS, then run the test suite on `windows-latest` and `macos-latest` in `tests.yml`, then add `Operating System :: Microsoft :: Windows` (or `OS Independent`) to the classifiers.
4. **Publish to conda-forge**: Submit a recipe to `conda-forge/staged-recipes` so users in conda environments can install `swvo` without pip.
5. **Reduce repository weight**: Trim or generate the large test fixtures (the 28 MB ARASE NetCDF and monthly OMNI CSVs) to minimal samples, or host them externally and download them during CI; consider moving `docs/examples/solar_wind_example.ipynb` to a separate examples repository or converting it to a Sphinx‑Gallery `.py` script.

### 🟢 Suggested Improvements
*Enhancements that would strengthen the package*

1. **Add a root‑level `LICENSE` file** (a copy of `LICENSES/Apache-2.0.txt`) so GitHub and PyPI license detection recognize the project as Apache‑2.0.
2. **Add GitHub issue and pull request templates** under `.github/ISSUE_TEMPLATE/` to guide bug reports and feature requests.
3. **Stabilize network‑dependent tests**: Mark all live‑download tests with `@pytest.mark.network` and skip them by default in CI (as already done for OMNIWeb), so `main` builds don't fail on upstream data‑service changes.
4. **Tighten coverage exclusions**: Remove the blanket `"raise"` and `"logger.error"` entries from `[tool.coverage.report] exclude_lines` so the reported 83% reflects error‑handling paths too.
5. **Expand tutorials**: Add short guides for the Kp/Hp ensemble forecasts, SuperMAG, and plasmasphere readers alongside the existing solar wind notebook.

## Conclusion

SWVO is a well‑engineered, actively maintained package that meets PyHC's "must" requirements for Community, Testing, Software Maturity, and License, with a particularly strong testing and automation setup for a project of its age. Its remaining compliance gaps are narrow and concrete: finish the docstrings (especially in the `RBMDataSet` subpackage and with examples) and loosen the numpy, scipy, and xarray pins to pass the PHEP 3 checker. The dependency fix is low‑risk: the full test suite already passes with the PHEP 3 minimum versions installed, so it reduces to editing `pyproject.toml` and adding a minimum‑versions CI job. The docstring work is larger but well‑scoped. With those changes, SWVO would achieve "Good" across all six standards and stand as a strong example of a modern PyHC package.
