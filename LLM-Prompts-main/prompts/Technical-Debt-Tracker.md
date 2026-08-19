# Technical Debt Tracker

When asked to identify, document, and manage technical debt, use this systematic approach to create a comprehensive technical debt management strategy.

## Purpose

Technical debt represents shortcuts, compromises, and suboptimal decisions made during development that may slow down future development. This prompt helps:
- Systematically identify technical debt
- Assess its impact and urgency
- Create actionable remediation plans
- Track debt evolution over time
- Make informed decisions about debt paydown vs. new features

## Technical Debt Categories

### Code Quality Debt
Issues in code structure, readability, and maintainability:
- Complex, hard-to-understand code
- Duplicated code
- Missing or inadequate tests
- Poor naming conventions
- Violation of coding standards

### Design Debt
Architectural and design shortcuts:
- Tight coupling between components
- Missing abstraction layers
- Violation of design principles (SOLID, DRY, etc.)
- Inappropriate design patterns
- Monolithic structures that should be modular

### Documentation Debt
Missing or outdated documentation:
- Undocumented APIs
- Missing architecture documentation
- Outdated technical specifications
- Missing deployment procedures
- Poor code comments

### Test Debt
Inadequate testing coverage and quality:
- Missing unit tests
- Inadequate integration tests
- No automated testing
- Flaky or unreliable tests
- Missing performance tests

### Infrastructure Debt
Operational and deployment issues:
- Manual deployment processes
- Outdated dependencies
- Security vulnerabilities
- Missing monitoring
- Inadequate backup procedures

### Knowledge Debt
Team knowledge and process issues:
- Knowledge silos
- Missing training
- Undocumented processes
- Lack of code reviews
- Missing onboarding procedures

## Technical Debt Assessment Template

For each identified debt item, use this structure:

```
**Debt ID**: [TD-001, TD-002, etc.]
**Title**: [Short descriptive name]
**Category**: [Code Quality/Design/Documentation/Test/Infrastructure/Knowledge]
**Description**: [Detailed description of the technical debt]
**Location**: [Where in the system this debt exists]
**Impact**: [How this debt affects development, performance, or maintenance]
**Interest Rate**: [How much this debt slows down development over time]
**Principal**: [Estimated effort to fix this debt completely]
**Current Workarounds**: [How the team currently deals with this issue]
**Business Impact**: [Effect on features, performance, or customer experience]
**Priority**: [Critical/High/Medium/Low]
**Owner**: [Who is responsible for addressing this debt]
**Target Date**: [When this should be addressed]
**Dependencies**: [What needs to happen before this can be fixed]
```

## Technical Debt Prioritization Matrix

### Impact vs. Effort Matrix
| Impact →<br>Effort ↓ | Low Impact | Medium Impact | High Impact |
|---|---|---|---|
| **Low Effort** | Medium Priority | High Priority | Critical Priority |
| **Medium Effort** | Low Priority | Medium Priority | High Priority |
| **High Effort** | Low Priority | Low Priority | Medium Priority |

### Priority Definitions
- **Critical**: Fix immediately, blocking current development
- **High**: Address in next sprint/iteration
- **Medium**: Plan for upcoming quarter
- **Low**: Address when convenient or during refactoring

## Interest Rate Calculation

Technical debt "interest" represents ongoing cost:

### Daily Interest (affects daily work)
- Build/deployment failures
- Frequent bug fixes in same area
- Difficulty adding new features
- Performance issues affecting users

### Weekly Interest (affects sprint work)
- Extra testing required
- Workarounds needed for features
- Knowledge transfer difficulties
- Code review complexity

### Monthly Interest (affects project delivery)
- Architecture limitations blocking features
- Maintenance overhead
- Team velocity reduction
- Customer impact

## AsciiDoc Technical Debt Register

