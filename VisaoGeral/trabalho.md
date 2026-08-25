# Atividade — 18/08/2026

# Sistema Integrado de Gestão de Clínica Médica

---

## 1. Stakeholders

Os stakeholders são todas as pessoas, grupos ou setores que possuem interesse no sistema, utilizam suas funcionalidades ou são impactados direta ou indiretamente por sua implantação.

Os principais stakeholders identificados para o sistema são:

### 1.1 Paciente

O paciente é um dos principais usuários beneficiados pelo sistema. Ele deve ser capaz de consultar informações sobre suas consultas, receber lembretes, confirmar ou cancelar agendamentos e, quando disponibilizado, utilizar canais de autoatendimento.

Os principais interesses do paciente são:

- Facilidade para realizar agendamentos;
- Rapidez no atendimento;
- Recebimento de lembretes;
- Comunicação clara sobre alterações na consulta;
- Redução do tempo de espera;
- Segurança e privacidade dos seus dados;
- Facilidade para cancelar ou reagendar consultas;
- Possibilidade de responder pesquisas de satisfação.

---

### 1.2 Recepcionista

A recepcionista é responsável por grande parte das operações administrativas relacionadas ao atendimento dos pacientes.

O sistema deve apoiar a recepcionista nas seguintes atividades:

- Cadastro de pacientes;
- Atualização de dados cadastrais;
- Consulta de horários disponíveis;
- Realização de agendamentos;
- Cancelamento e reagendamento;
- Confirmação da chegada do paciente;
- Alteração do status para **"Em Espera"**;
- Consulta da agenda dos médicos;
- Utilização da fila de espera.

O principal benefício para a recepcionista deve ser a redução do retrabalho e a diminuição de erros causados pela utilização de planilhas ou sistemas descentralizados.

---

### 1.3 Médico

O médico utiliza o sistema para acompanhar e administrar suas atividades relacionadas aos atendimentos.

O sistema deve permitir que o médico:

- Consulte sua agenda;
- Visualize os pacientes agendados;
- Gerencie sua disponibilidade;
- Bloqueie horários;
- Registre informações relacionadas ao atendimento;
- Acesse prontuários autorizados;
- Inicie o atendimento de pacientes que estejam aptos para atendimento.

O médico possui acesso a informações sensíveis e, por esse motivo, suas permissões devem respeitar as regras de segurança e privacidade do sistema.

---

### 1.4 Gerente da Clínica

O gerente da clínica utiliza o sistema para acompanhar o funcionamento da operação e analisar os resultados.

O sistema deve fornecer informações relacionadas a:

- Taxa de faltas;
- Ocupação da agenda;
- Cancelamentos;
- Tempo de espera;
- Reocupação de horários;
- Desempenho da recepção;
- Taxa de resposta aos lembretes;
- Satisfação dos pacientes;
- Disponibilidade do sistema.

---

### 1.5 Equipe de TI

A equipe de TI é responsável pelo suporte técnico, manutenção, segurança, disponibilidade e evolução do sistema.

Os principais interesses da equipe de TI são:

- Segurança dos dados;
- Controle de acessos;
- Realização de backups;
- Monitoramento da disponibilidade;
- Correção de falhas;
- Atualização do sistema;
- Integração com serviços externos;
- Manutenção da infraestrutura tecnológica.

---

### 1.6 Direção da Clínica

A direção possui interesse nos resultados estratégicos e operacionais gerados pela utilização do sistema.

A direção deve utilizar os indicadores e relatórios para:

- Avaliar a eficiência da clínica;
- Identificar problemas operacionais;
- Analisar o aproveitamento da agenda;
- Acompanhar a satisfação dos pacientes;
- Avaliar os impactos financeiros causados por faltas e horários ociosos;
- Apoiar decisões relacionadas à expansão e melhoria dos serviços.

---

# 2. Problemas de Negócio

## 2.1 Conflitos de Horários

