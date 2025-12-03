# Medication Adherence Project - Structured Context

## Project Overview
This project uses Structured Context Specification (SCS) to ensure all code aligns with architecture, security, and compliance requirements.

## Versioned SCD Bundle
**Current Version:** v1.0.2
**Location:** `bundles/project-bundle-v1.0.2.yaml`
**Manifest:** `bundles/VERSION-1.0.2-MANIFEST.yaml`

---

## HOW TO USE THIS CONTEXT - READ THIS FIRST

### Three-Tier Answer Strategy

**TIER 1: Answer from THIS loaded context (NO TOOLS NEEDED)**
Answer these questions instantly without reading any files:
- "What version is the current bundle?" → v1.0.2 (stated above)
- "Which SCDs should I reference for backend work?" → Listed in Role-Specific Guidance below
- "Where are the SCDs located?" → context/project/*.yaml
- "What bundle should I use?" → project-bundle-v1.0.2.yaml
- "What domains are covered?" → Listed in Important SCDs section below

**TIER 2: Read specific SCDs (USE Read tool strategically)**
When asked about specific requirements, architecture, or constraints:
- Read the relevant SCD(s) from the list below
- Examples:
  - "What are the HIPAA requirements?" → Read `context/project/hipaa-compliance.yaml`
  - "How should authentication work?" → Read `context/project/authn-authz.yaml`
  - "What's the data model?" → Read `context/project/data-model.yaml`
- Read MULTIPLE related SCDs when needed (e.g., authn-authz + data-protection + hipaa-compliance)

**TIER 3: Explore codebase (USE Grep/Glob/Read on source files)**
Only AFTER reading relevant SCDs:
- Explore code to understand current implementation
- Identify gaps between SCDs and actual code
- Plan specific code changes
- Verify implementation details

### Critical Rules - Follow These Always

1. **NEVER use tools to answer these questions** (answers are in THIS file):
   ✗ "What version is the bundle?"
   ✗ "Which SCDs exist?"
   ✗ "Where are SCDs located?"
   ✗ "Which SCDs should I read for [role]?"

2. **ALWAYS read relevant SCDs BEFORE writing any code**
   - Don't make assumptions
   - Don't guess based on code exploration
   - Verify requirements in the actual SCD files

3. **When writing code, follow this workflow:**
   ```
   Step 1: Identify which SCDs apply (use Role-Specific Guidance below)
   Step 2: Read those SCDs to understand requirements
   Step 3: Explore existing code if needed
   Step 4: Write code that satisfies SCD requirements
   Step 5: Verify compliance with SCDs
   ```

4. **When uncertain:**
   - Ask the user for clarification
   - Don't make architectural decisions without SCD guidance
   - Don't bypass security/compliance requirements

---

## Important SCDs to Reference

### Architecture Domain
- `context/project/system-context.yaml` - System boundaries and architecture
- `context/project/tech-stack.yaml` - Technologies and frameworks
- `context/project/component-model.yaml` - Component structure
- `context/project/integration-map.yaml` - External system integrations

### Security Domain
- `context/project/authn-authz.yaml` - Authentication and authorization
- `context/project/data-protection.yaml` - Encryption and data security
- `context/project/threat-model.yaml` - Security threats and mitigations

### Compliance & Governance Domain
- `context/project/hipaa-compliance.yaml` - HIPAA requirements (CRITICAL for PHI)
- `context/project/soc2-controls.yaml` - SOC2 controls
- `context/project/chai-adherence.yaml` - CHAI requirements

### Data & Provenance Domain
- `context/project/data-model.yaml` - Data structures and schemas
- `context/project/data-handling.yaml` - Data processing rules
- `context/project/provenance-tracking.yaml` - Data lineage requirements
- `context/project/retention-policy.yaml` - Data retention rules

### Operations Domain
- `context/project/infrastructure-definition.yaml` - Infrastructure requirements
- `context/project/observability.yaml` - Monitoring and logging
- `context/project/incident-response.yaml` - Incident handling

### Testing & Validation Domain
- `context/project/test-coverage.yaml` - Test coverage requirements
- `context/project/validation-plan.yaml` - Validation scenarios
- `context/project/qa-procedures.yaml` - QA processes

### Performance & Reliability Domain
- `context/project/response-time.yaml` - Performance requirements
- `context/project/availability.yaml` - Uptime requirements
- `context/project/scalability.yaml` - Scaling requirements
- `context/project/fault-tolerance.yaml` - Resilience requirements

### Usability & Accessibility Domain
- `context/project/ux-principles.yaml` - User experience guidelines
- `context/project/accessibility-compliance.yaml` - Accessibility standards
- `context/project/error-handling-ux.yaml` - User-facing error handling

### Business Context Domain
- `context/project/business-objectives.yaml` - Business goals
- `context/project/stakeholders.yaml` - Stakeholder information
- `context/project/success-criteria.yaml` - Success metrics

### Ethics & AI Accountability Domain
- `context/project/ai-usage-policy.yaml` - AI/ML usage guidelines
- `context/project/model-bias.yaml` - Bias detection and mitigation

### Safety & Risk Domain
- `context/project/risk-assessment.yaml` - Risk analysis
- `context/project/safety-checklist.yaml` - Safety requirements

---

## Role-Specific Guidance

### For Backend Development
**Primary SCDs to read FIRST:**
- system-context, tech-stack, component-model
- authn-authz, data-protection, data-handling
- hipaa-compliance, data-model
- test-coverage

**Workflow:**
1. Read architecture SCDs to understand system structure
2. Read security + compliance SCDs for requirements
3. Read data model for schemas
4. Explore existing backend code
5. Write code that satisfies all SCD requirements
6. Add tests per test-coverage.yaml

### For Frontend Development
**Primary SCDs to read FIRST:**
- system-context, tech-stack, component-model
- ux-principles, accessibility-compliance
- error-handling-ux, authn-authz
- test-coverage

**Workflow:**
1. Read architecture + UX SCDs
2. Read accessibility requirements
3. Explore existing frontend code
4. Build UI that satisfies SCD requirements
5. Test accessibility compliance

### For DevOps/Infrastructure
**Primary SCDs to read FIRST:**
- infrastructure-definition, observability
- deployment-operations, incident-response
- availability, scalability, fault-tolerance
- data-protection (for encryption at rest/transit)

**Workflow:**
1. Read infrastructure + reliability SCDs
2. Understand monitoring and incident requirements
3. Review current infrastructure code
4. Implement changes per SCD specs

### For QA/Testing
**Primary SCDs to read FIRST:**
- test-coverage, validation-plan, qa-procedures
- All domain SCDs (to understand what to test)

**Workflow:**
1. Read testing SCDs for coverage requirements
2. Read domain SCDs to understand requirements
3. Create test plans that verify SCD compliance
4. Execute validation scenarios

### For Security Review
**Primary SCDs to read FIRST:**
- All Security domain SCDs
- All Compliance domain SCDs
- threat-model, risk-assessment
- data-protection, authn-authz

**Workflow:**
1. Read all security + compliance SCDs
2. Review code against SCD requirements
3. Identify gaps and vulnerabilities
4. Recommend remediations per SCD specs

---

## Quick Self-Check Before Taking Action

**Before using ANY tools, ask yourself:**

1. **"Can I answer this from loaded context?"**
   - Bundle version? → YES (v1.0.2)
   - Which SCDs to read? → YES (see Role-Specific Guidance)
   - Where are files? → YES (context/project/*.yaml)
   → If YES: Answer immediately without tools

2. **"Do I need specific SCD content?"**
   - Requirements for authentication? → Read authn-authz.yaml
   - HIPAA rules? → Read hipaa-compliance.yaml
   - Data structures? → Read data-model.yaml
   → If YES: Use Read tool on specific SCD(s)

3. **"Do I need to explore code?"**
   - Only AFTER reading relevant SCDs
   - To understand current implementation
   - To identify gaps with SCD requirements
   → If YES: Use Grep/Glob/Read on source files

---

## Quick Reference Commands

```bash
# View versioned bundle
cat bundles/project-bundle-v1.0.2.yaml

# View manifest
cat bundles/VERSION-1.0.2-MANIFEST.yaml

# Read a specific SCD
cat context/project/system-context.yaml

# Search for a term across all SCDs
grep -r "authentication" context/project/

# List all SCDs
ls context/project/*.yaml

# Check current version
cat VERSION
```

---

## Example Interactions

### ✅ GOOD: Answer from loaded context
**User:** "What version is the current bundle?"
**AI:** "The current bundle version is v1.0.2."
*(No tools used - instant answer)*

### ✅ GOOD: Read SCDs before coding
**User:** "Add a new API endpoint for user registration"
**AI:** "I'll read the relevant SCDs first:
1. Reading authn-authz.yaml for authentication requirements
2. Reading data-model.yaml for user schema
3. Reading hipaa-compliance.yaml for PHI handling rules
[After reading SCDs]
Now I'll implement the endpoint according to these requirements..."

### ❌ BAD: Reading files for basic info
**User:** "Which SCDs should I reference for backend work?"
**AI:** *[Uses Grep/Read tools to search]*
*(Wrong - this info is in Role-Specific Guidance above)*

### ❌ BAD: Coding without reading SCDs
**User:** "Add user authentication"
**AI:** *[Immediately starts exploring code or writing code]*
*(Wrong - must read authn-authz.yaml, data-protection.yaml, hipaa-compliance.yaml first)*

---

## Summary

**Remember:**
- Basic info about bundle, SCDs, locations → Answer instantly from THIS file
- Specific requirements, constraints, architecture → Read relevant SCDs
- Implementation details → Explore code (only AFTER reading SCDs)
- Always verify code compliance with SCD requirements
- When in doubt, read the SCD rather than guessing

**This approach ensures:**
- Fast answers for basic questions
- Accurate, compliant code
- Proper use of versioned context
- Alignment with architecture and security requirements
