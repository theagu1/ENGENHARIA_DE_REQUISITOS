# Atividade — 18/08/2026

## 1. Stakeholders

Os principais stakeholders do sistema são:

* **Paciente**
* **Recepcionista**
* **Médico**
* **Gerente da clínica**
* **Equipe de TI**
* **Direção da clínica**

---

## 2. Problemas de Negócio

### Problemas

* Conflitos de horários;
* Retrabalho;
* Duplicidade de informações;
* Dificuldade de atualização dos dados;
* Falhas na comunicação com pacientes;
* Dificuldade para controlar cancelamentos.

### Causas

* Planilhas individuais sem sincronização;
* Ausência de banco de dados centralizado;
* Ausência de mecanismo automático de lembrete de consultas;
* Utilização de vários softwares diferentes.

---

## 3. Regras de Negócio

| Código   | Regra de Negócio                                                                                                               | Classificação                       |
| -------- | ------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------- |
| **RN01** | O cadastro do paciente exige obrigatoriamente um número de CPF válido e único.                                                 | Estudo de Caso (Duplicidade)        |
| **RN02** | O sistema não pode permitir mais de um agendamento para o mesmo médico no mesmo horário.                                       | Estudo de Caso (Overbooking)        |
| **RN03** | Agendamentos só podem ser realizados em horários previamente cadastrados na escala do médico.                                  | Processo de Negócio                 |
| **RN04** | O cancelamento de um agendamento deve disponibilizar o horário imediatamente para novas marcações.                             | Estudo de Caso (Cancelamentos)      |
| **RN05** | A alteração da escala médica deve acionar notificações automáticas a todos os pacientes agendados na faixa afetada.            | Estudo de Caso (Mudanças de Agenda) |
| **RN06** | Lembretes automáticos de consulta devem ser enviados via mensagem com 24h e 2h de antecedência.                                | Estudo de Caso (Faltas)             |
| **RN07** | Pacientes previamente cadastrados no sistema não precisam reconfirmar dados básicos a cada novo agendamento.                   | Estudo de Caso (Retrabalho)         |
| **RN08** | O registro e a visualização do prontuário médico são restritos exclusivamente aos profissionais de saúde autorizados.          | Regulamentação / LGPD               |
| **RN09** | Caso o paciente não confirme o lembrete até 4h antes do atendimento, o horário entra para a lista de prioridade de reocupação. | Política Operacional                |
| **RN10** | A consulta só pode ser iniciada pelo médico caso o paciente esteja com o status **"Em Espera"** confirmado na recepção.        | Operacional da Clínica              |

---

## 4. Melhorias Propostas

| Problema                                                                          | Melhoria                                                                                                                       |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **Conflitos de horários**                                                         | Utilização de uma agenda unificada, com informações do paciente e do médico definido.                                          |
| **Retrabalho, duplicidade de informações e dificuldade de atualização dos dados** | Implantação de um software centralizado com todas as informações e cadastros dos pacientes.                                    |
| **Falhas na comunicação com pacientes**                                           | Utilização de follow-ups, organização dos dados dos clientes em um único software e armazenamento do histórico de comunicação. |
| **Dificuldade para controlar cancelamentos**                                      | Implementação de uma fila de espera automatizada.                                                                              |

---

## 5. Requisitos Funcionais

| Código   | Requisito Funcional                                                                                             | Prioridade |
| -------- | --------------------------------------------------------------------------------------------------------------- | ---------- |
| **RF01** | O sistema deverá permitir cadastrar, consultar, atualizar e inativar dados dos pacientes.                       | —          |
| **RF02** | O sistema deverá permitir o cadastro de médicos, suas especialidades e suas escalas de atendimento.             | —          |
| **RF03** | O sistema deverá permitir a consulta de horários disponíveis em tempo real.                                     | —          |
| **RF04** | O sistema deverá efetuar o agendamento de consultas bloqueando concorrência de horários.                        | —          |
| **RF05** | O sistema deverá permitir o cancelamento e reagendamento de consultas.                                          | —          |
| **RF06** | O sistema deverá liberar automaticamente horários cancelados no mapa da agenda.                                 | —          |
| **RF07** | O sistema deverá enviar lembretes automáticos de consulta por WhatsApp e SMS.                                   | —          |
| **RF08** | O sistema deverá permitir ao médico gerenciar e bloquear seus horários na agenda.                               | —          |
| **RF09** | O sistema deverá permitir o registro de prontuários eletrônicos das consultas.                                  | —          |
| **RF10** | O sistema deverá manter uma fila de espera para remanejamento em horários vagos/cancelados.                     | —          |
| **RF11** | O sistema deverá enviar avisos automatizados em massa para pacientes quando houver alteração de escala médica.  | —          |
| **RF12** | O sistema deverá disponibilizar dashboards com indicadores de desempenho da clínica.                            | —          |
| **RF13** | O sistema deverá permitir o agendamento de consultas por portal web/chatbot de autoatendimento.                 | —          |
| **RF14** | O sistema deverá controlar os status do atendimento: **Agendado, Confirmado, Em Espera, Atendido e Cancelado**. | —          |
| **RF15** | O sistema deverá disparar pesquisas de satisfação após o encerramento do atendimento.                           | —          |

