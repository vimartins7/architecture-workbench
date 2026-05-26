# Padrões de Eventos

Padrões para eventos em arquitetura orientada a eventos.

---

## Nomenclatura de Eventos

### Formato
`{domain}.{entity}.{action}`

### Exemplos
- `order.created`
- `order.cancelled`
- `user.registered`
- `payment.processed`
- `notification.sent`

---

## Estrutura de Evento

### Campos Obrigatórios
```json
{
  "id": "event-uuid",
  "type": "order.created",
  "domain": "orders",
  "timestamp": "2026-05-26T14:30:00Z",
  "version": "1.0.0",
  "correlation_id": "request-uuid",
  "data": { ... }
}
```

### Campos Opcionais
- `user_id`: Quem disparou o evento
- `source`: Sistema originando o evento
- `trace_id`: Para rastreamento distribuído

---

## Versionamento de Eventos

### Versionamento Semântico
- Formato `1.0.0`
- Mudanças que quebram compatibilidade = versão major
- Mudanças que não quebram compatibilidade = versão minor

### Evolução de Evento
```json
{
  "type": "user.registered",
  "version": "2.0.0",
  "schema_uri": "https://schemas.company.com/user-registered-2.0.0.json"
}
```

---

## Registro de Schema

Todos os eventos devem ser registrados:
- Schema armazenado no registro
- Versão rastreada
- Regras de compatibilidade aplicadas

---

## Retenção de Eventos

| Tipo de Evento | Retenção | Replay |
|---|---|---|
| Crítico | 1 ano | Obrigatório |
| Negócio | 90 dias | Obrigatório |
| Auditoria | 1 ano | Obrigatório |
| Operacional | 30 dias | Opcional |

---

## Dead Letter Queue

Eventos falhados vão para DLQ:
- Reprocessamento automático após 1 hora
- Intervenção manual após 3 falhas
- Notificação enviada após 5 falhas
- Escalação após 10 falhas

---

## Idempotência

Eventos devem ser idempotentes:
- Use campo `id` para deduplicação
- Subscribers rastreiam IDs de eventos processados
- Seguro reprocessar mesmo evento

---

## Conformidade

Todos os eventos devem:
- [ ] Ter ID único
- [ ] Ter timestamp
- [ ] Ter Correlation ID
- [ ] Ter schema
- [ ] Ser versionados
- [ ] Ter política de retenção
