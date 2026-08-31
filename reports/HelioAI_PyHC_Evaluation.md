# PyHC Package Evaluation: HelioAI

**Package**: HelioAI  
**Version Evaluated**: 0.2.1 (`081aa52488c6809b5ce1b2b395f79539162ec2c2`)  
**Repository**: https://github.com/erdoganfurkan/HelioAI  
**Date**: 2026-08-27  
**Evaluator**: OpenAI GPT-5.6 Sol  

## Standards Compliance Summary

| Standard | Grade | Status |
|----------|-------|--------|
| Community | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Public development, clear contribution guidance, and a Contributor Covenant code of conduct |
| Documentation | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | Substantial hosted documentation, but incomplete examples and an unsupported export-verification claim |
| Testing | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Broad automated coverage, but a central advertised workflow was defective and lacked acceptance coverage |
| Software Maturity | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Reproducible release artifacts, modern packaging, release automation, Ruff, and semantic versioning |
| PHEP 3 | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | The official PHEP 3 action passed with zero errors and zero warnings |
| License | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Permissive, OSI-approved MIT license |

## Executive Summary

HelioAI v0.2.1 demonstrates generally strong compliance with PyHC standards and clearly fits PyHC's scientific scope. Under a literal reading of PyHC's required-versus-recommended testing criteria, the submitted Testing grade of Good is defensible. The release has substantial documentation, a large cross-platform test suite, reproducible package artifacts, modern automation, and full PHEP 3 and licensing compliance. However, the release lacked acceptance coverage for a central PlasmaPy workflow that was subsequently confirmed to produce coroutine objects and fail during export, while its export guide also referred to a verification script that was not shipped. Those gaps remain important recommendations, but they do not require lowering the overall Testing grade under this interpretation of the rubric.

This report is a historical evaluation of the tagged v0.2.1 release at the commit listed above. Later changes to the repository's `main` branch are outside its evaluation scope.

## Detailed Assessment

### 1. Community ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

HelioAI is developed publicly, provides explicit contribution and conduct guidance, and offers agent orchestration over existing scientific packages rather than obviously duplicating another PyHC package. It is a very young project with one contributor and no external pull-request history as of the evaluation date, but those contextual limitations do not defeat the formal grade.

