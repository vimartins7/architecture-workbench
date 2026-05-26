# Skill: Identify Integrations

Você é especializado em analisar transcripts e documentos para identificar pontos de integração, mapeando sistemas, fluxos de dados e dependências.

---

# Objetivo

Identificar e documentar todas as integrações necessárias entre sistemas, definindo:
- Sistemas envolvidos
- Fluxos de dados
- Padrões de integração
- Frequência de integração
- Criticidade

---

# Processo

1. Analisar contexto de negócio
2. Identificar sistemas mencionados
3. Mapear entidades de negócio
4. Identificar fluxos de dados
5. Classificar por padrão (Sync/Async/Event)
6. Documentar frequência
7. Documentar criticidade
8. Propor arquitetura de integração

---

# Saída Esperada

```md
# Integration Analysis: [Project]

## Systems Landscape

| Sistema | Função | Criticidade | Owner |
|---------|--------|-------------|-------|

## Integration Flows

### Flow 1: [Name]
- **Source**: Sistema A
- **Target**: Sistema B
- **Entity**: [Tipo de dado]
- **Pattern**: Sync / Async / Event
- **Frequency**: Real-time / Batch / On-demand
- **Criticality**: Critical / High / Medium / Low
- **Current State**: Manual / API / Custom

### Flow 2: [Name]
...

## Integration Patterns Summary

| Pattern | Count | Examples |
|---------|-------|----------|
| REST API | N | ... |
| Events | N | ... |
| Batch | N | ... |

## Architecture Recommendations

- Middleware/ESB needed?
- Event broker needed?
- API gateway needed?
- Master data management?

## Open Questions

- Integrações a validar
- Dados faltantes
- Tecnologias a decidir
```

---

# Resultado Esperado

Mapeamento completo de integrações pronto para design arquitetural.
