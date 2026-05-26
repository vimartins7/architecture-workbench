# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

**Architecture Workbench**: An enterprise AI platform that automatically transforms meeting transcripts into architectural documentation (ADRs, HLDs, requirements, risk assessments, roadmaps, presentations, and Mermaid diagrams).

**Language**: All outputs are Portuguese (pt-BR). See `GLOBAL-PORTUGUESE-GUIDELINES.md` for terminology mapping.

**Core Pattern**: Multi-agent system where specialized agents use reusable skills to execute workflows that consume transcripts and generate enterprise documentation.

---

## High-Level Architecture

### Component Structure

```
Agents (Decision makers)
    ↓
Skills (Reusable operations)
    ↓
Workflows (7 transcript-to-output pipelines)
    ↓
Templates (Output structure)
    ↓
Standards/Context (Constraints & patterns)
    ↓
Outputs (ADR, HLD, requirements, etc.)
```

### Key Components

**Agents** (`agents/`) — Specialized decision-makers, each with distinct responsibilities:
- `solution-architect.md` — Translates business requirements to architecture
- `requirements-engineer.md` — Extracts and validates requirements from transcripts
- `security-architect.md` — Threat modeling, LGPD compliance, vulnerability assessment
- `observability-engineer.md` — Logging strategy, metrics collection, tracing, SLA/SLO design
- `governance-agent.md` — Validates against standards, compliance review
- Plus 3 more for enterprise integration, executive presentation, and enterprise architecture

**Skills** (`skills/`) — Atomic, reusable operations invoked by agents:
- Transcript operations: `summarize-meeting`, `extract-requirements`, `detect-risks`
- Documentation: `create-adr`, `generate-hld`, `create-roadmap`, `validate-architecture`
- Executive: `create-executive-summary`

**Workflows** (`workflows/`) — Multi-agent orchestration pipelines:
- `transcript-to-adr.md` — 7-step process (~95 min) ending in Architecture Decision Record
- `transcript-to-hld.md` — 11-step process (2.5-3h) for complete solution architecture
- `transcript-to-requirements.md` — 7-step requirements extraction (1.5-2h)
- `transcript-to-mermaid.md` — Diagram generation (1.5h)
- `transcript-to-risk-analysis.md` — Risk matrix creation (2h)
- `transcript-to-presentation.md` — Executive presentation assembly (2.5h)
- `transcript-to-solution-design.md` — Full solution design (3.5-4h)

**Templates** (`templates/`) — Structured output formats:
- `adr-template.md` — ADR structure: Contexto, Problema, Decisão, Alternativas, Consequências
- `hld-template.md` — HLD structure: Resumo Executivo, Componentes, Integração, Segurança, Observabilidade
- Plus templates for requirements, risk assessment, solution design, executive presentation

**Standards & Context** — Constraints that shape output:
- `standards/naming-conventions.md` — Service, API, event, database, branch naming
- `standards/api-standards.md` — REST design, versioning, authentication
- `standards/event-standards.md` — Event naming, schema, versioning, retention
- `standards/logging-standards.md` — JSON structure, PII protection, mandatory fields
- `context/architecture-principles.md` — 10 required principles (API First, Event-Driven, Zero Trust, etc.)
- `context/security-standards.md` — OAuth2, mTLS, LGPD, OWASP compliance
- `context/lgpd-guidelines.md` — Brazilian data protection rules (mandatory read for compliance)

---

## Common Development Workflows

### Adding a New Skill

1. Create `skills/{skill-name}.md` following the skill template structure
2. Define input contract (what data it needs)
3. Define output contract (what it produces)
4. Implement 3-5 concrete steps
5. Add example usage
6. Reference it in relevant agent and workflow files
7. Test by invoking from a workflow

### Creating a New Workflow

1. Define the transcript-to-output pipeline (e.g., `transcript-to-{output-type}.md`)
2. List sequential steps showing which agent executes which skill
3. Include estimated duration, quality gates, and approval steps
4. Add decision points where human review is required (marked with 🔍)
5. Reference templates and standards that constrain output
6. Test with `sample-transcript.md`

### Modifying Standards or Principles

1. Read affected agents to understand impact
2. Update the standard in `context/` or `standards/`
3. Audit templates that reference the standard
4. Audit existing examples that might now be non-compliant
5. Document the change in `TRANSFORMATION-SUMMARY.md`

### Localizing Content to Portuguese (pt-BR)

Reference `GLOBAL-PORTUGUESE-GUIDELINES.md` — it contains:
- Complete mapping of 60+ technical terms (which stay in English, which translate)
- Rules for corporate Brazilian language
- Date, currency, and unit formatting
- Compliance checklist

When translating:
- Keep technical terms like API, OAuth2, JWT, Event-Driven, Kafka, Circuit Breaker in English
- Translate descriptions, titles, and explanations to pt-BR
- Use corporate Brazilian tone (formal, hierarchical)
- Format dates as "26 de maio de 2026" not "May 26, 2026"

---

## Key Architectural Decisions

### Why Multi-Agent?

No single agent can credibly produce an HLD that simultaneously addresses architecture, security, observability, and governance. Each agent has specialized knowledge and review responsibilities.

