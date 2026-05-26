# Padrões de Observabilidade

Requisitos obrigatórios para observabilidade em todos os sistemas.

---

## Logging Estruturado

### Requisitos
- Formato JSON
- Correlation ID em cada entrada de log
- Nível de log: DEBUG, INFO, WARN, ERROR
- Timestamp em ISO 8601 UTC

### Campos Obrigatórios
```json
{
  "timestamp": "2026-05-26T14:30:00Z",
  "level": "INFO",
  "service": "nome-do-servico",
  "request_id": "uuid-v4",
  "user_id": "uuid-v4",
  "message": "Mensagem legível para humanos",
  "context": {
    "duration_ms": 150,
    "status": 200
  }
}
```

---

## Coleta de Métricas

### Sinais Dourados (Todos os Serviços)
- Latência: p50, p95, p99
- Tráfego: requisições por segundo
- Erros: percentual de taxa de erro
- Saturação: utilização de recursos

### Métricas de Aplicação
- Métricas de negócio (Pedidos, receita, etc.)
- Métricas de domínio personalizadas
- Profundidade da fila
- Taxa de acerto de cache

---

## Rastreamento Distribuído

### Requisitos
- Todas as chamadas de API externas rastreadas
- Todos os eventos rastreados
- Mapa de serviços atualizado

### Estratégia de Amostragem
- Caminhos de alto tráfego: amostragem de 1%
- Caminhos de erro: amostragem de 100%
- Caminhos de baixo tráfego: amostragem de 100%

---

## Alertas

### Nomenclatura de Alerta
- Formato Service.Metric.Severity
- Exemplo: `api.latency.p99.warning`

### Níveis de Alerta
- CRITICAL: Página on-call
- HIGH: Notificação Slack
- MEDIUM: Apenas dashboard
- LOW: Resumo diário

### Runbooks
- Todo alerta deve ter runbook
- Runbook contém passos de solução de problemas
- Caminho de escalação claro

---

## Definição de SLA/SLO

Todos os serviços devem definir:
- **SLA**: Acordo de Nível de Serviço (contratual)
- **SLO**: Objetivo de Nível de Serviço (meta interna)
- **SLI**: Indicador de Nível de Serviço (métrica medida)

### Exemplo
- SLO: 99,9% de uptime
- SLI: Respostas HTTP 2xx + 3xx / total de requisições
- Orçamento de erro: 0,1% = 43 minutos por mês

---

## Conformidade

Todos os sistemas devem:
- [ ] Ter logging centralizado
- [ ] Ter métricas coletadas
- [ ] Ter rastreamento distribuído (se multi-serviço)
- [ ] Ter alertas configurados
- [ ] Ter SLA/SLO definidos
- [ ] Ter runbooks documentados
