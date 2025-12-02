# Medication Adherence Example Walk-Through

Step-by-step walkthrough of the reference implementation demonstrating how to use Structured Context Specification (SCS) to build a healthcare application with AI assistance.

## What You'll Learn

- How to scaffold an SCS healthcare project from scratch
- The 4-phase SCS development process (Intent → Validate → Version → Build)
- How to create Structured Context Documents (SCDs) for AI agents
- How to validate and version SCDs for team-wide consistency
- How to configure a development environment using versioned context bundles
- Best practices for AI-assisted development with governance and compliance built-in

## Table of Contents

1. [Goals](#goals)
2. [Setup](#setup)
3. [Understanding Structured Context](#understanding-structured-context)
4. [Project Structure](#project-structure)
5. [The Four Phases](#the-four-phases)
   - [Phase 1: Intent](#phase-1-intent)
   - [Phase 2: Validate](#phase-2-validate)
   - [Phase 3: Version](#phase-3-version)
   - [Phase 4: Build](#phase-4-build)
6. [Lessons Learned](#lessons-learned)
7. [Troubleshooting](#troubleshooting)

---

## Goals

This walkthrough demonstrates the complete SCS workflow through a real-world example. Our objectives:

- **Review & Refine Process** - Test the Intent → Validate → Version → Build workflow
- **Debug** - Identify and fix issues with tooling, templates, and validation
- **Document** - Create a reference implementation others can follow

---

## Setup

### Prerequisites

- Python 3.11 or higher
- Git

### Installation

1. **Clone the repositories**
   ```bash
   git clone https://github.com/tim-mccrimmon/scs-spec.git
   git clone https://github.com/tim-mccrimmon/scs-cli.git
   ```

2. **Install the tools**
   ```bash
   # Install scs-validator
   cd scs-spec/tools/scd-validator
   pip install -e .

   # Install scs-tools (includes validator as dependency)
   cd ../../../scs-cli
   pip install -e .
   ```

3. **Create the medication adherence project**
   ```bash
   scs new project med-adhere --type healthcare
   cd med-adhere
   ```

You now have a new project directory called `med-adhere` with healthcare-specific templates, compliance SCDs (HIPAA, CHAI, TEFCA), and the complete SCS structure.

---

## Understanding Structured Context

### Structured Context is for the Agents

This example assumes a team building the Medication Adherence Application where:
- Each team member has an AI assistant of their choice
- Governance and compliance agents monitor progress
- All agents need a consistent, authoritative view of the project

**Why This Matters:**

With multiple people and multiple agents, consistency is critical. Without a shared understanding of:
- Goals and requirements
- Technical architecture and constraints
- Security and compliance requirements
- Testing standards and procedures

...projects become unmanageable and may create legal liability.

### The AI-First Workflow

This walkthrough assumes AI is used throughout the development cycle. Each team member uses their preferred AI tool (though using the same LLM is recommended for consistency).

**Important Principle:**

> **In the future, humans should edit SCDs through AI agents, not directly.**

For now (v0.1), you'll edit YAML files directly. But the vision is agent-mediated editing where:
- Development agents build SCDs using templates and rules
- Validation agents ensure SCDs are complete, valid, and compliant
- These rules eliminate hallucinations and enforce governance

**Example of agent-mediated editing (future):**
```
User: "DevAgent - change the provenance author to Bob Smith in the system-context SCD"
DevAgent: [Makes the change while preserving all validation rules]
```

---

## Project Structure

When you run `scs new project med-adhere --type healthcare`, you get this structure:

| Directory/File | Purpose |
|----------------|---------|
| **bundles/** | SCD bundles organized by domain (architecture, security, compliance, etc.) |
| **bundles/project-bundle.yaml** | Top-level bundle referencing all project SCDs |
| **bundles/meta-bundle.yaml** | Meta-tier vocabulary and rules |
| **bundles/standards-bundle.yaml** | Compliance standards (HIPAA, CHAI, TEFCA for healthcare) |
| **bundles/domains/** | Domain-specific bundles (security, performance, data provenance, etc.) |
| **context/** | Individual Structured Context Documents (SCDs) |
| **context/project/** | Project-tier SCDs (system context, tech stack, security, compliance, etc.) |
| **docs/** | Getting started guide and documentation |
| **.scs/** | SCS configuration files |
| **README.md** | Project overview and quick start guide |
| **VERSION** | Project version tracking |

---

## The Four Phases

SCS defines a specific process for AI-assisted development:

```
Intent → Validate → Version → Build
```

Each phase has distinct goals, deliverables, and validation criteria.

---

### Phase 1: Intent

**Goal:** Define what you're building and capture all requirements, constraints, and governance expectations.

#### Define your team, Assign Roles

Define the team members, role on the team and assign responsibilities (Top-Down)

**Domains and SCDs**
- There are 11 domains listed in /yourProject/bundles/domains. 
- Each domain has several Structured Context Documents (SCDs). 
- SCD templates can be found in /your/project/context/project. 
- A Domain Owner is assigned to each domain, and the owner of each SCD is assigned an owner.

Each domain and SCD has *provenance*. Provenance identifies the owner (of the domain or SCD). This will help maintain transparency as the project moves forward.

Typically the domain owner will be responsible for all the SCDs in the domain although you may assign different owners for each. We would recommend that the domain owner be responsible for completeness and accuracy and testing of all SCDs in their domain.

#### Building initial context that defines Project Intent

The first domain to be filled out is Business Context

The team answers fundamental questions:

- **What are we building?** - Product vision, features, user needs
- **Who is it for?** - Target users, stakeholders, personas
- **What type of project is this?** - New product, upgrade, migration, etc.
- **What's the solution architecture?** - High-level design, technology choices
- **What are the governance requirements?**
  - Performance targets (response time, throughput)
  - Reliability and availability expectations
  - Scalability requirements
  - Runtime environment constraints
  - Testing standards and coverage
- **What are the security requirements?**
  - Authentication and authorization
  - Data protection and encryption
  - Threat model and mitigations
- **Are there regulatory requirements?**
  - HIPAA (healthcare)
  - GDPR (European users)
  - SOC2 (enterprise customers)
  - Industry-specific standards
- **What are the goals, expectations, and risks?**

#### How It Works

**Traditional approach:**
Business leaders, product managers, and architects create PRDs, MRDs, and Enterprise Architecture documents.

**SCS approach:**
Each person's AI assistant builds SCDs from this content using templates in /yourProject/context/project. Each individual reviews the generated SCDs and refines them with their AI assistant.

#### Deliverables

- **Draft SCDs** for all required project documents
- **Populated bundles** organizing SCDs by domain
- **Initial provenance** tracking who created what and why

#### Process

1. Team members discuss requirements and architecture
2. Each person works with their AI assistant to draft relevant SCDs
3. SCDs are reviewed for completeness and accuracy
4. AI assistant generates DRAFT versions and places them in appropriate directories
5. Another agent bundles the SCDs for team review

**Status:** This sums up the Intent Phase. As you work through this phase, document your experience below.

#### Notes from Implementation

**Completed:** December 1, 2025

**What Worked Well:**
- Project scaffolding with `scs new project` created proper structure
- Healthcare-specific templates included HIPAA, CHAI, TEFCA compliance SCDs
- Domain briefs (11 documents) provided clear structure for requirements capture
- AI-assisted content generation (transpose_briefs_to_scds.py) successfully created 39 SCDs from briefs

**Key Decisions:**
- Used 11 prescribed domains (all required for healthcare projects)
- Assigned domain owners for accountability
- Populated all SCDs with realistic medication adherence content
- Used provenance metadata to track who created what

**What We Learned:**
- Intent phase is more about organization and planning than code
- Having templates/briefs before starting is crucial
- AI can accelerate SCD creation but human review is essential
- Proper domain ownership prevents gaps in coverage

---

### Phase 2: Validate

**Goal:** Ensure all SCDs are syntactically correct, schema-compliant, semantically valid, and complete.

#### What Happens in the Validate Phase

The validation agent performs multi-level validation:

1. **Syntax Validation** - Ensures YAML is well-formed
2. **Schema Validation** - Validates against tier-specific JSON schemas
3. **Semantic Validation** - Checks type/tier matching, semver, provenance completeness
4. **Relationship Validation** - Ensures references between SCDs are valid
5. **Bundle Completeness** - Verifies all required SCDs are present
6. **Compliance Validation** - Checks domain-specific requirements

#### Tools

```bash
# Validate individual SCDs
scs validate context/project/system-context.yaml

# Validate all project SCDs
scs validate context/project/*.yaml

# Validate the complete bundle (strict mode)
scs validate --bundle bundles/project-bundle.yaml --strict

# Generate JSON validation report
scs validate --bundle bundles/project-bundle.yaml --output json
```

#### Deliverables

- **Validation report** showing errors and warnings
- **Corrected SCDs** with all validation issues resolved
- **Approval** from validation agents that bundle is ready for versioning

#### Notes from Implementation

**Completed:** December 2, 2025

**What Worked Well:**
- Validator successfully identified structural issues
- Multi-level validation (syntax, schema, semantic, bundle, completeness) caught real problems
- Clear error messages helped debug issues quickly

**Challenges Encountered:**

1. **Validator Incomplete** - Bundle validation couldn't load SCDs from domain bundles
   - **Issue:** Validator had stub code that didn't resolve SCD references
   - **Fix:** Implemented SCD loading logic in validate.py (lines 275-362)
   - **Impact:** Now properly loads and validates all 39 SCDs from 11 domain bundles

2. **Domain Grouping Bug** - SCDs not grouped correctly by domain
   - **Issue:** Validator parsed domain from SCD ID instead of using `domain` field
   - **Fix:** Updated completeness_validator.py to use `scd.get("domain")`
   - **Impact:** Resolved "Domain has 0 SCD(s)" errors

3. **Bundle Type Counting** - Incorrect counting of domain bundles
   - **Issue:** Validator counted bundle names instead of bundle types
   - **Fix:** Updated to distinguish meta/standards from domain bundles
   - **Impact:** Fixed "must have exactly 11 domain bundles" error

**Final Result:**
- ✓ Status: VALID
- ✓ 0 errors
- ⚠ 9 warnings (optional recommendations for additional SCDs)
- ✓ All 39 SCDs loaded and validated
- ✓ All 11 prescribed domains present

**Tools Used:**
```bash
scs validate --bundle bundles/project-bundle.yaml --schema-dir ../scs-spec/schema
```

**Time Investment:**
- Initial validation attempt: ~5 minutes
- Debugging and fixing validator: ~2 hours
- Final validation: ~5 seconds

**Key Learnings:**
- Validator tooling needed development to be production-ready
- Validation should happen continuously during Intent phase, not just at the end
- Having good error messages is crucial for debugging
- 0 errors is achievable; warnings are acceptable for v1.0

**Documentation Created:**
- None (validation is built into CLI)

---

### Phase 3: Version

**Goal:** Create a versioned, immutable snapshot of the SCD bundle that becomes the authoritative "contract" for development.

#### What Happens in the Version Phase

Once SCDs pass validation:

1. Bundle is assigned a semantic version (e.g., v1.0.0)
2. Immutable snapshot is created (typically in Git)
3. Bundle hash/checksum is generated for verification
4. Provenance metadata records who approved and when
5. Bundle becomes the authoritative source of truth for all agents

#### Why Versioning Matters

- **Consistency** - All agents use the same version
- **Traceability** - Track what requirements were in effect at any point
- **Governance** - Audit trail for compliance and legal requirements
- **Change Management** - Controlled updates to context

#### Deliverables

- **Versioned bundle** (e.g., `project-bundle-v1.0.0.yaml`)
- **Provenance record** documenting approval
- **Git tag** or equivalent version marker
- **Distribution** to all development environments

#### Notes from Implementation

**Completed:** December 2, 2025

**Approach:** We implemented BOTH manual and automated versioning to understand the process and build tooling.

#### Manual Versioning (v1.0.0)

**Process:**
1. Created versioned snapshot: `project-bundle-v1.0.0.yaml`
2. Added approval metadata to provenance section
3. Generated SHA-256 checksum: `283b5f13b49057386fc61caf16e0f8ba6df44daafe0b8bd4fde25e2f7ba67f1a`
4. Created version manifest: `VERSION-1.0.0-MANIFEST.yaml`
5. Git commit and annotated tag: `v1.0.0`

**Time Required:** ~15 minutes

**Documentation Created:** `manual-version-process.md` (516 lines, 13KB)

#### Automated Versioning (v1.0.2)

**Built CLI Command:**
```bash
scs bundle version --version 1.0.2 \
  --approved-by "timmccrimmon@example.com" \
  --notes "CLI-generated version"
```

**Time Required:** ~2 seconds

**What the Command Does:**
1. Validates bundle (unless --no-validate)
2. Creates versioned bundle with approval metadata
3. Generates SHA-256 checksum
4. Creates version manifest
5. Creates git commit and tag (unless --no-git)

**Documentation Created:** `automated-version-process.md` (954 lines, 21KB)

**Comparison:**

| Aspect | Manual | Automated |
|--------|--------|-----------|
| Time | ~15 minutes | ~2 seconds |
| Consistency | Prone to errors | Always consistent |
| Scriptable | No | Yes (CI/CD ready) |
| Error Handling | Manual checks | Built-in validation |

**What Worked Well:**
- Manual process helped us understand requirements deeply
- Building CLI command ensured repeatability
- Both approaches produce valid, immutable versioned bundles
- Git integration makes distribution easy

**Challenges:**
- Manual process is error-prone (typos, formatting, checksums)
- CLI command needed careful design for all edge cases
- Validation integration required finding schema directory dynamically

**Key Learnings:**
- Automation should come AFTER understanding manual process
- Immutability is enforced by convention (versioned files + git tags)
- Checksums are essential for verifying integrity
- Version manifests provide complete audit trail
- Both manual and automated documentation valuable for different audiences

**Files Created:**
- `bundles/project-bundle-v1.0.0.yaml` (manual)
- `bundles/VERSION-1.0.0-MANIFEST.yaml` (manual)
- `bundles/project-bundle-v1.0.2.yaml` (automated)
- `bundles/VERSION-1.0.2-MANIFEST.yaml` (automated)

**Git Tags:**
- `v1.0.0` (manual process)
- `v1.0.2` (automated process)

**Recommendation:** Use automated CLI command for all future versions. Keep manual documentation for training and understanding.

---

### Phase 4: Build

**Goal:** Configure development environments with the versioned SCD bundle and demonstrate AI-assisted development using Structured Context.

#### What Happens in the Build Phase

This is the critical test of whether SCS actually works:

1. **Configure IDE/Development Environment**
   - Load versioned SCD bundle into AI agent context
   - Configure App-Dev Agent Context (rules for how to use SCDs)
   - Verify agent can access and understand the context

2. **AI-Assisted Development**
   - Developers work with AI assistants that have full project context
   - AI generates code aligned with architecture, security, and compliance requirements
   - AI helps with testing, documentation, and governance tasks

3. **Continuous Validation**
   - Changes are validated against the versioned bundle
   - Compliance is checked automatically
   - Deviations are flagged for review

#### The Build Phase Test

This phase answers the question: **Does the whole system actually work?**

If the Build phase reveals that:
- SCDs are missing critical information
- Validation rules are too strict or too loose
- Context is too large for LLM windows
- Agent context structure doesn't work

...then you need time to fix the spec, templates, or tooling before Dec 5.

#### Deliverables

- **Configured development environment** with SCD bundle loaded
- **Working code** generated with AI assistance
- **Validation** that code meets requirements in SCDs
- **Documentation** of the development workflow

#### Notes from Implementation

[Document your experience here - this is the most important phase to document thoroughly]

---

## Lessons Learned

[Add lessons as you work through each phase]

### What Worked Well

- [Add items here]

### What Didn't Work

- [Add items here]

### What Would You Change

- [Add items here]

### Unexpected Insights

- [Add items here]

---

## Troubleshooting

[Document issues you encounter and how you resolved them]

### Common Issues

#### Issue: Validation fails with schema errors

**Symptom:** [Describe]

**Solution:** [Describe]

#### Issue: SCD bundle is too large for LLM context window

**Symptom:** [Describe]

**Solution:** [Describe]

#### Issue: [Add more as you encounter them]

**Symptom:**

**Solution:**

---

## Next Steps

After completing this walkthrough:

1. Extract examples from this implementation for the SCS specification
2. Document any spec gaps or unclear requirements
3. Update validation rules based on real-world use
4. Create explainer videos using this as the demonstration
5. Write blog posts/articles about the process

---

## Questions for Consideration

[Add questions that arise during implementation]

- [Question 1]
- [Question 2]
- [Question 3]

---

## Progress Summary

| Phase | Status | Completed | Key Deliverables |
|-------|--------|-----------|------------------|
| Phase 1: Intent | ✅ Complete | Dec 1, 2025 | 39 SCDs, 11 domain bundles, project structure |
| Phase 2: Validate | ✅ Complete | Dec 2, 2025 | Fixed validator, 0 errors, validated bundle |
| Phase 3: Version | ✅ Complete | Dec 2, 2025 | v1.0.0 (manual), v1.0.2 (CLI), tooling built |
| Phase 4: Build | ⏸️ Pending | - | Configure dev environments, AI-assisted development |

## Lessons Learned

### What Worked Well

1. **Structured Approach** - The 4-phase process provided clear milestones
2. **AI Assistance** - Used AI throughout for content generation and debugging
3. **Validation-First** - Catching errors early prevented downstream issues
4. **Both Manual & Automated** - Understanding manual process informed automation
5. **Documentation** - Creating docs alongside work captured knowledge while fresh

### What Didn't Work / Challenges

1. **Validator Immaturity** - Significant development needed to make validator functional
2. **Schema Path Issues** - Finding schema directory dynamically was tricky
3. **Time Estimation** - Phase 2 took longer than expected due to validator fixes
4. **Validation During Intent** - Should have validated SCDs continuously, not at end

### What We Would Change

1. **Validate Continuously** - Run validation on SCDs as they're created in Phase 1
2. **Test Tooling First** - Verify validator works before generating all content
3. **Automated Tests** - Add tests for validator to prevent regressions
4. **Better Templates** - Some SCD templates could be more specific
5. **Early Git Tags** - Consider tagging after each phase completion

### Unexpected Insights

1. **Validator is Critical** - Without working validation, the whole process stalls
2. **Immutability is Convention** - Git tags + versioned filenames enforce immutability
3. **Checksums are Essential** - SHA-256 provides confidence in integrity
4. **Manual First, Then Automate** - Understanding manual process crucial for good automation
5. **Documentation is a Deliverable** - Process docs as important as versioned bundles

### Technical Debt Created

1. **Validator Schema Path** - Hardcoded search paths, should be configurable
2. **Validation Integration** - CLI validation could be smarter about finding schemas
3. **Error Messages** - Some validator errors could be more actionable
4. **Test Coverage** - No automated tests for validator or CLI commands
5. **Bundle Command Registration** - Some bundle subcommands may not be fully registered

### Recommendations for Next Project

1. **Start with Validation** - Ensure all tooling works before Phase 1
2. **Continuous Validation** - Validate SCDs incrementally during Intent phase
3. **Automated Testing** - Add tests before building on tooling
4. **CI/CD from Start** - Set up automated validation in CI from day 1
5. **Version Early** - Consider versioning after each major milestone

---

*Last Updated: December 2, 2025*
*Status: Phases 1-3 Complete, Phase 4 Pending*
*Next Milestone: Configure development environment with versioned bundle (Phase 4)*
