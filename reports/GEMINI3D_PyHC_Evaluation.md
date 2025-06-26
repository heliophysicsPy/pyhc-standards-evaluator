# PyHC Package Evaluation: GEMINI3D

**Package**: GEMINI3D  
**Version Evaluated**: Latest (GitHub main branch)  
**Repository**: https://github.com/gemini3d/gemini3d  
**Date**: 2025-06-26  
**Evaluator**: Claude Sonnet 4  

## Standards Compliance Summary

| Standard | Grade | Status |
|----------|-------|--------|
| Community | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | Open development with contributions welcomed, but lacks code of conduct |
| Documentation | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Comprehensive documentation with inline docs, guides, and tutorials |
| Testing | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | Has unit tests and CI, but coverage and documentation unclear |
| Software Maturity | ![Requires improvement](https://img.shields.io/badge/Requires%20improvement-red.svg) | Not packaged as Python package, lacks Python 3 focus |
| Python 3 | ![Requires improvement](https://img.shields.io/badge/Requires%20improvement-red.svg) | Primarily Fortran code with minimal Python integration |
| License | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Apache 2.0 license - permissive and OSI-approved |

## Executive Summary

GEMINI3D demonstrates mixed compliance with PyHC standards as it is primarily a Fortran-based ionospheric modeling code rather than a Python package. The project excels in documentation quality and uses a permissive license, but requires significant improvement in Python packaging standards and Python 3 focus. The scientific value of this ionospheric fluid-electrodynamic model is substantial for heliophysics research. To achieve full PyHC compliance, the project would need to be restructured as a proper Python package or evaluated as the separate PyGemini Python interface instead.

## Detailed Assessment

### 1. Community ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

While the project demonstrates strong open development practices and unique scientific functionality, the lack of a formal code of conduct prevents a "Good" rating.

- **Open Development**\*: ✅ Code is publicly available on GitHub at https://github.com/gemini3d/gemini3d with active development
- **Duplication**: ✅ Provides unique 3D ionospheric fluid-electrodynamic modeling capabilities not duplicated elsewhere
- **Collaboration**\*: ⚠️ Has CONTRIBUTING.md and welcomes contributions, but lacks detailed contribution guidelines and issue templates
- **Code of Conduct**\*: ❌ No code of conduct file found in repository

### 2. Documentation ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The project provides excellent documentation across multiple formats and levels, meeting all PyHC documentation requirements.

- **Docstrings**\*: ✅ Extensive inline documentation in Fortran source code with automated rendering
- **Docstring Content**\*: ✅ Documentation describes purpose, inputs, outputs with mathematical formulations
- **Docstring Standards**\*: ✅ Follows consistent documentation standards appropriate for Fortran
- **High-Level Documentation**\*: ✅ Comprehensive guides including installation, usage, platform-specific instructions
- **Documentation Accessibility**\*: ✅ Documentation in version control and available online at https://gemini3d.github.io/GEMINI/

### 3. Testing ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

The project has testing infrastructure with CI/CD and self-tests, but lacks comprehensive Python testing standards expected for PyHC.

- **Unit Tests**\*: ⚠️ Has Fortran unit tests and some Python test files, but unclear coverage of all components
- **Integration Tests**\*: ✅ Comprehensive integration tests through CTest framework comparing to reference outputs
- **Test Coverage**: ❌ No visible test coverage measurement or reporting
- **Automated Testing**: ✅ GitHub Actions CI/CD pipeline with multiple platform testing
- **System/Acceptance Testing**: ✅ Self-tests verify complete simulation workflows against known references

### 4. Software Maturity ![Requires improvement](https://img.shields.io/badge/Requires%20improvement-red.svg)

While mature as a scientific software project, it fails to meet Python packaging standards required for PyHC compliance.

- **Packaging**\*: ❌ Not organized as an installable Python package (primarily Fortran with CMake build system)
- **Releases**: ❌ No evidence of PyPI releases; GitHub releases exist but for Fortran code
- **Semantic Versioning**: ⚠️ Uses version tags but unclear if following semantic versioning strictly
- **OS Support**: ✅ Explicitly supports Windows, macOS, Linux across multiple architectures
- **Version Control**\*: ✅ Uses Git with comprehensive version control practices
- **Coding Style**\*: ⚠️ Has coding style defined for Fortran (2-space indents) but limited Python style guidance
- **Static Analysis**: ⚠️ Has some Python linting configuration (black, mypy) but limited
- **Dependencies**: ✅ Minimal Python dependencies, well-managed Fortran dependencies
- **Binaries**: ✅ No inappropriate binaries in repository, uses Git submodules for external dependencies

### 5. Python 3 ![Requires improvement](https://img.shields.io/badge/Requires%20improvement-red.svg)

The project is primarily Fortran-based with minimal Python integration, not meeting PyHC's Python 3 focus requirements.

- **Python 3 Compatibility**\*: ❌ While it has some Python 3 code, it's primarily a Fortran project and doesn't function as a Python package

### 6. License ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The project has excellent licensing compliance with a permissive, OSI-approved license.

- **License Exists**\*: ✅ Apache 2.0 license file present in repository
- **License Type**: ✅ Apache 2.0 is a permissive license appropriate for scientific software
- **OSI Approved**: ✅ Apache 2.0 is OSI-approved and widely accepted

*(\* = "must")*

## Recommendations

### 🔴 "Musts"
*These must be addressed to meet minimum PyHC standards*

1. **Add Code of Conduct**: Create a code of conduct compatible with the Contributor Covenant and make it publicly available
2. **Python Package Structure**: Either restructure as a proper Python package or evaluate the separate PyGemini interface instead
3. **Python 3 Focus**: Ensure the package functions primarily as a Python 3 compatible package rather than Fortran code with Python interfaces

### 🟡 "Shoulds"
*Important for package quality but not blocking compliance*

1. **PyPI Distribution**: Publish Python package to PyPI for easier installation and discovery
2. **Test Coverage Measurement**: Implement and report test coverage metrics
3. **Enhanced Contribution Guidelines**: Expand CONTRIBUTING.md with detailed submission process, coding standards, and issue templates

### 🟢 Suggested Improvements
*Enhancements that would strengthen the package*

1. **Python Style Guide**: Establish comprehensive Python coding style guidelines and static analysis
2. **Conda Distribution**: Consider conda-forge distribution for scientific computing community
3. **Documentation Integration**: Better integrate Python-specific documentation with existing Fortran documentation

## Conclusion

GEMINI3D represents high-quality scientific software with excellent documentation and mature development practices, but it fundamentally misaligns with PyHC standards due to its nature as a Fortran-based modeling code rather than a Python package. The evaluation reveals that while the underlying scientific software is well-developed and valuable to the heliophysics community, it would need significant restructuring to meet PyHC's Python-focused standards. The project would be better served by having its separate Python interface (PyGemini) evaluated instead, as that would more appropriately represent the Python package aspect expected by PyHC standards.