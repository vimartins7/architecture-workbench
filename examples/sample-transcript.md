# Exemplo: Transcrição de Reunião

**Data**: 2026-05-26  
**Duração**: 1 hora e 30 minutos  
**Participantes**: Arquiteto, Gerente de Produto, Tech Lead  
**Tópico**: Decisão de Arquitetura de Integração

---

## Trecho da Transcrição

**GP**: "Precisamos integrar o Salesforce com nosso sistema SAP. Atualmente, a entrada de dados é manual."

**Arquiteto**: "Qual é o volume de registros?"

**GP**: "Cerca de 500 por dia, pico de 1000. Precisamos sincronizar dados de clientes e pedidos."

**Tech Lead**: "Temos investigado uma abordagem API-first. O Salesforce possui APIs REST."

**Arquiteto**: "Perfeito. Deixa eu perguntar sobre o tempo. Vamos fazer isso de forma síncrona ou assíncrona?"

**GP**: "Idealmente, precisamos de atualizações em até 5 minutos."

**Arquiteto**: "Cinco minutos sugere que deveríamos usar eventos. Poderíamos publicar eventos de pedidos e o Salesforce se inscrever."

**Tech Lead**: "Já usamos Kafka para outras integrações."

**Arquiteto**: "Excelente. Essa vira nossa decisão técnica. Kafka como base para streaming de eventos na integração Salesforce-SAP."

**GP**: "E quanto a falhas? E se o Kafka cair?"

**Arquiteto**: "Implementamos circuit breaker e Dead Letter Queue. Mensagens com falha ficam na fila local e tentam novamente quando o Kafka volta."

**Tech Lead**: "Precisamos de criptografia?"

**Arquiteto**: "Absolutamente. TLS para toda a comunicação, e precisamos ter cuidado com os dados PII de clientes."

**GP**: "LGPD, certo?"

**Arquiteto**: "Exatamente. Deixa eu documentar isso apropriadamente em uma ADR..."

---

## Principais Decisões Extraídas

1. **Padrão**: Orientado a eventos via Kafka (não chamadas de API síncronas)
2. **Volume**: 500-1000 eventos/dia
3. **Latência**: SLA de 5 minutos
4. **Resiliência**: Circuit breaker + DLQ
5. **Segurança**: TLS + cargas criptografadas
6. **Conformidade**: Tratamento de dados conforme LGPD

---

## Utilização

Essa transcrição seria entrada para:
- Fluxo `transcrição-para-adr` → Cria ADR documentando a decisão
- Fluxo `transcrição-para-requisitos` → Extrai requisitos funcionais/não-funcionais
- Fluxo `transcrição-para-hld` → Cria design de arquitetura
- Fluxo `transcrição-para-análise-de-riscos` → Identifica riscos técnicos/operacionais

---

## Documentos Relacionados

Uma vez processados pelos fluxos, gerariam:
- ADR-001-Integração-Salesforce-SAP-Orientada-a-Eventos-com-Kafka
- Documento de requisitos com SLAs
- HLD com arquitetura Kafka
- Avaliação de riscos com considerações LGPD
- Diagramas Mermaid
