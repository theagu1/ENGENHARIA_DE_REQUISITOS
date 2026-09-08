# Sistema de Gestão para Clínica Médica
## Clínica + Saúde

Projeto desenvolvido para a disciplina de Engenharia de Requisitos.

---

## 1. Identificação do Projeto

| Informação | Descrição |
|---|---|
| Turma | Turma A – Eng. de Software |
| Nome do projeto | Clínica + Saúde |
| Integrante 1 | Thiago Dos Santos |
| Integrante 2 | Pedro Ryan |
| Integrante 3 | Arthur Santos |
| Integrante 4 | Luiz Claudio |

---

## 2. Contexto do Projeto

### 2.1 Problema

A clínica apresenta problemas relacionados à organização dos atendimentos, principalmente conflitos de horários, dados desorganizados e dificuldades na comunicação com os pacientes.

Atualmente, parte do processo é realizada utilizando planilhas individuais e procedimentos manuais. Como essas informações não são sincronizadas, podem ocorrer conflitos de horários, duplicidade de dados, demora no atendimento e problemas relacionados às consultas.

O sistema tem como objetivo organizar esse processo, centralizando as informações e facilitando o gerenciamento das consultas, dos pacientes e das agendas.

### 2.2 Pessoas afetadas pelo problema

Os principais envolvidos são:

- Dono da clínica;
- Recepcionistas;
- Médicos;
- Equipe de TI;
- Pacientes.

### 2.3 Processo atual

Atualmente, os processos são realizados principalmente por meio de:

- Planilhas individuais;
- Atendimento telefônico;
- Atendimento presencial;
- Confirmações manuais;
- Atualização manual de horários;
- Consulta de diferentes planilhas para verificar disponibilidade.

Esse processo torna o atendimento mais lento e aumenta a possibilidade de erros.

### 2.4 Principais dificuldades

As principais dificuldades identificadas são:

- Conflitos de horários;
- Duplicidade de dados;
- Dados desatualizados;
- Trabalho manual excessivo;
- Falta de sincronização das informações;
- Falta de confirmação automática das consultas;
- Elevado índice de cancelamentos;
- Dificuldade para acompanhar os indicadores da clínica.

### 2.5 Resultado esperado

Com o sistema, espera-se:

- Melhor organização da agenda;
- Redução do trabalho manual;
- Redução dos conflitos de horários;
- Centralização dos dados dos pacientes;
- Melhoria na comunicação com os pacientes;
- Maior controle das consultas;
- Maior segurança das informações;
- Melhor acompanhamento dos indicadores da clínica.

---

## 3. Stakeholders

Stakeholders são as pessoas ou grupos que possuem interesse no sistema ou que serão afetados por ele.

| ID | Stakeholder | Papel | Necessidade/Interesse | Influência |
|---|---|---|---|---|
| ST01 | Dono da clínica | Administrador | Organização, otimização e acompanhamento dos resultados | Alta |
| ST02 | Recepcionista | Operador do sistema | Agilidade no cadastro e gerenciamento das consultas | Alta |
| ST03 | Médico | Profissional responsável pelo atendimento | Organização da agenda e acesso ao histórico dos pacientes | Alta |
| ST04 | Equipe de TI | Suporte e manutenção | Segurança, disponibilidade e manutenção do sistema | Média |
| ST05 | Paciente | Usuário final | Marcar, alterar e cancelar consultas e receber informações | Alta |

### 3.1 Stakeholder principal

**Paciente (ST05)**

O paciente é considerado o principal stakeholder porque é o usuário diretamente beneficiado pelo sistema. Ele precisa conseguir realizar ações relacionadas às suas consultas de maneira mais rápida e organizada, sem depender exclusivamente da recepção.

Além disso, a experiência do paciente influencia diretamente a satisfação com o atendimento e os resultados esperados pela clínica.

---

## 4. Levantamento das Necessidades

Antes da criação dos requisitos, foram identificadas as principais necessidades dos stakeholders.

| ID | Stakeholder | Necessidade | Problema relacionado |
|---|---|---|---|
| N01 | ST05 – Paciente | Marcar, alterar e cancelar consultas de forma rápida | Processo manual e dependente da recepção |
| N02 | ST05 – Paciente | Receber confirmações e lembretes | Esquecimento e cancelamento de consultas |
| N03 | ST02 – Recepcionista | Ter uma agenda centralizada e atualizada | Planilhas sem sincronização |
| N04 | ST02 – Recepcionista | Cadastrar e consultar pacientes rapidamente | Dados duplicados e desorganizados |
| N05 | ST03 – Médico | Acessar histórico e dados dos pacientes | Informações espalhadas |
| N06 | ST03 – Médico | Gerenciar sua agenda sem conflitos | Conflitos de horários |
| N07 | ST01 – Dono | Acompanhar relatórios e indicadores | Falta de informações gerenciais |
| N08 | ST04 – TI | Garantir segurança dos dados | Falta de controle e proteção adequada |

