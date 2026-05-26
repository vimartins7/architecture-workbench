# Exemplo: Diagramas Mermaid para Integração Salesforce-SAP

## 1. Arquitetura do Sistema

```mermaid
flowchart LR
    SAP["Sistema SAP ERP"]
    Pub["Publicador de Eventos"]
    Kafka["Broker Kafka"]
    Integrator["Integrador Salesforce"]
    SalesforceAPI["API REST Salesforce"]
    DLQ["Dead Letter Queue"]
    
    SAP -->|Eventos| Pub
    Pub -->|Publicar| Kafka
    Kafka -->|Consumir| Integrator
    Integrator -->|Sucesso| SalesforceAPI
    Integrator -->|Falha| DLQ
    DLQ -->|Retry| Integrator
```

## 2. Sequência de Fluxo de Dados

```mermaid
sequenceDiagram
    participant SAP
    participant Publisher as Publicador
    participant Kafka
    participant Integrator as Integrador
    participant Salesforce
    
    SAP->>Publisher: Evento PedidoCriado
    Publisher->>Kafka: Publicar evento
    Kafka->>Integrator: Entregar evento
    Integrator->>Integrator: Transformar dados
    Integrator->>Salesforce: Criar/Atualizar via API
    Salesforce-->>Integrator: Sucesso (200 OK)
    Integrator-->>Kafka: Evento de sucesso
```

## 3. Fluxo de Tratamento de Erros

```mermaid
sequenceDiagram
    participant Kafka
    participant Integrator as Integrador
    participant Salesforce
    participant DLQ
    
    Kafka->>Integrator: Entregar evento
    Integrator->>Salesforce: Chamada API (tentativa 1)
    Salesforce-->>Integrator: Erro (429 Muitas Requisições)
    Integrator->>Integrator: Aguardar 5 segundos
    Integrator->>Salesforce: Chamada API (tentativa 2)
    Salesforce-->>Integrator: Erro (429)
    Integrator->>Integrator: Aguardar 10 segundos
    Integrator->>Salesforce: Chamada API (tentativa 3)
    Salesforce-->>Integrator: Erro (429)
    Integrator->>DLQ: Enviar para Dead Letter Queue
    DLQ-->>Integrator: Revisão manual necessária
```

## 4. Topologia de Tópico Kafka

```mermaid
graph LR
    Input["salesforce-sync-events<br/>3 partições, retenção 7 dias"]
    
    Group1["Grupo de Consumidor: integrator<br/>3 consumidores"]
    
    DLQTopic["__dlq-salesforce-sync<br/>retenção 30 dias"]
    
    Input -->|Partições| Group1
    Input -->|Falhas| DLQTopic
```

## 5. Arquitetura de Deployment

```mermaid
graph TB
    K8S["Cluster Kubernetes"]
    
    K8S -->|Pod 1| Int1["Integrador<br/>Réplica 1"]
    K8S -->|Pod 2| Int2["Integrador<br/>Réplica 2"]
    K8S -->|Pod 3| Int3["Integrador<br/>Réplica 3"]
    K8S -->|Job| DLQProcessor["Processador DLQ<br/>Horário"]
    
    Int1 --> LB["Load Balancer"]
    Int2 --> LB
    Int3 --> LB
    
    LB --> Kafka["Cluster Kafka<br/>3 Brokers"]
    DLQProcessor --> Kafka
```

## Legenda

- **Caixas azuis** = Serviços internos
- **Caixas verdes** = Infraestrutura de mensagens
- **Caixas vermelhas** = Sistemas externos
- **Linhas sólidas** = Chamadas síncronas
- **Linhas tracejadas** = Eventos/Assíncronos
- **Números** = Ordem de sequência

---

## Usando Esses Diagramas

Esses diagramas podem ser:
1. Incluídos na documentação HLD
2. Apresentados a stakeholders
3. Usados em revisões de arquitetura
4. Referenciados em guias de implementação
5. Atualizados conforme a arquitetura evolui

## Atualizando Diagramas

Quando a arquitetura muda:
1. Atualizar o código Mermaid
2. Fazer commit no controle de versão
3. Atualizar referências cruzadas na documentação
4. Notificar equipes relevantes