A utilização de planilhas e sistemas não sincronizados pode causar conflitos de agendamento.

Um mesmo médico pode aparecer como disponível para diferentes usuários ao mesmo tempo, permitindo que mais de uma consulta seja marcada para o mesmo horário.

### Impactos

- Dupla marcação;
- Insatisfação dos pacientes;
- Necessidade de remanejamento;
- Sobrecarga da recepção;
- Perda de credibilidade;
- Desorganização da agenda médica.

---

## 2.2 Retrabalho

A ausência de um sistema centralizado faz com que informações já existentes precisem ser consultadas, copiadas ou preenchidas novamente.

Por exemplo, um paciente que já possui cadastro pode ter seus dados solicitados novamente em um novo atendimento.

### Impactos

- Perda de tempo;
- Aumento do tempo de atendimento;
- Maior possibilidade de erro humano;
- Baixa produtividade;
- Experiência negativa para o paciente.

---

## 2.3 Duplicidade de Informações

Sem uma base de dados centralizada e com validações adequadas, o mesmo paciente pode possuir mais de um cadastro.

### Impactos

- Informações divergentes;
- Dificuldade de atualização;
- Duplicidade de registros;
- Problemas na identificação do paciente;
- Risco de inconsistências em históricos e prontuários.

---

## 2.4 Dificuldade de Atualização dos Dados

A existência de diferentes planilhas e softwares faz com que uma alteração realizada em um local não seja automaticamente refletida nos demais.

### Impactos

- Informações desatualizadas;
- Divergências entre sistemas;
- Erros no atendimento;
- Retrabalho;
- Dificuldade de controle.

---

## 2.5 Falhas na Comunicação com Pacientes

A ausência de mecanismos automatizados de comunicação dificulta o envio de lembretes, confirmações e avisos sobre alterações na agenda.

### Impactos

- Aumento da taxa de faltas;
- Pacientes desinformados;
- Dificuldade para confirmar consultas;
- Perda de horários;
- Baixa eficiência no atendimento.

---

## 2.6 Dificuldade para Controlar Cancelamentos

Quando uma consulta é cancelada, o horário pode permanecer ocioso por falta de um mecanismo rápido de reocupação.

### Impactos

- Perda de oportunidades de atendimento;
- Baixa ocupação da agenda;
- Horários vagos;
- Redução da eficiência operacional.

---

# 3. Causas dos Problemas

As principais causas identificadas são:

- Utilização de planilhas individuais sem sincronização;
- Ausência de um banco de dados centralizado;
- Utilização de diferentes softwares para atividades relacionadas;
- Ausência de controle centralizado da agenda;
- Ausência de validações adequadas;
- Ausência de mecanismos automáticos de lembrete;
- Ausência de uma fila de espera automatizada;
- Dependência excessiva de processos manuais.

---

# 4. Regras de Negócio

## RN01 — CPF único

O sistema deve exigir o cadastro de um número de CPF válido e único para cada paciente.

O sistema não deve permitir a criação de mais de um cadastro ativo associado ao mesmo CPF.

**Classificação:** Estudo de Caso — Duplicidade de informações.

---

## RN02 — Conflito de horários

O sistema deve garantir que cada médico possua apenas um paciente agendado por horário.

O sistema não deve permitir a confirmação de um novo agendamento quando o horário selecionado já estiver ocupado para o mesmo médico.

**Classificação:** Estudo de Caso — Overbooking.

---

## RN03 — Horários disponíveis

O sistema deve permitir agendamentos apenas em horários previamente cadastrados como disponíveis na escala do médico.

O sistema não deve permitir o agendamento fora da disponibilidade cadastrada.

**Classificação:** Processo de Negócio.

---

## RN04 — Cancelamento e disponibilidade

Quando uma consulta for cancelada, o sistema deve alterar o status do agendamento para **"Cancelado"** e disponibilizar o horário para novas marcações ou para a fila de espera.

O sistema não deve manter um horário cancelado como ocupado na agenda.

