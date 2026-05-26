# Diretrizes Globais de Português do Brasil (pt-BR)

**Versão**: 1.0.0  
**Data**: 26 de maio de 2026  
**Status**: Em Vigor

---

## 📋 Regra Global

**TODAS AS SAÍDAS DEVEM SER GERADAS EM PORTUGUÊS DO BRASIL (pt-BR), EXCETO QUANDO EXPLICITAMENTE SOLICITADO OUTRO IDIOMA.**

---

## 🎯 Objetivo

Padronizar todo o Workbench de Arquitetura Empresarial para usar Português do Brasil como idioma padrão, mantendo termos técnicos em inglês quando apropriado e adaptando conteúdo corporativo para o contexto brasileiro.

---

## ✅ Aplicação Obrigatória

Estas diretrizes aplicam-se a:

- ✅ **Agentes** - Todos os agentes geram saída em pt-BR
- ✅ **Skills** - Todas as skills processam e geram em pt-BR
- ✅ **Templates** - Todos os templates são em pt-BR
- ✅ **Workflows** - Todos os workflows executam em pt-BR
- ✅ **Prompts** - System e review prompts em pt-BR
- ✅ **Context** - Contexto corporativo em pt-BR
- ✅ **Standards** - Padrões documentados em pt-BR
- ✅ **Exemplos** - Todos os exemplos em pt-BR
- ✅ **Playbooks** - Guias práticos em pt-BR
- ✅ **Outputs** - ADRs, HLDs, requisitos em pt-BR
- ✅ **Documentação** - README, guides em pt-BR

---

## 🔤 Mapeamento de Termos

### Termos Técnicos que Permanecem em Inglês

Estes termos devem ser mantidos em inglês pois são padrões de mercado:

| Termo | Contexto | Exemplo |
|-------|----------|---------|
| API | Interface de programação | "Documentar todas as APIs em OpenAPI" |
| REST | Padrão arquitetural | "Design REST é obrigatório" |
| GraphQL | Linguagem de query | "Use GraphQL para queries complexas" |
| gRPC | Framework RPC | "gRPC para comunicação interna" |
| Middleware | Componente de integração | "Middleware corporativo" |
| Event-Driven | Padrão arquitetural | "Arquitetura Event-Driven é preferida" |
| Async/Await | Padrão de codificação | "Use async/await para operações não-bloqueantes" |
| Retry Pattern | Padrão de resiliência | "Implementar Retry Pattern com exponential backoff" |
| Circuit Breaker | Padrão de resiliência | "Circuit Breaker protege serviços downstream" |
| DLQ (Dead Letter Queue) | Fila de mensagens mortas | "Mensagens com falha vão para DLQ" |
| Correlation ID | ID de rastreamento | "Incluir Correlation ID em todos os logs" |
| OAuth2 | Protocolo de autenticação | "OAuth2 é obrigatório para APIs externas" |
| JWT | Token de autenticação | "JWT para autenticação de APIs" |
| mTLS | Autenticação mútua | "mTLS para service-to-service" |
| Zero Trust | Modelo de segurança | "Implementar Zero Trust em todos os serviços" |
| OpenAPI | Especificação de API | "Especificação OpenAPI 3.0 obrigatória" |
| AsyncAPI | Especificação de eventos | "Usar AsyncAPI para documentar eventos" |
| Kafka | Message broker | "Kafka como broker de eventos padrão" |
| RabbitMQ | Message broker | "RabbitMQ como alternativa a Kafka" |
| Kubernetes | Orquestração de containers | "Deploy em Kubernetes" |
| Docker | Containerização | "Imagens Docker para tudo" |
| Gateway | Componente de API | "API Gateway como entrada única" |
| HLD | High-Level Design | "Criar HLD antes de implementação" |
| ADR | Architecture Decision Record | "Registrar decisões em ADR" |
| RFC | Request for Comments | "Usar RFC para propostas maiores" |
| CI/CD | Continuous Integration/Deployment | "Pipeline CI/CD obrigatório" |
| SLA | Service Level Agreement | "SLA contratual com cliente" |
| SLO | Service Level Objective | "SLO é meta interna" |
| SLI | Service Level Indicator | "SLI é a métrica medida" |
| MTTR | Mean Time to Recovery | "MTTR deve ser < 15 minutos" |
| MTTF | Mean Time to Failure | "MTTF deve ser > 720 horas" |
| JSON | Formato de dados | "Payload em JSON" |
| YAML | Formato de configuração | "Configurações em YAML" |
| LGPD | Lei Geral de Proteção de Dados | "Conformidade com LGPD obrigatória" |
| FAQ | Perguntas Frequentes | "Consulte a FAQ" |
| URL | Localizador de recurso | "URL deve ser clara e descritiva" |
| HTTP | Protocolo de transferência | "HTTP/2 mínimo" |
| TLS | Segurança de transporte | "TLS 1.2+ obrigatório" |

