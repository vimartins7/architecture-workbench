# Diretrizes de LGPD

Lei Geral de Proteção de Dados - Conformidade obrigatória.

---

## Escopo

LGPD se aplica a:
- Qualquer sistema processando dados pessoais
- Qualquer dado de residentes brasileiros
- Qualquer dado processado por entidades brasileiras

---

## Conceitos-Chave

### Dados Pessoais
Qualquer informação relacionada a uma pessoa física identificada ou identificável.

**Exemplos**:
- Nome, email, telefone
- Número de ID (CPF, RG)
- Endereço de IP
- Cookies, IDs de dispositivo
- Dados biométricos
- Dados de saúde
- Dados financeiros

### Processamento de Dados
Qualquer operação em dados pessoais:
- Coleta
- Registro
- Organização
- Estruturação
- Armazenamento
- Acesso
- Uso
- Transmissão
- Exclusão

---

## Base Legal para Processamento

Processamento requer UMA base legal:

1. **Consentimento** - Explícito, informado, inequívoco
2. **Contrato** - Necessário para cumprir contrato
3. **Obrigação Legal** - Exigido por lei
4. **Interesse Legítimo** - Documentado, proporcional
5. **Tarefa Pública** - Autorizado por lei
6. **Interesse Vital** - Proteção de vida/integridade física

---

## Práticas Obrigatórias

### 1. Minimização de Dados
- Coletar apenas dados necessários
- Retenção apenas enquanto necessário
- Limpeza regular de dados antigos

### 2. Limitação de Finalidade
- Usar dados apenas para finalidade declarada
- Novo uso = nova base legal obrigatória

### 3. Transparência
- Política de privacidade acessível
- Informações claras sobre processamento
- Linguagem simples e clara

### 4. Direitos de Acesso
- Direito de acesso: Responder em 15 dias
- Direito de correção: Atualizar dados incorretos
- Direito de exclusão: Deletar dados
- Direito de portabilidade: Fornecer em formato portável

### 5. Segurança
- Medidas técnicas razoáveis
- Classificação de dados
- Criptografia
- Controles de acesso
- Notificação de violação em 2 dias

### 6. Notificação de Violação
- Notificar autoridade em 2 dias
- Se alto risco, notificar titulares
- Documentar todos os incidentes

---

## Checklist de Implementação

Para cada sistema processando dados pessoais:

### Fase de Design
- [ ] Identificar quais dados são processados
- [ ] Determinar base legal
- [ ] Documentar avaliação de impacto de privacidade
- [ ] Desenhar controles de privacidade desde o início
- [ ] Criptografia em trânsito e em repouso

### Fase de Implementação
- [ ] Construir logging de auditoria
- [ ] Implementar controles de acesso
- [ ] Implementar exclusão/correção
- [ ] Formato de portabilidade de dados
- [ ] Detecção de violação

### Fase de Operações
- [ ] Política de privacidade atual
- [ ] Mecanismos de consentimento funcionando
- [ ] Política de retenção de dados aplicada
- [ ] Auditorias regulares de acesso
- [ ] Resposta a incidentes pronta

---

## Ciclo de Vida de Dados

### Coleta
- Base legal documentada
- Consentimento obtido (se necessário)
- Finalidade declarada claramente
- Período de retenção definido

### Armazenamento
- Criptografado em repouso
- Controles de acesso
- Backups regulares
- Método de exclusão segura definido

### Uso
- Limitado à finalidade
- Registrado em auditoria
- Consentimento respeitado

### Exclusão
- Limpeza automática por política de retenção
- Direito de exclusão respeitado (em 15 dias)
- Exclusão segura (sem recuperação)
- Exclusão verificada

---

## Requisitos de Documentação

Manter e atualizar:
1. **Registro LGPD** - Todas as atividades de processamento
2. **Política de Privacidade** - Atual e acessível
3. **Contratos de Processamento de Dados** - Com processadores
4. **Log de Incidentes** - Todos os incidentes LGPD
5. **Avaliações de Impacto** - Para processamento de alto risco

---

## Governança

- Encarregado de Proteção de Dados (DPO) designado
- Revisão de privacidade no comitê de arquitetura
- Auditorias regulares de conformidade
- Treinamento para pessoal relevante
- Plano de resposta a incidentes

---

## Penalidades

Não conformidade pode resultar em:
- Multas até 2% da receita ou R$ 50M (o maior)
- Bloqueio de dados
- Divulgação pública
- Ação judicial
- Perda de contratos públicos

---

## Contatos-Chave

- DPO (Encarregado de Proteção de Dados): [a definir]
- Legal/Conformidade: [a definir]
- Segurança: [a definir]

---

## Recursos

- [Lei LGPD](http://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm)
- [Diretrizes ANPD](https://www.gov.br/cidadania/pt-br/acesso-a-informacao/lgpd)
