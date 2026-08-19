# Quality Scenarios Builder

When asked to create quality scenarios or quality requirements, use this structured approach to develop testable, specific quality attributes.

## Purpose

Quality scenarios provide a systematic way to specify quality requirements that can be:
- Objectively measured
- Clearly communicated to stakeholders
- Used for architecture decision-making
- Validated through testing

## Quality Scenario Template

For each quality attribute, create scenarios using this structure:

```
**Scenario**: [Descriptive name]
**Quality Attribute**: [Performance, Security, Usability, etc.]
**Context**: [Normal operation, peak load, failure conditions, etc.]
**Stimulus**: [What triggers this scenario]
**Response**: [Expected system behavior]
**Response Measure**: [Quantifiable success criteria]
**Priority**: [High/Medium/Low]
**Rationale**: [Why this quality attribute matters for the system]
```

## Quality Attribute Categories

### Performance Scenarios
Focus on: Response time, throughput, capacity, resource utilization

Example questions to ask:
- "Under what load conditions must the system perform?"
- "What response times are acceptable to users?"
- "How many concurrent users must be supported?"
- "What happens when performance limits are exceeded?"

### Availability/Reliability Scenarios
Focus on: Uptime, fault tolerance, recovery time, data integrity

Example questions:
- "What level of system availability is required?"
- "How should the system respond to component failures?"
- "What is the acceptable recovery time after an outage?"
- "How critical are different system functions?"

### Security Scenarios
Focus on: Authentication, authorization, data protection, audit

Example questions:
- "What types of security threats must be prevented?"
- "How should unauthorized access attempts be handled?"
- "What data needs special protection?"
- "What audit requirements exist?"

### Usability Scenarios
Focus on: User experience, accessibility, learnability

Example questions:
- "How quickly should new users be able to complete basic tasks?"
- "What accessibility requirements must be met?"
- "How intuitive should the interface be?"

### Modifiability Scenarios
Focus on: Maintainability, extensibility, configuration

Example questions:
- "What types of changes are expected in the future?"
- "How quickly should common modifications be implementable?"
- "What configuration flexibility is needed?"

## Process for Creating Quality Scenarios

### Step 1: Stakeholder Quality Goals
Ask these questions:
1. "What does 'high quality' mean for your system and users?"
2. "What quality problems have you experienced with similar systems?"
3. "What are your biggest quality concerns for this project?"
4. "Which quality attributes could make or break user adoption?"

### Step 2: Prioritize Quality Attributes
Create a simple ranking:
1. **Critical**: System fails without this quality
2. **Important**: Significantly impacts user satisfaction  
3. **Desired**: Nice to have, but not essential

### Step 3: Develop Specific Scenarios
For each high-priority quality attribute, create 2-3 concrete scenarios covering:
- Normal operating conditions
- Stress/peak conditions  
- Failure/degraded conditions

### Step 4: Make Scenarios Measurable
Transform vague requirements into specific metrics:

**Instead of**: "System should be fast"
**Write**: "System responds to user search queries within 200ms for 95% of requests under normal load (up to 1000 concurrent users)"

**Instead of**: "System should be reliable"  
**Write**: "System maintains 99.9% uptime during business hours, with maximum 4-hour recovery time for critical functions"

## Quality Scenarios in AsciiDoc Format

```asciidoc
== Quality Requirements

=== Performance Requirements

==== Scenario: Normal User Response Time
[cols="1,3"]
|===
| Quality Attribute | Performance
| Context | Normal business operation with up to 500 concurrent users
| Stimulus | User submits a search query
| Response | System returns search results
| Response Measure | 95% of queries return results within 200ms
| Priority | High
| Rationale | Users expect immediate feedback for search operations
|===

==== Scenario: Peak Load Handling  
[cols="1,3"]
|===
| Quality Attribute | Performance
| Context | Peak usage during marketing campaigns (up to 2000 concurrent users)
| Stimulus | High volume of simultaneous user requests
| Response | System continues to function with graceful degradation
| Response Measure | Average response time < 500ms, no user requests fail
| Priority | High
| Rationale | Business campaigns drive traffic spikes that system must handle
|===

=== Security Requirements

==== Scenario: Unauthorized Access Attempt
[cols="1,3"]
|===
| Quality Attribute | Security
| Context | Production environment with active user sessions
| Stimulus | Malicious user attempts to access restricted data
| Response | System blocks access and logs security event
| Response Measure | 100% of unauthorized attempts blocked, incident logged within 1 second
| Priority | Critical
| Rationale | Customer data protection is legally required and business-critical
|===
```

## Integration with Architecture Decisions

### Link Quality Scenarios to ADRs
When creating Architecture Decision Records, reference specific quality scenarios:

```asciidoc
== ADR-003: Database Technology Selection

=== Decision
We will use PostgreSQL as our primary database.

=== Quality Scenarios Addressed
- **Performance Scenario PS-001**: Normal query response times
- **Availability Scenario AS-002**: Database failover requirements  
- **Security Scenario SS-001**: Data encryption at rest

=== Rationale
PostgreSQL best meets our quality requirements because...
```

## Validation and Testing

### Create Testable Acceptance Criteria
Each quality scenario should be translatable into:

**Performance Tests**:
```
Load test: 500 concurrent users submitting search queries
Success criteria: 95% of requests complete within 200ms
```

**Security Tests**:
```  
Penetration test: Attempt unauthorized data access
Success criteria: All attempts blocked and logged
```

**Availability Tests**:
```
Chaos engineering: Simulate database failure
Success criteria: System recovers within 4 hours
```

## Quality Scenario Review Template

Use this checklist to validate quality scenarios:

- [ ] **Specific**: Scenario describes a concrete situation
- [ ] **Measurable**: Success criteria are quantifiable  
- [ ] **Achievable**: Technically and economically feasible
- [ ] **Relevant**: Addresses real stakeholder needs
- [ ] **Testable**: Can be validated through testing
- [ ] **Prioritized**: Importance level is clear
- [ ] **Traceable**: Links to business goals and architecture decisions

## Getting Started

Begin with: "Let's define quality requirements for your system using specific, testable scenarios. 

First, help me understand what 'high quality' means for your system:
1. What are your users' main expectations for system performance?
2. What quality problems would be most damaging to your business?
3. What quality attributes have been challenging in similar systems you've worked with?"

---

*This approach ensures quality requirements are concrete, measurable, and directly useful for architecture decision-making and testing.*
