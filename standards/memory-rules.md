# Memory Rules (Regras de Memória)

## Objetivo

Guiar como agentes persistem e reutilizam conhecimento.

---

## Obrigações dos Agentes

1. **Consultar memória existente** antes de inferir contexto
2. **Reutilizar conhecimento** (global → initiative → domain)
3. **Persistir apenas conhecimento relevante** (não salvar tudo)
4. **Evitar duplicidade** (deduplicate com memória existente)
5. **Separar memória global de iniciativa** (contextos não se misturam)
6. **Resumir antes de salvar** (synopsis, não transcrição)
7. **Referenciar decisões** (ADRs, RFCs, decisões aprovadas)

---

## O Que Salvar

✅ Decisões arquiteturais (com justificativa)
✅ Riscos identificados (com mitigação)
✅ Integrações mapeadas (sistemas, padrões, APIs)
✅ Padrões descobertos (não convenções, mas patterns novos)
✅ Stakeholders e responsabilidades
✅ Constraints técnicos ou de negócio
✅ Histórico de evolução arquitetural

---

## O Que NÃO Salvar

❌ Conteúdo bruto desnecessário
❌ Arquivos temporários
❌ Conversas completas sem síntese
❌ Dados sensíveis (passwords, tokens, PII)
❌ Conhecimento que já existe em standards/
❌ Duplicatas de memória existente

---

## Estrutura de Memória

### Global (`memory/global/`)
```
- architecture-decisions.md (ADRs aprovadas)
- approved-vendors.md (tecnologias authorized)
- mandatory-patterns.md (patterns obrigatórios)
- lessons-learned.md (aprendizados corporativos)
- stakeholders.md (quem aprova o quê)
```

### Initiative (`memory/initiatives/{initiative-name}/`)
```
- context.md (contexto do projeto)
- decisions.md (decisões tomadas)
- risks.md (riscos do projeto)
- integrations.md (sistemas envolvidos)
- timeline.md (cronograma & dependências)
```

### Domain (`memory/domains/{domain}/`)
```
- patterns.md (patterns descobertos)
- technologies.md (tech stack)
- risks.md (riscos conhecidos)
- standards.md (padrões do domínio)
```
