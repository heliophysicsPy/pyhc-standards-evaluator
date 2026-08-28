# PyHC Package Evaluation: madrigalWeb

**Package**: madrigalWeb  
**Version Evaluated**: 3.3.8  
**Repository**: https://github.com/MITHaystack/madrigalWeb  
**Date**: 2026-08-19  
**Evaluator**: Claude Opus 5  

## Standards Compliance Summary

| Standard | Grade | Status |
|----------|-------|--------|
| Community | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | Open development and a code of conduct are in place; contribution guidance is a brief README paragraph |
| Documentation | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | 100% numpydoc docstring coverage and a published docs site, but no developer documentation |
| Testing | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Unit and integration tests now cover both the core class and all three CLI scripts, run in CI |
| Software Maturity | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Installable, semver-versioned, on both PyPI and conda-forge, OS-independent, ruff-linted in CI |
| PHEP 3 | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Supports all Python versions from the last 36 months with no upper cap; zero upstream dependencies |
| License | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Permissive, OSI-approved MIT license in a properly named `LICENSE` file |

## Executive Summary

**madrigalWeb** demonstrates strong compliance with PyHC standards, having improved markedly since its previous evaluation at version 3.3.7. The package excels in software maturity and testing — it is a dependency-free, MIT-licensed, pure-Python API distributed on both PyPI and conda-forge, with 100% numpydoc docstring coverage, a published Read the Docs site, and 49 test methods now covering both the `MadrigalData` class and all three command-line scripts, all exercised by GitHub Actions. The remaining gaps are documentary rather than technical: there are no developer docs (how to set up a dev environment, run tests, or build the documentation), and contribution guidance is a three-sentence README paragraph rather than a `CONTRIBUTING` file explaining when a contribution is not accepted. As the official remote-access API for the Madrigal database — a cornerstone data source for the upper-atmosphere and geospace community — the package provides unique and widely used functionality. To achieve full PyHC compliance, the primary focus should be adding a `CONTRIBUTING.md` and a developer-documentation page to the existing mkdocs site.

## Detailed Assessment

### 1. Community ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

Development is open, non-duplicative, and now governed by a published code of conduct; the sole shortfall is that contribution guidance is minimal and does not address when contributions are declined.

- **Open Development**\*: ✅ Code is publicly developed on GitHub at https://github.com/MITHaystack/madrigalWeb with a full commit history and CI runs visible on every push.
- **Duplication**: ✅ Provides the unique, official Python remote-access API for the Madrigal database; no ecosystem duplication.
- **Collaboration**\*: ⚠️ The README's "Contributing" section invites issues, emails, and pull requests, but there is no `CONTRIBUTING.md`, no issue or PR templates, and no statement of when a contribution would not be accepted (explicitly required by standard 13).
- **Code of Conduct**\*: ✅ `CODE_OF_CONDUCT.md` is present at the repository root, adapted from the HAPI-Server project, and is Contributor Covenant-compatible; it names the Madrigal admin (haystack-madrigal-admin@mit.edu) as a contact.

### 2. Documentation ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

Docstrings are complete, standards-conformant, and example-rich, and the docs are published online — but the required developer-documentation component of high-level documentation is absent.

- **Docstrings**\*: ✅ 100% coverage verified by AST inspection — all 44 modules/classes/functions in `madrigalWeb.py`, all 11 in `globalDownload.py`, all 12 in `globalIsprint.py`, and every module docstring are present.
- **Docstring Content**\*: ✅ Docstrings describe purpose, document every parameter and return value in typed `Parameters`/`Returns` sections, and 20 of 26 public objects carry runnable `Examples` blocks; the six without are the plain data-holder classes (`MadrigalInstrument`, `MadrigalExperiment`, `MadrigalExperimentFile`, `MadrigalParameter`) and two trivial helpers.
- **Docstring Standards**\*: ✅ Docstrings follow numpydoc convention, and this is machine-enforced — `pyproject.toml` selects ruff's `D` rules with `convention = "numpy"`, and `ruff check` passes cleanly on the current tree.
- **High-Level Documentation**\*: ⚠️ The mkdocs site provides a landing page, an API reference, and usage guides for each CLI script (`gd.md`, `gi.md`, `gc.md`), but there are **no developer docs** — nothing documents how to set up a development environment, run the test suite, or build the docs, which standard 8 requires alongside guides and tutorials.
- **Documentation Accessibility**\*: ✅ Documentation is in version control (`docs/`, `mkdocs.yml`, `.readthedocs.yaml`) and published in readable form at https://madrigalweb.readthedocs.io/en/latest/, which renders correctly.

### 3. Testing ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Both required testing sub-standards are met: unit tests now cover the core class *and* all three CLI scripts, integration tests exercise real multi-step server interactions, and the suite runs automatically in GitHub Actions.

