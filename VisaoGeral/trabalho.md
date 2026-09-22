# Atividade — 18/08/2026
# Sistema de Gestão para Clínica Médica — Escopo do MVP

Este documento descreve o escopo da **primeira versão (MVP)** do sistema. Os requisitos, regras e indicadores estão numerados em sequência dentro do escopo do MVP. As funcionalidades que não são bloqueantes para o lançamento estão documentadas em seções separadas de **backlog**, com a justificativa da decisão (Seções 6.1, 8.1 e 11).

---

#alunos
Thiago Braziellas,Arthur Santos,Luiz Claudio, Pedro Ryan
## 1. Stakeholders

Os stakeholders são as pessoas ou grupos que utilizam o sistema, participam do processo ou são afetados diretamente pelas mudanças que ele vai trazer para a clínica.

Neste projeto, foram identificados os seguintes stakeholders:

* **Paciente:** é o principal beneficiado pelo sistema. Deve conseguir realizar e acompanhar agendamentos, receber lembretes e ser informado quando houver alguma alteração em sua consulta.
* **Recepcionista:** utiliza o sistema no dia a dia para cadastrar pacientes, consultar horários, realizar agendamentos, cancelar consultas e controlar a chegada dos pacientes.
* **Médico:** utiliza o sistema para acompanhar sua agenda, consultar os pacientes agendados, organizar sua disponibilidade e registrar informações relacionadas ao atendimento.
* **Gerente da clínica:** acompanha o funcionamento da operação e utiliza os indicadores para identificar problemas e oportunidades de melhoria.
* **Equipe de TI:** é responsável pela manutenção, segurança, disponibilidade e evolução técnica do sistema.
* **Direção da clínica:** possui interesse nos resultados gerais do sistema, principalmente na redução de custos, melhora da organização e qualidade do atendimento.

Cada stakeholder possui necessidades diferentes. Por isso, o sistema deve considerar tanto as necessidades dos usuários que trabalham diretamente com a clínica quanto as necessidades dos gestores responsáveis por acompanhar os resultados.

---

## 2. Problemas de Negócio

Antes de definir as funcionalidades do sistema, foi necessário identificar os principais problemas enfrentados pela clínica.

### 2.1 Conflitos de horários

Um dos principais problemas é a possibilidade de ocorrerem conflitos de horários. Como as informações podem estar distribuídas em planilhas ou sistemas diferentes, um mesmo horário pode aparecer como disponível para mais de uma pessoa.

Isso pode causar:

* Dupla marcação de consultas;
* Sobrecarga do médico;
* Confusão na recepção;
* Necessidade de remarcar consultas;
* Insatisfação dos pacientes.

---

### 2.2 Retrabalho

Outro problema identificado é o retrabalho. Algumas informações precisam ser procuradas ou preenchidas novamente porque não estão centralizadas.

Por exemplo, um paciente que já possui cadastro pode precisar informar novamente seus dados básicos quando realiza uma nova consulta.

Isso aumenta:

* O tempo de atendimento;
* O trabalho da recepção;
* A possibilidade de erro;
* A insatisfação do paciente.

---

### 2.3 Duplicidade de informações

Sem um banco de dados centralizado e sem validações adequadas, existe a possibilidade de o mesmo paciente possuir mais de um cadastro.

Essa duplicidade pode gerar informações diferentes para uma mesma pessoa e dificultar a consulta do histórico correto.

---

### 2.4 Dificuldade para atualizar dados

Quando as informações estão distribuídas entre várias planilhas ou programas, uma alteração feita em um local pode não aparecer nos demais.

Isso faz com que diferentes usuários trabalhem com dados desatualizados.

---

### 2.5 Falhas na comunicação com os pacientes

A clínica também enfrenta dificuldades na comunicação com os pacientes.

Sem lembretes automáticos, o paciente pode esquecer a data ou o horário da consulta. Da mesma forma, quando ocorre uma alteração na agenda médica, pode ser difícil avisar todos os pacientes envolvidos.

*No MVP, a comunicação será feita manualmente pela recepção. A automação está no backlog (Seção 6.1).*

---

### 2.6 Dificuldade para controlar cancelamentos

Quando uma consulta é cancelada, o horário pode ficar vazio até o final do dia.

Sem uma fila de espera ou algum processo de reocupação, a clínica perde a oportunidade de utilizar aquele horário para atender outro paciente.

