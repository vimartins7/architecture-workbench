# Padrões de API

Padrões técnicos obrigatórios para todas as APIs.

---

## Design de API REST

### Convenções de Nomenclatura

**Recursos** (plural, minúsculo):
- `/api/v1/users`
- `/api/v1/orders`
- `/api/v1/products`

**Sub-recursos**:
- `/api/v1/users/{userId}/orders`
- `/api/v1/orders/{orderId}/items`

**Ações** (use POST com noun de ação apenas se necessário):
- `POST /api/v1/users/{userId}/send-email`
- `POST /api/v1/orders/{orderId}/cancel`

---

## Métodos HTTP

| Método | Finalidade | Idempotente |
|--------|-----------|-------------|
| GET | Recuperar | Sim |
| POST | Criar | Não |
| PUT | Substituir | Sim |
| PATCH | Atualização parcial | Não |
| DELETE | Deletar | Sim |

---

## Códigos de Status

| Código | Significado | Uso |
|--------|------------|-----|
| 200 | OK | Sucesso GET |
| 201 | Criado | Sucesso POST |
| 204 | Sem Conteúdo | Sucesso DELETE |
| 400 | Requisição Inválida | Entrada inválida |
| 401 | Não Autorizado | Autenticação necessária |
| 403 | Proibido | Autenticação OK, não permitido |
| 404 | Não Encontrado | Recurso ausente |
| 409 | Conflito | Violação de regra de negócio |
| 429 | Muitas Requisições | Rate limit |
| 500 | Erro de Servidor | Erro não tratado |

---

## Formato de Requisição/Resposta

### Resposta Padrão
```json
{
  "success": true,
  "data": { ... },
  "meta": {
    "timestamp": "2026-05-26T14:30:00Z",
    "request_id": "uuid-v4"
  }
}
```

### Resposta de Erro
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Um ou mais erros de validação ocorreram",
    "details": [
      {
        "field": "email",
        "message": "Formato de email inválido"
      }
    ]
  },
  "meta": {
    "request_id": "uuid-v4"
  }
}
```

---

## Paginação

### Requisição
```
GET /api/v1/users?limit=20&offset=0&sort=created_at:desc
```

### Resposta
```json
{
  "data": [ ... ],
  "pagination": {
    "limit": 20,
    "offset": 0,
    "total": 1000,
    "pages": 50
  }
}
```

---

## Filtragem

### Parâmetros de Query
- `?status=active`
- `?created_after=2026-01-01T00:00:00Z`
- `?created_before=2026-12-31T23:59:59Z`
- `?search=keyword`

### Operadores
- `?age[gte]=18` - Maior que ou igual
- `?age[lte]=65` - Menor que ou igual
- `?name[in]=John,Jane` - Na lista

---

## Versionamento de API

### Caminho de URL (Recomendado)
- `/api/v1/users`
- `/api/v2/users` (mudanças que quebram compatibilidade)

### Versão em Header
- `Accept: application/vnd.mycompany.v1+json`

### Deprecação
- Marcar endpoints deprecados com 12 meses de antecedência
- Fornecer caminho de migração
- Registrar aviso de deprecação

---

## Autenticação e Autorização

### Bearer Token
```
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

### Acesso Baseado em Escopo
```
scope: read:users write:users delete:users
```

---

## Documentação

Toda API deve ter:
- Especificação OpenAPI 3.0+
- Exemplos de requisições e respostas
- Cenários de erro documentados
- Rate limiting documentado
- Requisitos de autenticação claros
- Timeline de deprecação

---

## Conformidade

Todas as APIs devem:
- [ ] Usar HTTPS apenas
- [ ] Validar entradas
- [ ] Retornar códigos de status apropriados
- [ ] Tratar erros corretamente
- [ ] Ter Correlation IDs
- [ ] Ter rate limiting
- [ ] Ter monitoramento
- [ ] Estar documentadas