### Termos a Traduzir

Estes termos devem ser traduzidos para pt-BR:

| Inglês | Português | Exemplo |
|--------|-----------|---------|
| Requirements | Requisitos | "Extrair requisitos da reunião" |
| Architecture | Arquitetura | "Design de arquitetura" |
| Design | Design/Design/Desenho | "Solution design document" |
| Framework | Framework/Estrutura | "Usar o framework de governança" |
| Scalability | Escalabilidade | "Requisito de escalabilidade" |
| Performance | Desempenho/Performance | "Requisitos de desempenho" |
| Security | Segurança | "Revisão de segurança" |
| Compliance | Conformidade | "Avaliação de conformidade" |
| Governance | Governança | "Revisão de governança" |
| Risk | Risco | "Análise de riscos" |
| Integration | Integração | "Design de integração" |
| Monitoring | Monitoramento | "Estratégia de monitoramento" |
| Logging | Logging/Registro | "Logging estruturado" |
| Tracing | Rastreamento | "Rastreamento distribuído" |
| Dashboard | Dashboard/Painel | "Painel de controle" |
| Runbook | Runbook/Guia de operação | "Runbook para incidentes" |
| Roadmap | Roadmap/Mapa da estrada | "Roadmap técnico de 12 meses" |
| Workflow | Fluxo de trabalho/Workflow | "Workflow transcript-to-ADR" |
| Deployment | Implantação/Deployment | "Modelo de implantação" |
| Release | Lançamento/Release | "Release notes" |
| Sprint | Sprint | "Sprint de desenvolvimento" |
| Backlog | Backlog | "Product backlog" |
| User Story | História de usuário | "Escrever user stories claras" |

---

## 📐 Regras de Formatação

### Títulos e Seções

Todos os títulos devem ser traduzidos:

```markdown
# Mal ❌
# Requirements Analysis
# API Standards

# Bem ✅
# Análise de Requisitos
# Padrões de API
```

### Listas e Bullets

Traduzir conteúdo, manter estrutura:

```markdown
# Mal ❌
- Define API contracts
- Implement security controls
- Monitor performance

# Bem ✅
- Definir contratos de API
- Implementar controles de segurança
- Monitorar desempenho
```

### Tabelas

Traduzir cabeçalhos, manter dados técnicos:

```markdown
# Mal ❌
| Field | Type | Required |
| name | string | yes |

# Bem ✅
| Campo | Tipo | Obrigatório |
| name | string | sim |
```

### Código e Exemplos

Manter código em inglês, traduzir comentários:

```python
# Mal ❌
# Get user data
user = get_user(id)

# Bem ✅
# Obter dados do usuário
user = get_user(id)
```

---

## 💼 Adaptações Corporativas Brasileiras

### Linguagem Corporativa

Use linguagem apropriada para contexto corporativo brasileiro:

| Contexto | Exemplo |
|----------|---------|
| Executivo | "Solicitamos aprovação da Diretoria" (não "We request") |
| Técnico | "O componente implementa Circuit Breaker" (não "The component") |
| Formal | "Considerando as restrições operacionais" (não "Given the constraints") |
| Hierárquico | "Escalação ao CTO quando necessário" (não "Escalate to CTO") |

### Moeda e Valores

Sempre use Real Brasileiro (R$) e formato local:

```markdown
# Mal ❌
- Cost: $50,000

# Bem ✅
- Custo: R$ 250.000,00
```

### Datas

Use formato brasileiro padrão:

```markdown
# Mal ❌
2026-05-26 | May 26, 2026

# Bem ✅
26 de maio de 2026 | 26/05/2026
```

### Unidades

Use sistema métrico:

