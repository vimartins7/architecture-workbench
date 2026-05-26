mermaid
sequenceDiagram
    participant Cliente
    participant API
    participant Kafka

    Cliente->>API: Criar pedido
    API->>Kafka: Publicar evento