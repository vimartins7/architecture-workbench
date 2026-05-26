# Template: Arquitetura de Integração

```md
# Arquitetura de Integração: [Nome]

## Informações do Documento

| Campo | Valor |
|---|---|
| Projeto | |
| Sistemas | Sistema A ↔ Sistema B |
| Responsável | |
| Data | |
| Status | Rascunho / Revisão / Aprovado |

---

## Resumo Executivo

- Objetivo da integração
- Sistemas envolvidos
- Padrão de integração
- Benefícios esperados
- Timeline

---

## Contexto de Negócio

### Estado Atual
- Como está atualmente?
- Problemas atuais
- Impacto dos problemas

### Estado Alvo
- Como será após integração
- Benefícios esperados
- Impacto esperado

---

## Visão Geral dos Sistemas

### Sistema A
| Atributo | Valor |
|----------|-------|
| Nome | |
| Responsável | |
| Criticidade | |
| Tecnologia | |
| SLA | |

### Sistema B
| Atributo | Valor |
|----------|-------|
| Nome | |
| Responsável | |
| Criticidade | |
| Tecnologia | |
| SLA | |

---

## Fluxo de Integração

### Modelo de Dados

| Entidade | Descrição | Frequência |
|----------|-----------|-----------|

### Padrão de Integração

**Padrão**: API / Eventos / Batch / Customizado

**Justificativa**:
- Por que este padrão?
- Alternativas consideradas
- Trade-offs

### Fluxo Detalhado

```
Sistema A → [Integração] → Sistema B
   |            |            |
   └─ Trigger   ├─ Transform └─ Process
                └─ Route
```

**Passo a passo**:
1. [Ação Sistema A]
2. [Passo de Integração]
3. [Ação Sistema B]

---

## Projeto Técnico

### Interfaces e APIs

**Sistema A → Integração**
- Endpoint: [URL]
- Método: [HTTP Method]
- Autenticação: [Tipo]
- Payload: [Exemplo]

**Integração → Sistema B**
- Endpoint: [URL]
- Método: [HTTP Method]
- Autenticação: [Tipo]
- Payload: [Exemplo]

### Tratamento de Erros

| Cenário | Response | Retry | DLQ |
|---------|----------|-------|-----|

### Regras de Transformação

- Regra 1: [Descrição]
- Regra 2: [Descrição]

---

## Resiliência e Confiabilidade

### Estratégia de Retry
- Máximo de tentativas: [N]
- Backoff: [Exponencial/Linear]
- Timeout: [Duração]

### Idempotência
- Chave de idempotência: [Campo]
- Detecção de duplicatas: [Método]

### Circuit Breaker
- Limite de falhas: [N]
- Timeout antes de tentar novamente: [Duração]

### Dead Letter Queue (DLQ)
- Necessária: Sim/Não
- Retenção: [Duração]
- Processamento: [Manual/Automatizado]

---

## Observabilidade

### Logging
- Nível de log: [Debug/Info/Warn/Error]
- Correlation ID: [Campo]
- Campos-chave: [Lista]

### Métricas
- Throughput: [msgs/sec]
- Latência: [p50/p95/p99]
- Taxa de erro: [%]
- Taxa de sucesso: [%]

### Tracing
- Tracing distribuído? Sim/Não
- Mapa de serviços: [Sistemas envolvidos]

### Alertas
| Alerta | Condição | Severidade | Runbook |
|-------|-----------|----------|---------|

---

## Segurança e Compliance

### Autenticação
- Método: [OAuth2/JWT/API Key]
- Endpoint de token: [URL]
- Escopo: [Lista]

### Autorização
- Direitos do usuário de integração: [Detalhes]
- Princípio do menor privilégio: [Confirmado]

### Proteção de Dados
- Dados em trânsito: [Tipo de criptografia]
- Dados em repouso: [Tipo de criptografia]
- Tratamento de PII: [Detalhes]
- LGPD: [Compatível/Gaps]

### Auditoria e Compliance
- Logging de auditoria: [Detalhes]
- Retenção: [Duração]
- Compliance: [Padrões]

---

## Modelo Operacional

### Implantação
- Ambiente: [Dev/QA/Prod]
- Frequência: [Contínua/Semanal]
- Estratégia de rollback: [Manual/Automática]

### Monitoramento e Suporte
- Quem suporta: [Time]
- SLA: [Tempo de resposta/resolução]
- Escalação: [Caminho]

### Runbooks
- Falha de integração: [Passos]
- Falha do Sistema A: [Passos]
- Falha do Sistema B: [Passos]

---

## Performance e Escalabilidade

### Volume Esperado
- Atual: [msgs/dia]
- Alvo: [msgs/dia]
- Pico: [msgs/sec]

### Requisitos de Latência
- P50: [ms]
- P95: [ms]
- P99: [ms]

### Planejamento de Capacidade
- Capacidade atual: [Unidades]
- Capacidade alvo: [Unidades]
- Timeline: [Quando]

---

## Riscos e Mitigação

| Risco | Impacto | Mitigação |
|-------|---------|-----------|

---

## Timeline e Marcos

| Marco | Data Alvo | Responsável |
|-----------|-------------|-------|

---

## Dependências

### Dependências de Sistema
- [Lista]

### Dependências de Time
- [Lista]

### Dependências Externas
- [Lista]

---

## Questões Abertas

- [Pergunta 1]?
- [Pergunta 2]?

---

## Aprovação e Assinatura

| Papel | Nome | Data |
|------|------|------|

---

## Referências

- [Documentos relacionados]
- [Especificações de API]
- [Políticas de segurança]
```
