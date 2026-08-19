# Repository Structure Cleanup Plan

## Current Issues

### 1. Duplicate Content Structure
- `/prompts/` - Contains original Markdown prompts
- `/src/docs/Prompts/` - Contains AsciiDoc stubs that reference Markdown files
- Inconsistent file formats and incomplete documentation

### 2. Missing Integration
- Examples referenced but don't exist
- Broken includes in AsciiDoc files
- Inconsistent navigation

## Proposed Solution

### Phase 1: Immediate (High Priority) ✅
- [x] Create comprehensive examples in `/src/docs/examples/`
- [x] Add navigation component for website
- [x] Create complete AsciiDoc versions of prompts
- [x] Add CONTRIBUTING.md

### Phase 2: Structure Cleanup (Medium Priority)
- [ ] Keep `/prompts/` as source of truth for Markdown versions
- [ ] Complete all AsciiDoc files in `/src/docs/Prompts/`
- [ ] Add proper includes and cross-references
- [ ] Create integration documentation

### Phase 3: Enhancement (Lower Priority)
- [ ] Add GitHub issue templates
- [ ] Implement automated link checking
- [ ] Add search functionality
- [ ] Create video tutorials

## File Organization Strategy

```
LLM-Prompts/
├── prompts/                          # Source Markdown prompts (keep)
│   ├── Architecture-Communication-Canvas.md
│   ├── Architecture-Decision-Record.md
│   └── ...
├── src/docs/                         # docToolchain website content
│   ├── landingpage.gsp              # New improved landing page ✅
│   ├── navigation.adoc              # Navigation component ✅
│   ├── examples/                    # Complete examples ✅
│   │   ├── architecture-communication-canvas-example.adoc
│   │   ├── architecture-decision-record-example.adoc
│   │   └── quality-scenarios-example.adoc
│   ├── descriptions/                # Keep existing descriptions
│   └── Prompts/                     # Complete AsciiDoc versions
│       ├── 10-Intro.adoc
│       ├── 20-ACC.adoc              # Completed ✅
│       ├── 30-ADR.adoc
│       └── ...
├── .github/
│   ├── workflows/
│   │   └── gh-pages.yml            # Keep existing
│   ├── ISSUE_TEMPLATE/             # Add GitHub templates
│   │   ├── bug_report.md
│   │   ├── feature_request.md
│   │   └── prompt_suggestion.md
│   └── pull_request_template.md
├── README.adoc                      # Keep as main documentation
├── CONTRIBUTING.md                  # Added ✅
├── LICENSE                          # Add license file
└── docToolchainConfig.groovy       # Keep existing config
```

## Benefits of This Approach

1. **Clear Separation**: Markdown for development, AsciiDoc for publication
2. **Maintainability**: Single source of truth for each format
3. **User Experience**: Complete website with examples and navigation
4. **Community**: Clear contribution guidelines and templates
5. **Integration**: Proper docToolchain workflow

## Implementation Steps

### Immediate Actions Completed ✅
- Landing page redesigned with modern, engaging interface
- Navigation component created for consistent site navigation  
- Example outputs created for major prompts
- CONTRIBUTING.md with comprehensive guidelines
- Complete AsciiDoc version of ACC prompt with interactive features

### Next Actions Needed
1. Complete remaining AsciiDoc prompt files (ADR, Quality Scenarios, etc.)
2. Add GitHub issue and PR templates
3. Create LICENSE file
4. Add automated link checking workflow
5. Update main README to reflect new structure

## Quality Assurance

### Testing Checklist
- [ ] All AsciiDoc files generate correctly with docToolchain
- [ ] Navigation works on all pages
- [ ] Examples display properly
- [ ] Copy-to-clipboard functionality works
- [ ] Mobile responsiveness verified
- [ ] All internal links functional

### Validation Process
1. Test website generation locally: `./dtcw generateSite`
2. Validate AsciiDoc syntax: `./dtcw generateHTML`
3. Check responsive design on multiple screen sizes
4. Test prompt functionality with actual LLMs
5. Verify GitHub Pages deployment

This structured approach will transform the repository into a professional, user-friendly resource while maintaining backward compatibility.