**Classificação:** Estudo de Caso — Cancelamentos.

---

## RN05 — Alteração da escala médica

Quando houver alteração na escala de um médico, o sistema deve identificar os pacientes que possuem consultas impactadas.

O sistema deve gerar notificações automáticas para os pacientes afetados.

**Classificação:** Estudo de Caso — Mudanças de Agenda.

---

## RN06 — Lembretes automáticos

O sistema deve enviar lembretes automáticos de consulta com antecedência de 24 horas e 2 horas.

Os lembretes devem informar, no mínimo, a data, o horário e o profissional responsável pelo atendimento.

**Classificação:** Estudo de Caso — Faltas.

---

## RN07 — Reutilização do cadastro

Quando um paciente já possuir cadastro válido, o sistema deve reutilizar suas informações existentes em novos agendamentos.

O sistema não deve exigir o preenchimento novamente de dados básicos que já estejam armazenados e atualizados.

**Classificação:** Estudo de Caso — Retrabalho.

---

## RN08 — Acesso ao prontuário

O sistema deve permitir o registro e a visualização de prontuários apenas para usuários autorizados.

O sistema não deve permitir que usuários sem autorização profissional acessem informações médicas restritas.

**Classificação:** Segurança e Privacidade.

---

## RN09 — Prioridade para horários não confirmados

Quando um paciente não confirmar sua presença até quatro horas antes do horário da consulta, o sistema deve identificar o agendamento como candidato à prioridade de reocupação, conforme as políticas definidas pela clínica.

O sistema não deve cancelar automaticamente a consulta sem que essa política esteja definida e autorizada.

**Classificação:** Política Operacional.

---

## RN10 — Início do atendimento

O sistema deve permitir o início do atendimento pelo médico quando o paciente estiver com o status **"Em Espera"**.

O sistema não deve permitir que uma consulta seja marcada como iniciada quando o paciente ainda estiver com um status incompatível com o fluxo de atendimento.

**Classificação:** Operacional da Clínica.

---

# 5. Melhorias Propostas

| Problema | Melhoria Proposta | Resultado Esperado |
|---|---|---|
| Conflitos de horários | Implantação de agenda unificada em tempo real | Redução de dupla marcação |
| Retrabalho | Centralização do cadastro dos pacientes | Redução do preenchimento repetitivo |
| Duplicidade de dados | Validação de CPF único | Maior consistência das informações |
| Dados desatualizados | Base de dados centralizada | Informações mais confiáveis |
| Falhas na comunicação | Lembretes e notificações automáticas | Redução de faltas |
| Cancelamentos | Liberação automática de horários | Maior ocupação da agenda |
| Horários ociosos | Fila de espera automatizada | Reocupação mais rápida |
| Falta de acompanhamento | Dashboards e indicadores | Melhor apoio à gestão |

---

# 6. Requisitos Funcionais

Os requisitos funcionais descrevem as funções e os comportamentos que o sistema deve executar.

Para tornar os requisitos mais claros, foram utilizadas duas formas principais de redação:

- **O sistema deve...** para definir comportamentos obrigatórios;
- **O sistema não deve...** para definir restrições e comportamentos proibidos.

---

## RF01 — Gerenciamento de Pacientes

**Prioridade: Alta**

O sistema deve permitir cadastrar pacientes informando, no mínimo, nome completo, CPF, data de nascimento e informações de contato.

O sistema deve permitir consultar os dados cadastrais de um paciente.

O sistema deve permitir atualizar os dados cadastrais de pacientes.

O sistema deve permitir inativar pacientes sem excluir permanentemente o histórico existente.

O sistema deve validar a unicidade do CPF antes de concluir um novo cadastro.

O sistema não deve permitir a criação de dois cadastros ativos com o mesmo CPF.

O sistema não deve excluir automaticamente o histórico de consultas e registros relacionados ao paciente quando seu cadastro for inativado.

---

## RF02 — Gerenciamento de Médicos e Especialidades