*O MVP já libera o horário automaticamente (RF06). A fila de espera automatizada está no backlog (Seção 6.1).*

---

## 3. Principais Causas dos Problemas

Os problemas identificados possuem relação principalmente com a forma como as informações são armazenadas e utilizadas.

As principais causas são:

* Utilização de planilhas individuais sem sincronização;
* Ausência de um banco de dados centralizado;
* Utilização de diferentes softwares para processos relacionados;
* Falta de atualização em tempo real da agenda;
* Ausência de lembretes automáticos;
* Falta de uma fila de espera organizada;
* Dependência de processos manuais;
* Falta de integração entre os envolvidos no processo.

A principal proposta do sistema é justamente centralizar essas informações e permitir que todos trabalhem com uma base única e atualizada.

---

## 4. Regras de Negócio

As regras de negócio representam condições que devem ser respeitadas durante o funcionamento do sistema.

### 4.1 Regras de Negócio do MVP

---

### RN01 — CPF válido e único

O cadastro de um paciente deve possuir um CPF válido.

O mesmo CPF não deve ser utilizado em mais de um cadastro ativo.

**Classificação:** Estudo de Caso — Duplicidade de informações.

---

### RN02 — Um paciente por horário

Um médico não deve possuir mais de um paciente agendado para o mesmo horário.

O sistema deve verificar a disponibilidade antes de concluir o agendamento.

**Classificação:** Estudo de Caso — Conflito de horários.

---

### RN03 — Agendamento dentro da escala

Os agendamentos devem ser realizados apenas nos horários que estiverem cadastrados como disponíveis na escala do médico.

Um paciente não deve ser agendado fora da disponibilidade cadastrada.

**Classificação:** Processo de Negócio.

---

### RN04 — Liberação após cancelamento

Quando uma consulta for cancelada, o horário deve ficar disponível novamente.

O horário não deve continuar aparecendo como ocupado após o cancelamento.

**Classificação:** Estudo de Caso — Cancelamentos.

---

### RN05 — Reutilização de dados

Quando o paciente já possuir um cadastro válido, seus dados básicos devem ser reutilizados nos próximos agendamentos.

O paciente não deve precisar informar novamente informações que já estejam cadastradas e atualizadas.

**Classificação:** Estudo de Caso — Retrabalho.

---

### RN06 — Início do atendimento

O atendimento deve seguir o fluxo definido pela clínica.

A consulta deve ser iniciada quando o paciente estiver identificado e com o status adequado para atendimento.

**Classificação:** Operacional da clínica.

---

### RN07 — Controle de acesso a dados restritos

Informações protegidas do paciente devem ser acessadas apenas por usuários autorizados.

Usuários sem permissão não devem visualizar ou alterar informações restritas.

**Classificação:** Segurança e privacidade (LGPD).

---

### 4.2 Regras de Negócio para Fases Futuras

| Código | Regra | Ligada a (backlog) |
|---|---|---|
| RN-F01 | Quando uma alteração na escala médica afetar pacientes já agendados, o sistema deve identificá-los e notificá-los. | RF-B05 — Avisos sobre Alterações na Agenda |
| RN-F02 | Os pacientes devem receber lembretes automáticos com 24h e 2h de antecedência. | RF-B01 — Lembretes Automáticos |
| RN-F03 | Se o paciente não confirmar a consulta no prazo, o horário pode ser priorizado para reocupação. | RF-B04 — Fila de Espera |
| RN-F04 | O prontuário eletrônico deve controlar acesso conforme perfil médico. | RF-B03 — Prontuário Eletrônico |

---

## 5. Melhorias Propostas

| Problema                   | Melhoria                                                       |
| --------------------------- | ---------------------------------------------------------------- |
| Conflitos de horários      | Implantação de uma agenda unificada e atualizada em tempo real |
| Retrabalho                 | Centralização das informações dos pacientes                    |
| Duplicidade de dados       | Validação de CPF único no cadastro                             |
| Dificuldade de atualização | Utilização de um banco de dados centralizado                   |
| Falhas na comunicação      | Envio automático de lembretes e notificações *(backlog)*        |
| Cancelamentos              | Liberação automática do horário *(MVP)* + fila de espera *(backlog)* |
| Falta de acompanhamento    | Indicadores acompanhados via relatório simples no MVP; dashboard completo fica no backlog |

