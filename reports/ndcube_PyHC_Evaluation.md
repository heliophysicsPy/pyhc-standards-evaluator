# PyHC Package Evaluation: ndcube

**Package**: ndcube  
**Version Evaluated**: v2.4dev-254-g4eddfc8b  
**Repository**: https://github.com/sunpy/ndcube  
**Date**: 2025-06-24  
**Evaluator**: Claude Sonnet 4  

## Standards Compliance Summary

| Standard | Grade | Status |
|----------|-------|--------|
| Community | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Excellent open development and collaboration infrastructure |
| Documentation | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Comprehensive documentation with tutorials and API reference |
| Testing | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Robust testing suite with high coverage and automation |
| Software Maturity | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Professional packaging and development practices |
| Python 3 | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Modern Python 3.10+ compatibility |
| License | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | BSD 2-Clause permissive license |

## Executive Summary

ndcube demonstrates exceptional compliance with PyHC standards, achieving "Good" ratings across all six evaluation categories. The package excels in comprehensive documentation, robust testing infrastructure, modern packaging practices, and strong community governance through its SunPy project affiliation. As a JOSS-published package with professional development workflows, ndcube serves as an exemplary model for PyHC-compliant scientific software. The package fully meets all PyHC requirements and maintains high standards of software engineering excellence.

## Detailed Assessment

### 1. Community ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The package demonstrates excellent community practices with comprehensive open development infrastructure and clear collaboration pathways.

- **Open Development**\*: ✅ Code is publicly available on GitHub at https://github.com/sunpy/ndcube with open issue tracking and transparent development
- **Duplication**: ✅ Provides unique functionality for multi-dimensional coordinate-aware arrays, filling a specific niche in the scientific Python ecosystem
- **Collaboration**\*: ✅ Clear contribution guidelines through SunPy newcomer guide, active issue tracker, and community chat channel at #ndcube:openastronomy.org
- **Code of Conduct**\*: ✅ References SunPy Code of Conduct (https://sunpy.org/coc) which follows Contributor Covenant principles

### 2. Documentation ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Documentation is comprehensive and professionally maintained with excellent coverage of all required elements.

- **Docstrings**\*: ✅ All functions, classes, and modules have comprehensive docstrings throughout the codebase
- **Docstring Content**\*: ✅ Docstrings include purpose, detailed parameter descriptions, return values, and practical examples
- **Docstring Standards**\*: ✅ Follows numpydoc convention consistently, configured in .ruff.toml and Sphinx setup
- **High-Level Documentation**\*: ✅ Complete documentation suite with installation guide, tutorials, API reference, and examples at https://docs.sunpy.org/projects/ndcube/
- **Documentation Accessibility**\*: ✅ Documentation source in version control under docs/ directory with Read the Docs deployment

### 3. Testing ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Testing infrastructure is exemplary with comprehensive coverage, automation, and multiple testing levels implemented.

- **Unit Tests**\*: ✅ 21 test files covering individual components with comprehensive test suite in ndcube/tests/
- **Integration Tests**\*: ✅ Component interaction testing including slice/crop operations, arithmetic, and workflow tests
- **Test Coverage**: ✅ Coverage measurement configured with codecov integration and reporting pipeline
- **Automated Testing**: ✅ GitHub Actions CI/CD pipeline testing on Python 3.10-3.13 across Windows, macOS, and Linux
- **System/Acceptance Testing**: ✅ Documentation tests, figure comparison tests, and full integration testing across dependency versions

### 4. Software Maturity ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The package demonstrates professional software engineering practices with modern tooling and comprehensive development infrastructure.

- **Packaging**\*: ✅ Modern Python package using pyproject.toml with setuptools_scm for version management
- **Releases**: ✅ Available on both PyPI (https://pypi.org/project/ndcube/) and conda-forge with multiple stable versions
- **Semantic Versioning**: ✅ Uses setuptools_scm for automatic version management following semantic versioning principles
- **OS Support**: ✅ Cross-platform compatibility ensured through CI testing on Windows, macOS, and Linux
- **Version Control**\*: ✅ Uses Git with GitHub hosting and proper branching workflows
- **Coding Style**\*: ✅ PEP 8 compliance enforced through Ruff configuration with 120-character line length
- **Static Analysis**: ✅ Comprehensive linting with Ruff, pre-commit hooks including isort and codespell
- **Dependencies**: ✅ Minimal, well-justified dependencies: astropy, gwcs, numpy, scipy for the package's astronomy/WCS functionality
- **Binaries**: ✅ Pure Python package with no binary files in repository

### 5. Python 3 ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Full Python 3 compatibility with modern version requirements and contemporary language features.

- **Python 3 Compatibility**\*: ✅ Requires Python >=3.10 with CI testing on Python 3.10-3.13, utilizing modern Python features

### 6. License ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Proper licensing with permissive, OSI-approved license supporting open source scientific software development.

- **License Exists**\*: ✅ License file present at LICENSE.rst with additional license information in licenses/ directory
- **License Type**: ✅ BSD 2-Clause License (permissive, not copyleft) allowing broad usage and modification
- **OSI Approved**: ✅ BSD 2-Clause is OSI-approved and widely used in scientific Python ecosystem

*(\* = "must")*

## Recommendations

### 🟢 Suggested Improvements
*Enhancements that would strengthen the package*

1. **Consider adding automated dependency updates**: Implement Dependabot or similar tooling for automated dependency management
2. **Enhance contributor onboarding**: Consider adding specific contributor documentation beyond the general SunPy guidelines

## Conclusion

ndcube represents an exemplary implementation of PyHC standards, achieving full compliance across all evaluation categories. The package demonstrates professional-grade software engineering practices, comprehensive documentation, robust testing infrastructure, and strong community governance. As a SunPy-affiliated package with JOSS publication, ndcube serves as an excellent model for other PyHC packages seeking to achieve similar standards of excellence. The package's commitment to quality, maintainability, and scientific rigor makes it a valuable contribution to the Python in Heliophysics Community ecosystem.