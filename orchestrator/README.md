# AI Orchestrator

## Objetivo

Coordenar execução dos agentes IA para transformar transcritos em documentação arquitetural.

---

## Responsabilidades

- **Context Resolution** — Determinar estado, memoria, standards
- **Workflow Selection** — Qual transcript-to-output é apropriado?
- **Agent Orchestration** — Qual agente faz o quê?
- **Quality Gates** — Validar outputs antes de entregar
- **Memory Management** — Persistir conhecimento, evitar duplicidade

---

## Como Funciona

1. Usuário fornece transcript ou solicitação
2. Orchestrator resolve contexto (KB → Memory → Inputs)
3. Orchestrator seleciona workflow apropriado
4. Workflow executa agentes em sequência
5. Cada agente produz output (ADR, HLD, requirements, etc)
6. Outputs são validados contra standards e memory
7. Outputs consolidados e entregues

---

## Arquivos de Configuração

- `orchestrator-rules.md` — Regras de orquestração
- `../context-engine/context-resolution-rules.md` — Resolução de contexto
- `../standards/memory-rules.md` — Regras de memória

---

## Próximos Passos

- [ ] Implementar contexto-aware execution
- [ ] Criar initiative templates
- [ ] Integrar memory persistence
- [ ] Criar agent coordination examples
