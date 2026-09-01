# FORMULÁRIO - LEVANTAMENTO INICIAL DE REQUISITOS

*Projeto de Engenharia de Requisitos | Aula de 01/09*

**Objetivo:** registrar as necessidades dos stakeholders e transformá-las em requisitos funcionais, requisitos de qualidade, restrições e regras de negócio, mantendo foco no que é necessário para resolver o problema.

## 1. Identificação do grupo

| Informação | Preenchimento |
|---|---|
| Turma | Turma A – Eng. de Software |
| Nome do projeto | Clínica + Saúde |
| Integrante 1 | Thiago Dos Santos |
| Integrante 2 | Pedro Ryan |
| Integrante 3 | Arthur Santos |
| Integrante 4 | Luiz Claudio |
| Integrante 5 | |
| Integrante 6 | |

## 2. Contexto do projeto

**2.1 Qual problema o sistema pretende resolver?**
*Descreva o problema sem apresentar ainda uma solução tecnológica.*
Péssima organização, conflitos de horários, dados desorganizados e má comunicação com o paciente.

**2.2 Quem é afetado pelo problema?**
Dono da clínica, pacientes, médicos e recepcionistas.

**2.3 Como esse problema é resolvido atualmente?**
Através de planilhas individuais sem sincronização e processos lentos e manuais.

**2.4 Quais são as principais dificuldades do processo atual?**
Conflitos de horários, duplicidade de dados, trabalho manual excessivo e elevado índice de desmarcação.

**2.5 Qual resultado se espera alcançar com o novo sistema?**
Maior otimização, redução do trabalho manual, melhoria na comunicação e organização da agenda e dos dados.

## 3. Identificação dos stakeholders

*Identifiquem as pessoas, grupos ou organizações que possuem interesse no sistema.*

| ID | Stakeholder | Papel | Necessidade/Interesse | Influência |
|---|---|---|---|---|
| ST01 | Dono | Administrador da clínica | Otimização, organização e aumento da cartela de clientes | ALTA |
| ST02 | Recepcionista | Tirar dúvidas e marcar consultas | Agilidade em atendimentos e dúvidas | ALTA |
| ST03 | Médico | Atender os pacientes | Facilidade em organizar dados de pacientes e gerenciamento de consultas | ALTA |
| ST04 | Equipe de T.I. | Apoio e suporte do sistema | Segurança e criptografia | MÉDIA |
| ST05 | Paciente | Usuário | Marcar/alterar/cancelar consultas e tirar dúvidas | ALTA |

**Stakeholder principal:** Paciente (ST05)

**Por quê?**
O paciente é o stakeholder principal porque é o usuário final para quem o sistema existe: é ele quem gera a demanda por consultas e quem sente na prática o resultado do serviço prestado pela clínica. A maior parte das funcionalidades do sistema gira em torno de suas necessidades (marcar, alterar e cancelar consultas, tirar dúvidas), e a satisfação dele impacta diretamente o objetivo do dono do negócio (aumentar e reter a cartela de clientes). Além disso, os demais stakeholders (recepcionista, médico, TI e dono) atuam para viabilizar um bom atendimento a esse usuário — ou seja, o sucesso do sistema depende, em grande parte, da experiência do paciente.

## 4. Perguntas para o levantamento

*Para cada stakeholder, investiguem as questões abaixo. As respostas abaixo consolidam a visão dos diferentes stakeholders (paciente, recepcionista, médico, dono e equipe de TI), com foco no stakeholder principal (paciente).*

