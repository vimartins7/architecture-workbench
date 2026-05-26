# Exemplo ADR: Integração Salesforce-SAP Orientada a Eventos

## Status
Aceita

## Contexto

Salesforce e SAP são sistemas críticos para operações de negócio. Atualmente, os dados de clientes e pedidos são sincronizados manualmente, causando:
- Inconsistências de dados
- Sobrecarga operacional
- Processos de negócio lentos
- Risco de erros

Volume: 500-1000 registros diários
Requisito de latência: máximo 5 minutos

## Problema

Sincronização manual de dados não é escalável e propensa a erros. Precisamos de integração automatizada e confiável que mantenha a consistência de dados.

## Decisão

Implementar integração orientada a eventos usando Kafka como message broker:
1. SAP publica eventos de domínio (PedidoCriado, ClienteAtualizado)
2. Eventos consumidos pelo integrador do Salesforce
3. Dados sincronizados ao Salesforce via APIs REST
4. Event sourcing para trilha de auditoria

## Alternativas Avaliadas

### Alternativa 1: APIs de Sincronização em Tempo Real
**Rejeitada porque**:
- Acoplamento forte
- Latência maior (overhead de rede)
- Sem trilha de auditoria
- Mais difícil de lidar com falhas

### Alternativa 2: Processamento em Lote Agendado
**Rejeitada porque**:
- Latência muito alta (requisito >5 min)
- Não é tempo real
- Consome muitos recursos

## Compensações

**Ganhos**:
- Acoplamento fraco
- Trilha de auditoria de eventos
- Escalabilidade
- Semântica clara

**Perdidos**:
- Consistência imediata (consistência eventual)
- Infraestrutura adicional (Kafka)

## Riscos

| Risco | Impacto | Mitigação |
|------|---------|-----------|
| Tempo de inatividade do Kafka | Interrupção de processo de negócio | Circuit breaker + fila local |
| Perda de dados | Inconsistência | DLQ persistente + capacidade de replay |
| Violação de LGPD | Penalidade regulatória | Criptografia + controles de acesso |

## Consequências

**Positivas**:
- Escalável para 10K+ eventos/dia
- Trilha de auditoria clara
- Independência de equipes
- Resiliência a falhas

**Negativas**:
- Complexidade operacional aumenta
- Requer monitoramento/alertas
- Treinamento de equipe necessário
- Custo inicial de infraestrutura

## Dependências

- Setup do cluster Kafka
- Registro de schema de eventos
- Chaves/credenciais de API do Salesforce
- Certificados TLS
- Acesso de DBA ao SAP

## Perguntas em Aberto

- Localização do cluster Kafka (on-prem vs nuvem)?
- Tecnologia de registro de schema (Confluent vs open source)?
- Qual equipe é responsável pelas operações?

## Próximos Passos

1. POC do Kafka (1 semana)
2. Workshop de design de schema (1 semana)
3. Revisão de segurança (1 semana)
4. Implementação (4 semanas)
5. Deploy em produção (2 semanas)

## Aprovação

- Arquitetura: ✅ Aprovada
- Segurança: ✅ Aprovada
- Operações: ⏳ Pendente