A ideia principal é que as melhorias estejam diretamente relacionadas aos problemas encontrados. As melhorias marcadas como *backlog* não bloqueiam o lançamento — a causa raiz de cada problema já é endereçada no MVP; elas apenas tornam a solução mais completa.

---

## 6. Requisitos Funcionais do MVP

Os requisitos funcionais descrevem as ações que o sistema deve realizar.

Para manter os requisitos claros, foram utilizadas principalmente duas formas de escrita:

* **O sistema deve...** para definir o que é obrigatório;
* **O sistema não deve...** para definir o que não pode acontecer.

---

### RF01 — Gerenciamento de Pacientes

**Prioridade: MVP (Must)**

O sistema deve permitir cadastrar pacientes.

O sistema deve permitir consultar os dados cadastrados.

O sistema deve permitir atualizar informações do paciente.

O sistema deve permitir inativar um cadastro sem apagar o histórico já registrado.

O cadastro deve possuir, no mínimo, informações básicas para identificar e entrar em contato com o paciente.

O sistema deve validar o CPF informado.

O sistema não deve permitir dois pacientes ativos cadastrados com o mesmo CPF.

O sistema não deve apagar automaticamente o histórico do paciente quando seu cadastro for inativado.

---

### RF02 — Gerenciamento de Médicos e Escalas

**Prioridade: MVP (Must)**

O sistema deve permitir cadastrar médicos.

O sistema deve permitir registrar as especialidades dos médicos.

O sistema deve permitir cadastrar a escala e os horários de atendimento.

O sistema deve permitir atualizar a disponibilidade do médico.

O sistema deve permitir consultar os horários cadastrados.

O sistema não deve disponibilizar para agendamento um horário que esteja fora da escala ou bloqueado.

---

### RF03 — Consulta de Horários Disponíveis

**Prioridade: MVP (Must)**

O sistema deve permitir consultar os horários disponíveis para agendamento.

A consulta deve considerar o médico selecionado.

A consulta deve considerar a data escolhida.

O sistema deve considerar a escala cadastrada para o profissional.

O sistema deve atualizar os horários disponíveis sempre que ocorrer um novo agendamento, cancelamento ou bloqueio.

O sistema não deve apresentar como disponível um horário que já esteja ocupado ou bloqueado.

---

### RF04 — Agendamento de Consultas

**Prioridade: MVP (Must)**

O sistema deve permitir realizar o agendamento de consultas.

Cada agendamento deve estar relacionado a um paciente, um médico, uma data e um horário.

O sistema deve verificar se o horário continua disponível antes de confirmar o agendamento.

O sistema deve impedir conflitos de horários.

O sistema não deve permitir dois agendamentos para o mesmo médico no mesmo horário.

Ao criar um novo agendamento, o sistema deve registrar inicialmente o status **"Agendado"**.

O sistema deve registrar a data e o horário em que o agendamento foi criado.

---

### RF05 — Cancelamento e Reagendamento

**Prioridade: MVP (Must)**

O sistema deve permitir cancelar uma consulta.

O sistema deve registrar o cancelamento no histórico do agendamento.

O sistema deve alterar o status da consulta para **"Cancelado"**.

O sistema deve permitir reagendar uma consulta para outro horário disponível.

Antes de confirmar o reagendamento, o sistema deve verificar a disponibilidade do novo horário.

O sistema não deve manter dois horários ativos para a mesma consulta depois que o reagendamento for concluído.

---

### RF06 — Liberação Automática de Horários

**Prioridade: MVP (Must)**

Quando uma consulta for cancelada, o sistema deve liberar o horário automaticamente.

O sistema deve atualizar a agenda após o cancelamento.

O horário liberado deve ficar disponível para novos agendamentos.

O sistema não deve manter como ocupado um horário pertencente a uma consulta cancelada.

---

### RF07 — Controle do Status do Atendimento

**Prioridade: MVP (Must)**

O sistema deve controlar os seguintes status:

* **Agendado**;
* **Confirmado**;
* **Em Espera**;
* **Atendido**;
* **Cancelado**.

O sistema deve permitir atualizar o status conforme o andamento do atendimento.

Quando o paciente chegar à clínica, a recepção deve poder alterar seu status para **"Em Espera"**.

O sistema deve registrar as alterações importantes de status.

O sistema não deve permitir que uma consulta cancelada seja iniciada como atendimento.

---

### 6.1 Backlog Funcional (fora do escopo do MVP)