- **Unit Tests**\*: ✅ 49 test methods across two files — `tests/testMadrigalWeb.py` (21 methods on `MadrigalData` and the result classes) and the new `tests/testGlobalScriptsCLI.py` (28 methods on `globalDownload.py`, `globalIsprint.py`, and `globalCitation.py`), closing the CLI coverage gap flagged in the previous evaluation.
- **Integration Tests**\*: ✅ Tests run against the live `cedar.openmadrigal.org` server and exercise multi-step flows (`getExperiments` → `getExperimentFiles` → `downloadFile`/`isprint`), plus end-to-end subprocess invocations of the CLI scripts.
- **Test Coverage**: ⚠️ No coverage tool is configured (`coverage`/`pytest-cov` appear nowhere in the repo) and no coverage figure is reported, so coverage remains unquantified.
- **Automated Testing**: ⚠️ `.github/workflows/unit-test.yml` runs both suites on every push, but two issues weaken the gate: the test files invoke `unittest.TextTestRunner().run(suite)` at module level without propagating the result to an exit code, so a failing test still exits 0 and the job reports green; and the workflow triggers only `on: push`, not `on: pull_request`.
- **System/Acceptance Testing**: ✅ The CLI subprocess tests are genuine acceptance tests — they invoke the installed console scripts as a user would and assert on downloaded artifacts, output formats, and directory hierarchies, with a deliberate offline/online split for argument-validation versus network paths.

### 4. Software Maturity ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Every software-maturity sub-standard is now met, including the conda distribution that was missing at the previous evaluation.

- **Packaging**\*: ✅ Modern `pyproject.toml` (setuptools ≥61 backend) with a `setup.py` shim declaring the four console scripts; installable via `pip install madrigalweb`.
- **Releases**: ✅ Stable releases are on **both** PyPI (3.3.8, released 2026-07-24) and **conda-forge** (`conda install conda-forge::madrigalweb`, 3.3.8, noarch) — resolving the conda gap noted previously. Version 3.3.8 is ≥1.0, appropriate for a stable API, with a steady release cadence (eight releases since 2024).
- **Semantic Versioning**: ✅ Version `3.3.8` follows a MAJOR.MINOR.PATCH scheme.
- **OS Support**: ✅ Pure Python with no OS-specific code (no `sys.platform`, `os.name`, or `win32` branches) and classified `Operating System :: OS Independent`; the `globalDownload.py` docstring explicitly notes it runs on unix or Windows.
- **Version Control**\*: ✅ Uses git, hosted on GitHub with a complete history.
- **Coding Style**\*: ✅ `ruff check` passes with no findings on the current tree; formatting is space-indented per `[tool.ruff.format]`. The camelCase method names deviate from PEP 8 naming but are a longstanding public-API convention that cannot change without breaking users.
- **Static Analysis**: ✅ ruff is configured in `pyproject.toml` (`E4`, `E7`, `E9`, `F`, `D`; line length 100) **and enforced in CI** via `.github/workflows/do-lint.yml` on every push.
- **Dependencies**: ✅ Exemplary — `dependencies = []`; the package uses only the Python standard library.
- **Binaries**: ✅ No binary files (HDF5, notebooks, compiled artifacts, images) are committed to the repository.

### 5. PHEP 3 (Python & Upstream Package Support) ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The package declares broad Python support with no upper cap and has zero upstream scientific dependencies, so there is nothing to fall behind on. See [PHEP 3](https://doi.org/10.5281/zenodo.17794207) for full policy details.

- **Python Version Support**: ✅ `requires-python = ">=3.7"` with no upper bound covers every minor Python release from the last 36 months (3.12, 3.13, 3.14); note that only 3.12 is actually exercised in CI, and no per-version `Programming Language :: Python :: 3.x` classifiers are declared.
- **Upstream Package Support**: ✅ The package has no upstream dependencies (`dependencies = []`), so upstream-version currency is not applicable.
- **New Version Adoption**: ✅ With no version cap, no dependencies, and pure-stdlib code, new Python releases are supported immediately upon release.

### 6. License ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The project ships a permissive, OSI-approved MIT license in a conventionally named file, fully satisfying the License standard.

- **License Exists**\*: ✅ `LICENSE` is present at the repository root (Copyright 2024 Massachusetts Institute of Technology), correctly named for automatic detection by GitHub and PyPI — an improvement over the previous `license.txt`.
- **License Type**: ✅ MIT — a permissive license appropriate for open-source scientific software; also declared in `CITATION.cff`.
- **OSI Approved**: ✅ MIT is OSI-approved and declared via the `License :: OSI Approved :: MIT License` classifier.

*(\* = "must")*

## Recommendations

### 🔴 "Musts"
*These must be addressed to meet minimum PyHC standards*