---

## 5. Requisitos Funcionais

Os requisitos funcionais descrevem o que o sistema deve permitir que seus usuários façam.

#### RF01 — Gerenciamento de pacientes

O sistema deve permitir que usuários autorizados cadastrem, consultem, editem e inativem pacientes.
O sistema deve validar o CPF informado e impedir o cadastro de dois pacientes ativos com o mesmo CPF.
Ao inativar um paciente, o sistema deve preservar seu histórico de consultas.

- **Stakeholder:** ST02 – Recepcionista
- **Necessidade relacionada:** N04
- **Prioridade:** Alta

#### RF02 — Gerenciamento de médicos e escalas

O sistema deve permitir o cadastro de médicos, especialidades, horários e escalas de atendimento.
O sistema deve permitir o cadastro de exceções na escala quando necessário.
O sistema não deve permitir agendamentos fora dos horários em que o médico estiver disponível.

- **Stakeholder:** ST03 – Médico / ST02 – Recepcionista
- **Necessidade relacionada:** N06
- **Prioridade:** Alta

#### RF03 — Consulta de horários disponíveis

O sistema deve permitir consultar horários disponíveis utilizando filtros como:

- Médico;
- Especialidade;
- Data;
- Período.

O sistema deve atualizar os horários disponíveis de acordo com os agendamentos realizados.

O sistema não deve apresentar horários:

- Já ocupados;
- Bloqueados;
- Fora da escala do médico;
- Que já tenham passado.

- **Stakeholder:** ST05 – Paciente / ST02 – Recepcionista
- **Necessidades relacionadas:** N01, N03
- **Prioridade:** Alta

#### RF04 — Agendamento de consulta

O sistema deve permitir realizar o agendamento associando:

- Paciente;
- Médico;
- Data;
- Horário.

Antes de confirmar o agendamento, o sistema deve verificar novamente se o horário continua disponível.
Após a confirmação, a consulta deve receber inicialmente o status **Agendado**.
O sistema não deve permitir dois agendamentos para o mesmo médico no mesmo horário.

- **Stakeholder:** ST05 – Paciente / ST02 – Recepcionista
- **Necessidades relacionadas:** N01, N03, N06
- **Prioridade:** Alta

#### RF05 — Cancelamento e reagendamento

O sistema deve permitir cancelar ou reagendar consultas conforme as regras definidas pela clínica.
Quando uma consulta for cancelada, o sistema deve registrar o status **Cancelado** e o motivo informado.
O horário anteriormente ocupado deve deixar de ficar reservado.

- **Stakeholder:** ST05 – Paciente / ST02 – Recepcionista
- **Necessidade relacionada:** N01
- **Prioridade:** Alta

#### RF06 — Liberação automática de horários

O sistema deve liberar imediatamente o horário de uma consulta que tenha sido cancelada.
Após a liberação, o sistema deve permitir que o horário seja disponibilizado novamente para agendamento ou para pacientes presentes na lista de espera.

- **Stakeholder:** ST02 – Recepcionista
- **Necessidade relacionada:** N03
- **Prioridade:** Alta

#### RF07 — Lembretes automáticos

O sistema deve enviar lembretes automáticos das consultas.

Os lembretes devem ser enviados:

- 24 horas antes;
- 2 horas antes.

O paciente deve poder informar se irá comparecer.
O sistema não deve enviar lembretes para consultas que estejam canceladas.

- **Stakeholder:** ST05 – Paciente
- **Necessidade relacionada:** N02
- **Prioridade:** Alta

#### RF08 — Agenda do médico

O sistema deve permitir que o médico visualize sua agenda diária e semanal.

O médico deve poder:

- Visualizar consultas;
- Bloquear horários;
- Consultar pacientes;
- Identificar pacientes que estão aguardando atendimento.

- **Stakeholder:** ST03 – Médico
- **Necessidade relacionada:** N06
- **Prioridade:** Alta

#### RF09 — Prontuário eletrônico

O sistema deve permitir que usuários autorizados registrem informações clínicas relacionadas às consultas.

O prontuário deve permitir registrar informações como:

- Anotações clínicas;
- Diagnósticos;
- Prescrições;
- Informações relacionadas ao atendimento.

O sistema deve associar os registros ao paciente e à consulta correspondente.
Após a finalização e assinatura do registro, o sistema não deve permitir alterações não autorizadas.

