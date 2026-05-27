# Context Resolution Rules

## Objetivo

Definir como os agentes IA devem resolver contexto, prioridade de informação e escopo de análise.

---

# Ordem Obrigatória de Contexto

Os agentes SEMPRE devem utilizar contexto na seguinte ordem:

## 1. Knowledge Base Global (Prioridade Máxima)

Consultar primeiro:

- /knowledge-base
- /context
- /standards
- /memory

Objetivo:
- reutilizar conhecimento corporativo
- seguir padrões oficiais
- evitar inconsistências
- manter governança

Nunca ignorar:
- padrões arquiteturais
- regras LGPD
- padrões de integração
- padrões de observabilidade
- decisões arquiteturais existentes

---

## 2. Contexto Local da Pasta

Após consultar a KB global, utilizar o conteúdo da pasta atual analisada.

Exemplo:

/transcripts/mapeamento-integracoes-roadmap

Todos os arquivos da pasta devem ser considerados parte do mesmo contexto.

Tipos suportados:
- transcripts
- markdown
- pdf
- excel
- csv
- png
- jpg
- mermaid
- swagger/openapi
- json
- xml
- drawio exports

---

# Regras de Contexto

## Todos os arquivos da pasta representam:
- mesma iniciativa
- mesmo domínio
- mesmo projeto
- mesmo discovery
- mesmo roadmap

---

# Correlação de Informação

Os agentes devem:
- correlacionar arquivos
- cruzar informações
- detectar inconsistências
- detectar evolução arquitetural
- detectar mudanças de decisão
- reutilizar contexto previamente descoberto

---

# Regra Obrigatória

Antes de:
- buscar internet
- gerar hipótese
- inferir contexto
- usar conhecimento externo

Os agentes DEVEM:
1. consultar KB global
2. consultar contexto local
3. reutilizar conhecimento existente

---

# Uso de Internet

A internet somente pode ser utilizada quando:
- explicitamente solicitado
- informação não existir na KB
- informação não existir no contexto local
- houver necessidade de validação externa

---

# Persistência de Conhecimento

Sempre que descobrir:
- novos sistemas
- integrações
- padrões
- vendors
- decisões recorrentes

Os agentes devem sugerir atualização da knowledge-base.

---

# Resultado Esperado

Os agentes devem operar como:
- arquitetos enterprise contextualizados
- sistemas de memória corporativa
- motores de discovery inteligente
- plataformas de documentação viva