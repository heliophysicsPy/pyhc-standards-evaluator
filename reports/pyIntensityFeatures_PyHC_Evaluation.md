# PyHC Package Evaluation: pyIntensityFeatures

**Package**: pyIntensityFeatures  
**Version Evaluated**: 0.2.0  
**Repository**: https://github.com/aburrell/pyIntensityFeatures  
**Date**: 2026-03-26  
**Evaluator**: Codex (GPT-5.4)  

## Standards Compliance Summary

| Standard | Grade | Status |
|----------|-------|--------|
| Community | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Open GitHub development with contribution guidance, templates, and a code of conduct |
| Documentation | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Comprehensive documentation with only minor API docstring cleanup remaining |
| Testing | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Comprehensive automated testing with 130 passing tests and 99% measured coverage |
| Software Maturity | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Modern packaging, PyPI releases, cross-platform CI, and active lint/docs automation |
| PHEP 3 | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Supports current Python releases and recent upstream package versions |
| License | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Permissive BSD license is present and properly declared |

## Executive Summary

**pyIntensityFeatures** demonstrates strong compliance with PyHC standards across all six categories. The package is particularly strong in testing, software maturity, community infrastructure, and modern Python support, with public development on GitHub, active CI, PyPI releases, and successful local verification against current dependency versions. Its documentation is also strong overall: the package has substantial guides, examples, API reference material, and public hosting, with only minor residual cleanup needed around a handful of property setter docstrings and some stale wording in installation docs. The package provides valuable, domain-specific functionality for identifying auroral luminosity boundaries in imager data, and the main follow-up work is documentation polish rather than a compliance gap.

## Detailed Assessment

### 1. Community ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The project meets all required PyHC community standards with open development, clear contribution pathways, and an explicit code of conduct.

- **Open Development**\*: ✅ Code is publicly developed on GitHub at https://github.com/aburrell/pyIntensityFeatures with open issues, pull requests, tags, and full git history.
- **Duplication**: ✅ The package targets a specialized heliophysics use case, identifying auroral luminosity boundaries and related features in imager data, and does not appear to duplicate an existing PyHC package.
- **Collaboration**\*: ✅ `CONTRIBUTING.md`, issue templates, `pull_request_template.md`, and the developer guide in `docs/develop_guide.rst` clearly encourage outside contributions and explain the expected workflow.
- **Code of Conduct**\*: ✅ `CODE_OF_CONDUCT.md` contains a Contributor Covenant-compatible code of conduct with a reporting contact.

### 2. Documentation ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The documentation is comprehensive and publicly accessible. Under a substance-over-technicalities interpretation, the remaining API docstring gaps are minor enough not to outweigh the package's otherwise strong guide, example, API, and developer documentation.

- **Docstrings**\*: ⚠️ The non-test package code has docstrings for all 14 modules, its 1 public class, all 31 public top-level functions, and all 2 other public methods; the only missing docstrings are 4 property setter methods in `pyIntensityFeatures/_main.py` (`AuroralBounds.alt`, `hemisphere`, `stime`, and `etime`), while the corresponding property getters are documented.
- **Docstring Content**\*: ⚠️ Public docstrings generally describe purpose, inputs, and outputs. Many do not include embedded `Example` sections, but the package does provide multiple substantial worked examples and tutorials in the high-level docs, which this evaluation treats as substantively adequate.
- **Docstring Standards**\*: ✅ The codebase uses consistent NumPy-style docstrings and builds API documentation through `numpydoc` and `sphinx-autoapi` as configured in `docs/conf.py`.
- **High-Level Documentation**\*: ✅ The documentation tree includes overview, installation, citation, examples, API reference, developer guidance, history, and acknowledgements through `docs/index.rst` and linked pages.
- **Documentation Accessibility**\*: ✅ Documentation is stored in version control and available online at https://pyintensityfeatures.readthedocs.io/en/latest/ ; local `sphinx-build -E -b html` and `sphinx-build -b linkcheck` both succeeded, though each reported 2 warnings.

### 3. Testing ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Testing is a clear strength of the package, with broad source coverage, automated CI across platforms, and successful local verification.

- **Unit Tests**\*: ✅ The repository contains 10 dedicated test modules and about 4,029 lines of tests, and a local run completed successfully with `Ran 130 tests in 41.393s` and `OK (skipped=2)`.
- **Integration Tests**\*: ✅ `test_main.py` and `test_proc_intensity.py` exercise higher-level `AuroralBounds` workflows across dict/list/array/pandas/xarray inputs and both AACGMV2 and apexpy coordinate paths.
- **Test Coverage**: ✅ Coverage measurement is configured in `pyproject.toml`, and a local `coverage report` measured 99% total coverage with source modules ranging from 93% to 100%.
- **Automated Testing**: ✅ `.github/workflows/main.yml` runs linting, coverage, and tests on Linux, macOS, and Windows across Python 3.10, 3.12, 3.13, and 3.14, with extra jobs for NumPy 2.0 and optional apexpy support; `.github/workflows/docs.yml` checks docs builds and links.
- **System/Acceptance Testing**: ⚠️ There is no separate system or acceptance test suite labeled as such, but the package does include higher-level workflow tests that approximate end-to-end use.

