# Sistema de Gestão para Clínica Médica
### Engenharia de Requisitos — MVP

**Centro Universitário de Brasília (CEUB)** • Engenharia de Requisitos • 2026/2

**Alunos:** Thiago Braziellas, Pedro Ryan, Luiz Claudio e Arthur Santos

**Base metodológica:** BABoK v3 (IIBA) • ISO/IEC 25010:2023 • MoSCoW • LGPD (Lei nº 13.709/2018)

---

## 1. Contexto e Objetivo

O projeto tem como finalidade desenvolver a **Engenharia de Requisitos** para um Sistema de Gestão de Clínica Médica, com o objetivo de **unificar a operação** e **eliminar processos manuais** apoiados em planilhas descentralizadas.

A proposta é entregar um **MVP enxuto e inegociável** — focado em resolver os problemas centrais do negócio (conflitos de agenda, retrabalho, duplicidade de dados e conformidade legal) — e evoluir a solução por meio de um backlog priorizado.

Todo o trabalho segue as diretrizes do **BABoK (Business Analysis Body of Knowledge)**, que estrutura a análise de negócio como a ponte entre os stakeholders e a solução de software.

---

## 2. Stakeholders

| Stakeholder | Necessidade Principal |
|---|---|
| **Paciente** | Agilidade no agendamento, transparência e lembretes de consulta |
| **Recepcionista** | Escala organizada em tempo real e agilidade no balcão |
| **Médico** | Consulta segura da agenda e dos dados do paciente |
| **Gerente da Clínica** | Indicadores operacionais e visibilidade da eficiência |
| **Equipe de TI** | Estabilidade técnica, segurança e evolução do sistema |
| **Direção** | Redução de custos, conformidade com a LGPD e qualidade do atendimento |

Cada stakeholder possui necessidades distintas — o sistema equilibra as demandas dos usuários operacionais com os interesses estratégicos da gestão.

---

## 3. Diagnóstico dos Problemas (AS-IS)

- **Conflitos de horários:** informações distribuídas em planilhas causam dupla marcação e sobrecarga do médico.
- **Retrabalho:** pacientes já cadastrados precisam informar dados novamente, aumentando o tempo de atendimento.
- **Duplicidade de informações:** sem validação, o mesmo paciente pode possuir mais de um cadastro.
- **Dificuldade de atualização:** alterações feitas em um local não refletem nos demais.
- **Falhas na comunicação:** ausência de lembretes gera esquecimento e alta taxa de no-show.
- **Cancelamentos sem reocupação:** horários cancelados ficam ociosos até o fim do dia.

### Causa Raiz

Utilização de **planilhas individuais sem sincronização**, **ausência de banco de dados centralizado** e **dependência de processos manuais** entre os envolvidos no fluxo.

---

## 4. Regras de Negócio (MVP)

| Código | Regra | Classificação |
|---|---|---|
| **RN01** | Cadastro de paciente deve possuir CPF válido e único por cadastro ativo | Duplicidade |
| **RN02** | Um médico não pode ter mais de um paciente agendado no mesmo horário | Conflito |
| **RN03** | Agendamentos apenas nos horários cadastrados na escala do médico | Processo |
| **RN04** | Horário deve ser liberado automaticamente após cancelamento | Cancelamento |
| **RN05** | Dados de pacientes já cadastrados devem ser reutilizados | Retrabalho |
| **RN06** | O atendimento deve seguir o fluxo de status definido pela clínica | Operacional |
| **RN07** | Informações protegidas devem ser acessadas apenas por usuários autorizados | LGPD |

Regras de negócio ligadas ao backlog (lembretes automáticos, notificação de alterações na agenda, fila de espera e prontuário eletrônico) estão documentadas mas não integram o escopo do MVP.

---

## 5. Requisitos Funcionais (MVP)

Todos os requisitos abaixo foram classificados como **Must Have** — sem eles o sistema não resolve o problema para o qual foi contratado.

### RF01 — Gerenciamento de Pacientes
Cadastrar, consultar, atualizar e inativar pacientes preservando o histórico. Validação de CPF e bloqueio de duplicidade em cadastros ativos.

### RF02 — Gerenciamento de Médicos e Escalas
Cadastro de médicos, especialidades e horários de atendimento. Não permite oferecer horários fora da escala ou bloqueados.

### RF03 — Consulta de Horários Disponíveis
Busca por médico e data, atualizada em tempo real a cada agendamento, cancelamento ou bloqueio.

