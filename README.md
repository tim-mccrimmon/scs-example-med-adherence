# med-adhere1

**Project Type**: healthcare
**SCS Version**: 0.1.0
**Created**: 2025-12-01T16:12:23.785813+00:00

## Overview

This project follows the Structured Context Specification (SCS) for organizing project context, requirements, and compliance information.

## Project Structure

```
med-adhere1/
├── bundles/                    # SCS bundles
│   ├── project-bundle.yaml    # Top-level project bundle
│   ├── meta-bundle.yaml       # Meta vocabulary bundle
│   ├── standards-bundle.yaml  # Compliance standards bundle
│   └── domains/               # Domain-specific bundles
│       ├── architecture.yaml
│       ├── security.yaml
│       └── ...
├── context/                   # SCD files
│   └── project/              # Project-tier SCDs
│       ├── system-context.yaml
│       ├── tech-stack.yaml
│       └── ...
├── docs/                      # Documentation
│   └── GETTING_STARTED.md
├── .scs/                      # SCS configuration
│   └── config
└── README.md                  # This file
```

## Getting Started

See [docs/GETTING_STARTED.md](docs/GETTING_STARTED.md) for detailed instructions on:
- Understanding the SCS structure
- Editing SCDs and bundles
- Working with domains and concerns
- Validating your context

## SCDs Included

This project includes the minimum recommended set of SCDs for a healthcare project:

- **business-context**: Domain bundle for business-context concerns
- **architecture**: Domain bundle for architecture concerns
- **security**: Domain bundle for security concerns
- **performance-reliability**: Domain bundle for performance-reliability concerns
- **usability-accessibility**: Domain bundle for usability-accessibility concerns
- **compliance-governance**: Domain bundle for compliance-governance concerns
- **data-provenance**: Domain bundle for data-provenance concerns
- **testing-validation**: Domain bundle for testing-validation concerns
- **deployment-operations**: Domain bundle for deployment-operations concerns
- **safety-risk**: Domain bundle for safety-risk concerns
- **ethics-ai-accountability**: Domain bundle for ethics-ai-accountability concerns


## Editing Context

All context is stored in YAML files:

1. **SCDs** (`context/project/*.yaml`): Structured Context Documents containing specific project information
2. **Bundles** (`bundles/**/*.yaml`): Organize and group related SCDs

Start by editing the SCDs in `context/project/` to match your project requirements.

## SCS Resources

- [SCS Specification](https://github.com/tim-mccrimmon/scs-spec)
- [Documentation](https://github.com/tim-mccrimmon/scs-spec/tree/main/docs)
- [Examples](https://github.com/tim-mccrimmon/scs-spec/tree/main/examples)

## Provenance

- **Author**: timmccrimmon
- **Email**: timmccrimmon@example.com
- **Created At**: 2025-12-01T16:12:23.785813+00:00
- **Generator**: scs-tools v0.1.0