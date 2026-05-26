# Padrões de Segurança

Requisitos obrigatórios de segurança para todos os sistemas.

---

## Autenticação

### Método Primário: OAuth2 + OpenID Connect
- Para integrações externas
- Segurança de endpoint de token
- Rotação de refresh token

### mTLS para Serviço a Serviço
- Gerenciamento de certificados via PKI corporativo
- Rotação de certificados a cada 90 dias
- TLS 1.2 mínimo

### Chaves de API (Legado, Não Recomendado)
- Apenas para compatibilidade retroativa
- Rotação a cada 90 dias
- Rate limiting por chave

---

## Autorização

### Controle de Acesso Baseado em Função (RBAC)
- Princípio do menor privilégio
- Definições de função claras
- Logging de auditoria de mudanças

### Controle de Acesso Baseado em Atributo (ABAC)
- Para cenários complexos
- Engine de política centralizado

---

## Proteção de Dados

### Criptografia em Trânsito
- TLS 1.2+ para toda comunicação externa
- TLS 1.2+ para toda comunicação interna sobre redes

### Criptografia em Repouso
- AES-256 para dados sensíveis
- Rotação de chave anualmente
- Gerenciamento de chaves via KMS corporativo

### Classificação de Dados Sensíveis
- Público
- Interno
- Confidencial
- Restrito (PII)

---

## Gerenciamento de Segredos

### Requisitos
- Sem segredos hardcoded
- Segredos em gerenciador de segredos corporativo
- Rotação: A cada 90 dias
- Logging de acesso: Todos os acessos de segredos registrados

### Tipos de Segredo
- Credenciais de banco de dados
- Chaves de API
- Chaves privadas
- Certificados

---

## Mitigação de OWASP Top 10

Todos os sistemas devem:
- [ ] Validar todas as entradas
- [ ] Codificar todas as saídas
- [ ] Sem vulnerabilidades de SQL injection
- [ ] Autenticação segura
- [ ] Criptografar dados sensíveis
- [ ] Registrar eventos de segurança
- [ ] Sem vulnerabilidades de XXE
- [ ] Desserialização segura
- [ ] Sem vulnerabilidades de componentes conhecidos
- [ ] Sem segredos hardcoded

---

## Modelo Zero Trust

### Princípios
- Verificar cada solicitação de acesso
- Assumir cenário de violação
- Minimizar raio de explosão
- Criptografar tudo
- Monitorar tudo

### Implementação
- Service mesh para verificação de identidade
- mTLS em todo lugar
- Rastreamento distribuído para detecção de anomalias
- Aplicação de política centralizada

---

## Auditoria e Conformidade

### Requisitos de Logging de Auditoria
- Todos os eventos relevantes de segurança registrados
- Log de auditoria imutável
- Detecção de violação
- Retenção: Mínimo 1 ano

### Eventos para Registrar
- Tentativas de autenticação (sucesso e falha)
- Decisões de autorização
- Acesso a dados (PII)
- Mudanças de configuração
- Ações administrativas

---

## Resposta a Incidentes

### Plano de Resposta a Incidentes de Segurança Obrigatório
- Mecanismos de detecção
- Caminho de escalação
- Protocolo de comunicação
- Procedimentos de recuperação
- Revisão pós-incidente

---

## Risco de Terceiros

Todas as integrações de terceiros devem:
- [ ] Avaliação de segurança concluída
- [ ] Proteção de dados verificada
- [ ] Conformidade confirmada
- [ ] Contrato revisado por departamento jurídico
- [ ] Plano de resposta a incidentes estabelecido
