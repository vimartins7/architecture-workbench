# Fluxo de Trabalho: Transcript → HLD

## Propósito

Transforma um transcript em um HLD (Design de Alto Nível) completo e pronto para apresentação.

---

## Entrada

- Transcript de reunião
- Contexto do projeto
- Requisitos de negócio
- Arquitetura existente (se houver)

---

## Etapas de Execução

### Etapa 1: Sumarizar Reunião
**Agente**: requirements-engineer | **Duração**: 10 min

### Etapa 2: Extrair Requisitos
**Agente**: requirements-engineer | **Duração**: 15 min
- Requisitos funcionais
- Requisitos não-funcionais
- Restrições

### Etapa 3: Identificar Integrações
**Agente**: enterprise-architect | **Duração**: 20 min
- Sistemas envolvidos
- Padrões de integração
- Fluxos de dados

### Etapa 4: Identificar Eventos
**Agente**: enterprise-architect | **Duração**: 15 min
- Eventos de domínio
- Oportunidades orientadas a eventos
- Necessidades de event sourcing

### Etapa 5: Gerar Diagramas Mermaid
**Agente**: enterprise-architect | **Duração**: 20 min
- Diagrama de arquitetura
- Diagrama de componentes
- Diagrama de integração
- Diagrama de fluxo de dados

### Etapa 6: Gerar HLD
**Agente**: enterprise-architect | **Duração**: 30 min
- Resumo executivo
- Visão geral da arquitetura
- Componentes & responsabilidades
- Integrações
- Modelo de dados
- Modelo de implantação

### Etapa 7: Detectar Riscos
**Agente**: enterprise-architect | **Duração**: 20 min

### Etapa 8: Segurança & Compliance
**Agente**: security-architect | **Duração**: 15 min

### Etapa 9: Design de Observabilidade
**Agente**: observability-engineer | **Duração**: 15 min
- Estratégia de logging
- Coleta de métricas
- Abordagem de tracing
- Regras de alertas

### Etapa 10: Revisão de Governance
**Agente**: governance-agent | **Duração**: 10 min

### Etapa 11: Revisão de Qualidade
**Agente**: enterprise-architect | **Duração**: 15 min

---

## Saída

**Arquivo**: `/outputs/hld/HLD-[projeto]-[versão].md`

**Contém**:
- Resumo executivo
- Contexto de negócio
- Visão geral da solução
- Componentes & arquitetura
- Integrações & fluxos de dados
- Diagramas Mermaid
- Modelo de segurança
- Estratégia de observabilidade
- Modelo de implantação
- Riscos & mitigação
- Questões abertas

---

## Cronograma

**Duração Total**: ~2,5-3 horas

---

## Quality Gate

```
Checklist de Qualidade do HLD
├─ [ ] Todos os requisitos abordados
├─ [ ] Todos os sistemas identificados
├─ [ ] Todas as integrações mapeadas
├─ [ ] Diagramas válidos & completos
├─ [ ] Modelo de implantação claro
├─ [ ] Segurança/LGPD validada
├─ [ ] Observabilidade projetada
├─ [ ] Riscos identificados
├─ [ ] Pronto para engineering
└─ [ ] Pronto para stakeholders
```