### 4. Software Maturity ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The package shows strong software maturity with modern packaging, repeatable releases, explicit platform support, and automated quality checks.

- **Packaging**\*: ✅ The package is organized as an installable Python project with `pyproject.toml`, `setuptools.build_meta`, and successful isolated installation of `.[test,doc]`.
- **Releases**: ✅ Stable releases are published on PyPI and GitHub (`0.1.0` on 2025-03-28 and `0.2.0` on 2026-03-20); no package was found on Anaconda for either `conda-forge` or `aburrell`, but PyPI alone satisfies the release expectation.
- **Semantic Versioning**: ✅ The release progression `0.0.1` -> `0.1.0` -> `0.2.0` is coherent, and the project correctly remains below `1.0` while marked as alpha in `pyproject.toml`.
- **OS Support**: ✅ `pyproject.toml` classifiers and the GitHub Actions matrix explicitly cover Linux, macOS, and Windows.
- **Version Control**\*: ✅ The project uses git and GitHub with public history, tags, issue tracking, and pull request workflows.
- **Coding Style**\*: ✅ `CONTRIBUTING.md` documents PEP 8 and numpydoc expectations, and a clean `flake8 pyIntensityFeatures --select=D,E,F,H,W` run in the evaluation environment returned `0` selected violations for the package sources.
- **Static Analysis**: ✅ GitHub Actions runs linting and documentation validation automatically, and a local `flake8 --max-complexity=10` pass reported 8 `C901` complexity findings, showing the static-analysis tooling is active and surfacing refactor opportunities.
- **Dependencies**: ✅ Runtime dependencies are limited to `aacgmv2`, `numpy`, `pandas`, `scipy>=1.9.0`, and `xarray`, with optional `apexpy` separated into extras.
- **Binaries**: ✅ The repository contains only documentation images and no unnecessary notebooks, executables, or bundled binary artifacts.

### 5. PHEP 3 (Python & Upstream Package Support) ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The package passes the official PyHC PHEP 3 compliance checker locally with no errors. A local run of `phep3-check` from `/Users/shpo9723/git/pyhc-actions` against `pyIntensityFeatures/pyproject.toml` returned `0 error(s), 2 warning(s)` on 2026-03-26; both warnings were advisory only and indicated that Python 3.10 and SciPy 1.9 support can now be dropped.

- **Python Version Support**: ✅ The official checker accepted `requires-python = ">=3.10"`; it is compliant because, as of 2026-03-26, the minimum required Python version is 3.12 and supporting older versions is allowed.
- **Upstream Package Support**: ✅ The official checker accepted the package's base dependency constraints, including `scipy>=1.9.0`, with no dependency errors; its only SciPy message was a warning that support for 1.9 can be dropped because the current minimum required SciPy is `>=1.13`.
- **New Version Adoption**: ✅ The official checker reported no adoption errors, and the project metadata/CI already includes current Python releases through 3.14 and recent upstream versions.

### 6. License ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The project has a clear, permissive, OSI-approved license suitable for scientific open source software.

- **License Exists**\*: ✅ A `LICENSE` file is present in the repository root and is referenced in `pyproject.toml`.
- **License Type**: ✅ The project uses a BSD 3-Clause-style permissive license, which aligns well with PyHC recommendations.
- **OSI Approved**: ✅ BSD is an OSI-approved license family, and the package metadata includes the classifier `License :: OSI Approved :: BSD License`.

*(\* = "must")*

## Recommendations

### 🟡 "Shoulds"
*Important for package quality but not blocking compliance*

1. **Complete the remaining setter docstrings**: Add docstrings for the 4 undocumented property setter methods in `pyIntensityFeatures/_main.py` so API coverage is fully consistent.
2. **Tighten the installation and API documentation wording**: Update `docs/installation.rst`, which still says PyPI availability is in the future and still contains a placeholder repository URL, and consider adding more API-level usage examples where they would help readers.
3. **Document the package's PHEP 3 policy explicitly**: Add a short dependency support policy page or section describing supported Python/dependency windows and the intended minimum and maximum tested versions.
4. **Consider conda-forge distribution**: Publishing on conda-forge would improve accessibility for users working in scientific conda environments.

### 🟢 Suggested Improvements
*Enhancements that would strengthen the package*

1. **Make docs warnings fail CI after cleanup**: Once the current Sphinx warnings are fixed, adding `-W` to the docs build would help keep the documentation consistently clean.
2. **Refactor the highest-complexity functions**: Several functions currently exceed the configured complexity threshold of 10, especially `find_intensity_boundaries`, `locate_mult_peak_boundaries`, and `get_auroral_slice`.
3. **Tighten installation and release messaging across docs**: Align README, installation docs, and ReadTheDocs version labeling so users always see the current supported release story.

## Conclusion

**pyIntensityFeatures** is a strong PyHC candidate with mature testing, clear community infrastructure, solid packaging, and up-to-date Python support. The project already behaves like a professionally maintained scientific package: installation works cleanly, tests pass with excellent coverage, documentation is published online, and releases are available on PyPI and GitHub. The remaining work is documentation polish rather than a substantive standards gap. Under a substance-over-technicalities review standard, the package merits a `Good` documentation rating while still benefiting from a small cleanup pass on API docstrings and installation text.