- **Stakeholder:** ST03 – Médico
- **Necessidade relacionada:** N05
- **Prioridade:** Alta

#### RF10 — Lista de espera

O sistema deve permitir o gerenciamento de uma lista de espera por médico ou especialidade.
Quando um horário for liberado, o sistema deve identificar pacientes compatíveis com a vaga e permitir a sugestão do horário disponível.

- **Stakeholder:** ST02 – Recepcionista
- **Necessidades relacionadas:** N01, N03
- **Prioridade:** Média

#### RF11 — Notificação de alterações na agenda

Quando ocorrer uma alteração na agenda que afete uma consulta já marcada, o sistema deve identificar os pacientes afetados.
O sistema deve enviar uma notificação informando a alteração, cancelamento ou mudança de horário.

- **Stakeholder:** ST05 – Paciente / ST02 – Recepcionista
- **Necessidade relacionada:** N02
- **Prioridade:** Alta

#### RF12 — Dashboard e indicadores

O sistema deve disponibilizar indicadores gerenciais para o administrador da clínica.

Os indicadores devem incluir:

- Número de consultas realizadas;
- Número de cancelamentos;
- Taxa de ocupação;
- Taxa de faltas;
- Tempo médio de espera.

Os dados devem poder ser filtrados por:

- Período;
- Médico;
- Especialidade.

- **Stakeholder:** ST01 – Dono da clínica
- **Necessidade relacionada:** N07
- **Prioridade:** Média

#### RF13 — Atendimento pelo paciente

O sistema deve permitir que o paciente consulte informações de suas consultas e realize ações relacionadas ao atendimento.

O paciente deve poder:

- Consultar suas consultas;
- Agendar consultas;
- Confirmar consultas;
- Cancelar consultas;
- Consultar informações de seus horários.

As validações utilizadas nesse processo devem ser as mesmas aplicadas aos agendamentos realizados pela recepção.

- **Stakeholder:** ST05 – Paciente
- **Necessidade relacionada:** N01
- **Prioridade:** Alta

#### RF14 — Controle do status do atendimento

O sistema deve controlar o ciclo de atendimento utilizando os seguintes status:

1. Agendado;
2. Confirmado;
3. Em Espera;
4. Em Atendimento;
5. Atendido;
6. Cancelado.

O sistema não deve permitir que uma consulta seja iniciada enquanto o paciente não estiver com o status **Em Espera**.

- **Stakeholder:** ST02 – Recepcionista / ST03 – Médico
- **Necessidade relacionada:** N06
- **Prioridade:** Alta

#### RF15 — Pesquisa de satisfação

Após uma consulta ser registrada como **Atendido**, o sistema deve permitir o envio de uma pesquisa de satisfação.

A pesquisa poderá utilizar indicadores como:

- NPS;
- CSAT.

Consultas canceladas ou pacientes que não compareceram não devem receber a pesquisa.

- **Stakeholder:** ST01 – Dono / ST05 – Paciente
- **Necessidade relacionada:** N07
- **Prioridade:** Média

---

## 6. Requisitos de Qualidade

Os requisitos de qualidade foram definidos considerando as características apresentadas pela ISO/IEC 25010:2023.

O modelo apresenta nove características de qualidade:

1. Adequação funcional;
2. Eficiência de desempenho;
3. Compatibilidade;
4. Capacidade de interação;
5. Confiabilidade;
6. Segurança;
7. Manutenibilidade;
8. Flexibilidade;
9. Proteção contra riscos (Safety).

A proposta é transformar características gerais em requisitos específicos, mensuráveis ou verificáveis.

#### RQ01 — Eficiência de desempenho: tempo de resposta

O sistema deve apresentar os horários disponíveis para agendamento em até 1,5 segundo em 95% das requisições, considerando condições normais de utilização.

- **Critério de aceitação:** Em um teste de carga, pelo menos 95% das consultas de horários devem apresentar resposta em até 1,5 segundo.
- **Forma de verificação:** Teste de desempenho utilizando K6 ou JMeter.
- **Característica ISO/IEC 25010:** Eficiência de desempenho.

#### RQ02 — Eficiência de desempenho: usuários simultâneos

O sistema deve suportar pelo menos 100 usuários simultâneos, mantendo a integridade dos dados e tempo de resposta inferior a 3 segundos nas principais operações.

- **Critério de aceitação:** Durante o teste com 100 usuários simultâneos, não devem ocorrer:
  - Agendamentos duplicados;
  - Perda de dados;
  - Conflitos de informações;
  - Falhas que comprometam os dados.
