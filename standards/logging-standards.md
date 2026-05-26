# Padrões de Logging

Padrões obrigatórios para logs em toda a plataforma.

---

## Formato de Log

### Logging Estruturado (JSON)
```json
{
  "timestamp": "2026-05-26T14:30:00.123Z",
  "level": "INFO",
  "service": "order-service",
  "request_id": "uuid-v4",
  "user_id": "user-uuid",
  "message": "Pedido criado com sucesso",
  "context": {
    "order_id": "order-uuid",
    "amount": 99.99,
    "duration_ms": 145
  }
}
```

---

## Níveis de Log

| Nível | Uso | Exemplo |
|-------|-----|---------|
| DEBUG | Desenvolvimento/solução de problemas | Valores de variáveis, rastreamento de fluxo |
| INFO | Eventos de negócio importantes | Pedido criado, usuário conectado |
| WARN | Potenciais problemas | Tentativas de retry, API deprecada |
| ERROR | Erro mas serviço continua | Timeout de API, retry esgotado |
| FATAL | Serviço não pode continuar | Conexão de banco de dados perdida |

---

## Campos Obrigatórios

Toda entrada de log DEVE ter:
- `timestamp` (ISO 8601 UTC)
- `level` (DEBUG, INFO, WARN, ERROR, FATAL)
- `service` (serviço originando o log)
- `request_id` (Correlation ID)
- `message` (legível para humanos)

---

## Campos Recomendados

- `user_id`: Contexto do usuário
- `trace_id`: ID de rastreamento distribuído
- `duration_ms`: Duração da operação
- `status_code`: Status HTTP (se aplicável)
- `error_code`: Código de erro de negócio

---

## Proteção de PII

Nunca registre em logs:
- ❌ Senhas
- ❌ Números de cartão de crédito
- ❌ Chaves de API
- ❌ Dados de saúde pessoal
- ❌ Números de CPF/ID completos

Registre em logs:
- ✅ Valores hashed ou mascarados
- ✅ Últimos 4 dígitos do cartão
- ✅ ID do usuário (não nome)
- ✅ Primeiros 2 e últimos 2 caracteres do CPF

---

## Retenção de Log

| Tipo de Log | Retenção | Arquivamento |
|---|---|---|
| Aplicação | 30 dias | 1 ano |
| Auditoria | 1 ano | 7 anos |
| Segurança | 1 ano | 7 anos |

---

## Conformidade

Todos os serviços devem:
- [ ] Usar logging estruturado (JSON)
- [ ] Incluir Correlation ID
- [ ] Sem PII em logs
- [ ] Níveis de log apropriados
- [ ] Agregação centralizada de logs
- [ ] Política de retenção aplicada