```asciidoc
= Technical Debt Register

== Executive Summary

This document tracks technical debt in the [System Name] project, providing prioritization and remediation strategies.

=== Debt Overview by Category

[cols="2,1,1,1,1"]
|===
| Category | Critical | High | Medium | Low

| Code Quality | 2 | 5 | 8 | 12
| Design | 1 | 3 | 4 | 6
| Documentation | 0 | 2 | 7 | 15
| Test | 3 | 4 | 6 | 8
| Infrastructure | 1 | 2 | 3 | 4
| Knowledge | 0 | 1 | 5 | 10
|===

=== High-Priority Debt Items

[cols="1,2,1,1,2"]
|===
| Debt ID | Title | Category | Priority | Target Date

| TD-001 | Missing Unit Tests for Core Logic | Test | Critical | Sprint 23
| TD-003 | Monolithic Service Architecture | Design | High | Q2 2025
| TD-007 | Manual Deployment Process | Infrastructure | High | Sprint 25
|===

== Detailed Debt Analysis

=== TD-001: Missing Unit Tests for Core Logic

[cols="1,3"]
|===
| **Category** | Test Debt
| **Description** | Core business logic modules lack unit tests, making refactoring risky and bug detection difficult
| **Location** | 
- `src/core/business-rules/`
- `src/core/calculations/`
- `src/core/validation/`
| **Impact** | 
- **Development**: 40% slower feature development in core areas
- **Quality**: Higher bug rate in production (3x normal)
- **Confidence**: Developers afraid to refactor critical code
| **Interest Rate** |
- **Daily**: 2 hours extra debugging per developer
- **Weekly**: 1 day extra testing per sprint
- **Monthly**: 20% velocity reduction for core features
| **Principal** | 3 developer-weeks to add comprehensive unit tests
| **Current Workarounds** |
- Extensive manual testing before releases
- Feature flags for gradual rollouts
- Extra code review time
| **Business Impact** |
- Slower time-to-market for new features
- Higher support costs due to production bugs
- Customer satisfaction impact from defects
| **Priority** | **CRITICAL**
| **Owner** | Senior Developer Team
| **Target Date** | End of Sprint 23
| **Dependencies** | 
- Test framework setup (TD-015)
- Mock service creation (TD-016)
|===

=== TD-003: Monolithic Service Architecture

[cols="1,3"]
|===
| **Category** | Design Debt
| **Description** | Single large service handling multiple business domains, making scaling and team autonomy difficult
| **Location** | Main application service (`/src/monolith/`)
| **Impact** |
- **Scaling**: Cannot scale individual components
- **Development**: Multiple teams stepping on each other
- **Deployment**: All-or-nothing deployment risk
| **Interest Rate** |
- **Daily**: Deployment conflicts, longer build times
- **Weekly**: Cross-team coordination overhead
- **Monthly**: Inability to scale high-traffic features independently
| **Principal** | 12 developer-weeks to extract 3 core services
| **Current Workarounds** |
- Feature toggles for gradual releases
- Extensive integration testing
- Careful deployment coordination
| **Business Impact** |
- Limited ability to handle traffic spikes
- Slower feature delivery due to coordination
- Higher operational risk
| **Priority** | **HIGH**
| **Owner** | Architecture Team
| **Target Date** | Q2 2025
| **Dependencies** |
- Service mesh setup (TD-018)
- Data migration strategy (TD-019)
- Monitoring enhancement (TD-020)
|===

== Debt Remediation Plan

=== Sprint-Level Actions (Next 2-4 Weeks)
- [ ] **TD-001**: Add unit tests for payment processing module
- [ ] **TD-005**: Update API documentation for user service
- [ ] **TD-009**: Fix security vulnerability in authentication

=== Quarterly Actions (Next 3 Months)
- [ ] **TD-003**: Extract user management service from monolith
- [ ] **TD-007**: Implement automated deployment pipeline
- [ ] **TD-011**: Refactor complex calculation engine

=== Annual Actions (Next 12 Months)
- [ ] **TD-013**: Complete microservices migration
- [ ] **TD-021**: Implement comprehensive monitoring
- [ ] **TD-025**: Team knowledge sharing program

== Debt Prevention Strategies

=== Definition of Done Enhancements
- [ ] Unit test coverage > 80%
- [ ] Documentation updated
- [ ] Code review completed
- [ ] Security scan passed
- [ ] Performance impact assessed

=== Process Improvements
- [ ] Weekly debt review in retrospectives
- [ ] Debt impact assessment for new features
- [ ] Regular refactoring time allocation (20% of sprint)
- [ ] Architecture review for significant changes

=== Tooling and Automation
- [ ] Automated code quality checks
- [ ] Technical debt tracking in JIRA
- [ ] Regular dependency updates
- [ ] Continuous security scanning

== Metrics and Tracking

=== Leading Indicators
- Lines of code without tests
- Cyclomatic complexity trends
- Code duplication percentage
- Documentation coverage

=== Lagging Indicators  
- Bug fix time trends
- Feature delivery velocity
- Production incident frequency
- Developer satisfaction scores

=== Monthly Review Process
1. Update debt register with new items
2. Reassess priorities based on business impact
3. Review progress on remediation efforts
4. Identify emerging debt patterns
5. Report to stakeholders on debt trends
```

## Integration with Development Process

### Sprint Planning Integration
```
Debt Allocation Rule: Reserve 20% of sprint capacity for technical debt

Sprint Planning Checklist:
- [ ] Review critical and high-priority debt items
- [ ] Select debt items that support upcoming features
- [ ] Estimate debt work alongside feature work
- [ ] Identify opportunities to address debt during feature development
```

### Code Review Integration
```
Code Review Debt Checklist:
- [ ] Does this change introduce new technical debt?
- [ ] Could this change address existing debt?
- [ ] Are workarounds being added that create future debt?
- [ ] Is adequate testing included?
- [ ] Is documentation updated?
```

### Architecture Decision Integration
```asciidoc
== ADR-008: Service Extraction Strategy

=== Technical Debt Addressed
- **TD-003**: Monolithic Service Architecture
- **TD-012**: Deployment Coordination Overhead
- **TD-017**: Team Autonomy Limitations

=== Decision
Extract user management functionality into separate microservice.

=== Debt Remediation Impact
- Reduces monolith complexity by 30%
- Enables independent user service scaling
- Eliminates cross-team deployment dependencies
```

## Getting Started

Begin with: "Let's systematically identify and assess technical debt in your project. I'll help you create a comprehensive debt register that can guide your remediation efforts.

First, let's start with code quality debt:
1. What areas of your codebase do developers avoid or complain about working in?
2. Where do you frequently find bugs or spend extra time debugging?
3. What code makes it hard to add new features or make changes?

Then we'll move through other debt categories to get a complete picture."

---

*This systematic approach ensures technical debt is properly identified, prioritized, and managed as part of the regular development process, balancing debt paydown with feature delivery.*