- **Forma de verificação:** Teste de carga e concorrência utilizando K6 ou JMeter.
- **Característica ISO/IEC 25010:** Eficiência de desempenho.

#### RQ03 — Adequação funcional

O sistema deve disponibilizar as funções necessárias para o gerenciamento da clínica, incluindo cadastro de pacientes, gerenciamento de médicos, escalas, horários, agendamentos, cancelamentos, reagendamentos, notificações, agenda médica, prontuário, lista de espera, atendimento, indicadores e pesquisa de satisfação.

- **Critério de aceitação:** Os requisitos funcionais RF01 a RF15 devem estar implementados e atender às respectivas regras de negócio.
- **Forma de verificação:** Testes funcionais baseados nos requisitos definidos.
- **Característica ISO/IEC 25010:** Adequação funcional.

#### RQ04 — Capacidade de interação: facilidade de uso

O sistema deve permitir que um paciente sem treinamento prévio realize um agendamento em no máximo 3 etapas principais.

- **Critério de aceitação:** Em um teste de usabilidade, usuários que nunca utilizaram o sistema devem conseguir realizar um agendamento sem auxílio externo e dentro do limite estabelecido.
- **Forma de verificação:** Teste de usabilidade com usuários representativos.
- **Característica ISO/IEC 25010:** Capacidade de interação.

#### RQ05 — Capacidade de interação: clareza

O sistema deve apresentar mensagens de confirmação, erro e orientação de forma clara, permitindo que o usuário compreenda o resultado das ações realizadas.

- **Critério de aceitação:** Pelo menos 90% dos usuários avaliados devem conseguir identificar corretamente as principais ações e compreender as mensagens apresentadas durante o teste.
- **Forma de verificação:** Teste de usabilidade e avaliação das interfaces.
- **Característica ISO/IEC 25010:** Capacidade de interação.

#### RQ06 — Compatibilidade

O sistema deve funcionar corretamente nas versões mais recentes e nas duas versões anteriores dos navegadores:

- Google Chrome;
- Mozilla Firefox;
- Microsoft Edge.

As principais funcionalidades devem permanecer disponíveis nesses ambientes.

- **Critério de aceitação:** As funcionalidades de login, cadastro, consulta de horários, agendamento, cancelamento e acesso às agendas devem funcionar nos navegadores definidos.
- **Forma de verificação:** Testes de compatibilidade nos navegadores especificados.
- **Característica ISO/IEC 25010:** Compatibilidade.

#### RQ07 — Flexibilidade

O sistema deve permitir alterações de médicos, especialidades, escalas e horários de atendimento por meio das funções administrativas, sem necessidade de alteração no código-fonte para cada nova configuração.

- **Critério de aceitação:** Um usuário autorizado deve conseguir cadastrar e alterar médicos, especialidades, escalas e horários utilizando as funcionalidades administrativas.
- **Forma de verificação:** Testes funcionais das configurações administrativas.
- **Característica ISO/IEC 25010:** Flexibilidade.

#### RQ08 — Confiabilidade: disponibilidade

O sistema deve apresentar disponibilidade mínima de 99% durante o horário de funcionamento da clínica, desconsiderando manutenções previamente programadas.

- **Critério de aceitação:** O sistema deve permanecer disponível em pelo menos 99% do período de operação monitorado.
- **Forma de verificação:** Monitoramento de disponibilidade e análise dos registros de indisponibilidade.
- **Característica ISO/IEC 25010:** Confiabilidade.

#### RQ09 — Confiabilidade: integridade dos agendamentos

O sistema deve impedir que dois pacientes sejam agendados para o mesmo médico no mesmo horário, inclusive quando as solicitações ocorrerem simultaneamente.

- **Critério de aceitação:** Em testes de concorrência, somente um agendamento deve ser confirmado para uma determinada combinação de médico, data e horário.
- **Forma de verificação:** Teste de concorrência e integridade do banco de dados.
- **Característica ISO/IEC 25010:** Confiabilidade.

#### RQ10 — Segurança: controle de acesso

O sistema deve utilizar autenticação e controle de permissões para garantir que cada usuário tenha acesso somente às funcionalidades e informações permitidas para seu perfil.

- **Critério de aceitação:** Um usuário não deve conseguir acessar ou alterar informações que não estejam autorizadas para seu perfil.
- **Forma de verificação:** Testes de autenticação, autorização e tentativa de acesso indevido.
- **Característica ISO/IEC 25010:** Segurança.

#### RQ11 — Segurança: proteção dos dados

O sistema deve proteger os dados pessoais e clínicos dos pacientes utilizando mecanismos adequados de segurança e seguindo os requisitos aplicáveis da LGPD.

