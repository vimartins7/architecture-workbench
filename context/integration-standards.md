# Padrões de Integração

Padrões obrigatórios para todas as integrações entre sistemas.

---

## Padrões de API

### REST API (Primária)
- HTTP/1.1 ou HTTP/2
- Payloads JSON
- Verbos HTTP padrão (GET, POST, PUT, DELETE)
- Códigos de status HTTP conforme especificação
- Versionamento de API (v1, v2, etc.)
- Compatibilidade retroativa por 2 versões menores

### API Assíncrona (Baseada em Eventos)
- Tecnologia de message broker: [a definir]
- Registro de schema de eventos obrigatório
- Versionamento de eventos: [estratégia]
- Retenção: [política]
- Capacidade de replay: obrigatória

### gRPC (Alto Desempenho)
- Para comunicação interna entre serviços
- Protocol Buffers para schemas
- Criptografia TLS obrigatória

---

## Retry e Resiliência

### Estratégia de Retry
- Máximo de retries: 3
- Backoff: Exponencial (2^n segundos)
- Jitter: ±20%
- Timeout: 30 segundos por requisição

### Circuit Breaker
- Limiar de falha: 5 falhas consecutivas
- Timeout antes de retry: 60 segundos
- Estado half-open: 30 segundos

### Dead Letter Queue
- Obrigatória para integrações assíncronas
- Retenção: 30 dias
- Processo de intervenção manual

---

## Tratamento de Erros

### Respostas de Erro HTTP
```json
{
  "error": {
    "code": "INVALID_REQUEST",
    "message": "Mensagem amigável ao usuário",
    "details": {
      "field": "email",
      "reason": "formato inválido"
    },
    "request_id": "correlation-id"
  }
}
```

---

## Padrões de Dados

### Formato de Data e Hora
- ISO 8601: YYYY-MM-DDTHH:mm:ssZ
- Fuso horário: UTC sempre

### Formato de Número
- Use strings para números de alta precisão
- Moeda: use centavos (ex: 1000 = R$ 10,00)

---

## Padrões de Segurança

### Autenticação
- OAuth2 para integrações externas
- mTLS para serviço a serviço interno

### Autorização
- Escopos claramente definidos
- Princípio do menor privilégio
- Logging de auditoria de acesso

---

## Observabilidade

### Logging
- Correlation ID em cada requisição
- Nível de log: INFO mínimo
- Logging estruturado (JSON)

### Métricas
- Latência de requisição HTTP (p50, p95, p99)
- Taxa de erro
- Taxa de sucesso
- Throughput

### Rastreamento
- Rastreamento distribuído para fluxos > 2 hops
- Visualização de mapa de serviços obrigatória

---

## Governança

Todas as integrações devem:
1. Ter SLA claro
2. Ter contrato de API documentado
3. Ter estratégia de monitoramento
4. Ter revisão de segurança
5. Estar em conformidade com padrões
6. Estar no registro de integrações
