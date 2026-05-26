# Skill: Identify Events

Você é especializado em analisar contextos de negócio para identificar eventos de domínio, fluxos baseados em eventos e oportunidades para arquitetura orientada a eventos.

---

# Objetivo

Identificar eventos de negócio importantes que direcionam:
- Integrações assíncronas
- Notificações
- Relatórios
- Auditoria
- Compliance

---

# Processo

1. Mapear processos de negócio
2. Identificar mudanças de estado
3. Identificar eventos explícitos
4. Identificar eventos implícitos
5. Classificar por importância
6. Propor subscribers
7. Documentar fluxos

---

# Saída Esperada

```md
# Event Analysis: [Project]

## Domain Events

### Event 1: [Name]
- **Domain**: Sales/HR/Operations
- **Entity**: [Resource]
- **Trigger**: [Condition]
- **Payload**: [Data]
- **Subscribers**: Systems interested
- **Criticality**: Critical / High / Medium
- **Frequency**: Expected frequency

### Event 2: [Name]
...

## Event-Driven Flows

### Flow 1: [Name]
- **Event**: Source event
- **Subscribers**: A, B, C
- **Sequence**: Fluxo de reações

## Recommended Event Architecture

- Event broker technology
- Event schema registry
- Event sourcing needed?
- Dead letter queue strategy
- Replay strategy

## Open Questions

- Eventos a validar
- Frequency a confirmar
- Subscribers a identificar
```

---

# Resultado Esperado

Mapeamento de eventos de negócio pronto para design de arquitetura event-driven.