- **Critério de aceitação:** Dados pessoais e clínicos não devem estar disponíveis para usuários sem autorização. Os dados devem possuir mecanismos adequados de proteção durante armazenamento e transmissão.
- **Forma de verificação:** Testes de segurança, análise das permissões e verificação dos mecanismos de proteção.
- **Característica ISO/IEC 25010:** Segurança.

#### RQ12 — Manutenibilidade

O sistema deve possuir uma estrutura organizada e modular, permitindo que alterações ou correções em um módulo sejam realizadas sem causar alterações indevidas nos demais módulos.

- **Critério de aceitação:** Uma alteração em determinado módulo não deve causar falhas nas funcionalidades dos demais módulos.
- **Forma de verificação:** Testes de regressão e análise da estrutura do sistema durante as manutenções.
- **Característica ISO/IEC 25010:** Manutenibilidade.

#### RQ13 — Proteção contra riscos (Safety)

O sistema deve impedir operações que possam causar riscos operacionais no atendimento da clínica, principalmente relacionadas a agendamentos, prontuários e início das consultas.

- **Critério de aceitação:** O sistema deve impedir o início de uma consulta quando o paciente não estiver com o status Em Espera. O sistema também deve impedir alterações não autorizadas em registros clínicos.
- **Forma de verificação:** Testes funcionais e de segurança envolvendo o fluxo de atendimento e o prontuário.
- **Característica ISO/IEC 25010:** Proteção contra riscos (Safety).

#### RQ14 — Capacidade de interação: responsividade

O sistema deve adaptar sua interface para computadores e dispositivos móveis, mantendo suas principais funcionalidades disponíveis em diferentes tamanhos de tela.

- **Critério de aceitação:** As principais funções do sistema devem permanecer utilizáveis em telas com largura mínima de 360 pixels, sem sobreposição ou perda de informações essenciais.
- **Forma de verificação:** Testes em diferentes resoluções e dispositivos.
- **Característica ISO/IEC 25010:** Capacidade de interação.

#### RQ15 — Confiabilidade: recuperação de dados

O sistema deve possuir mecanismos de backup e recuperação dos dados da clínica para reduzir o risco de perda de informações em caso de falhas.

- **Critério de aceitação:** Deve ser possível restaurar os dados a partir de um backup válido após uma simulação de falha.
- **Forma de verificação:** Teste de backup e restauração.
- **Característica ISO/IEC 25010:** Confiabilidade.

---

## 7. Resumo das Características da ISO/IEC 25010:2023

| Característica | Requisitos relacionados |
|---|---|
| Adequação funcional | RQ03 |
| Eficiência de desempenho | RQ01, RQ02 |
| Compatibilidade | RQ06 |
| Capacidade de interação | RQ04, RQ05, RQ14 |
| Confiabilidade | RQ08, RQ09, RQ15 |
| Segurança | RQ10, RQ11 |
| Manutenibilidade | RQ12 |
| Flexibilidade | RQ07 |
| Proteção contra riscos (Safety) | RQ13 |

---

## 8. Restrições

#### RES01 — Prazo

O sistema deve ser desenvolvido e entregue dentro do cronograma definido para a disciplina e do semestre letivo.

- **Categoria:** Prazo
- **Prioridade:** Alta

#### RES02 — Custo

O sistema deve utilizar ferramentas e tecnologias gratuitas ou de baixo custo, considerando o orçamento limitado da clínica.

- **Categoria:** Custo
- **Prioridade:** Média

#### RES03 — LGPD

O sistema deve estar em conformidade com os requisitos aplicáveis da Lei Geral de Proteção de Dados (LGPD), considerando principalmente o tratamento de dados pessoais e dados relacionados à saúde dos pacientes.

- **Categoria:** Legal
- **Prioridade:** Alta

---

## 9. Regras de Negócio

- **RN01 — CPF:** Cada paciente ativo deve possuir um CPF válido e único no sistema.
- **RN02 — Conflito de horário:** Não é permitido realizar dois agendamentos para o mesmo médico na mesma data e horário.
- **RN03 — Usuários autorizados:** Somente usuários autenticados e autorizados podem acessar ou alterar dados clínicos dos pacientes.
- **RN04 — Horário de atendimento:** O paciente somente poderá ser agendado em horários pertencentes à escala ativa do médico.
- **RN05 — Liberação de horário:** Quando uma consulta for cancelada, o horário deve ser liberado imediatamente para novos agendamentos.
- **RN06 — Alteração de consulta:** Quando uma consulta for reagendada, o horário anterior deve ser liberado e o novo horário deve passar pelas mesmas validações de disponibilidade.
- **RN07 — Notificações:** Alterações, cancelamentos e confirmações de consultas devem gerar as notificações correspondentes aos usuários afetados.
- **RN08 — Lembretes:** O sistema deve enviar lembretes da consulta 24 horas e 2 horas antes do horário marcado, desde que a consulta não esteja cancelada.
- **RN09 — Prontuário:** O acesso às informações clínicas deve ser limitado aos usuários autorizados conforme seu perfil de acesso.
- **RN10 — Início do atendimento:** Uma consulta somente poderá ser iniciada quando o paciente estiver com o status Em Espera.