**Prioridade: Alta**

O sistema deve permitir cadastrar médicos.

O sistema deve permitir associar um ou mais dados profissionais e especialidades ao cadastro do médico, conforme as regras da clínica.

O sistema deve permitir cadastrar a escala e a disponibilidade de atendimento de cada médico.

O sistema deve permitir consultar e atualizar as informações relacionadas à disponibilidade médica.

O sistema não deve disponibilizar horários para agendamento quando não existir escala cadastrada ou quando o horário estiver bloqueado.

---

## RF03 — Consulta de Horários Disponíveis

**Prioridade: Alta**

O sistema deve permitir consultar horários disponíveis para agendamento.

A consulta deve considerar o médico selecionado.

A consulta deve considerar a data selecionada.

A consulta deve considerar a escala cadastrada para o profissional.

A consulta deve apresentar apenas horários efetivamente disponíveis.

O sistema não deve apresentar como disponível um horário que já possua um agendamento confirmado ou bloqueado.

O sistema deve atualizar a disponibilidade dos horários após a criação, alteração ou cancelamento de um agendamento.

---

## RF04 — Agendamento de Consultas

**Prioridade: Muito Alta**

O sistema deve permitir realizar agendamentos de consultas para pacientes cadastrados.

O sistema deve associar cada agendamento a um paciente, médico, data e horário.

O sistema deve validar a disponibilidade do horário no momento da confirmação do agendamento.

O sistema deve bloquear a concorrência de horários durante o processo de confirmação.

O sistema não deve permitir a conclusão de dois agendamentos para o mesmo médico, data e horário.

O sistema deve registrar o status inicial do novo agendamento como **"Agendado"**.

O sistema deve registrar a data e o horário da criação do agendamento.

---

## RF05 — Cancelamento e Reagendamento

**Prioridade: Muito Alta**

O sistema deve permitir cancelar consultas.

O sistema deve registrar o cancelamento no histórico do agendamento.

O sistema deve atualizar o status da consulta para **"Cancelado"**.

O sistema deve permitir realizar o reagendamento de uma consulta para outro horário disponível.

O sistema deve validar a disponibilidade do novo horário antes de concluir o reagendamento.

O sistema não deve manter simultaneamente dois horários ativos para a mesma consulta após a conclusão do reagendamento.

---

## RF06 — Liberação Automática de Horários Cancelados

**Prioridade: Muito Alta**

O sistema deve liberar automaticamente um horário quando uma consulta for cancelada.

O sistema deve atualizar a agenda imediatamente após a confirmação do cancelamento.

O sistema deve permitir que o horário liberado seja utilizado para um novo agendamento.

O sistema deve permitir que o horário liberado seja oferecido aos pacientes elegíveis da fila de espera.

O sistema não deve manter um horário cancelado indisponível sem uma regra específica de bloqueio cadastrada.

---

## RF07 — Lembretes Automáticos

**Prioridade: Muito Alta**

O sistema deve enviar lembretes automáticos aos pacientes com consultas futuras.

O sistema deve enviar um lembrete com antecedência de 24 horas.

O sistema deve enviar um novo lembrete com antecedência de 2 horas.

O sistema deve utilizar os canais de comunicação configurados pela clínica, como WhatsApp e SMS, quando esses canais estiverem disponíveis.

O sistema deve registrar o envio dos lembretes.

O sistema deve permitir registrar a resposta do paciente quando houver interação de confirmação.

O sistema não deve enviar lembretes para consultas canceladas.

---

## RF08 — Gerenciamento da Agenda pelo Médico

**Prioridade: Alta**

O sistema deve permitir que o médico autorizado consulte sua própria agenda.

O sistema deve permitir que o médico bloqueie horários disponíveis.

O sistema deve permitir que o médico solicite ou realize alterações na sua disponibilidade, conforme suas permissões.

O sistema deve impedir novos agendamentos em horários bloqueados.

