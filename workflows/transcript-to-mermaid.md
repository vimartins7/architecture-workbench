# Fluxo de Trabalho: Transcript → Mermaid

## Propósito

Extrai diagramas Mermaid válidos e prontos para documentação a partir de transcripts.

---

## Entrada

- Transcript de reunião
- Contexto de arquitetura
- Paisagem do sistema

---

## Etapas de Execução

### Etapa 1: Sumarizar & Extrair Sistemas
**Agente**: enterprise-architect | **Duração**: 15 min

### Etapa 2: Mapear Fluxos de Dados
**Agente**: enterprise-architect | **Duração**: 20 min

### Etapa 3: Gerar Diagramas
**Agente**: enterprise-architect | **Duração**: 40 min

**Diagramas gerados**:
1. **Diagrama de Arquitetura** (flowchart)
   - Sistemas, componentes, integrações
   
2. **Diagrama de Componentes** (graph)
   - Relacionamentos entre componentes
   
3. **Diagrama de Fluxo de Dados** (graph)
   - Movimento e transformação de dados
   
4. **Fluxo de Integração** (sequence)
   - Fluxos de integração passo a passo
   
5. **Fluxo de Eventos** (sequence)
   - Sequências orientadas a eventos

### Etapa 4: Validar Diagramas
**Agente**: enterprise-architect | **Duração**: 15 min
- Validação de sintaxe
- Verificação de completude
- Revisão de clareza

### Etapa 5: Documentar Diagramas
**Agente**: enterprise-architect | **Duração**: 10 min
- Adicionar legendas
- Adicionar descrições
- Adicionar referências

---

## Saída

**Arquivo**: `/outputs/mermaid/[projeto]-diagrams.md`

**Contém**:
- Diagrama de arquitetura (flowchart/graph)
- Relacionamentos entre componentes
- Fluxos de dados
- Sequências de integração
- Fluxos de eventos
- Topologia de implantação
- Paisagem do sistema

**Formato**: Sintaxe Mermaid válida

---

## Cronograma

**Duração Total**: ~1,5 horas

---

## Padrões de Diagrama

Todos os diagramas seguem:
- Convenções de nomeação corporativa
- Melhores práticas de Mermaid
- Padrões de legibilidade
- Padrões de acessibilidade

---

## Quality Gate

```
Checklist de Diagramas Mermaid
├─ [ ] Sintaxe Mermaid válida
├─ [ ] Todos os sistemas representados
├─ [ ] Integrações claras
├─ [ ] Fluxos de dados visíveis
├─ [ ] Legenda presente
├─ [ ] Layout legível
├─ [ ] Sem elementos sobrepostos
└─ [ ] Pronto para documentação
```
