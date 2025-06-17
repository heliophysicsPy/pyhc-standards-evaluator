# PyHC Evaluation Report Format Specification

This document defines the standardized format for PyHC package evaluation reports. All evaluation reports must follow this format to ensure consistency and clarity.

**Note**: All sub-standards referenced in this format are defined in the [PyHC Community Standards](https://github.com/heliophysicsPy/standards/blob/main/standards.md) document, which should be consulted for detailed requirements.

## File Naming Convention

Report files must be named: `[PACKAGE_NAME]_PyHC_Evaluation.md`

Example: `SunPy_PyHC_Evaluation.md`

## Report Structure

### 1. Title
```markdown
# PyHC Package Evaluation: [PACKAGE_NAME]
```

Example:
```markdown
# PyHC Package Evaluation: SunPy
```

### 2. Metadata Header
```markdown
**Package**: [Package Name]  
**Version Evaluated**: [X.Y.Z]  
**Repository**: [URL]  
**Date**: [YYYY-MM-DD]  
**Evaluator**: [Model Name and Version, e.g., "Claude Sonnet 4" or "Claude Opus 4"]  
```

Example:
```markdown
**Package**: SunPy  
**Version Evaluated**: 6.1.1  
**Repository**: https://github.com/sunpy/sunpy  
**Date**: 2025-02-24  
**Evaluator**: Claude Sonnet 4  
```

### 3. Executive Summary Table

Place this table immediately after the metadata. Use badge images for visual clarity:

```markdown
## Standards Compliance Summary

| Standard | Grade | Status |
|----------|-------|--------|
| Community | ![Badge](URL) | Brief status description |
| Documentation | ![Badge](URL) | Brief status description |
| Testing | ![Badge](URL) | Brief status description |
| Software Maturity | ![Badge](URL) | Brief status description |
| Python 3 | ![Badge](URL) | Brief status description |
| License | ![Badge](URL) | Brief status description |
```

Badge URLs:
- Good: `https://img.shields.io/badge/Good-brightgreen.svg`
- Partially met: `https://img.shields.io/badge/Partially%20met-orange.svg`
- Requires improvement: `https://img.shields.io/badge/Requires%20improvement-red.svg`

### 4. Executive Summary Paragraph

Write a 3-5 sentence paragraph that:
- States the overall compliance level
- Highlights the package's main strengths
- Identifies the most critical gaps
- Provides a high-level recommendation

Example:
```markdown
## Executive Summary

[Package] demonstrates [strong/moderate/weak] compliance with PyHC standards. The package excels in [list 1-2 key strengths] but requires significant improvement in [list 1-2 critical gaps]. [One sentence about scientific value/impact]. To achieve full PyHC compliance, the primary focus should be on [most critical improvement needed].
```

### 5. Detailed Standards Assessment

For each of the six standards, use this format with all sub-standards derived from the [PyHC Standards document](https://github.com/heliophysicsPy/standards/blob/main/standards.md):

```markdown
## Detailed Assessment
```

**Note**: In the templates below, replace the bracketed questions with actual findings. The questions are prompts to guide your evaluation.

\* = "musts"  
No \* = "shoulds"

```markdown
## Detailed Assessment

### 1. Community ![Grade](Badge URL)

[1-2 sentences explaining why this specific grade was assigned]

- **Open Development**: ✅/⚠️/❌ [Is code publicly available and developed in the open?\*]
- **Duplication**: ✅/⚠️/❌ [Does this duplicate existing functionality in the ecosystem?]
- **Collaboration**: ✅/⚠️/❌ [Are there contribution guidelines and a welcoming environment?\*]
- **Code of Conduct**: ✅/⚠️/❌ [Is there a Contributor Covenant-compatible code of conduct?\*]

### 2. Documentation ![Grade](Badge URL)

[1-2 sentences explaining the grade]

- **Docstrings**: ✅/⚠️/❌ [Are all functions, classes, and modules documented?\*]
- **Docstring Content**: ✅/⚠️/❌ [Do docstrings describe purpose, inputs, outputs, and examples?\*]
- **Docstring Standards**: ✅/⚠️/❌ [Do they follow standard conventions (e.g., numpydoc)?\*]
- **High-Level Documentation**: ✅/⚠️/❌ [Are there guides, tutorials, and developer docs?\*]
- **Documentation Accessibility**: ✅/⚠️/❌ [Is documentation in version control and available online?\*]

### 3. Testing ![Grade](Badge URL)

[1-2 sentences explaining the grade]

- **Unit Tests**: ✅/⚠️/❌ [Do unit tests cover individual components?\*]
- **Integration Tests**: ✅/⚠️/❌ [Are component interactions tested?\*]
- **Test Coverage**: ✅/⚠️/❌ [Is coverage measured and adequate?]
- **Automated Testing**: ✅/⚠️/❌ [Are tests run automatically on commits/PRs?]
- **System/Acceptance Testing**: ✅/⚠️/❌ [Are these higher-level tests implemented?]

### 4. Software Maturity ![Grade](Badge URL)

[1-2 sentences explaining the grade]

- **Packaging**: ✅/⚠️/❌ [Is code organized and provided as part of an installable Python package?\*]
- **Releases**: ✅/⚠️/❌ [Are there stable releases on PyPI/Conda? Version < 1.0 for unstable?]
- **Semantic Versioning**: ✅/⚠️/❌ [Does the project follow semantic versioning?]
- **OS Support**: ✅/⚠️/❌ [Does it work on Windows, macOS, Linux?]
- **Version Control**: ✅/⚠️/❌ [Uses git or other distributed VCS?\*]
- **Coding Style**: ✅/⚠️/❌ [Follows PEP 8?\*]
- **Static Analysis**: ✅/⚠️/❌ [Uses linting tools?]
- **Dependencies**: ✅/⚠️/❌ [Are dependencies minimal and justified?]
- **Binaries**: ✅/⚠️/❌ [Are binaries avoided in the repository?]

### 5. Python 3 ![Grade](Badge URL)

[1-2 sentences explaining the grade]

- **Python 3 Compatibility**: ✅/⚠️/❌ [Is the package compatible with Python 3?\* Has Python 2 support been dropped?]

### 6. License ![Grade](Badge URL)

[1-2 sentences explaining the grade]

- **License Exists**: ✅/⚠️/❌ [Is a license file present?\*]
- **License Type**: ✅/⚠️/❌ [Is it permissive (BSD, MIT) rather than copyleft (GPL)?]
- **OSI Approved**: ✅/⚠️/❌ [Is it an OSI-approved license?]
```

**Emoji Usage:**
- ✅ = Fully meets the sub-standard
- ⚠️ = Partially meets or has minor issues
- ❌ = Does not meet the sub-standard

**Example (from actual evaluation):**
```markdown
### 1. Community - ![Partially met](https://img.shields.io/badge/Partially%20met-orange.svg)

While the project demonstrates open development and unique functionality, the lack of a code of conduct and limited collaboration infrastructure prevents a "Good" rating.

- **Open Development**: ✅ Code is publicly available on GitHub at https://github.com/example/package
- **Duplication**: ✅ Provides unique model-agnostic analysis functionality not found elsewhere
- **Collaboration**: ⚠️ Basic README exists but no CONTRIBUTING.md or issue templates
- **Code of Conduct**: ❌ No code of conduct file found in repository

### 3. Testing - ![Requires improvement](https://img.shields.io/badge/Requires%20improvement-red.svg)

Testing infrastructure is critically lacking with minimal unit tests, no automation, and no coverage measurement, requiring immediate attention for PyHC compliance.

- **Unit Tests**: ❌ Only one module has unit tests out of 25+ modules
- **Integration Tests**: ❌ No comprehensive integration testing framework
- **Test Coverage**: ❌ No coverage measurement implemented, estimated <5% coverage
- **Automated Testing**: ❌ No CI/CD pipeline configured
- **System/Acceptance Testing**: ⚠️ Manual validation notebooks exist but aren't automated
```

### 6. Recommendations for Full Compliance

Organize recommendations for achieving full compliance by priority:

```markdown
## Recommendations

### 🔴 "Musts"
*These must be addressed to meet minimum PyHC standards*

1. **[Action Item]**: [Specific description of what needs to be done]
   - [Sub-task if applicable]

### 🟡 "Shoulds"
*Important for package quality but not blocking compliance*

1. **[Action Item]**: [Description]

### 🟢 Suggested Improvements
*Enhancements that would strengthen the package*

1. **[Action Item]**: [Description]
```

### 7. Conclusion

```markdown
## Conclusion

[Concluding thoughts about this report, the package, and how the package complies with PyHC Standards.]
```

## Formatting Guidelines

1. **Consistency**: Use the exact section headers and structure defined above (including the italicized statements under the recommendation priority headers)
2. **Self-Identification**: The AI evaluator must identify itself with its actual model name and version (e.g., "Claude Opus 4", "Claude Sonnet 4", not generic terms)
3. **Complete Sub-standard Evaluation**: Every sub-standard listed must be explicitly evaluated with an emoji (✅/⚠️/❌) and explanation
4. **Evidence-Based**: Every assessment must include specific evidence (URLs, file references, examples)
5. **Actionable**: All recommendations must be specific and implementable
6. **Balanced**: Include both strengths and weaknesses for each standard
7. **Professional Tone**: Maintain constructive, helpful language throughout

## Evaluation Logic

**Good** (Green badge):
- All sub-standards must be met (✅)
- Minor suggestions for improvement are acceptable but not required

**Partially Met** (Orange badge):  
- Most sub-standards are met, but one or more have issues (⚠️)
- OR one sub-standard is not met (❌) but it's not critical to the standard's core purpose

**Requires Improvement** (Red badge):
- Multiple sub-standards are not met (❌)
- OR a critical sub-standard is missing that undermines the entire standard
- OR the standard is so poorly implemented that it needs major work

## Visual Elements

- Use emoji sparingly but consistently:
  - ✅ for met requirements
  - ⚠️ for partial/warning items
  - ❌ for unmet requirements
  - 🔴🟡🟢 for priority levels only
- Use badge images in tables and section headers
- Bold key terms and package names on first use
- Use code formatting for file names, commands, and code snippets

## Length Guidelines

- Executive Summary: 3-5 sentences
- Grade Justification (per standard): 1-2 sentences
- Each Sub-standard Evaluation: 1-2 sentences
- Conclusion: 3-5 sentences