Quando uma alteração na agenda impactar consultas existentes, o sistema deve identificar os pacientes afetados.

O sistema deve gerar o processo de notificação para os pacientes impactados.

---

## RF09 — Prontuário Eletrônico

**Prioridade: Alta**

O sistema deve permitir registrar informações relacionadas às consultas no prontuário eletrônico.

O sistema deve associar cada registro ao paciente e ao atendimento correspondente.

O sistema deve permitir a visualização do histórico autorizado do paciente.

O sistema deve controlar o acesso ao prontuário de acordo com o perfil do usuário.

O sistema não deve permitir que usuários sem autorização acessem, alterem ou visualizem informações médicas restritas.

---

## RF10 — Fila de Espera

**Prioridade: Alta**

O sistema deve permitir cadastrar pacientes em uma fila de espera.

O sistema deve permitir registrar preferências relacionadas à disponibilidade do paciente, quando aplicável.

Quando um horário for liberado, o sistema deve identificar pacientes compatíveis com o horário disponível.

O sistema deve permitir utilizar critérios de prioridade definidos pela clínica.

O sistema deve registrar o resultado das tentativas de contato e reocupação.

O sistema não deve oferecer o mesmo horário a pacientes diferentes como confirmado simultaneamente.

---

## RF11 — Avisos sobre Alteração da Agenda Médica

**Prioridade: Alta**

Quando uma alteração na escala médica afetar consultas existentes, o sistema deve identificar todos os pacientes impactados.

O sistema deve gerar avisos automáticos para os pacientes afetados.

O sistema deve registrar o envio das notificações.

A comunicação deve informar que ocorreu uma alteração na agenda.

O sistema deve disponibilizar à equipe responsável as informações necessárias para acompanhar os pacientes impactados.

O sistema não deve enviar avisos sobre alterações que não afetem o agendamento do paciente.

---

## RF12 — Dashboard Gerencial

**Prioridade: Média**

O sistema deve disponibilizar dashboards para acompanhamento do desempenho da clínica.

O dashboard deve apresentar indicadores relacionados a:

- Taxa de no-show;
- Taxa de ocupação da agenda;
- Tempo médio de reocupação de vagas;
- Taxa de conversão da lista de prioridade;
- Tempo médio de atendimento na recepção;
- Tempo médio de espera do paciente;
- Índice de retrabalho no cadastro;
- Taxa de resposta aos lembretes;
- Índice de satisfação;
- Disponibilidade do sistema;
- Tempo de resposta de busca.

O sistema deve permitir a visualização dos indicadores em períodos definidos.

---

## RF13 — Autoatendimento

**Prioridade: Alta**

O sistema deve disponibilizar meios de autoatendimento para consultas e agendamentos.

O sistema pode disponibilizar esse acesso por portal web, chatbot ou outros canais integrados.

O sistema deve validar a disponibilidade do horário antes da confirmação.

O sistema deve registrar o agendamento realizado pelo canal de autoatendimento.

O sistema não deve permitir que o canal de autoatendimento confirme um horário indisponível.

O sistema não deve permitir que o autoatendimento contorne as mesmas regras aplicadas ao agendamento realizado pela recepção.

---

## RF14 — Controle de Status do Atendimento

**Prioridade: Muito Alta**

O sistema deve controlar os seguintes status do processo de atendimento:

- **Agendado**;
- **Confirmado**;
- **Em Espera**;
- **Atendido**;
- **Cancelado**.

O sistema deve permitir alterar o status do atendimento de acordo com o fluxo operacional definido pela clínica.

Quando o paciente chegar à clínica e for identificado pela recepção, o sistema deve permitir que seu status seja alterado para **"Em Espera"**.

O sistema deve permitir o início do atendimento quando o paciente estiver apto conforme o fluxo definido.

O sistema não deve permitir que um atendimento cancelado seja iniciado sem um novo processo de agendamento.

O sistema deve registrar as alterações relevantes de status no histórico do atendimento.

---

## RF15 — Pesquisa de Satisfação

