# Convenções de Nomenclatura

Convenções obrigatórias para nomes em toda a arquitetura.

---

## Serviços

**Formato**: `{team}-{domain}-{capability}`

**Exemplos**:
- `billing-payment-processor`
- `sales-order-service`
- `notification-email-sender`
- `analytics-event-aggregator`

---

## APIs

**Formato**: `/api/{version}/{resource}`

**Exemplos**:
- `/api/v1/users`
- `/api/v2/orders`
- `/api/v1/products/{id}`

---

## Eventos

**Formato**: `{domain}.{entity}.{action}`

**Exemplos**:
- `order.created`
- `user.registered`
- `payment.processed`

---

## Bancos de Dados

**Formato**: `{environment}_{service}_{db_type}`

**Exemplos**:
- `prod_order_mysql`
- `dev_user_postgres`
- `staging_payment_mongo`

---

## Tabelas/Coleções

**Formato**: `{entity_plural_lowercase}`

**Exemplos**:
- `users`
- `orders`
- `order_items`
- `payments`

---

## Colunas/Campos

**Formato**: `snake_case`

**Exemplos**:
- `user_id`
- `created_at`
- `updated_at`
- `email_address`

---

## Variáveis de Ambiente

**Formato**: `UPPERCASE_WITH_UNDERSCORES`

**Exemplos**:
- `DATABASE_URL`
- `API_KEY`
- `LOG_LEVEL`
- `ENV_NAME`

---

## Arquivos e Pastas

**Formato**: `kebab-case`

**Exemplos**:
- `user-service.md`
- `api-standards.md`
- `order-processing/`
- `payment-gateway/`

---

## Branches Git

**Formato**: `{type}/{feature-name}`

**Tipos**:
- `feature/` - Nova funcionalidade
- `bugfix/` - Correção de bug
- `hotfix/` - Correção urgente em produção
- `refactor/` - Refatoração de código
- `docs/` - Documentação

**Exemplos**:
- `feature/user-authentication`
- `bugfix/payment-retry-logic`
- `hotfix/critical-security-issue`

---

## Identificadores de Código

**Classes**: `PascalCase`
- `UserService`
- `OrderProcessor`

**Funções/Métodos**: `camelCase`
- `getUserById()`
- `processOrder()`

**Constantes**: `UPPER_SNAKE_CASE`
- `MAX_RETRY_COUNT`
- `DEFAULT_TIMEOUT`

---

## Conformidade

Revisões de código verificam convenções de nomenclatura:
- [ ] Serviços seguem padrão de nomenclatura
- [ ] APIs seguem padrão de nomenclatura
- [ ] Bancos de dados seguem padrão de nomenclatura
- [ ] Identificadores de código seguem convenções da linguagem
- [ ] Variáveis de ambiente são claras