### RF04 — Agendamento de Consultas
Vincula paciente, médico, data e horário. Verifica disponibilidade antes de confirmar, impedindo conflitos. Status inicial: "Agendado".

### RF05 — Cancelamento e Reagendamento
Registra o cancelamento no histórico, altera o status para "Cancelado" e valida a disponibilidade do novo horário antes do reagendamento.

### RF06 — Liberação Automática de Horários
O horário de uma consulta cancelada retorna imediatamente para a agenda como disponível.

### RF07 — Controle do Status do Atendimento
Estados suportados: **Agendado → Confirmado → Em Espera → Atendido / Cancelado**. Recepção altera para "Em Espera" na chegada do paciente. Consulta cancelada não pode ser iniciada.

### Backlog Funcional

| Código | Requisito | MoSCoW |
|---|---|---|
| RF-B01 | Lembretes Automáticos (WhatsApp/SMS) | Should |
| RF-B02 | Gerenciamento da Agenda pelo Médico | Should |
| RF-B03 | Prontuário Eletrônico | Should |
| RF-B04 | Fila de Espera Automatizada | Should |
| RF-B05 | Avisos sobre Alterações na Agenda | Should |
| RF-B06 | Dashboard de Indicadores | Could |
| RF-B07 | Autoatendimento (portal/chatbot) | Could |
| RF-B08 | Pesquisa de Satisfação | Won't |

---

## 6. Requisitos Não Funcionais (ISO/IEC 25010:2023)

A qualidade do sistema foi ancorada no modelo de qualidade de produto da **ISO/IEC 25010:2023**, com critérios **mensuráveis e testáveis** — evitando requisitos vagos como "o sistema deve ser rápido" ou "o sistema deve ser seguro".

| Código | Requisito | Característica ISO 25010 | Critério de Aceitação | Verificação |
|---|---|---|---|---|
| **RNF01** | Busca de horários responde em até 2 segundos | Eficiência de desempenho | ≤ 2s em 95% das requisições, sob carga de até 500 usuários simultâneos | Teste de carga (k6 / JMeter) |
| **RNF02** | Comunicação criptografada via HTTPS/TLS 1.2+ | Segurança | 100% das rotas com TLS ativo | Varredura OWASP ZAP |
| **RNF03** | Disponibilidade mínima de 99,5% ao mês | Confiabilidade | Uptime ≥ 99,5% | Monitoramento contínuo |
| **RNF04** | Backup diário automatizado do banco de dados | Confiabilidade | Backup sem falha; restauração testada mensalmente | Simulação de recuperação |
| **RNF05** | Controle de acesso a dados sensíveis (LGPD) | Segurança | Tentativa não autorizada bloqueada e registrada | Teste de controle de acesso |

### Backlog Não Funcional

| Código | Requisito | Característica ISO 25010 |
|---|---|---|
| RNF-B01 | Facilidade de agendamento (≤ 3 ações) | Capacidade de Interação |
| RNF-B02 | Suporte a 50 acessos simultâneos | Eficiência de desempenho |
| RNF-B03 | Autenticação em duas etapas (2FA) | Segurança |
| RNF-B04 | Compatibilidade multi-navegador | Compatibilidade |
| RNF-B05 | Responsividade em múltiplas telas | Capacidade de Interação |

---

## 7. Priorização MoSCoW

Para evitar a **"síndrome do tudo é urgente"**, cada requisito passou por um filtro objetivo:

> **"Se o sistema for lançado sem este item, a operação da clínica trava ou existe violação legal?"**

Apenas os itens que passaram nesse teste foram classificados como **Must Have**. Resultado consolidado:

- **7 requisitos funcionais Must** (RF01 a RF07) — núcleo vital do fluxo de agendamento.
- **5 requisitos não funcionais Must** (RNF01 a RNF05) — exigências de LGPD, segurança, disponibilidade e integridade dos dados.
- **Total do MVP: 12 itens inegociáveis.**

Requisitos como lembretes automáticos, prontuário eletrônico e fila de espera foram rebaixados para **Should Have** — a clínica consegue operar manualmente na V1 sem eles.

---

## 8. Análise de Trade-offs

### 8.1 Segurança vs. Capacidade de Interação
2FA obrigatório para médicos e gerentes (dados clínicos, LGPD); autenticação simplificada por SMS ou e-mail no autoatendimento do paciente, onde o risco de exposição é menor.