**Prioridade: Média**

Após o encerramento do atendimento, o sistema deve permitir disparar automaticamente uma pesquisa de satisfação.

O sistema deve associar a pesquisa ao atendimento concluído.

O sistema deve registrar as respostas recebidas.

O sistema deve permitir utilizar os resultados para cálculo dos indicadores de satisfação.

O sistema não deve enviar pesquisa de satisfação para consultas canceladas ou que não tenham sido concluídas.

---

# 7. Resumo dos Requisitos Funcionais

| Código | Nome | Prioridade |
|---|---|---|
| RF01 | Gerenciamento de Pacientes | Alta |
| RF02 | Gerenciamento de Médicos e Especialidades | Alta |
| RF03 | Consulta de Horários Disponíveis | Alta |
| RF04 | Agendamento de Consultas | Muito Alta |
| RF05 | Cancelamento e Reagendamento | Muito Alta |
| RF06 | Liberação Automática de Horários | Muito Alta |
| RF07 | Lembretes Automáticos | Muito Alta |
| RF08 | Gerenciamento da Agenda pelo Médico | Alta |
| RF09 | Prontuário Eletrônico | Alta |
| RF10 | Fila de Espera | Alta |
| RF11 | Avisos sobre Alterações da Agenda | Alta |
| RF12 | Dashboard Gerencial | Média |
| RF13 | Autoatendimento | Alta |
| RF14 | Controle de Status | Muito Alta |
| RF15 | Pesquisa de Satisfação | Média |

---

# 8. Requisitos Não Funcionais

Os requisitos não funcionais definem as características de qualidade que o sistema deve possuir.

Eles não descrevem diretamente uma funcionalidade de negócio, mas estabelecem condições relacionadas ao desempenho, segurança, disponibilidade, confiabilidade, privacidade, compatibilidade e usabilidade.

---

## RNF01 — Tempo de Resposta da Busca

**Categoria:** Desempenho

O sistema deve apresentar o resultado da busca por horários disponíveis em até 2 segundos em condições normais de operação.

---

## RNF02 — Segurança da Comunicação

**Categoria:** Segurança

O sistema deve utilizar comunicação segura para a transmissão de dados.

O sistema deve utilizar HTTPS/TLS nas comunicações realizadas entre os usuários e a aplicação.

O sistema não deve transmitir informações sensíveis por conexões não seguras.

---

## RNF03 — Eficiência da Operação de Agendamento

**Categoria:** Usabilidade

A interface utilizada pela recepção deve ser projetada para reduzir o número de etapas necessárias para realizar um agendamento.

Após a seleção do paciente, do profissional e do horário, o processo de confirmação deve exigir o menor número possível de ações adicionais.

A meta inicial da interface é permitir a conclusão da operação principal de agendamento em até três interações principais após a definição das informações necessárias.

---

## RNF04 — Disponibilidade

**Categoria:** Disponibilidade

O sistema deve manter uma disponibilidade mensal mínima de 99,5%.

A indisponibilidade deve ser monitorada para permitir o acompanhamento do indicador de uptime.

---

## RNF05 — Backup

**Categoria:** Confiabilidade

O sistema deve realizar rotinas automatizadas diárias de backup do banco de dados.

O sistema deve manter mecanismos que permitam a recuperação dos dados conforme as políticas técnicas da organização.

---

## RNF06 — Privacidade

**Categoria:** Privacidade

O tratamento dos dados pessoais deve respeitar as diretrizes aplicáveis de proteção de dados.

O sistema deve limitar o acesso às informações de acordo com as permissões dos usuários.

---

## RNF07 — Acessos Simultâneos

**Categoria:** Desempenho

O sistema deve suportar no mínimo 50 acessos simultâneos sem degradação significativa das funcionalidades essenciais.

---

## RNF08 — Autenticação em Duas Etapas

**Categoria:** Segurança

O sistema deve exigir autenticação em duas etapas para os perfis definidos como sensíveis, incluindo médicos e gerentes.

