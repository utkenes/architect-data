# Risk Assessment Matrix

When asked to identify and assess architecture risks, use this systematic approach to create a comprehensive risk management strategy.

## Purpose

This prompt helps systematically identify, assess, and mitigate risks in software architecture projects. It creates a structured risk register that can be used for:
- Architecture decision-making
- Project planning and risk management
- Stakeholder communication
- Continuous risk monitoring

## Risk Assessment Process

### Step 1: Risk Identification Categories

Ask questions in these categories to systematically discover risks:

#### Technical Risks
- "What technologies are you using that your team has limited experience with?"
- "Which external systems or APIs does your system depend on?"
- "What assumptions are you making about system performance or scalability?"
- "Are there any unproven or cutting-edge technologies in your stack?"

#### Organizational Risks  
- "What skills gaps exist in your team for this project?"
- "How stable is your team composition during the project timeline?"
- "What competing priorities might affect resource allocation?"
- "Are there knowledge silos or key person dependencies?"

#### External Risks
- "What external dependencies could impact your project?"
- "Are there regulatory or compliance changes on the horizon?"
- "How might market or business changes affect requirements?"
- "What vendor or third-party risks exist?"

#### Business Risks
- "What happens if the system doesn't meet performance expectations?"
- "How critical is the go-live timeline to business success?"
- "What are the consequences of security breaches or data loss?"
- "How might user adoption challenges impact the project?"

### Step 2: Risk Assessment Matrix

For each identified risk, evaluate using this template:

```
**Risk ID**: [R-001, R-002, etc.]
**Risk Title**: [Short descriptive name]
**Category**: [Technical/Organizational/External/Business]
**Description**: [Detailed description of the risk]
**Probability**: [High/Medium/Low - likelihood of occurrence]
**Impact**: [High/Medium/Low - consequence if it occurs]
**Risk Level**: [Critical/High/Medium/Low - combination of probability and impact]
**Current Controls**: [What measures are already in place]
**Additional Mitigation**: [What else could be done]
**Owner**: [Who is responsible for monitoring this risk]
**Timeline**: [When might this risk materialize]
**Early Warning Signs**: [Indicators that this risk is becoming reality]
```

## Risk Priority Matrix

### Risk Level Calculation
| Impact →<br>Probability ↓ | Low | Medium | High |
|---|---|---|---|
| **Low** | Low | Low | Medium |
| **Medium** | Low | Medium | High |  
| **High** | Medium | High | Critical |

### Priority Definitions
- **Critical**: Immediate attention required, could stop the project
- **High**: Needs active management and mitigation planning
- **Medium**: Monitor regularly, have contingency plans ready
- **Low**: Monitor periodically, accept or transfer risk

## Risk Categories with Examples

### Technical Architecture Risks

**Example: Technology Maturity Risk**
```
Risk ID: R-001
Risk Title: New Framework Adoption Risk
Category: Technical
Description: Using a recently released framework (v1.0) for core functionality
Probability: Medium (framework bugs are common in early versions)
Impact: High (could require significant rework)
Risk Level: High
Current Controls: Prototype testing, community monitoring
Additional Mitigation: Plan fallback to proven alternative, allocate extra testing time
Owner: Technical Lead
Timeline: Throughout development phase
Early Warning Signs: Bug reports increase, breaking changes in patch versions
```

### Integration Risks

**Example: External API Dependency**
```
Risk ID: R-002
Risk Title: Third-Party API Availability Risk
Category: External
Description: Core functionality depends on external payment processing API
Probability: Low (established provider with good SLA)
Impact: High (system unusable without payment processing)
Risk Level: Medium
Current Controls: SLA monitoring, error handling
Additional Mitigation: Implement backup payment provider, circuit breaker pattern
Owner: Integration Lead
Timeline: Any time during operation
Early Warning Signs: Increased API response times, intermittent failures
```

### Performance Risks

**Example: Scalability Assumptions**
```
Risk ID: R-003
Risk Title: Database Performance Under Load
Category: Technical
Description: Current database design untested at expected production volumes
Probability: Medium (common issue with new systems)
Impact: High (user experience degradation, potential system failure)
Risk Level: High
Current Controls: Load testing planned
Additional Mitigation: Database optimization, read replicas, caching layer
Owner: Database Administrator
Timeline: After go-live under increased load
Early Warning Signs: Query response times increasing, database CPU utilization high
```

## AsciiDoc Risk Register Template