Itens que não bloqueiam o lançamento. A justificativa completa está na Seção 11.1.

| Código | Requisito | MoSCoW | Resumo |
|---|---|---|---|
| RF-B01 | Lembretes Automáticos | S | Envio automático de lembretes 24h/2h antes via WhatsApp/SMS |
| RF-B02 | Gerenciamento da Agenda pelo Médico | S | Médico consulta/bloqueia sua própria agenda |
| RF-B03 | Prontuário Eletrônico | S | Registro de informações clínicas por consulta |
| RF-B04 | Fila de Espera | S | Reaproveitamento automático de horários cancelados |
| RF-B05 | Avisos sobre Alterações na Agenda | S | Notificação de pacientes afetados por mudança de escala |
| RF-B06 | Dashboard de Indicadores | C | Painel gerencial visual da operação |
| RF-B07 | Autoatendimento | C | Portal web/chatbot para o paciente agendar sozinho |
| RF-B08 | Pesquisa de Satisfação | W | Coleta de feedback pós-atendimento |

---

## 7. Resumo dos Requisitos Funcionais do MVP

| Código | Requisito                           | Prioridade   |
| ------ | ------------------------------------ | ------------ |
| RF01   | Gerenciamento de Pacientes          | MVP (Must)   |
| RF02   | Gerenciamento de Médicos e Escalas  | MVP (Must)   |
| RF03   | Consulta de Horários Disponíveis    | MVP (Must)   |
| RF04   | Agendamento de Consultas            | MVP (Must)   |
| RF05   | Cancelamento e Reagendamento        | MVP (Must)   |
| RF06   | Liberação Automática de Horários    | MVP (Must)   |
| RF07   | Controle do Status do Atendimento   | MVP (Must)   |

*O backlog funcional (RF-B01 a RF-B08) está resumido na Seção 6.1 e priorizado na Seção 11.1.*

---

## 8. Requisitos Não Funcionais do MVP

Os requisitos não funcionais definem características relacionadas à qualidade do sistema, com base nas 9 características da ISO/IEC 25010:2023.

---

### RNF01 — Desempenho da Busca

**Característica ISO/IEC 25010: Eficiência de desempenho**

O sistema deve apresentar os resultados da busca por horários disponíveis em até 2 segundos, para 95% das requisições, considerando até 500 usuários simultâneos.

---

### RNF02 — Segurança da Comunicação

**Característica ISO/IEC 25010: Segurança**

Os dados transmitidos entre o usuário e o sistema devem utilizar uma conexão segura.

O sistema deve utilizar HTTPS/TLS para a comunicação entre a aplicação e seus usuários.

O sistema não deve transmitir informações sensíveis por conexões não seguras.

---

### RNF03 — Disponibilidade

**Característica ISO/IEC 25010: Confiabilidade**

O sistema deve manter uma disponibilidade mínima de 99,5% ao mês.

A disponibilidade deve ser monitorada para permitir o acompanhamento do indicador de uptime.

---

### RNF04 — Backup

**Característica ISO/IEC 25010: Confiabilidade**

O sistema deve realizar backups automatizados do banco de dados diariamente.

Deve existir um processo que permita recuperar os dados quando necessário.

---

### RNF05 — Controle de Acesso e Proteção de Dados

**Característica ISO/IEC 25010: Segurança**

O tratamento dos dados pessoais deve respeitar as regras aplicáveis de proteção de dados (LGPD).

O acesso às informações deve ser controlado de acordo com as permissões de cada usuário.

---

### 8.1 Backlog Não Funcional (fora do escopo do MVP)

| Código | Requisito | Característica ISO/IEC 25010 | MoSCoW | Resumo |
|---|---|---|---|---|
| RNF-B01 | Facilidade de Agendamento | Capacidade de Interação | S | Concluir agendamento em até 3 ações principais |
| RNF-B02 | Acessos Simultâneos | Eficiência de desempenho | S | Suportar 50 acessos simultâneos |
| RNF-B03 | Autenticação em Duas Etapas | Segurança | S | 2FA para médicos e gerentes |
| RNF-B04 | Compatibilidade | Compatibilidade | S | Suporte a Chrome, Firefox, Edge e Safari |
| RNF-B05 | Responsividade | Capacidade de Interação | S | Adaptação a diferentes tamanhos de tela |

---

