# PyHC Package Evaluation: sunkit-image

**Package**: sunkit-image  
**Version Evaluated**: 0.7.0  
**Repository**: https://github.com/sunpy/sunkit-image  
**Date**: 2025-06-25  
**Evaluator**: Claude Sonnet 4  

## Standards Compliance Summary

| Standard | Grade | Status |
|----------|-------|--------|
| Community | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | Strong open development and collaboration within SunPy ecosystem, but lacks dedicated contribution guidelines |
| Documentation | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Comprehensive documentation with API reference, examples, and online presence |
| Testing | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Excellent testing infrastructure with unit tests, integration tests, and automated CI/CD |
| Software Maturity | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Modern packaging, proper releases, multi-OS support, and professional development practices |
| Python 3 | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Full Python 3 compatibility with support for Python 3.10-3.12 |
| License | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | BSD 3-Clause license with proper attribution and multiple license files |

## Executive Summary

sunkit-image demonstrates strong compliance with PyHC standards and represents a high-quality scientific Python package. The package excels in documentation, testing infrastructure, software maturity practices, and licensing. It is well-integrated into the SunPy ecosystem with professional development practices including automated testing, proper packaging, and comprehensive documentation. The primary gap is in community infrastructure, lacking dedicated contribution guidelines and GitHub templates within the repository itself. To achieve full PyHC compliance, the focus should be on adding explicit contribution documentation to the repository.

## Detailed Assessment

### 1. Community ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

While the project demonstrates excellent open development practices and is well-integrated into the SunPy community, it lacks some explicit community infrastructure within the repository itself.

- **Open Development***: ✅ Code is publicly available and developed on GitHub at https://github.com/sunpy/sunkit-image with active development
- **Duplication**: ✅ Provides unique solar physics image processing functionality that complements but doesn't duplicate existing packages
- **Collaboration***: ⚠️ Part of the SunPy community with collaborative development, but lacks dedicated CONTRIBUTING.md file in repository
- **Code of Conduct***: ✅ References SunPy community code of conduct (https://sunpy.org/coc) although no local CODE_OF_CONDUCT file

### 2. Documentation ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The documentation is comprehensive and well-structured, meeting all PyHC requirements with online availability and proper formatting.

- **Docstrings***: ✅ All functions, classes, and modules have comprehensive docstrings following NumPy conventions
- **Docstring Content***: ✅ Docstrings include purpose, parameters, returns, and examples with proper formatting
- **Docstring Standards***: ✅ Follows NumPy docstring conventions as configured in ruff.toml
- **High-Level Documentation***: ✅ Comprehensive online documentation at https://docs.sunpy.org/projects/sunkit-image with guides and tutorials
- **Documentation Accessibility***: ✅ Documentation is in version control and available online with proper Sphinx setup

### 3. Testing ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Testing infrastructure is excellent with comprehensive unit tests, integration tests, automated CI/CD, and coverage measurement across multiple platforms.

- **Unit Tests***: ✅ Comprehensive unit tests covering all major functionality in sunkit_image/tests/ directory
- **Integration Tests***: ✅ Tests cover component interactions and full workflows including figure tests and remote data tests
- **Test Coverage**: ✅ Coverage measurement implemented with codecov integration and .coveragerc configuration
- **Automated Testing**: ✅ GitHub Actions CI/CD pipeline tests on Windows, macOS, and Linux with Python 3.10-3.13
- **System/Acceptance Testing**: ✅ Multiple test environments including oldest/newest dependencies and online tests

### 4. Software Maturity ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The package demonstrates exceptional software maturity with modern packaging, proper releases, comprehensive tooling, and professional development practices.

- **Packaging***: ✅ Well-organized installable Python package with modern pyproject.toml configuration
- **Releases**: ✅ Available on PyPI (https://pypi.org/project/sunkit-image/) with automated publishing and proper version management
- **Semantic Versioning**: ✅ Uses setuptools_scm for version management with semantic versioning practices
- **OS Support**: ✅ CI testing confirms compatibility with Windows, macOS, and Linux
- **Version Control***: ✅ Uses Git with distributed version control on GitHub
- **Coding Style***: ✅ Follows PEP 8 with Ruff formatting and linting configuration
- **Static Analysis**: ✅ Comprehensive pre-commit setup with Ruff, isort, MyPy, and other tools
- **Dependencies**: ✅ Well-chosen minimal dependencies (astropy, numpy, matplotlib, scipy, scikit-image, sunpy)
- **Binaries**: ✅ No unnecessary binary files in repository, proper package structure

### 5. Python 3 ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Full Python 3 compatibility with support for modern Python versions and no legacy Python 2 support.

- **Python 3 Compatibility***: ✅ Supports Python 3.10, 3.11, and 3.12 with no Python 2 support

### 6. License ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

The package has proper licensing with BSD 3-Clause license, which is OSI-approved and permissive for scientific software.

- **License Exists***: ✅ LICENSE.rst file present with clear BSD 3-Clause license
- **License Type**: ✅ Uses BSD 3-Clause license, which is permissive and recommended for scientific software
- **OSI Approved**: ✅ BSD 3-Clause is OSI-approved and properly classified in pyproject.toml

*(\* = "must")*

## Recommendations

### 🟡 "Shoulds"
*Important for package quality but not blocking compliance*

1. **Add CONTRIBUTING.md**: Create a dedicated CONTRIBUTING.md file in the repository root with contribution guidelines, even if it references the main SunPy guidelines
   - Include local development setup instructions
   - Add links to SunPy community resources

2. **Add GitHub Templates**: Create GitHub issue and pull request templates
   - .github/ISSUE_TEMPLATE/ directory with bug report and feature request templates
   - .github/pull_request_template.md for consistent PR descriptions

3. **Add CODE_OF_CONDUCT.md**: Include a local CODE_OF_CONDUCT.md file that references the SunPy community code of conduct for better discoverability

### 🟢 Suggested Improvements
*Enhancements that would strengthen the package*

1. **Security Policy**: Consider adding a SECURITY.md file with security reporting procedures
2. **Citation Information**: Add CITATION.cff file for proper academic citation
3. **Conda Packaging**: While PyPI distribution exists, consider official conda-forge distribution

## Conclusion

sunkit-image is an exemplary scientific Python package that demonstrates strong compliance with PyHC standards. The package excels in all technical areas including documentation, testing, software maturity, and licensing. It represents professional-grade scientific software with comprehensive CI/CD, proper packaging, and excellent integration with the broader SunPy ecosystem. The minor community infrastructure gaps are easily addressable and don't significantly impact the package's overall quality or compliance with PyHC standards.