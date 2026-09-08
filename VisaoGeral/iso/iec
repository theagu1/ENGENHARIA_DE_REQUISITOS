# Gabarito — Qualidade de Software com a ISO/IEC 25010

**Disciplina:** Engenharia de Requisitos
**Base:** Material do estudante — ISO/IEC 25010:2023

---

## 1. Situação inicial (Seção 3)

**Cenário:** sistema acadêmico completo funcionalmente, mas com página de notas lenta (15s), mau funcionamento em celulares, mensagens confusas e vazamento de dados entre usuários.

**1) O sistema pode ser considerado de qualidade? Justifique.**
Não. Ele cumpre as funções solicitadas, mas falha em várias outras características do modelo: desempenho (15s para carregar), interação/flexibilidade (não funciona bem em celulares), capacidade de interação (mensagens difíceis de entender) e segurança (acesso indevido a informações de outros usuários).

**2) Cumprir os requisitos funcionais é suficiente?**
Não. Adequação funcional é apenas uma das nove características do modelo. Um sistema pode fazer tudo o que foi pedido e, ainda assim, ser lento, inseguro, difícil de usar ou pouco confiável.

**3) Quais problemas podem ser identificados?**
- Lentidão no carregamento → *eficiência de desempenho*
- Mau funcionamento em celulares → *capacidade de interação / flexibilidade*
- Mensagens difíceis de compreender → *capacidade de interação*
- Acesso indevido a informações → *segurança*

**4) Como esses problemas poderiam ser avaliados objetivamente?**
Definindo métricas verificáveis para cada característica: tempo de resposta medido em teste de carga, taxa de sucesso em teste de usabilidade, testes em diferentes resoluções de tela e testes de controle de acesso/autorização.

---

## 2. Atividade prática — Avaliação de um sistema acadêmico (Seção 8)

| Ocorrência | Característica predominante | Justificativa | Requisito de qualidade | Critério de aceitação | Teste ou avaliação |
|---:|---|---|---|---|---|
| 1. Média final incorreta | Adequação funcional | A função existe, mas o resultado calculado está errado — falha de correção funcional | O sistema deve calcular a média final conforme a fórmula oficial, com resultado correto em 100% dos casos testados | Resultado do sistema idêntico ao valor de referência em todos os casos de teste | Teste funcional comparando saída do sistema com cálculo de referência |
| 2. Página de notas demora ~12s | Eficiência de desempenho | Tempo de resposta muito acima do aceitável | A página de notas deve carregar em até 2s para 95% das requisições | Em teste de carga, 95% das requisições carregam em até 2s | Teste de desempenho (ex.: JMeter/K6) |
| 3. Dificuldade para localizar renovação de matrícula | Capacidade de interação | Problema de reconhecimento/facilidade de uso da interface | O estudante deve localizar a renovação de matrícula em no máximo 2 cliques a partir da tela inicial | 90% dos usuários encontram a opção sem ajuda externa | Teste de usabilidade com usuários reais |
| 4. App falha com muitos acessos simultâneos | Eficiência de desempenho | Falta de capacidade para lidar com carga de utilização | O sistema deve suportar pelo menos 500 usuários simultâneos sem falhas ou indisponibilidade | Teste de carga com 500 usuários simultâneos sem erros ou queda | Teste de carga e estresse |
| 5. Estudante visualizou histórico de outro usuário | Segurança | Falha de confidencialidade/controle de acesso | Cada usuário deve acessar exclusivamente as informações do seu próprio perfil | Nenhum usuário consegue visualizar dados de outro em testes de tentativa de acesso indevido | Teste de segurança e controle de acesso |
| 6. Alteração no cadastro quebrou outros módulos | Manutenibilidade | Falta de modularidade — baixo isolamento entre componentes | Alterações em um módulo não devem provocar falhas em outros módulos | Testes de regressão não identificam falhas em módulos não alterados | Teste de regressão |
| 7. Não importa dados do sistema financeiro | Compatibilidade | Falta de interoperabilidade com outro sistema | O sistema deve importar dados do sistema financeiro via API ou arquivo padronizado | Dados importados corretamente em ambiente de teste de integração | Teste de integração/compatibilidade |
| 8. Implantação em novo servidor exige ajustes manuais | Flexibilidade | Baixa capacidade de instalação/adaptação a novo ambiente | A implantação em novo ambiente compatível deve seguir procedimento documentado, sem passos manuais adicionais | Implantação concluída seguindo o procedimento padrão, sem alterações não documentadas | Teste de instalação/implantação |
| 9. Equipamento acionado com sensor indicando condição insegura | Proteção contra riscos (*safety*) | Risco de dano físico não bloqueado pelo sistema | O sistema não deve permitir o acionamento do equipamento quando o sensor indicar condição insegura | Em 100% dos testes com condição insegura simulada, o acionamento é bloqueado | Teste funcional de segurança operacional |