---

## 10. Matriz de Rastreabilidade

A matriz relaciona as necessidades identificadas aos requisitos que foram criados para atendê-las.

| Necessidade | Requisitos relacionados |
|---|---|
| N01 – Marcar, alterar e cancelar consultas | RF03, RF04, RF05, RF06, RF13 |
| N02 – Receber lembretes e confirmações | RF07, RF11 |
| N03 – Agenda centralizada | RF02, RF03, RF04, RF06, RF10 |
| N04 – Cadastro rápido de pacientes | RF01 |
| N05 – Histórico organizado | RF09 |
| N06 – Agenda médica sem conflitos | RF02, RF04, RF08, RF14 |
| N07 – Relatórios e indicadores | RF12, RF15 |
| N08 – Segurança dos dados | RF09, RQ10, RQ11, RES03 |

---

## 11. Matriz de Requisitos

| ID | Tipo | Descrição | Prioridade |
|---|---|---|---|
| RF01 | Funcional | Gerenciamento de pacientes | Alta |
| RF02 | Funcional | Gerenciamento de médicos e escalas | Alta |
| RF03 | Funcional | Consulta de horários disponíveis | Alta |
| RF04 | Funcional | Agendamento de consultas | Alta |
| RF05 | Funcional | Cancelamento e reagendamento | Alta |
| RF06 | Funcional | Liberação automática de horários | Alta |
| RF07 | Funcional | Lembretes automáticos | Alta |
| RF08 | Funcional | Agenda do médico | Alta |
| RF09 | Funcional | Prontuário eletrônico | Alta |
| RF10 | Funcional | Lista de espera | Média |
| RF11 | Funcional | Notificações de alterações | Alta |
| RF12 | Funcional | Dashboard e indicadores | Média |
| RF13 | Funcional | Atendimento pelo paciente | Alta |
| RF14 | Funcional | Controle do status do atendimento | Alta |
| RF15 | Funcional | Pesquisa de satisfação | Média |
| RQ01 | Qualidade | Tempo de resposta | Alta |
| RQ02 | Qualidade | Usuários simultâneos | Alta |
| RQ03 | Qualidade | Adequação funcional | Alta |
| RQ04 | Qualidade | Facilidade de uso | Alta |
| RQ05 | Qualidade | Clareza da interação | Média |
| RQ06 | Qualidade | Compatibilidade | Média |
| RQ07 | Qualidade | Flexibilidade | Média |
| RQ08 | Qualidade | Disponibilidade | Alta |
| RQ09 | Qualidade | Integridade dos agendamentos | Alta |
| RQ10 | Qualidade | Controle de acesso | Alta |
| RQ11 | Qualidade | Proteção dos dados | Alta |
| RQ12 | Qualidade | Manutenibilidade | Média |
| RQ13 | Qualidade | Proteção contra riscos | Alta |
| RQ14 | Qualidade | Responsividade | Média |
| RQ15 | Qualidade | Recuperação de dados | Alta |
| RES01 | Restrição | Prazo do projeto | Alta |
| RES02 | Restrição | Tecnologias gratuitas ou de baixo custo | Média |
| RES03 | Restrição | Conformidade com a LGPD | Alta |

---

## 12. Critérios de Aceitação

| Requisito | Critério de aceitação | Forma de teste |
|---|---|---|
| RQ01 | 95% das consultas respondem em até 1,5s | Teste de desempenho |
| RQ02 | 100 usuários simultâneos sem perda ou conflito de dados | Teste de carga |
| RQ03 | RF01–RF15 implementados corretamente | Testes funcionais |
| RQ04 | Agendamento realizado em até 3 etapas | Teste de usabilidade |
| RQ05 | 90% dos usuários compreendem as principais mensagens | Teste de usabilidade |
| RQ06 | Sistema funciona nos navegadores definidos | Teste de compatibilidade |
| RQ07 | Configurações podem ser alteradas sem modificar código | Teste funcional |
| RQ08 | Disponibilidade mínima de 99% | Monitoramento |
| RQ09 | Nenhum agendamento duplicado em testes simultâneos | Teste de concorrência |
| RQ10 | Usuários acessam somente recursos autorizados | Teste de segurança |
| RQ11 | Dados protegidos contra acesso não autorizado | Teste de segurança |
| RQ12 | Alterações isoladas não causam falhas nos outros módulos | Teste de regressão |
| RQ13 | Operações de risco são bloqueadas | Teste funcional |
| RQ14 | Sistema utilizável a partir de 360px | Teste responsivo |
| RQ15 | Backup pode ser restaurado após falha simulada | Teste de recuperação |

