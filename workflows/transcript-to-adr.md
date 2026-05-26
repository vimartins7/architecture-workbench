# Fluxo de Trabalho: Transcript → ADR

## Propósito

Transforma um transcript de reunião técnica em um ADR (Registro de Decisão de Arquitetura) estruturado e pronto para governance.

---

## Entrada

- Transcript de reunião (texto, vídeo ou anotações)
- Contexto do projeto
- Princípios de arquitetura

---

## Etapas de Execução

### Etapa 1: Sumarizar Reunião (Skill: summarize-meeting)

**Agente**: requirements-engineer

**Ação**:
1. Ler transcript completo
2. Identificar participantes e contexto
3. Extrair decisões explícitas
4. Extrair contexto de negócio
5. Listar itens de ação

**Saída**: Resumo de Reunião

---

### Etapa 2: Extrair Decisões (Skill: extract-requirements)

**Agente**: solution-architect

**Ação**:
1. Analisar resumo de reunião
2. Identificar decisões técnicas
3. Classificar por tipo (arquitetura, tecnologia, padrão)
4. Extrair justificativas
5. Documentar alternativas mencionadas

**Saída**: Lista de Decisões

---

### Etapa 3: Detectar Riscos (Skill: detect-risks)

**Agente**: enterprise-architect

**Ação**:
1. Analisar cada decisão
2. Identificar riscos técnicos
3. Identificar riscos operacionais
4. Identificar riscos financeiros
5. Propor mitigações

**Saída**: Avaliação de Riscos

---

### Etapa 4: Validar Contra Standards (Governance)

**Agente**: governance-agent

**Ação**:
1. Carregar standards corporativos
2. Validar decisões contra standards
3. Avaliar conformidade
4. Identificar gaps
5. Sinalizar escalações

**Saída**: Revisão de Governance

---

### Etapa 5: Revisão de Segurança & Compliance (Security)

**Agente**: security-architect

**Ação**:
1. Avaliar implicações de segurança
2. Avaliar LGPD
3. Avaliar proteção de dados
4. Identificar gaps de compliance
5. Propor controles

**Saída**: Avaliação de Segurança

---

### Etapa 6: Gerar ADR (Skill: create-adr)

**Agente**: enterprise-architect

**Ação**:
1. Consolidar todas as análises
2. Preencher template de ADR
3. Documentar contexto
4. Documentar problema
5. Documentar decisão
6. Documentar alternativas
7. Documentar riscos
8. Documentar impactos
9. Documentar dependências

**Saída**: Rascunho de ADR

---

### Etapa 7: Revisão de Qualidade

**Agente**: enterprise-architect

**Ação**:
1. Revisar completude
2. Revisar consistência
3. Revisar clareza
4. Revisar rastreabilidade
5. Validar referências

**Saída**: ADR Pronto para Aprovação

---

## Saída

**Arquivo**: `/outputs/adr/ADR-XXX-[nome].md`

**Formato**: Markdown estruturado

**Contém**:
- Contexto completo
- Problema bem definido
- Decisão tomada
- Alternativas avaliadas
- Trade-offs documentados
- Riscos identificados
- Impactos listados
- Segurança/compliance validada
- Pronto para assinatura

---

## Cronograma

| Etapa | Duração | Agente |
|-------|---------|--------|
| 1. Sumarizar | 10 min | requirements-engineer |
| 2. Extrair Decisões | 15 min | solution-architect |
| 3. Detectar Riscos | 20 min | enterprise-architect |
| 4. Revisão de Governance | 10 min | governance-agent |
| 5. Revisão de Segurança | 10 min | security-architect |
| 6. Gerar ADR | 20 min | enterprise-architect |
| 7. Revisão de Qualidade | 10 min | enterprise-architect |
| **Total** | **~95 min** | |

---

## Quality Gate

```
Checklist de Qualidade do ADR
├─ [ ] Contexto claro
├─ [ ] Problema bem definido
├─ [ ] Decisão documentada
├─ [ ] Alternativas avaliadas
├─ [ ] Trade-offs explicados
├─ [ ] Riscos identificados & mitigados
├─ [ ] Segurança/LGPD validada
├─ [ ] Dependências listadas
├─ [ ] Pronto para aprovação
└─ [ ] Sem problemas bloqueadores
```

---

## Variações

### Variação 1: ADR Rápido (30 min)
- Pular revisão detalhada de risco/segurança
- Para decisões não críticas
- Revisão de agente único

### Variação 2: ADR Aprofundado (3-4 horas)
- Múltiplas rodadas de revisão
- Revisão legal se necessário
- Documentação no nível de conselho
- Para decisões estratégicas

---

## Fluxos de Trabalho Relacionados

- transcript-to-hld
- transcript-to-requirements
- transcript-to-risk-analysis

---

## Solução de Problemas

**Problema**: Transcript carece de detalhe suficiente
- **Solução**: Solicitar esclarecimento de reunião ou documentação adicional

**Problema**: Decisões conflitantes identificadas
- **Solução**: Sinalizar para reunião de resolução

**Problema**: Gaps de segurança encontrados
- **Solução**: Escalar para security-architect para avaliação detalhada