```markdown
# Mal ❌
- 100 MB of storage
- 2,000 requests/sec

# Bem ✅
- 100 MB de armazenamento
- 2.000 requisições/segundo
```

---

## 📋 Checklist de Conformidade pt-BR

Toda documentação deve passar por este checklist:

- ✅ Conteúdo primário em pt-BR
- ✅ Termos técnicos em inglês quando apropriado
- ✅ Títulos e seções traduzidos
- ✅ Nenhuma mistura de idiomas em parágrafos
- ✅ Linguagem corporativa brasileira
- ✅ Formato local (datas, moeda, unidades)
- ✅ Consistência terminológica

---

## 🚫 O Que Evitar

| Padrão | Exemplo Ruim | Exemplo Bom |
|--------|--------------|-------------|
| Code-switching | "O API gateway processa requests" | "O API Gateway processa requisições" |
| Tradução literal | "Eu gosto de fazer" | "É preferível" |
| Diminutivos excessivos | "O servicinho faz uns processamentos" | "O serviço processa dados" |
| Informalidade | "Tá bom, vamo lá" | "Está bem, vamos prosseguir" |
| Siglas não explicadas | "O SDLC é importante" | "O ciclo de vida de desenvolvimento é importante" |

---

## 📝 Exemplos de Conformidade

### ADR em pt-BR

```markdown
# ADR-001: Migração para Event-Driven Architecture

## Status
Aceita

## Contexto
Sistema atual usa integração síncrona, causando acoplamento forte entre serviços.

## Decisão
Implementar arquitetura orientada a eventos usando Apache Kafka como broker.

## Consequências
Positivas:
- Acoplamento mais frouxo
- Melhor escalabilidade
- Trilha de auditoria clara

Negativas:
- Consistência eventual
- Infraestrutura adicional (Kafka)
```

### HLD em pt-BR

```markdown
# HLD: Sistema de Integração Salesforce-SAP

## Visão Geral
Integração assíncrona baseada em eventos entre Salesforce (CRM) e SAP (ERP).

## Componentes
- **Publisher SAP**: Publica eventos de domínio
- **Kafka**: Message broker central
- **Integrador Salesforce**: Consome eventos e sincroniza dados
- **DLQ**: Fila para mensagens com falha
```

### Requisitos em pt-BR

```markdown
# Requisitos: Sistema de Integração

## Requisitos Funcionais

### RF-001: Sincronizar Clientes
**Descrição**: Sincronizar dados de clientes entre SAP e Salesforce

**Critérios de Aceitação**:
- Dado um cliente criado no SAP
- Quando um evento CriadoCliente é publicado
- Então o cliente deve aparecer no Salesforce dentro de 5 minutos

## Requisitos Não-Funcionais

### RNF-001: Latência
- Latência máxima de sincronização: 5 minutos
- P99 de latência de API: 200ms

### RNF-002: Disponibilidade
- Disponibilidade mínima: 99,9%
```

---

## 🔄 Processo de Aprovação

Toda documentação traduzida deve passar por:

1. **Tradução Inicial**: Agente ou skill traduz para pt-BR
2. **Revisão Técnica**: Valida termos técnicos e estrutura
3. **Revisão Corporativa**: Valida linguagem e contexto brasileiro
4. **Revisão de Qualidade**: Checklist de conformidade
5. **Aprovação**: Governança revisa e aprova

---

## 📚 Referências Corporativas

Para linguagem corporativa brasileira, consulte:

- **LGPD**: Lei Geral de Proteção de Dados (oficial)
- **Banco Central**: Padrões de comunicação corporativa
- **ABNT**: Normas técnicas brasileiras
- **Cultura corporativa**: Documentos internos da organização

---

## 🤝 Governança

Estas diretrizes são governadas por:

- **Proprietário**: Agente de Governança
- **Revisão**: Trimestral
- **Atualizações**: Via processo RFC
- **Conformidade**: Verificada em governance reviews

---

## 📞 Dúvidas?

Para dúvidas sobre aplicação destas diretrizes:

1. Consulte este documento
2. Verifique exemplos em `/examples/`
3. Revise templates correspondentes
4. Escalpe para Agente de Governança

---

**Última atualização**: 26 de maio de 2026  
**Versão**: 1.0.0 - Em Vigor  
**Aplicação**: Obrigatória para todos os agentes, skills e documentação