- **Open Development**\*: ✅ Development and issue history are public in the [GitHub repository](https://github.com/erdoganfurkan/HelioAI/tree/081aa52488c6809b5ce1b2b395f79539162ec2c2).
- **Duplication**: ✅ Its agent orchestration over Speasy and PlasmaPy does not obviously duplicate an existing PyHC package.
- **Collaboration**\*: ✅ [`CONTRIBUTING.md`](https://github.com/erdoganfurkan/HelioAI/blob/081aa52488c6809b5ce1b2b395f79539162ec2c2/CONTRIBUTING.md#L1-L120) provides setup, testing, dependency policy, and explicit examples of contributions that will not be accepted.
- **Code of Conduct**\*: ✅ [`CODE_OF_CONDUCT.md`](https://github.com/erdoganfurkan/HelioAI/blob/081aa52488c6809b5ce1b2b395f79539162ec2c2/CODE_OF_CONDUCT.md#L1-L120) uses Contributor Covenant 2.1.

### 2. Documentation ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

The release has a substantial hosted MkDocs site that built successfully in strict mode, and its source is extensively documented. The grade is limited by sparse examples across the public API and by an export guide that claimed a repository verification script existed when it did not.

- **Docstrings**\*: ✅ An AST audit found docstrings on all 51 Python modules and 177 of 178 public definitions.
- **Docstring Content**\*: ⚠️ Only 39 of 178 public definitions included examples; for instance, [`theta_bn()`](https://github.com/erdoganfurkan/HelioAI/blob/081aa52488c6809b5ce1b2b395f79539162ec2c2/helioai/data/recipes/theta_bn.py#L33-L56) had none.
- **Docstring Standards**\*: ✅ The audited documentation consistently used structured, readable API documentation and passed the project's strict documentation build.
- **High-Level Documentation**\*: ⚠️ Guides and tutorials exist, but the [export guide](https://github.com/erdoganfurkan/HelioAI/blob/081aa52488c6809b5ce1b2b395f79539162ec2c2/docs/guide/export.md#L45-L57) said the repository shipped `verify_export.sh` and used it to execute notebooks outside the repository; that file was absent.
- **Documentation Accessibility**\*: ✅ Documentation is version-controlled and published as a readable hosted site.

### 3. Testing ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The tagged release had a genuinely substantial automated test suite, but acceptance testing did not cover a central advertised PlasmaPy workflow that was defective in v0.2.1. PyHC formally requires unit and integration tests, while automated, system, and acceptance testing are recommended. Applying that must/should distinction, the overall category qualifies as Good, while the acceptance gap remains a substantive criticism.

- **Unit Tests**\*: ✅ The tagged release CI collected 797 tests, with 794 passing and 3 skipped.
- **Integration Tests**\*: ⚠️ Integration coverage existed, but did not exercise the synchronous agent-to-async-PlasmaPy path that later failed.
- **Test Coverage**: ⚠️ Coverage was measured at 79.54%, with no omit list and a 70% floor, but significant advertised workflow behavior remained uncovered.
- **Automated Testing**: ✅ [Release CI run 31810351708](https://github.com/erdoganfurkan/HelioAI/actions/runs/31810351708) ran on Linux with Python 3.12 through 3.14, macOS 3.12, and experimental Windows 3.12.
- **System/Acceptance Testing**: ❌ Example notebooks were validated and syntax-checked but not executed in CI, and exported notebooks lacked the documented fresh-environment execution check.

The `plasma_physicist` prompt directed synchronous sandbox code to import and call async PlasmaPy wrappers ([skill](https://github.com/erdoganfurkan/HelioAI/blob/081aa52488c6809b5ce1b2b395f79539162ec2c2/helioai/core/skills/plasma_physicist/SKILL.md#L53-L65), [async implementation](https://github.com/erdoganfurkan/HelioAI/blob/081aa52488c6809b5ce1b2b395f79539162ec2c2/helioai/tools/plasmapy_tools.py#L37-L78)). The maintainer's later [PR #3](https://github.com/erdoganfurkan/HelioAI/pull/3) confirmed that these templates returned coroutine objects and failed during export; it also corrected interpolation across telemetry gaps, fill-value handling, and a NaN fraction calculation that returned 0.25 instead of 0.5. Those corrections were not part of v0.2.1.

### 4. Software Maturity ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

HelioAI v0.2.1 was an installable alpha release with semantic versioning, modern packaging, Ruff, git-based development, release automation, and trusted publishing. Rebuilt wheel and source-distribution artifacts were byte-identical to the files published on PyPI.

- **Packaging**\*: ✅ The project is organized as an installable Python package with modern project metadata.
- **Releases**: ✅ v0.2.1 was published on PyPI as an alpha release, appropriately using a version below 1.0; a conda release was not identified during this evaluation.
- **Semantic Versioning**: ✅ Releases use a conventional MAJOR.MINOR.PATCH version scheme.
- **OS Support**: ⚠️ CI covered Linux and macOS, with Windows explicitly non-gating; genuine code isolation was Linux/bubblewrap-only.
- **Version Control**\*: ✅ The project uses git and is publicly hosted on GitHub.
- **Coding Style**\*: ✅ Ruff was configured and the audited release passed its style checks.
- **Static Analysis**: ✅ Ruff and automated checks were part of the project workflow.
- **Dependencies**: ⚠️ All 25 runtime dependencies except Solar-MACH were mandatory, increasing the base installation footprint.
- **Binaries**: ⚠️ The wheel contained all expected recipes, skills, and licensing material, but two notebooks were committed despite PyHC standard 14 recommending that notebooks not reside in the package repository.

### 5. PHEP 3 (Python & Upstream Package Support) ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The release's official PHEP 3 GitHub Actions job passed with zero errors and zero warnings. Its metadata and CI coverage supported the Python and core Scientific Python versions required at the time of evaluation.

- **Python Version Support**: ✅ Metadata required Python `>=3.12`, and CI exercised Python 3.12, 3.13, and 3.14.
- **Upstream Package Support**: ✅ NumPy, SciPy, Matplotlib, and IPython dependency floors were within the required support window ([project dependencies](https://github.com/erdoganfurkan/HelioAI/blob/081aa52488c6809b5ce1b2b395f79539162ec2c2/pyproject.toml#L13-L56)).
- **New Version Adoption**: ✅ The official action found no violations of the six-month adoption rule.

### 6. License ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The repository and release distributions carry an OSI-approved MIT license.

- **License Exists**\*: ✅ A [`LICENSE`](https://github.com/erdoganfurkan/HelioAI/blob/081aa52488c6809b5ce1b2b395f79539162ec2c2/LICENSE) file is present in the repository and packaged distributions.
- **License Type**: ✅ MIT is a permissive license appropriate for open-source scientific software.
- **OSI Approved**: ✅ The MIT License is OSI-approved.

*(\* = "must")*

## Security and Scientific-Claim Qualification

The website description's "sandboxed analysis" wording was materially misleading without qualification. [`SECURITY.md`](https://github.com/erdoganfurkan/HelioAI/blob/081aa52488c6809b5ce1b2b395f79539162ec2c2/SECURITY.md#L15-L37) correctly said that macOS, Windows, and Linux systems without functional bubblewrap run model-written code with the user's filesystem permissions, but it also claimed that API keys were unreadable on every platform ([lines 43–49](https://github.com/erdoganfurkan/HelioAI/blob/081aa52488c6809b5ce1b2b395f79539162ec2c2/SECURITY.md#L43-L49)). Filtering the subprocess environment does not prevent unisolated code from reading accessible `.env` files. Even bubblewrap masked only `_ROOT/.env`, whereas installed usage loaded an `.env` discovered from the launch directory. The Docker guide's "fully isolated" wording was also too strong because network access remained available and bubblewrap could be unavailable under container policy.

The package contained thoughtful scientific checks and cited recipes, but v0.2.1 did not establish general scientific validity. Its reference workflow centered on one 2015 storm, example notebooks were nondeterministic and unexecuted in CI, and later maintainer benchmarks exposed real incorrect-result paths. PyHC listing should not be presented as scientific validation.

## Recommendations

### 🔴 "Musts"
*These must be addressed to meet minimum PyHC standards*

1. **Qualify the security claim**: Remove or qualify "sandboxed" in the website description because isolation was only provided by functional bubblewrap on Linux, and fix the `.env`/API-key masking claim and behavior.
2. **Release the fixes**: Ship the corrections merged through HelioAI PR #3 in a new PyPI release and require a green release-tag CI run before accepting the website submission.

### 🟡 "Shoulds"
*Important for package quality but not blocking compliance*

1. **Correct the reported test metrics**: Use "797 collected; 794 passed, 3 skipped; 79.54% coverage" rather than "797 tests, 79.7%."
2. **Verify exported notebooks**: Add the documented `verify_export.sh` plus an executed fresh-environment notebook test, or remove the unsupported claim.
3. **Resolve the notebook-policy exception**: Acknowledge the committed notebooks as a deliberate standard-14 exception or move them to a separate examples repository.

## Conclusion

HelioAI v0.2.1 is a promising, well-engineered young project that fits the PyHC scientific ecosystem and earns Good grades for Community, Testing, Software Maturity, PHEP 3, and License. Its documentation is substantial but contains an unsupported verification claim and uneven examples, supporting a Partially met grade. Its broad automated test suite satisfies the rubric's required unit-and-integration-testing elements, supporting a Good Testing grade, while the uncovered advertised agent workflow and the scientific-data handling defects found there remain serious recommended improvements. Acceptance was recommended after publishing the known fixes and obtaining green release CI.

At the time of evaluation, current `main` was red across every test matrix in [run 33080653910](https://github.com/erdoganfurkan/HelioAI/actions/runs/33080653910) because `test_spz_still_resolves_when_actually_touched` timed out. That appeared to be a live Speasy/inventory integration failure rather than evidence that the tagged release failed, but it still needed to be resolved or cleanly rerun before acceptance.