---

## 13. Revisão de Ambiguidade

Durante a elaboração dos requisitos, devem ser evitados termos vagos como:

- Rápido;
- Fácil;
- Moderno;
- Seguro;
- Adequado;
- Robusto;
- Muitos;
- Poucos;
- Quando possível;
- Se necessário.

Sempre que possível, esses termos devem ser substituídos por valores, condições ou critérios que possam ser verificados.

### Exemplos

**Requisito vago**
O sistema deve ser rápido.

**Requisito verificável**
O sistema deve apresentar os horários disponíveis em até 1,5 segundo para 95% das requisições.

**Requisito vago**
O sistema deve ser fácil de usar.

**Requisito verificável**
Um paciente sem treinamento prévio deve conseguir realizar um agendamento em no máximo 3 etapas principais.

**Requisito vago**
O sistema deve ser seguro.

**Requisito verificável**
O sistema deve utilizar autenticação e controle de permissões para restringir o acesso às informações de acordo com o perfil do usuário.

---

## 14. Fluxo Principal de Agendamento

```text
Início
  |
  v
Paciente acessa o sistema
  |
  v
Seleciona especialidade
  |
  v
Seleciona médico
  |
  v
Seleciona data
  |
  v
Sistema consulta horários disponíveis
  |
  v
Paciente seleciona horário
  |
  v
Sistema valida disponibilidade novamente
  |
  +------ Horário indisponível ------> Selecionar outro horário
  |
  v
Confirmação do agendamento
  |
  v
Status = Agendado
  |
  v
Sistema envia confirmação
  |
  v
Fim
```

---

## 15. Fluxo de Atendimento

```text
Agendado
    |
    v
Confirmado
    |
    v
Em Espera
    |
    v
Em Atendimento
    |
    v
Atendido
```

Caso o paciente cancele:

```text
Agendado / Confirmado
          |
          v
      Cancelado
```

A consulta não deve ser iniciada enquanto o paciente não estiver no status Em Espera.

---

## 16. Fluxo de Cancelamento

```text
Paciente solicita cancelamento
          |
          v
Sistema verifica regra de antecedência
          |
     +----+----+
     |         |
   Permitido  Não permitido
     |         |
     v         v
Cancelamento  Exibe mensagem
     |
     v
Status = Cancelado
     |
     v
Horário liberado
     |
     v
Lista de espera é consultada
     |
     v
Paciente compatível pode ser notificado
```

---

## 17. Arquitetura Conceitual dos Módulos

```text
                    SISTEMA CLÍNICA + SAÚDE
                              |
       -------------------------------------------------
       |                 |               |             |
   Pacientes          Agenda         Atendimento    Relatórios
       |                 |               |             |
       |                 |               |             |
   Cadastro          Médicos          Status       Indicadores
   Histórico         Escalas          Consulta      Ocupação
   Contatos          Horários          Prontuário   Cancelamentos
       |
       -------------------------------------------------
                              |
                         Notificações
                              |
                    ---------------------
                    |         |          |
                  E-mail     SMS      WhatsApp
```

---

## 18. Segurança e LGPD

O sistema trabalha com dados pessoais e informações relacionadas à saúde dos pacientes.

Por isso, o projeto considera como pontos importantes:

- Controle de acesso;
- Autenticação;
- Permissões por perfil;
- Proteção dos dados;
- Restrição de acesso ao prontuário;
- Preservação do histórico;
- Proteção das credenciais;
- Registro de operações importantes;
- Backup;
- Recuperação dos dados.

O acesso às informações clínicas deve ser limitado aos usuários autorizados.

---

## 19. Perfis de Acesso

| Perfil | Principais permissões |
|---|---|
| Paciente | Consultar e gerenciar suas próprias consultas |
| Recepcionista | Cadastrar pacientes e gerenciar consultas |
| Médico | Consultar agenda e informações clínicas autorizadas |
| Administrador | Gerenciar usuários, configurações e indicadores |
| TI | Administrar aspectos técnicos e de segurança |

---

## 20. Análise de Conflitos de Qualidade

As características de qualidade podem influenciar umas às outras.