---

## 6. Requisitos Não Funcionais

| Código    | Categoria       | Requisito Não Funcional                                                                                    |
| --------- | --------------- | ---------------------------------------------------------------------------------------------------------- |
| **RNF01** | Desempenho      | O sistema deverá exibir o resultado da busca por horários disponíveis em no máximo 2 segundos.             |
| **RNF02** | Segurança       | Todos os dados pessoais e prontuários médicos trafegados deverão utilizar criptografia HTTPS/TLS.          |
| **RNF03** | Usabilidade     | A interface do operador de recepção deve permitir concluir um agendamento em no máximo 3 cliques.          |
| **RNF04** | Disponibilidade | O sistema em nuvem deve apresentar um índice de disponibilidade (uptime) mínimo de 99,5% ao mês.           |
| **RNF05** | Confiabilidade  | O sistema deve realizar rotinas automatizadas diárias de backup do banco de dados.                         |
| **RNF06** | Privacidade     | O tratamento de dados pessoais do sistema deve seguir estritamente as diretrizes da LGPD.                  |
| **RNF07** | Desempenho      | O sistema deve suportar no mínimo 50 acessos simultâneos sem perda de performance.                         |
| **RNF08** | Segurança       | A autenticação de médicos e gerentes deve exigir verificação em duas etapas (2FA).                         |
| **RNF09** | Compatibilidade | A aplicação Web deve ser acessível e responsiva nos navegadores Chrome, Safari, Firefox e Edge.            |
| **RNF10** | Usabilidade     | A plataforma deve possuir interface adaptada e intuitiva para dispositivos móveis (smartphones e tablets). |

---

## 7. Indicadores para Acompanhar o Processo

### 7.1 Taxa de No-Show (Absenteísmo)

Percentual de pacientes que faltaram sem avisar. Mede a eficácia dos lembretes automáticos de 24h e 2h.

### 7.2 Taxa de Ocupação da Agenda

Percentual de horários efetivamente preenchidos em relação ao total de horários disponíveis na escala dos médicos.

### 7.3 Tempo Médio de Reocupação de Vaga

Tempo que o sistema leva para preencher um horário que ficou vago após um cancelamento, utilizando a fila de espera automatizada.

### 7.4 Taxa de Conversão da Lista de Prioridade

Percentual de horários ociosos, ou seja, não confirmados até 4h antes, que foram recuperados e preenchidos por novos pacientes.

### 7.5 Tempo Médio de Atendimento na Recepção (TMA)

Tempo gasto para identificar o paciente e mudar seu status para **"Em Espera"**. Deve ser baixo, já que o sistema elimina a reconfirmação de dados básicos.

### 7.6 Tempo Médio de Espera do Paciente

Tempo que o paciente passa na recepção aguardando o médico, medido entre o status **"Em Espera"** e o início do atendimento.

### 7.7 Índice de Retrabalho no Cadastro

Quantidade de cadastros duplicados ou corrigidos por CPF inválido após a implantação da validação rígida.

### 7.8 Taxa de Resposta aos Lembretes

Percentual de pacientes que interagem e respondem às mensagens automáticas de confirmação via WhatsApp/SMS.

### 7.9 Índice de Satisfação do Paciente (NPS)

Nota média coletada através das pesquisas de satisfação enviadas automaticamente após o encerramento das consultas.

### 7.10 Índice de Disponibilidade (Uptime)

Validação mensal para verificar se a plataforma em nuvem permaneceu ativa no mínimo 99,5% do tempo.

### 7.11 Tempo de Resposta de Busca

Tempo médio que o sistema leva para retornar a consulta de horários vagos, garantindo o teto de 2 segundos.

---

## 8. Principais Requisitos

### 1º — Agenda e Agendamento

**RF06, RF07, RF08 e RF13**

São os requisitos mais importantes porque resolvem o principal gargalo da clínica: conflitos e desorganização da agenda.

### 2º — Cadastro e Cancelamento

**RF01, RF09 e RF10**

Reduzem retrabalho, duplicidade e perda de horários.

### 3º — Atendimento

**RF14 e RF15**

Permitem completar o processo de atendimento de ponta a ponta, incluindo o controle dos status e a pesquisa de satisfação.

### 4º — Comunicação

**RF07 e RF11**

Melhoram a experiência do paciente e ajudam a reduzir faltas e problemas decorrentes de alterações na agenda médica.

### 5º — Gestão

**RF12**

Permite acompanhar os resultados do processo por meio de indicadores e dashboards.

### 6º — Melhorias Futuras

**RF10**

A lista de espera pode ser aprimorada posteriormente para otimizar ainda mais a ocupação da agenda e o aproveitamento de horários cancelados.