| Pergunta | Resposta |
|---|---|
| O que esse usuário precisa fazer? | Paciente: marcar, alterar e cancelar consultas e tirar dúvidas. Recepcionista: cadastrar pacientes e agendar/reagendar consultas. Médico: consultar sua agenda e o histórico dos pacientes. Dono: acompanhar indicadores de atendimento. TI: administrar acessos e a segurança do sistema. |
| Qual problema ele enfrenta atualmente? | Agendamento feito majoritariamente por telefone ou presencialmente, com uso de planilhas individuais sem sincronização, o que gera conflitos de horário, demora no atendimento e falta de confirmação clara ao paciente. |
| Quais informações ele precisa consultar? | Horários disponíveis, status da própria consulta (data, horário, médico), histórico de atendimentos, e, para a equipe interna, a agenda geral e os dados cadastrais dos pacientes. |
| Quais informações ele precisa cadastrar ou alterar? | Dados pessoais e de contato do paciente, dados da consulta (data, horário, especialidade) e, pela equipe interna, o cadastro de pacientes e os registros clínicos das consultas. |
| Quais tarefas são repetitivas? | Agendamento de consultas de retorno, confirmação de presença, atualização de dados cadastrais e lançamento manual de horários nas planilhas. |
| Quais tarefas consomem mais tempo? | Marcação e confirmação de consultas por telefone, e a conferência manual de disponibilidade em planilhas separadas para evitar conflitos de horário. |
| Quais erros acontecem atualmente? | Duplicidade de agendamento no mesmo horário, dados de pacientes duplicados ou desatualizados entre planilhas e esquecimento de consultas por falta de lembrete. |
| O usuário precisa receber notificações? | Sim. O paciente deve receber confirmação de agendamento, lembrete próximo à data da consulta e aviso em caso de alteração ou cancelamento. Recepcionista e médico devem ser notificados sobre novos agendamentos e cancelamentos. |
| O sistema precisará gerar documentos ou relatórios? | Sim. Comprovante/confirmação de agendamento para o paciente e relatórios gerenciais de consultas realizadas, canceladas e taxa de ocupação da agenda para o dono da clínica. |
| Existem informações que precisam ser protegidas? | Sim. Dados pessoais e de saúde dos pacientes, protegidos conforme a LGPD, além do sigilo do histórico clínico e das credenciais de acesso da equipe. |
| O sistema precisará se comunicar com outro sistema? | Possivelmente sim, com serviços de envio de notificação (SMS, e-mail ou WhatsApp) e, futuramente, com sistemas de convênio/plano de saúde ou de pagamento. |
| Existem regras que precisam obrigatoriamente ser respeitadas? | Sim. Não permitir dois agendamentos no mesmo horário para o mesmo médico, respeitar a LGPD no tratamento dos dados e restringir o acesso às informações clínicas a usuários autorizados. |
| O que faria o usuário considerar a solução satisfatória? | Conseguir marcar, alterar ou cancelar uma consulta de forma rápida e sem precisar ligar, receber lembretes automáticos e ter confiança de que seus dados estão seguros — resultando em uma agenda mais organizada e menos desmarcações para a clínica. |

## 5. Necessidades identificadas

*Antes de transformar as descobertas em requisitos, registram-se aqui as necessidades encontradas.*

| ID | Stakeholder | Necessidade identificada | Problema relacionado |
|---|---|---|---|
| N01 | ST05 – Paciente | Marcar, alterar e cancelar consultas de forma rápida e autônoma | Agendamento manual/telefônico lento e dependente da recepção |
| N02 | ST05 – Paciente | Receber lembretes e confirmações da consulta | Alto índice de desmarcação e esquecimento de consultas |
| N03 | ST02 – Recepcionista | Ter uma agenda centralizada e atualizada em tempo real | Planilhas individuais sem sincronização geram conflitos de horário |
| N04 | ST02 – Recepcionista | Cadastrar e consultar dados dos pacientes rapidamente | Dados desorganizados e duplicados dificultam o atendimento |
| N05 | ST03 – Médico | Acessar o histórico e os dados dos pacientes de forma organizada | Falta de centralização das informações clínicas |
| N06 | ST03 – Médico | Gerenciar a própria agenda de consultas sem conflitos | Conflitos de horário no processo manual atual |
| N07 | ST01 – Dono | Obter relatórios e indicadores de atendimento e ocupação da agenda | Falta de visibilidade sobre o desempenho da clínica e as desmarcações |
| N08 | ST04 – Equipe de T.I. | Garantir segurança e proteção dos dados armazenados | Ausência de criptografia e controle de acesso nos processos atuais |

## 6. Levantamento dos Requisitos Funcionais

*Pergunta-chave: O que o sistema deve permitir que seus usuários façam? Redijam os requisitos de forma objetiva, preferencialmente iniciando com "O sistema deve...".*