O sistema não deve permitir o acesso desses perfis apenas com uma senha quando a política de autenticação em duas etapas estiver ativa.

---

## RNF09 — Compatibilidade

**Categoria:** Compatibilidade

A aplicação web deve ser compatível com os principais navegadores definidos no projeto:

- Google Chrome;
- Mozilla Firefox;
- Microsoft Edge;
- Safari.

A aplicação deve manter suas funcionalidades essenciais nos navegadores suportados.

---

## RNF10 — Responsividade

**Categoria:** Usabilidade

A interface deve ser responsiva e adaptada para utilização em:

- Computadores;
- Smartphones;
- Tablets.

O sistema não deve exigir o uso exclusivo de um computador para acesso às funcionalidades essenciais.

---

# 9. Indicadores para Acompanhar o Processo

## 9.1 Taxa de No-Show

A taxa de no-show mede o percentual de pacientes que não comparecem à consulta sem realizar um cancelamento ou aviso prévio.

### Objetivo

Avaliar a quantidade de faltas e a eficiência das estratégias de comunicação e lembrete.

### Fórmula

**Taxa de No-Show = (Quantidade de pacientes que faltaram / Quantidade total de consultas agendadas) × 100**

---

## 9.2 Taxa de Ocupação da Agenda

Mede o percentual de horários disponíveis que estão efetivamente preenchidos.

### Objetivo

Avaliar o aproveitamento da capacidade de atendimento da clínica.

### Fórmula

**Taxa de Ocupação = (Horários ocupados / Total de horários disponíveis) × 100**

---

## 9.3 Tempo Médio de Reocupação de Vaga

Mede o tempo necessário para que um horário cancelado seja ocupado novamente.

### Objetivo

Avaliar a eficiência da fila de espera e do processo de reocupação.

Quanto menor o tempo, maior tende a ser a eficiência do processo.

---

## 9.4 Taxa de Conversão da Lista de Prioridade

Mede o percentual de horários recuperados e preenchidos por meio da lista de prioridade.

### Objetivo

Avaliar a eficiência da estratégia de recuperação de horários que poderiam permanecer ociosos.

---

## 9.5 Tempo Médio de Atendimento na Recepção

Mede o tempo gasto pela recepção para identificar o paciente e encaminhá-lo para o fluxo de atendimento.

### Objetivo

Avaliar a eficiência do processo operacional da recepção.

---

## 9.6 Tempo Médio de Espera do Paciente

Mede o período entre o momento em que o paciente é registrado como **"Em Espera"** e o início do atendimento.

### Objetivo

Avaliar a qualidade da experiência do paciente e a pontualidade da operação.

---

## 9.7 Índice de Retrabalho no Cadastro

Mede a quantidade de situações em que os dados precisam ser cadastrados novamente ou corrigidos.

### Objetivo

Avaliar se o sistema centralizado está reduzindo atividades repetitivas e duplicidades.

---

## 9.8 Taxa de Resposta aos Lembretes

Mede o percentual de pacientes que interagem com os lembretes enviados.

### Fórmula

**Taxa de Resposta = (Quantidade de pacientes que responderam / Quantidade de pacientes que receberam lembrete) × 100**

---

## 9.9 Índice de Satisfação do Paciente

Mede o resultado das pesquisas de satisfação realizadas após os atendimentos.

### Objetivo

Avaliar a percepção do paciente sobre o serviço prestado.

---

## 9.10 Índice de Disponibilidade

Mede o percentual de tempo em que o sistema permaneceu disponível.

### Objetivo

Verificar o cumprimento da meta de disponibilidade mínima estabelecida no RNF04.

---

## 9.11 Tempo de Resposta de Busca

Mede o tempo necessário para retornar os resultados da consulta de horários disponíveis.

### Objetivo

Verificar o cumprimento do requisito de desempenho definido para o sistema.

---

# 10. Priorização dos Principais Requisitos

