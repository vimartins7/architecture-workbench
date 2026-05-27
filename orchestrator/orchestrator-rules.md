# AI Orchestrator Rules

## Objetivo

Coordenar execução dos agentes IA para produzir outputs de qualidade consistente.

---

## Responsabilidades do Orchestrator

1. **Resolver contexto** — Determinar estado atual (KB, memory, initiative, inputs)
2. **Consultar KB primeiro** — Knowledge Base é fonte de verdade
3. **Enriquecer com memória** — Adicionar contexto global, initiative, domain
4. **Analisar iniciativa atual** — Se em projeto, ativar initiative memory
5. **Selecionar workflows** — Qual transcript-to-output é apropriado?
6. **Selecionar agentes** — Quais agentes são necessários?
7. **Evitar redundância** — Não reexecutar se output já existe
8. **Consolidar outputs** — Mesclar resultados, validar consistência

---

## Ordem Obrigatória de Resolução

1. **Knowledge Base** (`standards/`, `context/`, `templates/`)
2. **Standards** (naming, API, events, logging, Mermaid)
3. **Memory Global** (`memory/global/`)
4. **Initiative Memory** (`memory/initiatives/{current}/`)
5. **Domain Memory** (`memory/domains/{domain}/`)
6. **Inputs locais** (transcripts, requisições do usuário)

---

## Workflow Selection

| Input | Workflow | Agentes | Duração |
|-------|----------|---------|---------|
| Transcript técnico | transcript-to-adr | Solution Architect, Security, Governance | 95 min |
| Requisitos de negócio | transcript-to-requirements | Requirements Engineer, Solution Architect | 1.5-2h |
| Arquitetura completa | transcript-to-hld | Enterprise Architect, Security, Observability, Governance | 2.5-3h |
| Análise de risco | transcript-to-risk-analysis | Security Architect, Governance | 2h |
| Apresentação executiva | transcript-to-presentation | Executive Presentation Agent | 2.5h |
| Diagramas | transcript-to-mermaid | Enterprise Architect | 1.5h |
| Solução completa | transcript-to-solution-design | Solution Architect, Security, Observability, Governance | 3.5-4h |

---

## Agent Selection Logic

```
IF análise de requisitos THEN
  SELECT requirements-engineer
  ADD solution-architect
END

IF arquitetura THEN
  SELECT solution-architect OR enterprise-architect
  ADD security-architect
  ADD observability-engineer
  ADD governance-agent
END

IF segurança THEN
  SELECT security-architect (sempre)
  ADD governance-agent
END

IF executivo THEN
  SELECT executive-presentation-agent
END
```

---

## Outputs Possíveis

- **ADR** — Architecture Decision Record (governance gate)
- **HLD** — High-Level Design (multi-agent review)
- **Mermaid** — Diagramas (arquitetura, fluxos, sequência)
- **Requirements** — Requisitos funcionais e não-funcionais
- **Risk Analysis** — Matriz de riscos e mitigações
- **Executive Summary** — Resumo C-level (ROI, timeline, risks)
- **Roadmap** — Timeline técnico e dependências
- **Solution Design** — Design completo com WBS, EAP, estimativas

---

## Validação e Qualidade

Antes de entregar output:
- ✅ Validar contra padrões (`standards/`)
- ✅ Validar contra princípios (`context/architecture-principles.md`)
- ✅ Validar contra conformidade LGPD (`context/lgpd-guidelines.md`)
- ✅ Detectar inconsistências com memoria existente
- ✅ Detectar conflitos com decisões anteriores

---

## Regras

**Nunca:**
- Ignorar Knowledge Base
- Gerar contexto duplicado
- Sobrescrever outputs sem validação
- Usar internet sem consentimento
- Ignorar memory existente

**Sempre:**
- Reutilizar conhecimento
- Correlacionar com arquivos existentes
- Detectar inconsistências
- Preservar decisões anteriores
- Documentar evolução arquitetural