| ID | Requisito Funcional | Stakeholder/Fonte | Necessidade relacionada | Prioridade |
|---|---|---|---|---|
| RF01 | O sistema deve permitir que o paciente marque, altere e cancele consultas. | ST05 – Paciente | N01 | Alta |
| RF02 | O sistema deve enviar notificações de confirmação e lembrete de consulta ao paciente. | ST05 – Paciente | N02 | Alta |
| RF03 | O sistema deve exibir a agenda de horários disponíveis de forma centralizada e atualizada em tempo real. | ST02 – Recepcionista | N03 | Alta |
| RF04 | O sistema deve permitir que a recepcionista cadastre, edite e consulte os dados dos pacientes. | ST02 – Recepcionista | N04 | Alta |
| RF05 | O sistema deve permitir que o médico consulte o histórico e os dados dos pacientes atendidos. | ST03 – Médico | N05 | Alta |
| RF06 | O sistema deve permitir que o médico visualize e gerencie sua agenda de consultas. | ST03 – Médico | N06 | Alta |
| RF07 | O sistema deve gerar relatórios de consultas realizadas, canceladas e da taxa de ocupação da agenda. | ST01 – Dono | N07 | Média |
| RF08 | O sistema deve controlar o acesso às informações por meio de autenticação e permissões conforme o perfil do usuário. | ST04 – Equipe de T.I. | N08 | Alta |

## 7. Levantamento dos Requisitos de Qualidade

*Pergunta-chave: além de funcionar, quais características o sistema precisa apresentar para ser considerado adequado pelos stakeholders? Requisitos mensuráveis e verificáveis, evitando termos vagos.*

| ID | Característica de qualidade | Requisito mensurável | Como verificar? |
|---|---|---|---|
| RQ01 | Desempenho | O sistema deve apresentar os horários disponíveis para agendamento em até 2 segundos para 95% das requisições. | Testes de carga/tempo de resposta, medindo o intervalo entre a solicitação e a exibição dos horários. |
| RQ02 | Segurança | O sistema deve armazenar os dados pessoais e clínicos dos pacientes com criptografia, em conformidade com a LGPD. | Auditoria/teste de segurança verificando se os dados sensíveis estão criptografados em repouso e em trânsito. |
| RQ03 | Usabilidade/Interação | Um paciente sem treinamento prévio deve conseguir concluir o agendamento de uma consulta em no máximo 3 telas/passos. | Teste de usabilidade com usuários reais, contabilizando o número de etapas até a confirmação do agendamento. |
| RQ04 | Confiabilidade | O sistema deve garantir disponibilidade mínima de 99% ao mês durante o horário comercial da clínica. | Monitoramento de uptime e registro (log) de indisponibilidade ao longo do mês. |
| RQ05 | Compatibilidade/Portabilidade | O sistema deve funcionar corretamente nos navegadores Chrome, Firefox e Edge (últimas duas versões) e em telas a partir de 360px (celular). | Testes manuais e/ou automatizados em diferentes navegadores e tamanhos de tela. |

## 8. Levantamento das Restrições

*Identifiquem limitações relacionadas a tecnologia, ambiente, processo, prazo, custo, recursos ou aspectos legais.*

| ID | Restrição | Categoria | Justificativa/Fonte |
|---|---|---|---|
| RES01 | O sistema deve ser desenvolvido e entregue dentro do cronograma definido para a disciplina/semestre letivo. | Prazo | Cronograma acadêmico do projeto. |
| RES02 | O sistema deve utilizar ferramentas e tecnologias gratuitas ou de baixo custo. | Custo | Clínica de pequeno porte, com orçamento limitado para licenças de software. |
| RES03 | O sistema deve estar em conformidade com a Lei Geral de Proteção de Dados (LGPD). | Legal | Tratamento de dados pessoais e de saúde exige adequação legal obrigatória. |

## 9. Regras de negócio identificadas

*Registrem políticas, normas ou regras do domínio que definem ou restringem o negócio.*

| ID | Regra de negócio | Fonte |
|---|---|---|
| RN01 | Não é permitido agendar duas consultas para o mesmo médico no mesmo horário. | ST02/ST03 – Recepcionista e Médico (N03, N06) |
| RN02 | Apenas usuários autenticados e autorizados podem acessar ou alterar os dados clínicos dos pacientes. | ST04 – Equipe de T.I. (N08) |
| RN03 | O paciente só pode cancelar ou remarcar uma consulta respeitando um prazo mínimo de antecedência definido pela clínica. | ST05 – Paciente / ST01 – Dono (N02) |

## 10. Matriz consolidada de requisitos