## 1º — Agendamento e Controle da Agenda

**RF03, RF04, RF05, RF06 e RF08**

Esta é a maior prioridade do sistema.

Esses requisitos resolvem diretamente os principais problemas identificados no processo atual:

- Conflitos de horários;
- Dupla marcação;
- Dificuldade para consultar horários;
- Problemas com cancelamentos;
- Desorganização da agenda médica.

O RF04 é especialmente importante porque representa o processo principal do negócio: realizar o agendamento de uma consulta sem gerar conflitos.

---

## 2º — Cadastro e Integridade dos Dados

**RF01 e RF02**

Esses requisitos são fundamentais para garantir que o sistema trabalhe com informações organizadas e confiáveis.

O cadastro centralizado reduz:

- Retrabalho;
- Duplicidade;
- Informações desatualizadas;
- Erros de identificação.

---

## 3º — Comunicação e Redução de Faltas

**RF07 e RF11**

Esses requisitos são responsáveis pela comunicação automática com os pacientes.

Eles ajudam a:

- Reduzir no-show;
- Melhorar a confirmação das consultas;
- Informar alterações na agenda;
- Melhorar a experiência do paciente.

---

## 4º — Fluxo de Atendimento

**RF09 e RF14**

Esses requisitos garantem que o sistema acompanhe o paciente durante o processo de atendimento.

O sistema passa a controlar o fluxo desde a chegada do paciente até a conclusão da consulta.

---

## 5º — Fila de Espera e Reocupação

**RF10**

A fila de espera permite aproveitar horários que seriam perdidos por cancelamentos ou desistências.

Esse requisito possui grande potencial de melhoria da ocupação da agenda.

---

## 6º — Autoatendimento

**RF13**

O autoatendimento amplia os canais disponíveis para o paciente.

Ele permite que determinados processos sejam realizados sem depender exclusivamente da recepção.

---

## 7º — Gestão e Indicadores

**RF12**

O dashboard permite acompanhar os resultados obtidos após a implantação do sistema.

Por meio dos indicadores, a gestão pode identificar:

- Problemas recorrentes;
- Gargalos;
- Melhorias necessárias;
- Resultados das mudanças implementadas.

---

## 8º — Pesquisa de Satisfação

**RF15**

A pesquisa de satisfação permite que o paciente participe do processo de melhoria contínua.

As informações coletadas podem ser utilizadas para identificar pontos positivos e problemas na experiência de atendimento.

---

# 11. Melhorias Futuras

Após a implementação das funcionalidades principais, o sistema pode ser ampliado.

Algumas possibilidades são:

- Aprimoramento da fila de espera;
- Integração com novos canais de comunicação;
- Novos dashboards gerenciais;
- Integração com outros sistemas da clínica;
- Aplicativo móvel dedicado;
- Análises preditivas para identificação de risco de no-show;
- Sugestão automática de horários;
- Automação de processos administrativos;
- Integração com sistemas financeiros;
- Ampliação dos recursos de autoatendimento.

---

# 12. Conclusão

A proposta do sistema é centralizar e organizar os processos relacionados ao agendamento, atendimento e gestão da clínica.

Os principais problemas identificados no cenário atual estão relacionados à descentralização das informações, utilização de processos manuais, falta de integração e ausência de mecanismos automáticos de comunicação.

A implantação do sistema deve permitir:

- Reduzir conflitos de horários;
- Evitar duplicidade de informações;
- Diminuir o retrabalho;
- Melhorar a comunicação com os pacientes;
- Automatizar lembretes;
- Controlar cancelamentos;
- Reaproveitar horários disponíveis;
- Organizar o fluxo de atendimento;
- Proteger informações sensíveis;
- Fornecer indicadores para apoio à gestão.

Dessa forma, o sistema não deve apenas substituir processos manuais. Ele deve organizar e integrar as informações da clínica, criando uma base para melhorar a operação, reduzir erros e acompanhar os resultados de forma contínua.