### 8.2 Tabela Consolidada de Requisitos Não Funcionais do MVP

| Código | Requisito (resumo mensurável) | Característica ISO/IEC 25010:2023 | Prioridade (MoSCoW) | Critério de Aceitação / Verificação |
|---|---|---|---|---|
| RNF01 | Busca de horários responde em até 2s | Eficiência de desempenho | M | ≤2s para 95% das requisições, com até 500 usuários — testado por teste de carga |
| RNF02 | Comunicação via HTTPS/TLS | Segurança | M | 100% das rotas com TLS ativo — verificado por scanner de vulnerabilidade |
| RNF03 | Disponibilidade mínima de 99,5%/mês | Confiabilidade | M | Uptime medido por monitoramento contínuo (status page/logs) |
| RNF04 | Backup diário automatizado | Confiabilidade | M | Restauração testada periodicamente por simulação de recuperação |
| RNF05 | Controle de acesso a dados sensíveis | Segurança | M | Tentativa de acesso não autorizado deve falhar — testado por controle de acesso |

---

## 9. Requisitos de Qualidade (Estudo de Caso) — MVP

### 9.1 Do Conceito ao Requisito Mensurável (vago vs. mensurável)

Antes de aplicar o modelo, vale mostrar a diferença entre um requisito vago e a versão mensurável usada no projeto:

| Característica | Inadequado (vago) | Melhorado (mensurável — usado no projeto) |
|---|---|---|
| Eficiência de desempenho | "O sistema deve ser rápido para buscar horários." | RNF01: "O sistema deverá retornar os horários disponíveis em até 2 segundos, para 95% das requisições, considerando até 500 usuários simultâneos." |
| Segurança | "O sistema deve ser seguro." | RNF02: "O sistema deverá utilizar HTTPS/TLS em toda a comunicação entre cliente e servidor." |
| Confiabilidade | "O sistema deve estar sempre disponível." | RNF03: "O sistema deverá manter disponibilidade mínima de 99,5% ao mês, monitorada continuamente." |

### 9.2 Aplicação ao Projeto

Seguindo o modelo trabalhado em aula (identificar característica → justificar → formular requisito → definir critério de aceitação → indicar como testar), aplicado às situações do MVP:

| Nº | Situação / Problema | Característica ISO/IEC 25010 | Justificativa | Requisito Formulado | Critério de Aceitação | Como Testar |
|---|---|---|---|---|---|---|
| 1 | Busca de horários lenta prejudica o atendimento na recepção | Eficiência de desempenho | O tempo de resposta afeta diretamente o fluxo de atendimento e a adoção do sistema pela equipe | O sistema deverá retornar os horários disponíveis em até 2 segundos, para 95% das requisições, considerando até 500 usuários simultâneos | 95% das buscas respondem em ≤2s sob carga de até 500 usuários simultâneos | Teste de carga (ex.: k6/JMeter) simulando 500 usuários, medindo o percentil 95 do tempo de resposta |
| 2 | Dados de pacientes trafegando sem proteção entre app e servidor | Segurança | Dados de saúde são sensíveis e protegidos por lei (LGPD); vazamento gera risco legal e de confiança | O sistema deverá criptografar toda a comunicação entre cliente e servidor utilizando TLS 1.2 ou superior | 100% das rotas usando HTTPS; nenhuma rota aceita conexão HTTP não criptografada | Varredura de segurança (ex.: OWASP ZAP) e verificação de certificado válido em todas as rotas |
| 3 | Sistema indisponível impede o atendimento aos pacientes | Confiabilidade | Em saúde, indisponibilidade impede diretamente o atendimento; risco operacional alto | O sistema deverá manter disponibilidade mínima de 99,5% ao mês, monitorada continuamente | Uptime mensal ≥99,5%, medido por ferramenta de monitoramento | Acompanhamento contínuo (ex.: status page/logs) com relatório mensal de uptime |
| 4 | Perda de dados de pacientes em caso de falha do sistema | Confiabilidade | Perda de histórico clínico é inaceitável no domínio de saúde | O sistema deverá realizar backup diário automatizado do banco de dados, com restauração testada mensalmente | Backup executado diariamente sem falha; restauração completa validada em teste mensal | Simulação de restauração de backup em ambiente de teste, validando integridade dos dados |
| 5 | Usuário sem permissão acessa dados restritos de outro paciente | Segurança | Risco de exposição de dados protegidos pela legislação (LGPD) | O sistema não deverá permitir que usuários sem autorização visualizem ou alterem informações restritas de outros perfis | Tentativa de acesso não autorizado é bloqueada e registrada em log | Teste de controle de acesso tentando abrir dados com um perfil sem permissão |

