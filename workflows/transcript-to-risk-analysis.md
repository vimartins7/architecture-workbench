# Fluxo de Trabalho: Transcript → Análise de Riscos

## Propósito

Analisa riscos técnicos, operacionais, financeiros e de negócio a partir de um transcript.

---

## Entrada

- Transcript de reunião
- Solução/arquitetura proposta
- Contexto de negócio
- Restrições operacionais

---

## Etapas de Execução

### Etapa 1: Sumarizar Reunião
**Agente**: enterprise-architect | **Duração**: 10 min

### Etapa 2: Identificar Cenários
**Agente**: enterprise-architect | **Duração**: 20 min
- O que pode dar errado?
- Cenários de falha
- Falhas em cascata

### Etapa 3: Avaliar Riscos Técnicos
**Agente**: enterprise-architect | **Duração**: 25 min
- Riscos de escalabilidade
- Riscos de desempenho
- Riscos de integração
- Riscos de tecnologia

### Etapa 4: Avaliar Riscos Operacionais
**Agente**: observability-engineer | **Duração**: 20 min
- Complexidade de suporte
- Desafios de monitoramento
- Recuperação de falhas
- Habilidades operacionais

### Etapa 5: Avaliar Riscos Financeiros
**Agente**: solution-architect | **Duração**: 15 min
- Estouros de orçamento
- Vendor lock-in
- Riscos de licença
- Riscos de TCO

### Etapa 6: Avaliar Riscos de Segurança/Compliance
**Agente**: security-architect | **Duração**: 20 min
- Riscos de proteção de dados
- Gaps de compliance
- Violações de LGPD
- Controles de segurança

### Etapa 7: Criar Matriz de Riscos
**Agente**: enterprise-architect | **Duração**: 15 min
- Avaliação de probabilidade
- Avaliação de impacto
- Priorização

### Etapa 8: Propor Mitigações
**Agente**: enterprise-architect | **Duração**: 20 min
- Para cada risco
- Estratégia de mitigação
- Timeline
- Proprietário

### Etapa 9: Revisão de Risco
**Agente**: governance-agent | **Duração**: 10 min

---

## Saída

**Arquivo**: `/outputs/risk-analysis/[projeto]-risk-analysis.md`

**Contém**:
- Resumo executivo
- Categorias de risco (Técnico, Operacional, Financeiro, Negócio, Segurança)
- Matriz de riscos
- Análise detalhada de risco por risco
- Plano de mitigação
- Estratégia de monitoramento
- Caminho de escalação

---

## Cronograma

**Duração Total**: ~2 horas

---

## Quality Gate

```
Checklist de Análise de Riscos
├─ [ ] Todas as categorias de risco cobertas
├─ [ ] Riscos quantificados
├─ [ ] Mitigações específicas
├─ [ ] Proprietários atribuídos
├─ [ ] Timeline realista
├─ [ ] Monitoramento definido
├─ [ ] Escalação clara
└─ [ ] Pronto para governance
```