### 8.2 Eficiência de Desempenho vs. Confiabilidade
Priorizar consistência do banco (verificação e bloqueio antes de confirmar), aceitando milissegundos a mais de latência. Evitar um conflito (RN02) é mais crítico do que otimizar tempo de resposta.

### 8.3 Adequação Funcional vs. Fluidez
Executar todas as validações (escala, CPF, disponibilidade) no backend, sem telas intermediárias, preservando a fluidez sem abrir mão da integridade dos dados.

### 8.4 Confiabilidade vs. Custo
Aceitar o custo de alta disponibilidade e backups redundantes. O domínio é saúde — indisponibilidade impacta diretamente o atendimento.

### 8.5 Compatibilidade vs. Privacidade
Quando RF-B01 for priorizado, restringir o conteúdo enviado ao mínimo necessário — nome, data e horário — sem informação clínica.

### 8.6 Flexibilidade vs. Manutenibilidade
Arquitetura modular simples no MVP, evitando over-engineering prematuro. A generalização vem quando a expansão for confirmada.

---

## 9. Indicadores de Desempenho (KPIs)

| Indicador | O que mede | Fórmula / Método |
|---|---|---|
| **Taxa de No-Show** | Percentual de faltas — linha de base para eficácia dos lembretes | (Faltas / Total agendado) × 100 |
| **Taxa de Ocupação da Agenda** | Aproveitamento da capacidade de atendimento | (Horários ocupados / Horários disponíveis) × 100 |
| **Tempo Médio de Atendimento na Recepção** | Eficiência do balcão | Tempo entre chegada e alteração para "Em Espera" |
| **Tempo Médio de Espera do Paciente** | Experiência do paciente | Tempo entre "Em Espera" e início do atendimento |
| **Índice de Retrabalho no Cadastro** | Eficácia da centralização de dados | Ocorrências de recadastro ou correção |
| **Índice de Disponibilidade** | Cumprimento da meta de uptime (RNF03) | Monitoramento contínuo |
| **Tempo de Resposta de Busca** | Cumprimento da meta de desempenho (RNF01) | Percentil 95 do tempo de resposta |

---

## 10. Visão de Futuro

- **Curto prazo (backlog Should):** lembretes automáticos, gerenciamento da agenda pelo médico, prontuário eletrônico, fila de espera e notificações de alterações.
- **Médio prazo (backlog Could):** dashboard gerencial visual e portal de autoatendimento.
- **Longo prazo (visão estratégica):** aplicativo móvel próprio, análise preditiva de padrões de faltas, sugestões automáticas de horários, integração com sistemas financeiros e novos canais de comunicação.

---

## 11. Conclusão

O projeto propõe **integrar os principais processos da clínica** em uma base única, começando por um MVP enxuto composto por **12 itens inegociáveis** — 7 requisitos funcionais e 5 não funcionais — todos ancorados nos problemas reais do negócio e nas exigências da LGPD.

Com a implantação do MVP, espera-se:

- Eliminar conflitos de horários;
- Evitar cadastros duplicados;
- Reduzir o retrabalho na recepção;
- Facilitar a atualização e a consulta dos dados;
- Organizar o fluxo de atendimento;
- Proteger informações sensíveis conforme a legislação;
- Estabelecer uma linha de base mensurável para as próximas fases.

Os demais ganhos — automação da comunicação com o paciente, redução ativa de faltas, reocupação inteligente de vagas e acompanhamento visual por dashboards — dependem dos itens do backlog e fazem parte da evolução planejada.

A proposta não é substituir planilhas ou automatizar tarefas isoladas. É **integrar processos, garantir integridade dos dados e disponibilizar informação organizada** para quem realmente precisa utilizá-la.

---

## 12. Referências

- **ISO/IEC 25010:2023** — Systems and software engineering — Systems and software Quality Requirements and Evaluation (SQuaRE) — Product quality model. 2ª ed.
- **ISO/IEC 25002:2024** — Quality model overview and usage.
- **IIBA** — A Guide to the Business Analysis Body of Knowledge (BABoK Guide), v3.
- **SOMMERVILLE, I.** — Software Engineering. 10ª ed. Pearson.
- **Agile Business Consortium / DSDM Consortium** — MoSCoW Prioritisation.
- **BRASIL** — Lei nº 13.709/2018 (Lei Geral de Proteção de Dados Pessoais — LGPD).
- **VALÉRIA, Kadidja.** Qualidade de Software com a ISO/IEC 25010. Material de aula, CEUB, Engenharia de Requisitos, 2026/2.
