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

[Document your experience here as you work through Intent Phase]

- What worked well?
- What was confusing?
- What took longer than expected?
- What would you change?

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

[Document your experience here]

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

[Document your experience here]

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

*Last Updated: [Date]*
*Status: Intent Phase in progress*