| ID | Descrição | Tipo | Stakeholder/Fonte | Prioridade |
|---|---|---|---|---|
| RF01 | Paciente marca, altera e cancela consultas | Funcional | ST05 – Paciente | Alta |
| RF02 | Notificações de confirmação e lembrete ao paciente | Funcional | ST05 – Paciente | Alta |
| RF03 | Agenda de horários centralizada e em tempo real | Funcional | ST02 – Recepcionista | Alta |
| RF04 | Cadastro, edição e consulta de dados de pacientes | Funcional | ST02 – Recepcionista | Alta |
| RF05 | Consulta ao histórico dos pacientes pelo médico | Funcional | ST03 – Médico | Alta |
| RF06 | Visualização e gestão da agenda pelo médico | Funcional | ST03 – Médico | Alta |
| RF07 | Relatórios de consultas e taxa de ocupação | Funcional | ST01 – Dono | Média |
| RF08 | Controle de acesso por autenticação e permissões | Funcional | ST04 – Equipe de T.I. | Alta |
| RQ01 | Exibição de horários em até 2s para 95% das requisições | Qualidade | ST05 – Paciente | Alta |
| RQ02 | Criptografia dos dados pessoais e clínicos (LGPD) | Qualidade | ST04 – Equipe de T.I. | Alta |
| RQ03 | Agendamento concluído em até 3 telas/passos | Qualidade | ST05 – Paciente | Média |
| RQ04 | Disponibilidade mínima de 99% ao mês | Qualidade | ST01 – Dono | Alta |
| RQ05 | Compatibilidade com navegadores e telas mobile | Qualidade | ST05 – Paciente | Média |
| RES01 | Entrega dentro do cronograma da disciplina | Restrição | Grupo/Professor | Alta |
| RES02 | Uso de tecnologias gratuitas ou de baixo custo | Restrição | ST01 – Dono | Média |
| RES03 | Conformidade com a LGPD | Restrição | ST04 – Equipe de T.I. | Alta |

## 11. Revisão por pares - Caça à ambiguidade

*Troquem os requisitos com outro grupo. Procurem termos vagos, como: rápido, amigável, adequado, melhor, robusto, muitos, poucos, quando possível e se necessário.*

*A preencher após a troca de requisitos com outro grupo (dinâmica em sala de aula).*

| ID | Problema encontrado | Sugestão do grupo revisor |
|---|---|---|
| | | |
| | | |
| | | |
| | | |
| | | |

## 12. Checklist de qualidade

*Autoavaliação preliminar dos requisitos elaborados nas seções 6 a 9. O grupo deve confirmar/ajustar após a revisão por pares.*

| Pergunta | Sim | Não | Observação |
|---|---|---|---|
| O requisito está completo? | X | | Cada item traz sujeito, ação e condição claros. |
| Está correto em relação à necessidade do stakeholder? | X | | Todos os RF/RQ/RES foram vinculados a uma necessidade (seção 5). |
| Descreve apenas uma capacidade ou característica? | X | | Requisitos redigidos de forma unitária, sem misturar múltiplas funções. |
| É necessário? | X | | Decorre diretamente do problema descrito na seção 2. |
| É viável? | X | | Compatível com as restrições de prazo e custo da seção 8. |
| Possui prioridade? | X | | Prioridade Alta/Média/Baixa definida em cada tabela. |
| Está livre de ambiguidades? | X | | A confirmar na revisão por pares (seção 11). |
| Pode ser verificado ou testado? | X | | Requisitos de qualidade trazem métrica e forma de verificação. |
| A fonte/stakeholder está identificada? | X | | Coluna Stakeholder/Fonte preenchida em todas as tabelas. |

## 13. Entrega da etapa - 31/08

Ao final da aula, o grupo produziu: 8 requisitos funcionais (RF), 5 requisitos de qualidade (RQ), 3 restrições (RES) e 3 regras de negócio (RN), todos associados às necessidades e aos stakeholders identificados.

## 14. Reflexão final do grupo

*Espaço para o grupo preencher com base na discussão real em sala de aula.*

**Qual requisito gerou mais discussão durante o levantamento e por quê?**
_______________________________________________________________________________________

**Qual necessidade do usuário inicialmente parecia simples, mas gerou vários requisitos?**
_______________________________________________________________________________________

**O grupo identificou algum requisito implícito que somente apareceu durante a discussão? Qual?**
_______________________________________________________________________________________

---

*Orientação: nesta etapa, o foco não é projetar telas nem escolher tecnologias. O objetivo é compreender e registrar o que é necessário para resolver o problema, mantendo os requisitos claros, verificáveis e rastreáveis às necessidades dos stakeholders.*