**Segurança x Desempenho**
A utilização de mecanismos adicionais de autenticação, criptografia e validação pode aumentar o processamento de algumas operações.
Por isso, é necessário garantir que os mecanismos de segurança sejam implementados sem comprometer os limites de desempenho definidos nos requisitos.

**Segurança x Capacidade de interação**
Quanto mais etapas forem adicionadas para proteger uma conta, maior pode ser a dificuldade para o usuário realizar determinadas operações.
Por isso, o sistema deve buscar equilíbrio entre proteção das informações e facilidade de utilização.

**Flexibilidade x Manutenibilidade**
Um sistema muito flexível pode exigir uma estrutura mais complexa.
É necessário organizar os módulos para que novas configurações possam ser adicionadas sem tornar o sistema difícil de compreender ou modificar.

**Confiabilidade x Custo**
Mecanismos de backup, recuperação e disponibilidade podem aumentar os custos de infraestrutura.
Como o projeto possui uma restrição de custo, esses mecanismos devem ser definidos considerando a realidade da clínica.

---

## 21. Objetivos do Sistema

O sistema possui como principais objetivos:

1. Centralizar as informações da clínica;
2. Reduzir conflitos de horários;
3. Facilitar o agendamento de consultas;
4. Reduzir tarefas manuais;
5. Melhorar a comunicação com os pacientes;
6. Organizar as informações dos pacientes;
7. Melhorar o controle das agendas;
8. Aumentar a segurança dos dados;
9. Permitir acompanhamento dos indicadores da clínica;
10. Melhorar a experiência do paciente e dos profissionais.

---

## 22. Relação entre Problema, Necessidade e Requisito

A construção dos requisitos foi realizada buscando manter a rastreabilidade entre o problema identificado, a necessidade do stakeholder e a solução definida como requisito.

### Exemplo 1 — Conflitos de horários

**Problema:** Conflitos de horários.

**Necessidade:** N06 – Médico precisa gerenciar sua agenda sem conflitos.

**Requisitos relacionados:**

- RF02;
- RF03;
- RF04;
- RF06;
- RF08;
- RF14;
- RQ09.

### Exemplo 2 — Cancelamento de consultas

**Problema:** Esquecimento e cancelamento de consultas.

**Necessidade:** N02 – Paciente precisa receber lembretes e confirmações.

**Requisitos relacionados:**

- RF07;
- RF11.

### Exemplo 3 — Dados desorganizados

**Problema:** Dados desorganizados e duplicados.

**Necessidade:** N04 – Recepcionista precisa cadastrar e consultar pacientes rapidamente.

**Requisito relacionado:**

- RF01.

### Exemplo 4 — Segurança

**Problema:** Risco de acesso indevido aos dados dos pacientes.

**Necessidade:** N08 – Equipe de TI precisa garantir a segurança dos dados.

**Requisitos relacionados:**

- RF09;
- RQ10;
- RQ11;
- RES03.

---

## 23. Checklist de Qualidade dos Requisitos

| Pergunta | Resultado |
|---|---|
| O requisito está completo? | Sim |
| O requisito possui uma ação clara? | Sim |
| O requisito está relacionado a uma necessidade? | Sim |
| O requisito possui stakeholder identificado? | Sim |
| O requisito é necessário para o projeto? | Sim |
| O requisito é viável dentro das restrições? | Sim |
| O requisito possui prioridade? | Sim |
| O requisito pode ser testado ou verificado? | Sim |
| Os requisitos de qualidade possuem critérios objetivos? | Sim |
| As características da ISO/IEC 25010 foram consideradas? | Sim |
| Os requisitos evitam termos vagos sempre que possível? | Sim |
| Existe rastreabilidade entre necessidades e requisitos? | Sim |

---

## 24. Conclusão

O projeto Clínica + Saúde foi desenvolvido a partir dos problemas identificados no processo atual da clínica e das necessidades dos seus principais stakeholders.

Os requisitos funcionais definem as principais funções que o sistema deve oferecer, enquanto os requisitos de qualidade estabelecem condições relacionadas ao desempenho, interação, segurança, confiabilidade, compatibilidade, manutenção, flexibilidade e proteção contra riscos.

A utilização da ISO/IEC 25010:2023 ajudou a estruturar os requisitos de qualidade de forma mais objetiva. Em vez de utilizar apenas termos como "rápido", "seguro" ou "fácil", os requisitos foram associados a métricas, condições, critérios de aceitação e formas de verificação.

Dessa forma, o projeto considera que um sistema de qualidade não precisa apenas executar suas funções corretamente. Ele também precisa apresentar características adequadas para os usuários, para o negócio e para os riscos envolvidos no contexto da clínica.