*As situações relacionadas a itens do backlog poderão ser formalizadas neste mesmo formato quando essas funcionalidades forem priorizadas.*

---

## 10. Indicadores para Acompanhar o MVP

Os indicadores permitem acompanhar se o sistema está realmente ajudando a resolver os problemas identificados no início do projeto, mesmo sem as automações do backlog.

---

### 10.1 Taxa de No-Show

Representa o percentual de pacientes que não comparecem à consulta sem realizar o cancelamento.

Serve como linha de base para comparação futura, quando os lembretes automáticos forem implementados.

**Fórmula:**

> Taxa de No-Show = (Quantidade de faltas / Total de consultas agendadas) × 100

---

### 10.2 Taxa de Ocupação da Agenda

Mostra a quantidade de horários preenchidos em relação ao total de horários disponíveis.

Esse indicador permite avaliar se a capacidade de atendimento da clínica está sendo bem aproveitada.

**Fórmula:**

> Taxa de Ocupação = (Horários ocupados / Total de horários disponíveis) × 100

---

### 10.3 Tempo Médio de Atendimento na Recepção

Mede o tempo necessário para realizar o processo inicial do paciente na recepção.

Pode envolver a identificação do paciente, consulta do agendamento e alteração do status para **"Em Espera"**.

---

### 10.4 Tempo Médio de Espera do Paciente

Mede o tempo que o paciente permanece aguardando depois de ser registrado como **"Em Espera"** até o início do atendimento.

Esse indicador está diretamente relacionado à experiência do paciente.

---

### 10.5 Índice de Retrabalho no Cadastro

Acompanha situações em que os dados precisam ser cadastrados novamente ou corrigidos.

O objetivo é verificar se a centralização das informações está reduzindo o trabalho repetitivo.

---

### 10.6 Índice de Disponibilidade

Mostra o percentual de tempo em que o sistema permaneceu disponível.

Esse indicador permite acompanhar a meta de disponibilidade definida no RNF03.

---

### 10.7 Tempo de Resposta de Busca

Mede o tempo necessário para o sistema retornar os horários disponíveis.

O objetivo é verificar se o sistema está cumprindo a meta de resposta definida no RNF01.

---

## 11. Priorização MoSCoW (Escopo do MVP e Backlog)

