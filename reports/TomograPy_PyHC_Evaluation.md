# PyHC Package Evaluation: TomograPy

**Package**: TomograPy  
**Version Evaluated**: 0.3.1  
**Repository**: https://github.com/nbarbey/TomograPy.git  
**Date**: 2025-06-25  
**Evaluator**: Claude Sonnet 4  

## Standards Compliance Summary

| Standard | Grade | Status |
|----------|-------|--------|
| Community | ![Requires improvement](https://img.shields.io/badge/Requires%20improvement-red.svg) | Limited community infrastructure, no code of conduct |
| Documentation | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | Inconsistent docstrings, no modern documentation system |
| Testing | ![Requires improvement](https://img.shields.io/badge/Requires%20improvement-red.svg) | Comprehensive but broken testing infrastructure |
| Software Maturity | ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg) | Good packaging but missing modern practices |
| Python 3 | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | Code appears Python 3 compatible but no explicit requirements |
| License | ![Good](https://img.shields.io/badge/Good-brightgreen.svg) | CeCILL-B permissive open source license |

## Executive Summary

TomograPy demonstrates weak to moderate compliance with PyHC standards overall. The package excels in providing specialized solar tomography functionality with a solid mathematical foundation and comprehensive test coverage scope, but suffers from critical infrastructure gaps. The project requires significant improvement in community governance, testing automation, and documentation modernization. While the core scientific functionality appears robust, the lack of community infrastructure, broken testing framework, and inconsistent documentation limit its accessibility and maintainability. To achieve full PyHC compliance, the primary focus should be on modernizing the testing infrastructure and establishing basic community governance.

## Detailed Assessment

### 1. Community ![Requires improvement](https://img.shields.io/badge/Requires%20improvement-red.svg)

Multiple required community standards are not met, preventing proper collaborative development.

- **Open Development**\*: ✅ Code is publicly available on GitHub at https://github.com/nbarbey/TomograPy.git
- **Duplication**: ❌ Project explicitly states a new version is being developed as "solartom", indicating duplication and transition
- **Collaboration**\*: ❌ No CONTRIBUTING.md, no issue templates, no PR templates, minimal collaborative infrastructure  
- **Code of Conduct**\*: ❌ No code of conduct file found in repository

### 2. Documentation ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

Documentation exists with good module coverage but lacks consistency and modern tooling.

- **Docstrings**\*: ⚠️ Only 46.7% of functions have docstrings (56 out of ~120 functions)
- **Docstring Content**\*: ⚠️ Well-documented functions include purpose and parameters, but coverage is incomplete
- **Docstring Standards**\*: ❌ Mixed formats (numpydoc, custom styles), no consistent standard followed
- **High-Level Documentation**\*: ⚠️ Basic README and 13 example files exist, but no comprehensive guides or tutorials
- **Documentation Accessibility**\*: ⚠️ Basic pydoc2 HTML generation via make_doc script, but no modern documentation hosting

### 3. Testing ![Requires improvement](https://img.shields.io/badge/Requires%20improvement-red.svg)

Testing infrastructure is critically lacking with comprehensive scope but broken execution framework.

- **Unit Tests**\*: ❌ Tests exist but fail to run due to missing nose dependency (deprecated framework)
- **Integration Tests**\*: ❌ Integration scenarios exist in examples but no automated framework
- **Test Coverage**: ❌ No coverage measurement tools configured or functional
- **Automated Testing**: ❌ No CI/CD pipeline, no automated testing on commits/PRs
- **System/Acceptance Testing**: ⚠️ Manual validation examples exist but aren't automated

### 4. Software Maturity ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

Good basic packaging practices but missing several modern software maturity requirements.

- **Packaging**\*: ✅ Properly organized as installable Python package with setup.py
- **Releases**: ❌ No evidence of PyPI releases; ❌ No evidence of Conda releases
- **Semantic Versioning**: ✅ Uses semantic versioning (0.3.1 indicates pre-1.0 unstable)
- **OS Support**: ⚠️ OpenMP compilation suggests Linux/macOS focus, Windows support unclear
- **Version Control**\*: ✅ Uses git for version control
- **Coding Style**\*: ⚠️ No evidence of PEP 8 enforcement or style checking
- **Static Analysis**: ❌ No linting tools configured (pylint, flake8, etc.)
- **Dependencies**: ⚠️ Uses several dependencies (numpy, scipy, pyfits, fitsarray, lo) but justification unclear
- **Binaries**: ✅ No binary files in repository (notebooks are in separate exemples directory)

### 5. Python 3 ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Code appears Python 3 compatible but lacks explicit version requirements or compatibility statements.

- **Python 3 Compatibility**\*: ⚠️ Code uses modern Python 3 syntax and patterns, but no explicit python_requires in setup.py

### 6. License ![Good](https://img.shields.io/badge/Good-brightgreen.svg)

Project has a comprehensive permissive open source license that meets all requirements.

- **License Exists**\*: ✅ LICENSE file present with full license text
- **License Type**: ✅ CeCILL-B is a permissive open source license (BSD-style)
- **OSI Approved**: ✅ CeCILL-B is an OSI-approved permissive license

*(\* = "must")*

## Recommendations

### 🔴 "Musts"
*These must be addressed to meet minimum PyHC standards*

1. **Fix Testing Infrastructure**: Replace deprecated nose framework with pytest and make tests executable
   - Install and configure pytest
   - Update all test files to use pytest syntax
   - Add test dependencies to setup.py

2. **Establish Code of Conduct**: Add a Contributor Covenant-compatible code of conduct file

3. **Improve Collaboration Infrastructure**: Create CONTRIBUTING.md with clear contribution guidelines

4. **Standardize Documentation**: Adopt numpydoc format consistently across all modules
   - Convert all docstrings to numpydoc format
   - Improve docstring coverage to at least 80% of public functions

### 🟡 "Shoulds"
*Important for package quality but not blocking compliance*

1. **Implement CI/CD Pipeline**: Set up GitHub Actions for automated testing and quality checks

2. **Add Coverage Measurement**: Configure coverage.py and establish coverage targets

3. **Modern Documentation System**: Migrate from pydoc2 to Sphinx with automated documentation builds

4. **Package Distribution**: Publish releases to PyPI for easier installation

5. **Code Quality Tools**: Add static analysis tools (flake8, pylint) and enforce PEP 8 compliance

### 🟢 Suggested Improvements
*Enhancements that would strengthen the package*

1. **Address Project Transition**: Clarify relationship with the successor "solartom" project to avoid duplication

2. **Cross-platform Testing**: Ensure Windows compatibility and add multi-OS testing

3. **Performance Optimization**: Leverage the existing performance testing framework for optimization

4. **User Documentation**: Create comprehensive tutorials and user guides beyond basic examples

## Conclusion

TomograPy provides valuable specialized functionality for solar tomography with solid mathematical foundations and comprehensive algorithmic testing. However, the project requires substantial infrastructure modernization to meet PyHC standards. The broken testing framework, lack of community governance, and inconsistent documentation significantly impact its maintainability and accessibility. While the core scientific functionality appears robust, addressing the critical infrastructure gaps is essential for PyHC compliance and long-term sustainability. The project would benefit from either substantial modernization or clear transition to its successor "solartom" project.