1. **Add contribution guidelines**: Create a `CONTRIBUTING.md` that expands the README's three-sentence "Contributing" paragraph into concrete guidance — how to report an issue, how to open a pull request, what review looks like, and, as standard 13 explicitly requires, **when a contribution will not be accepted** (e.g. changes that break the camelCase public API, or features better suited to the Madrigal server itself).
   - Optionally add `.github/ISSUE_TEMPLATE/` and a PR template to lower the barrier for new contributors.
2. **Add developer documentation**: Add a developer page to the existing mkdocs site (e.g. `docs/dev.md`, registered in `mkdocs.yml`'s `nav`) covering how to install from source for development, how to run the two test suites (including the offline-versus-online split and the `MADRIGAL_ONLINE` convention), how to run `ruff check`/`ruff format`, and how to build the docs locally.

### 🟡 "Shoulds"
*Important for package quality but not blocking compliance*

1. **Make CI actually fail on test failure**: The test files call `unittest.TextTestRunner().run(suite)` at module level and discard the result, so the workflow exits 0 even when tests fail. Either guard the runner with `if __name__ == '__main__':` and `sys.exit(not runner.run(suite).wasSuccessful())`, or invoke the suites via `python -m unittest` in `unit-test.yml` so the runner sets the exit code.
2. **Run tests on pull requests**: `unit-test.yml` and `do-lint.yml` trigger only `on: push`; add `pull_request` so contributions are checked before merge, as PyHC standard 9 recommends.
3. **Measure test coverage**: Integrate `coverage`/`pytest-cov` into `unit-test.yml` and publish a figure (e.g. a Codecov badge in the README) — the only Testing sub-standard still unaddressed.
4. **Honor the documented `MADRIGAL_ONLINE` switch**: `testGlobalScriptsCLI.py` hardcodes `ONLINE = 1` despite its module docstring stating that network tests are skipped unless `MADRIGAL_ONLINE=1` is set. Reading the environment variable (`ONLINE = os.environ.get('MADRIGAL_ONLINE') == '1'`) would match the documentation and make the default run fast, deterministic, and independent of live-server availability.
5. **Test across supported Python versions**: Add a matrix to `unit-test.yml` covering at least 3.12, 3.13, and 3.14 to verify the uncapped `>=3.7` declaration in practice, and add matching `Programming Language :: Python :: 3.x` classifiers.

### 🟢 Suggested Improvements
*Enhancements that would strengthen the package*

1. **Use `ruff format --check` in CI**: `do-lint.yml` runs bare `ruff format`, which reformats files in the runner and exits 0; `ruff format --check` (or `--diff`) would actually fail the job on unformatted code.
2. **Adopt the PHEP 3 Compliance Checker**: Add PyHC's [PHEP 3 Compliance Checker GitHub Action](https://github.com/heliophysicsPy/pyhc-actions) to make PHEP 3 conformance continuously verifiable rather than inferred from metadata.
3. **Replace bare `except:` clauses**: There are 58 bare `except:` statements (28 in `madrigalWeb.py`, 14 each in `globalDownload.py` and `globalIsprint.py`), currently silenced via `ignore = ["E722"]`. Narrowing these to specific exception types would prevent masking `KeyboardInterrupt` and genuine bugs.
4. **Reconcile CLI date-format inconsistencies**: The tests document that `globalDownload.py`/`globalIsprint.py` accept `MM/DD/YYYY` while their `--help` text advertises `YYYY-MM-DD`, and that `globalCitation.py` requires `YYYY-MM-DD` — plus `--format=hdf5` versus `--format=Hdf5` case differences between scripts. Aligning these (or at minimum fixing the help text) would remove a real user-facing trap.
5. **Add examples to the result classes**: Short `Examples` blocks on `MadrigalInstrument`, `MadrigalExperiment`, `MadrigalExperimentFile`, and `MadrigalParameter` showing typical attribute access would round out the already-strong docstring coverage.

## Conclusion

madrigalWeb is a mature, focused, dependency-free package providing essential remote access to the Madrigal database, and this evaluation records substantial progress since version 3.3.7: it now earns "Good" on four of the six standards, up from three. The additions of a code of conduct, a full numpydoc docstring migration with ruff-enforced `D` rules, a published Read the Docs site, a 28-method CLI test suite, unit-test and lint GitHub Actions workflows, a conda-forge distribution, and a properly named `LICENSE` file collectively resolved most of the previously identified gaps. The two remaining shortfalls are small and documentary: contribution guidelines that state when contributions are declined, and a developer-documentation page on the site that already exists. Adding those two files would bring madrigalWeb to full compliance across all six PyHC standards, and the highest-value follow-up beyond that is making the new CI gate propagate test failures into its exit code so the green checkmark means what it appears to mean.
