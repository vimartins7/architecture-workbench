# Fluxo de Trabalho: Transcript → Requisitos

## Propósito

Extrai e estrutura requisitos funcionais e não-funcionais de um transcript.

---

## Entrada

- Transcript de reunião
- Contexto de stakeholder
- Objetivos de negócio

---

## Etapas de Execução

### Etapa 1: Sumarizar Reunião
**Agente**: requirements-engineer | **Duração**: 10 min

### Etapa 2: Extrair Requisitos Funcionais
**Agente**: requirements-engineer | **Duração**: 25 min
- Histórias de usuário
- Features
- Critérios de aceitação

### Etapa 3: Extrair Requisitos Não-Funcionais
**Agente**: requirements-engineer | **Duração**: 20 min
- Requisitos de desempenho
- Necessidades de escalabilidade
- Metas de confiabilidade
- Requisitos de segurança
- Necessidades de compliance

### Etapa 4: Identificar Restrições
**Agente**: requirements-engineer | **Duração**: 15 min
- Restrições técnicas
- Restrições operacionais
- Restrições de orçamento
- Restrições de timeline

### Etapa 5: Detectar Conflitos
**Agente**: requirements-engineer | **Duração**: 15 min

### Etapa 6: Criar Matriz de Rastreabilidade
**Agente**: solution-architect | **Duração**: 15 min
- Requisito ↔ Stakeholder
- Requisito ↔ Caso de Uso
- Requisito ↔ Caso de Teste

### Etapa 7: Validar Completude
**Agente**: requirements-engineer | **Duração**: 10 min

---

## Saída

**Arquivo**: `/outputs/requirements/[projeto]-requirements.md`

**Contém**:
- Resumo executivo
- Análise de stakeholders
- Requisitos funcionais (numerados, com critérios de aceitação)
- Requisitos não-funcionais
- Restrições
- Matriz de rastreabilidade
- Pressupostos
- Questões abertas

---

## Cronograma

**Duração Total**: ~1,5-2 horas

---

## Quality Gate

```
Checklist de Requisitos
├─ [ ] Todos os FR identificados
├─ [ ] Todos os NFR identificados
├─ [ ] Critérios de aceitação definidos
├─ [ ] Conflitos resolvidos
├─ [ ] Rastreabilidade mapeada
├─ [ ] Pressupostos documentados
├─ [ ] Restrições claras
└─ [ ] Pronto para design
```