### Why Workflows Are Sequential

Workflows run through agents in order because later stages depend on earlier outputs (e.g., risk detection requires extracted requirements, security review requires threat model). Steps are parallelizable only when explicitly noted.

### Why Templates Are Mandatory

Templates enforce consistent structure, reduce review friction, and make outputs machine-readable for further processing or integration with external tools.

### Why Skills Are Reusable

A skill like `extract-requirements` is invoked by multiple workflows. Changes to the skill improve all workflows simultaneously. Skills are unit tests for agent capabilities.

### Enterprise First, Simplicity Second

This platform prioritizes enterprise-grade output (secure, observable, compliant, resilient) over simplicity. Every decision assumes production use and regulatory oversight.

---

## Important Standards & Patterns

### Naming Conventions (Read `standards/naming-conventions.md`)

- **Services**: `{team}-{domain}-{capability}` e.g. `billing-payment-processor`
- **APIs**: `/api/{version}/{resource}` e.g. `/api/v1/orders`
- **Events**: `{domain}.{entity}.{action}` e.g. `order.created`
- **Database**: `{environment}_{service}_{type}` e.g. `prod_order_mysql`
- **Columns**: `snake_case` e.g. `user_id`, `created_at`
- **Environment vars**: `UPPERCASE_WITH_UNDERSCORES`
- **Files/folders**: `kebab-case`
- **Git branches**: `{type}/{feature-name}` e.g. `feature/user-authentication`
- **Code**: Classes=PascalCase, methods=camelCase, constants=UPPER_SNAKE_CASE

### Mandatory Fields in Events (Read `standards/event-standards.md`)

Every event must include: `id`, `type`, `domain`, `timestamp`, `version`, `correlation_id`, `data`. Optional: `user_id`, `source`, `trace_id`.

### Security Architecture Baseline (Read `context/security-standards.md`)

- Authentication: OAuth2 for external APIs, mTLS for service-to-service
- Authorization: Role-based (RBAC) or attribute-based (ABAC)
- Data: Encryption in transit (TLS 1.2+) and at rest
- Compliance: LGPD mandatory for any Brazilian customer data
- Zero Trust: Validate every request, no implicit trust

### LGPD Compliance (Read `context/lgpd-guidelines.md`)

Key requirement: Data is a responsibility, not an asset. Before any design:
- Identify what personal data flows through the system
- Document legal basis for processing (consent, contract, legal obligation, etc.)
- Design for data minimization (collect only what's needed)
- Plan retention policies (cannot keep longer than necessary)
- Enable subject rights (access, deletion, portability)
- Implement DPA (Data Processing Agreements) with any processor

LGPD review gates are mandatory in workflows for any system handling personal data.

---

## Input/Output Specifications

### Transcript Input Format (See `examples/sample-transcript.md`)

Transcripts should be formatted as:
```
**[Time]** Speaker Name
Statement or dialogue

**[Time]** Speaker Name
Next statement
```

Include timestamps and speaker roles (Arquiteto, PO, DevOps, etc.). Workflows auto-extract decisions, risks, and requirements from the text.

### Output Quality Gates

Every workflow includes a final quality review step (marked 🔍) that validates:
- ✅ Completeness (all discussed topics covered)
- ✅ Alignment (matches principles in `context/architecture-principles.md`)
- ✅ Feasibility (technically realistic, operationally viable)
- ✅ Security (LGPD, Zero Trust, no PII exposure)
- ✅ Observability (includes logging, metrics, tracing strategy)
- ✅ Governance (approved decision records where required)

---

## Memory System

The workspace includes a persistent memory layer at `.claude/memory/` for tracking:
- User preferences and collaboration patterns
- Non-obvious decisions (why certain architecture choices were made)
- Project context (deadlines, stakeholder constraints)
- External references (Linear projects, Grafana dashboards, etc.)

Future Claude instances will read this to maintain consistency and context.

---

## Extending the Platform

### To Add a New Agent Type

1. Create `agents/{agent-name}.md` with clear scope and capabilities
2. Assign specific review responsibilities
3. List skills it can invoke
4. Reference which standards and context it enforces
5. Add to at least one workflow

### To Add a New Document Type

1. Create template in `templates/{type}-template.md`
2. Create workflow `transcript-to-{type}.md`
3. Add example in `examples/`
4. Document in README.md
5. Ensure quality gates validate against all relevant standards

### To Add a New Standard or Principle

1. Add to `context/` (for principles, compliance) or `standards/` (for technical patterns)
2. Update `GLOBAL-PORTUGUESE-GUIDELINES.md` if it affects terminology
3. Reference in relevant workflows
4. Update examples to demonstrate compliance
5. Note that new or modified standards may require governance approval before use

---

## Continuous Improvement

- All files are versioned in git; track changes via commit history
- Governance reviews happen on all architecture outputs; quality gates are non-negotiable
- Standards evolve via RFC (Request for Comment) process; document rationale in ADRs
- Templates and examples are living documents; keep them in sync with actual usage
- Portuguese localization follows the global guidelines; inconsistencies should be rare after TRANSFORMATION-SUMMARY phase