A priorização foi feita considerando principalmente se o sistema consegue ser lançado e resolver o problema central do negócio sem cada requisito. Cada item recebeu uma letra (**M**ust, **S**hould, **C**ould, **W**on't) e uma justificativa própria.

### 11.1 Requisitos Funcionais

| Código | Requisito | MoSCoW | Justificativa |
|---|---|---|---|
| RF01 | Gerenciamento de Pacientes | **M** | Sem cadastro não existe agendamento nem histórico — é a base de todo o sistema |
| RF02 | Gerenciamento de Médicos e Escalas | **M** | Sem escala cadastrada não há horários a oferecer; pré-requisito de RF03/RF04 |
| RF03 | Consulta de Horários Disponíveis | **M** | É o passo que viabiliza o agendamento; sem ele o paciente não sabe o que reservar |
| RF04 | Agendamento de Consultas | **M** | Funcionalidade central; resolve o problema principal do projeto (conflitos de horário) |
| RF05 | Cancelamento e Reagendamento | **M** | Operação básica esperada em qualquer sistema de agenda; sem ela o uso real trava |
| RF06 | Liberação Automática de Horários | **M** | Consequência direta do cancelamento; sem ela horários cancelados ficam presos |
| RF07 | Controle do Status do Atendimento | **M** | Sem controle de status a recepção não sabe quem chegou/foi atendido — essencial no dia a dia |
| RF-B01 | Lembretes Automáticos | **S** | Reduz faltas, mas a clínica opera (pior) sem isso no lançamento; pode ser manual no início |
| RF-B02 | Gerenciamento da Agenda pelo Médico | **S** | Importante para autonomia do médico, mas a recepção pode cobrir isso no MVP |
| RF-B03 | Prontuário Eletrônico | **S** | Relevante para continuidade do cuidado, mas não bloqueia o núcleo do problema (agenda) |
| RF-B04 | Fila de Espera | **S** | Melhora ocupação, mas o sistema funciona sem ela — só perde eficiência |
| RF-B05 | Avisos sobre Alterações na Agenda | **S** | Pode ser feito manualmente pela recepção como paliativo inicial |
| RF-B06 | Dashboard de Indicadores | **C** | Não afeta a operação do agendamento; pode vir depois, inclusive com dados retroativos |
| RF-B07 | Autoatendimento | **C** | Amplia o canal de acesso, mas a recepção já cobre o fluxo essencial |
| RF-B08 | Pesquisa de Satisfação | **W** | Não afeta a operação nem resolve os problemas de negócio levantados nesta versão |

### 11.2 Requisitos Não Funcionais

| Código | Requisito | MoSCoW | Justificativa |
|---|---|---|---|
| RNF01 | Desempenho da busca (≤2s) | **M** | Se a busca travar, o fluxo crítico de agendamento inteiro trava |
| RNF02 | HTTPS/TLS | **M** | Trafegar dados de paciente sem criptografia viola exigência legal mínima (LGPD) |
| RNF03 | Disponibilidade 99,5% | **M** | Indisponibilidade impede o uso do sistema num serviço de saúde — risco alto |
| RNF04 | Backup diário | **M** | Perda de dados de pacientes é risco inaceitável no domínio de saúde |
| RNF05 | Controle de acesso a dados sensíveis | **M** | Ligado à RN07 e à legislação de proteção de dados — não é negociável |
| RNF-B01 | Facilidade de agendamento | **S** | Melhora a experiência, mas o sistema funciona mesmo com mais etapas que o ideal |
| RNF-B02 | 50 acessos simultâneos | **S** | Importante para escalar, mas o volume inicial da clínica provavelmente não exige isso já no lançamento |
| RNF-B03 | 2FA (médicos/gerentes) | **S** | Reforça segurança, mas pode entrar numa segunda fase sem inviabilizar o uso |
| RNF-B04 | Compatibilidade multi-navegador | **S** | Importante para alcance, mas não bloqueia lançar com 1-2 navegadores prioritários |
| RNF-B05 | Responsividade | **S** | Melhora o acesso mobile, mas a recepção usa majoritariamente desktop |

### 11.3 Composição Final do MVP

Após a revisão de prioridades (o "Must" original estava inflado com 13 itens), o MVP ficou composto por exatamente **12 itens inegociáveis**:

- **7 requisitos funcionais (RF01 a RF07):** todos pré-requisitos diretos do fluxo central de agendamento — sem eles o sistema não resolve o problema para o qual foi contratado.
- **5 requisitos não funcionais (RNF01 a RNF05):** todos ligados a risco legal (LGPD), risco de perda de dados ou bloqueio total do uso do sistema.

O teste aplicado em cada item foi: *"se este requisito não existir na V1, o sistema deixa de resolver o problema de negócio central (conflito de horários, retrabalho, duplicidade) ou gera risco legal/de segurança?"* — só esses 12 itens passaram nesse teste. Os demais formam o backlog (RF-B01 a RF-B08 e RNF-B01 a RNF-B05).

---

## 12. Análise de Conflitos de Qualidade (Trade-offs)

As características de qualidade não são independentes — priorizar uma pode prejudicar outra. Alguns dos trade-offs abaixo envolvem funcionalidades do backlog; ficam documentados desde já para quando essas funcionalidades forem priorizadas.

**1. Segurança (RNF05, RNF-B03) vs. Capacidade de Interação (RF-B07)**
Exigir autenticação forte para acessar áreas sensíveis aumenta a segurança, mas cria fricção no autoatendimento do paciente.
*Decisão:* manter 2FA obrigatório para médicos e gerentes quando implementado (dados sensíveis, exigência legal), mas usar autenticação simplificada no autoatendimento, já que o risco de exposição de dados nesse fluxo é menor.

**2. Eficiência de Desempenho (RNF01, RNF-B02) vs. Confiabilidade (RF06)**
Liberar e reocupar horários automaticamente em tempo real, sob alta concorrência de acessos, pode gerar condição de corrida — dois pacientes disputando o mesmo horário liberado.
*Decisão:* priorizar consistência (verificação/bloqueio antes de confirmar) mesmo com pequeno aumento de latência na confirmação. Evitar um conflito de agendamento (RN02) é mais crítico do que ganhar milissegundos.

**3. Compatibilidade (RF-B01 — integração WhatsApp/SMS) vs. Segurança/Privacidade (RNF05)**
Integrar com canais externos amplia o alcance da comunicação, mas expõe dados do paciente a provedores terceiros.
*Decisão:* quando RF-B01 for implementado, restringir o conteúdo enviado ao mínimo necessário (nome, data e horário), sem dados clínicos.

**4. Flexibilidade (visão futura — múltiplas unidades, integração financeira) vs. Manutenibilidade**
Projetar já pensando em expansão futura aumenta a complexidade da arquitetura desde o início.
*Decisão:* adotar arquitetura modular simples no MVP (Manutenibilidade priorizada) e adiar a generalização para quando a expansão for confirmada — evita over-engineering prematuro.

**5. Capacidade de Interação vs. Adequação Funcional (RF04 — validações antes de confirmar)**
Quanto mais validações de negócio (escala, bloqueios, CPF, disponibilidade) o sistema faz antes de confirmar, mais isso pode aumentar o tempo do fluxo.
*Decisão:* manter todas as validações (são regras de negócio inegociáveis — RN01 a RN04), executando-as no backend sem telas extras, preservando a fluidez do agendamento sem abrir mão da integridade dos dados.

**6. Confiabilidade (RNF03, RNF04) vs. Custo/Recursos**
Alta disponibilidade e backups redundantes têm custo de infraestrutura maior.
*Decisão:* aceitar o custo, porque o domínio é saúde — indisponibilidade impacta diretamente o atendimento a pacientes.

---

## 13. Melhorias Futuras

Além dos itens já mapeados como backlog priorizado (Seções 6.1, 8.1 e 11), após a validação do MVP o sistema poderá receber novos recursos mais adiante, tais como:

* Novos canais de comunicação;
* Integração com outros sistemas da clínica;
* Aplicativo móvel próprio;
* Sugestões automáticas de horários;
* Análise de padrões de faltas;
* Automação de processos administrativos;
* Integração com processos financeiros;
* Novos recursos de autoatendimento.

Essas melhorias não precisam fazer parte da primeira versão do sistema, mas podem ser consideradas conforme a necessidade da clínica e a validação do MVP.

---

## 14. Conclusão

O principal objetivo deste projeto é melhorar a organização dos processos da clínica por meio de um sistema integrado, começando por um MVP enxuto e evoluindo com base no backlog priorizado.

Os problemas identificados estão relacionados principalmente à falta de centralização das informações, à utilização de processos manuais e à dificuldade de comunicação entre os envolvidos.

Com a implantação do MVP, espera-se:

* Reduzir conflitos de horários;
* Evitar cadastros duplicados;
* Diminuir o retrabalho;
* Facilitar a atualização dos dados;
* Melhorar o controle de cancelamentos;
* Organizar o fluxo de atendimento;
* Proteger informações sensíveis.

Os demais ganhos mapeados — melhorar a comunicação com os pacientes, reduzir faltas, reaproveitar horários via fila de espera e acompanhar resultados por dashboards — dependem dos itens do backlog e ficam para as próximas fases.

O sistema não deve apenas substituir planilhas ou automatizar tarefas isoladas. A proposta é integrar os principais processos da clínica, começando pelo essencial, e permitir que as informações estejam organizadas, atualizadas e disponíveis para quem realmente precisa utilizá-las.

---

## 15. Fontes

- ISO/IEC 25010:2023 — *Systems and software engineering — Systems and software Quality Requirements and Evaluation (SQuaRE) — Product quality model*. 2ª ed.
- ISO/IEC 25002:2024 — *Quality model overview and usage*.
- IIBA — *A Guide to the Business Analysis Body of Knowledge (BABOK Guide)*, v3. International Institute of Business Analysis.
- SOMMERVILLE, I. *Software Engineering*. 10ª ed. Pearson.
- Agile Business Consortium / DSDM Consortium — *MoSCoW Prioritisation*.
- BRASIL. Lei nº 13.709/2018 (LGPD) — *Lei Geral de Proteção de Dados Pessoais*.
- VALÉRIA, Kadidja. *Qualidade de Software com a ISO/IEC 25010 — Modelo de qualidade de produto da ISO/IEC 25010:2023*. Material de aula, CEUB, Engenharia de Requisitos, 2026/2.