> **Observação:** os casos 1, 4 e 9 possuem relação secundária com outras características (por exemplo, o caso 9 também toca em adequação funcional e segurança), mas a característica predominante é a indicada na tabela.

---

## 3. Análise de conflitos de qualidade (Seção 9)

**1) A inclusão de novas verificações de segurança pode impactar o desempenho?**
Sim. Validações extras, criptografia e autenticação adicionam processamento, podendo aumentar o tempo de resposta. É necessário dimensionar os mecanismos de segurança para caber dentro dos limites de desempenho definidos.

**2) Como mecanismos adicionais de autenticação afetam a interação do usuário?**
Camadas extras de autenticação (ex.: verificação em duas etapas) protegem a conta, mas tornam o processo mais longo, exigindo equilíbrio entre proteção e facilidade de uso.

**3) Uma arquitetura muito flexível pode aumentar a complexidade?**
Sim. Uma arquitetura muito genérica/configurável tende a ficar mais complexa internamente, o que pode dificultar a compreensão, os testes e a manutenção futura.

**4) Que impactos surgem ao aumentar a redundância para melhorar a confiabilidade?**
Mais redundância (réplicas, failover, backups) aumenta a confiabilidade, mas também eleva custos de infraestrutura e a complexidade operacional.

**5) Como a equipe deve decidir as prioridades entre características?**
Com base no contexto do produto — riscos envolvidos, criticidade para o negócio, necessidades dos stakeholders e restrições de prazo/custo — buscando equilíbrio entre as características em vez de otimizar apenas uma isoladamente.

---

## 4. Exercícios de revisão (Seção 10)

| Questão | Resposta | Justificativa |
|---|---|---|
| 1 | **B** — Eficiência de desempenho | Tempo de processamento excessivo (20s) é o problema central |
| 2 | **A** — Compatibilidade | Troca correta de dados entre sistemas é interoperabilidade |
| 3 | **D** | Única alternativa com condição e valor numérico verificável; as demais usam termos vagos |
| 4 | **B** — Manutenibilidade | Facilidade de alterar e testar um componente é a definição da característica |
| 5 | **C** — Proteção contra riscos (*safety*) | Bloquear operação perigosa para o paciente é redução de risco de dano |

### Questão 6 — Produção textual (exemplo: Confiabilidade)

- **Requisito vago:** "O sistema deve ser confiável."
- **Versão mensurável:** "O sistema deve apresentar disponibilidade mínima de 99,5% durante o horário de funcionamento, desconsiderando manutenções programadas."
- **Critério de aceitação:** monitoramento contínuo deve registrar disponibilidade igual ou superior a 99,5% no período avaliado.
- **Estratégia de teste:** monitoramento de *uptime* com ferramenta de observabilidade ao longo de um mês, registrando incidentes e tempo total de indisponibilidade.

---

*Gabarito elaborado com base no material "Qualidade de Software com a ISO/IEC 25010" (CEUB — Engenharia de Requisitos).*
