# PyHC Package Evaluation: hxform

**Package**: hxform  
**Version Evaluated**: v1.0.0 tag (with `hxform/version.py` set to `0.1.0`)  
**Repository**: https://github.com/rweigel/hxform  
**Date**: 2026-02-17  
**Evaluator**: GPT-5.3 Codex  

## Standards Compliance Summary

| Standard | Grade | Status |
|----------|-------|--------|
| Community | ![Requires improvement](https://img.shields.io/badge/Requires%20improvement-red.svg) | Public development is strong, but contribution policy and code of conduct are missing |
| Documentation | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | Strong README and core API docs, but incomplete docstring coverage and no full docs set |
| Testing | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Required unit/integration testing exists; CI automation and coverage reporting are still recommended |
| Software Maturity | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | Installable package with GitHub release, but release channels, static analysis, and portability need work |
| PHEP 3 | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Python/dependency posture is current; explicit written policy and CI matrix would still strengthen compliance |
| License | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | BSD-3-Clause permissive license is present and OSI-approved |

## Executive Summary

**hxform** shows moderate-to-strong compliance with PyHC standards. The package’s strongest areas are open/public development, practical unit/integration testing across multiple transform backends, current Python-version support, and permissive licensing. The most significant remaining gaps are community governance (no code of conduct and no contribution guide), plus inconsistent documentation completeness and absent CI/coverage enforcement. The package is technically valuable for cross-library heliophysics coordinate transforms, and it can reach stronger overall compliance with targeted process improvements. The highest-priority next steps remain adding community governance files and formalizing automated quality gates.

## Detailed Assessment

### 1. Community ![Requires improvement](https://img.shields.io/badge/Requires%20improvement-red.svg)

The repository is public and actively developed, but two required collaboration/governance artifacts are missing.

- **Open Development**\*: ✅ Code is publicly developed on GitHub (`https://github.com/rweigel/hxform`), with recent commits (e.g., latest commit dated 2026-02-16).
- **Duplication**: ✅ The package positions itself as a common interface across multiple existing transform libraries rather than a direct clone of one implementation (`pyhc_packages/hxform/README.md:24`).
- **Collaboration**\*: ❌ No `CONTRIBUTING.md` or equivalent contribution policy is present in the repository root or standard locations.
- **Code of Conduct**\*: ❌ No `CODE_OF_CONDUCT.md` (or Contributor Covenant-compatible policy) was found.

### 2. Documentation ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

Documentation quality is mixed: there is strong high-level README content and some detailed API documentation, but full docstring completeness is not met.

- **Docstrings**\*: ⚠️ Major API functions like `transform` are documented (`pyhc_packages/hxform/hxform/transform.py:1`), but several public functions lack docstrings (e.g., `pyhc_packages/hxform/hxform/matrix.py:1`, `pyhc_packages/hxform/hxform/compare.py:3`, `pyhc_packages/hxform/hxform/subsolar_point.py:261`).
- **Docstring Content**\*: ⚠️ Some docstrings include parameters/returns/examples (notably `transform`), while others are minimal or missing key sections (`pyhc_packages/hxform/hxform/sph2car.py:1`).
- **Docstring Standards**\*: ⚠️ Style is inconsistent across modules; some sections resemble NumPy style, but usage is not uniform repository-wide.
- **High-Level Documentation**\*: ⚠️ README includes installation, examples, and testing notes (`pyhc_packages/hxform/README.md:43`, `pyhc_packages/hxform/README.md:65`), but there is no dedicated user guide/tutorial/developer-doc structure.
- **Documentation Accessibility**\*: ✅ Documentation is stored in version control and publicly accessible through GitHub (`README.md`, demo scripts/logs).

### 3. Testing ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Under the template’s must/should logic, this category qualifies as **Good** because both required items (unit and integration tests) are present. Coverage tracking and CI automation are important should-level improvements, but they are not must-level blockers for this category.

- **Unit Tests**\*: ✅ Unit tests exist for core coordinate-conversion behavior in `test/c2s_s2c_test.py`, with passing multi-version JUnit artifacts (`pyhc_packages/hxform/test/log/tests-3.11.xml`, `pyhc_packages/hxform/test/log/tests-3.14.xml`).
- **Integration Tests**\*: ✅ Cross-library/component interaction tests exist (`pyhc_packages/hxform/test/api2_test.py`, `pyhc_packages/hxform/test/consistency_test.py`) and exercise many frame-to-frame transformations.
- **Test Coverage**: ❌ No `coverage`/`pytest-cov` configuration or coverage report was found.
- **Automated Testing**: ❌ No CI workflow files were found (e.g., no `.github/workflows/*`), so tests are not automatically enforced on PR/merge.
- **System/Acceptance Testing**: ⚠️ Demo scripts and log outputs provide practical end-to-end checks (`pyhc_packages/hxform/demo/`, `pyhc_packages/hxform/demo-native/`), but these are not formalized as automated acceptance gates.

### 4. Software Maturity ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

The package is installable and version-controlled with a tagged release, but release distribution, policy enforcement, and engineering hygiene are uneven.

- **Packaging**\*: ✅ Installable Python package via `setup.py` and `pyproject.toml` (`pyhc_packages/hxform/setup.py:131`, `pyhc_packages/hxform/pyproject.toml:1`).
- **Releases**: ⚠️ A GitHub release exists (`v1.0.0`, published 2026-02-16), but no package entry was found on PyPI (`https://pypi.org/pypi/hxform/json` returns 404) and no conda-forge package was found (`https://api.anaconda.org/package/conda-forge/hxform`).
- **Semantic Versioning**: ⚠️ `v1.0.0` tag exists, but package internal version currently reports `0.1.0` (`pyhc_packages/hxform/hxform/version.py:1`), creating release/version ambiguity.
- **OS Support**: ⚠️ README gives macOS/Linux guidance and explicitly says Windows is not tested (`pyhc_packages/hxform/README.md:47`).
- **Version Control**\*: ✅ Repository uses Git with clear tag/release history.
- **Coding Style**\*: ⚠️ Code is readable but not consistently aligned with standard PEP 8 conventions (e.g., pervasive 2-space indentation patterns).
- **Static Analysis**: ❌ No linting/static-analysis tooling (e.g., `ruff`, `flake8`, `pylint`, `mypy`) configuration was found.
- **Dependencies**: ⚠️ Dependencies are explicitly declared (`pyhc_packages/hxform/setup.py:10`), but include a direct VCS dependency (`utilrsw` via Git URL) and a comparatively heavy runtime stack.
- **Binaries**: ⚠️ Repository includes large binary assets (e.g., `pyhc_packages/hxform/kernels/de440s.bsp`), which may be scientifically justified but increase repository weight significantly.

### 5. PHEP 3 (Python & Upstream Package Support) ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Under the report template, PHEP 3 sub-items are should-level (no starred musts), so this category is not blocked by missing policy formalization. Available evidence indicates a current support posture for recent Python and dependency versions.

- **Python Version Support**: ✅ README and `nox` include Python 3.11-3.14 (`pyhc_packages/hxform/README.md:51`, `pyhc_packages/hxform/noxfile.py:13`). As of 2026-02-17, versions released within the last 36 months include 3.12 (2023-10-02), 3.13 (2024-10-07), and 3.14 (2025-10-07), all included.
- **Upstream Package Support**: ✅ Dependency constraints are modern and open-ended for core stack use (e.g., `numpy>=1.26` in `pyhc_packages/hxform/setup.py:11` and `pyhc_packages/hxform/pyproject.toml:2`), avoiding restrictive upper pins that would block recent upstream releases.
- **New Version Adoption**: ✅ Evidence of timely adoption includes active Python 3.14 testing and recently updated minimums for key dependencies (`sunpy>=7.0.3`, `pyspedas>=1.7.28`) in `pyhc_packages/hxform/setup.py:12` and `pyhc_packages/hxform/setup.py:15`.

### 6. License ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Licensing is clear, permissive, and aligned with PyHC recommendations.

- **License Exists**\*: ✅ `LICENSE.txt` is present at repository root.
- **License Type**: ✅ License text matches BSD 3-Clause terms (`pyhc_packages/hxform/LICENSE.txt`), a permissive license class recommended by PyHC.
- **OSI Approved**: ✅ BSD 3-Clause is OSI-approved.

*(\* = "must")*

## Recommendations

### 🔴 "Musts"
*These must be addressed to meet minimum PyHC standards*

1. **Add a project code of conduct**: Create `CODE_OF_CONDUCT.md` compatible with Contributor Covenant and link it from `README.md`.
2. **Add contribution guidelines**: Create `CONTRIBUTING.md` with contribution workflow, review expectations, and acceptance/rejection criteria.
3. **Complete required documentation coverage**: Add docstrings for all public functions/modules (starting with `matrix`, `compare`, `subsolar_point`, `ned`) and standardize on one convention (e.g., numpydoc).
4. **Bring coding-style compliance to baseline PEP 8**: Apply a formatter/linter policy and resolve key style inconsistencies.

### 🟡 "Shoulds"
*Important for package quality but not blocking compliance*

1. **Automate tests in CI**: Add GitHub Actions to run `pytest`/`nox` on pull requests and main-branch pushes.
2. **Add test coverage measurement**: Integrate `pytest-cov` and set an initial minimum coverage threshold with trend reporting.
3. **Clarify release/distribution channel strategy**: Publish releases to PyPI and/or conda-forge (in addition to GitHub releases) for easier adoption and reproducibility.
4. **Document explicit PHEP-3 support policy**: State supported Python/dependency windows and test min/max ranges in CI.

### 🟢 Suggested Improvements
*Enhancements that would strengthen the package*

1. **Improve OS confidence**: Add at least one Windows validation path (CI or documented manual support statement with constraints).
2. **Reduce repository weight**: Move non-essential large binaries/artifacts to external storage or release assets when practical.
3. **Expand high-level docs**: Add a structured docs site with user tutorial(s), API reference, and developer notes.

## Conclusion

**hxform** is a technically useful package with clear heliophysics relevance and a practical multi-library interoperability goal. The codebase demonstrates real testing effort and modern Python-version awareness, including Python 3.14 support. However, minimum PyHC community requirements are currently blocked by missing contribution/governance files, and quality gates are weakened by absent CI/coverage enforcement. With focused improvements in community governance, documentation completeness, and automation, the project can move from moderate to strong PyHC compliance quickly.
