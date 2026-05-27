# Context Resolution Rules

## Objetivo

Definir como agentes resolvem contexto antes de tomar decisões ou gerar outputs.

---

## Ordem Obrigatória de Contexto

```
┌─────────────────────────────────────┐
│ 1. Knowledge Base                   │ ← Source of truth
│    (standards/, context/, templates)│
├─────────────────────────────────────┤
│ 2. Standards                        │ ← Constraints
│    (naming, API, events, logging)   │
├─────────────────────────────────────┤
│ 3. Memory - Global                  │ ← Corporate context
│    (architecture-decisions, vendors)│
├─────────────────────────────────────┤
│ 4. Memory - Initiative              │ ← Project context
│    (se em projeto)                  │
├─────────────────────────────────────┤
│ 5. Memory - Domain                  │ ← Domain expertise
│    (patterns, tech stack, risks)    │
├─────────────────────────────────────┤
│ 6. Inputs Locais                    │ ← New information
│    (transcripts, requisições)       │
└─────────────────────────────────────┘
```

---

## Regras de Resolução

Os agentes **DEVEM**:

1. **Consultar KB antes de inferir** — Se `standards/api-standards.md` existe, usar, não inventar
2. **Reutilizar memória existente** — Se decision já foi tomada, não decidir novamente
3. **Correlacionar arquivos** — Se ADR-001 existe, relacionar com HLD, requirements, risk analysis
4. **Detectar inconsistências** — Se memory contradiz KB, reportar e escalate para governance
5. **Evitar duplicidade** — Se output já existe, validar antes de recriar
6. **Rastrear evolução** — Documentar quando decisões mudam e por quê

---

## Internet

Internet **só pode ser utilizada**:
- ✅ Quando explicitamente solicitado ("pesquise na web sobre X")
- ✅ Quando KB não possuir contexto relevante
- ✅ Quando iniciativa não possuir informação suficiente
- ✅ Para validar tecnologias novas não documentadas

Internet **nunca pode ser utilizada**:
- ❌ Para substituir contexto corporativo
- ❌ Para ignorar padrões internos
- ❌ Para buscar informações sensíveis
- ❌ Para compartilhar conhecimento corporativo

---

## Conflito de Contexto

Se contextos conflitarem (ex: memory diz use Kafka, mas novo transcript sugere RabbitMQ):

1. **Reportar o conflito** ao usuário
2. **Não escolher sozinho**
3. **Sugerir RFC** para atualizar padrão
4. **Escalate para governance** se impacto é alto
5. **Documentar a decisão** quando for tomada

---

## Lifecycle de Contexto

```
Resolve → Enrich → Validate → Use → Document
```

1. **Resolve** — Determinar contexto necessário
2. **Enrich** — Adicionar memoria, KB, standards
3. **Validate** — Verificar consistência e conflitos
4. **Use** — Utilizar contexto para gerar output
5. **Document** — Atualizar memoria, rastrear evolução