```asciidoc
= Risk Assessment Matrix

== Executive Summary

This document identifies and assesses risks for the [System Name] project, providing mitigation strategies and ownership assignments.

== Risk Overview

[cols="1,2,1,1,1,2"]
|===
| Risk ID | Risk Title | Category | Probability | Impact | Risk Level

| R-001 | New Framework Adoption | Technical | Medium | High | High
| R-002 | Third-Party API Dependency | External | Low | High | Medium
| R-003 | Database Performance | Technical | Medium | High | High
|===

== Detailed Risk Analysis

=== R-001: New Framework Adoption Risk

[cols="1,3"]
|===
| **Category** | Technical
| **Description** | Using recently released framework (v1.0) for core functionality
| **Probability** | Medium - Framework bugs common in early versions
| **Impact** | High - Could require significant rework
| **Risk Level** | **HIGH**
| **Current Controls** | 
- Prototype testing completed
- Active community monitoring
- Technical spike completed
| **Additional Mitigation** | 
- Identify and test fallback framework
- Allocate 20% extra time for framework issues
- Establish direct contact with framework maintainers
| **Owner** | Technical Lead
| **Timeline** | Throughout development phase
| **Early Warning Signs** |
- Increasing bug reports in framework repository
- Breaking changes in patch versions
- Community discussions about stability issues
| **Review Date** | Monthly during development
|===

=== R-002: Third-Party API Availability Risk

[cols="1,3"]
|===
| **Category** | External
| **Description** | Core functionality depends on external payment processing API
| **Probability** | Low - Established provider with 99.9% SLA
| **Impact** | High - System unusable without payment processing
| **Risk Level** | **MEDIUM**
| **Current Controls** |
- SLA monitoring in place
- Error handling implemented
- Provider status page monitoring
| **Additional Mitigation** |
- Implement secondary payment provider
- Add circuit breaker pattern
- Create manual payment fallback process
| **Owner** | Integration Lead
| **Timeline** | Any time during operation
| **Early Warning Signs** |
- Increased API response times
- Intermittent API failures
- Provider status page alerts
| **Review Date** | Quarterly
|===

== Risk Mitigation Plan

=== Immediate Actions (Next 30 Days)
- [ ] Complete framework fallback analysis (R-001)
- [ ] Implement API monitoring dashboard (R-002)
- [ ] Conduct load testing (R-003)

=== Short-term Actions (Next 90 Days)  
- [ ] Develop secondary payment integration (R-002)
- [ ] Implement caching layer (R-003)
- [ ] Create risk monitoring automation

=== Long-term Actions (Next 6 Months)
- [ ] Quarterly risk assessment reviews
- [ ] Post-implementation risk validation
- [ ] Risk register maintenance process

== Risk Monitoring

=== Weekly Reviews
- Monitor early warning indicators
- Update risk status
- Escalate critical risks

=== Monthly Reviews
- Assess risk mitigation progress
- Identify new risks
- Update risk levels

=== Quarterly Reviews
- Complete risk register review
- Validate mitigation effectiveness
- Update risk management process
```

## Risk-Driven Architecture Decisions

### Linking Risks to ADRs

When creating Architecture Decision Records, reference relevant risks:

```asciidoc
== ADR-005: Caching Strategy Selection

=== Context
Performance requirements and scalability risks drive need for caching solution.

=== Risks Addressed
- **R-003**: Database Performance Under Load
- **R-007**: Response Time Requirements

=== Decision
Implement Redis-based caching with write-through strategy.

=== Risk Mitigation
- Reduces database load (addresses R-003)
- Improves response times (addresses R-007)
- Introduces new dependency risk (R-008: Redis availability)
```

## Continuous Risk Management

### Risk Review Cadence
- **Daily**: Monitor critical risk indicators
- **Weekly**: Review high-priority risks  
- **Monthly**: Update risk assessments
- **Quarterly**: Complete comprehensive risk review

### Risk Escalation Triggers
- Risk level increases to Critical
- Mitigation actions are not effective
- New risks emerge that threaten project success
- Early warning signs indicate risk materialization

## Getting Started

Begin with: "Let's systematically identify and assess risks for your architecture project. I'll guide you through different risk categories to ensure we don't miss anything important.

First, let's look at technical risks:
1. What technologies or frameworks are you planning to use that are new to your team?
2. Which external systems or APIs will your system depend on?
3. What assumptions are you making about performance, scalability, or capacity?"

---

*This systematic approach ensures comprehensive risk identification and provides a structured framework for ongoing risk management throughout the project lifecycle.*
