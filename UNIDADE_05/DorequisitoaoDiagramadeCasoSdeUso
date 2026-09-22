# Do requisito ao Diagrama de Casos de Uso

## Objetivos de aprendizagem

### 1. Identificar atores e requisitos funcionais em uma descrição de sistema

**Ator:** Jogador/usuário/heróis/vilões/NPCs

### Requisitos

- O software deverá permitir ao usuário selecionar uma fase.
- O software deverá permitir ao usuário selecionar a opção de tutorial.
- O software deverá permitir ao usuário selecionar a opção de estudar conceitos.
- O software deverá permitir ao usuário escolher um tema para estudar.
- O software deverá permitir ao usuário consultar o conteúdo do tema selecionado.
- O software deverá permitir ao usuário enfrentar um vilão respondendo charadas.
- O software deverá permitir ao usuário responder as charadas apresentadas durante o combate.
- O software deverá permitir ao usuário utilizar uma habilidade para receber uma dica.
- O software deverá permitir ao usuário acessar o modo de treinamento.
- O software deverá permitir ao usuário configurar recursos de acessibilidade.

---

### 2. Transformar requisitos textuais em casos de uso

- Selecionar fase
- Acessar tutorial
- Estudar conceitos
- Selecionar tema de estudo
- Consultar conteúdo
- Enfrentar vilão
- Responder charada
- Utilizar habilidade
- Receber dica
- Acessar modo de treinamento
- Configurar recursos de acessibilidade

---

### 3. Construir um Diagrama de Casos de Uso em UML

- Jogador → Selecionar fase
- Jogador → Acessar tutorial
- Jogador → Estudar conceitos
- Jogador → Selecionar tema de estudo
- Jogador → Consultar conteúdo
- Jogador → Enfrentar vilão
- Jogador → Responder charada
- Jogador → Utilizar habilidade
- Jogador → Receber dica
- Jogador → Acessar modo de treinamento
- Jogador → Configurar recursos de acessibilidade

---

### 4. Relacionar acessibilidade, requisitos e modelagem

A acessibilidade está relacionada aos requisitos por meio de recursos como narração, sons, músicas, treinamento e configuração dos recursos de acessibilidade.

Na modelagem, esses requisitos podem ser representados como casos de uso, mostrando como o jogador interage com o sistema.

---

### 5. Verificar a rastreabilidade entre requisitos e elementos do diagrama

Verificar se cada requisito possui um caso de uso correspondente no diagrama, garantindo que os requisitos estejam representados e que não existam elementos do diagrama sem relação com os requisitos.

---

# Leitura e identificação

### 1. Qual é o objetivo principal do U.C. Battle?

O objetivo principal do U.C. Battle é ensinar conceitos de UML, principalmente sobre Diagrama de Casos de Uso, por meio de um jogo educativo e acessível.

### 2. Quem interage diretamente com o sistema?

Quem interage diretamente com o sistema é o jogador.

### 3. Quais funcionalidades são oferecidas ao jogador?

Selecionar fase, acessar tutorial, estudar conceitos, selecionar tema de estudo, consultar conteúdo, enfrentar vilões, responder charadas, utilizar habilidades, receber dicas e acessar o modo de treinamento.

### 4. Quais regras condicionam o uso da habilidade de receber uma dica?

A habilidade só pode ser utilizada uma vez por batalha e quando o jogador possuir dois ou menos pontos de vida.

### 5. Quais funcionalidades contribuem para a acessibilidade do jogo?

O modo de treinamento, a configuração de recursos de acessibilidade, a narração, os sons e as músicas, além de recursos como áudio e ausência de limite de tempo.

---

# Elementos identificados

| Elemento identificado | Evidência no artigo | Classificação |
|---|---|---|
| Jogador | O jogador interage diretamente com o sistema. | Ator |
| Selecionar uma fase | O software permite selecionar uma fase. | Requisito funcional |
| Enfrentar vilão | O jogador enfrenta vilões respondendo perguntas. | Requisito funcional |
| Responder charada | O jogador responde às charadas durante o combate. | Requisito funcional |
| Utilizar habilidade | O jogador pode utilizar uma habilidade para receber uma dica. | Requisito funcional |
| Receber dica | A habilidade permite receber uma dica durante a batalha. | Requisito funcional |
| Acessar modo de treinamento | O jogo possui um modo de treinamento para praticar. | Requisito funcional |
| Estudar conceitos | O jogador pode estudar conceitos de UML. | Requisito funcional |
| Selecionar tema de estudo | O jogador pode selecionar um tema para estudar. | Requisito funcional |
| Consultar conteúdo | O sistema apresenta o conteúdo do tema selecionado. | Requisito funcional |
| Usar habilidade uma vez por batalha | A habilidade de receber dica só pode ser usada uma vez por batalha. | Regra de negócio |
| Usar habilidade com 2 pontos de vida ou menos | A habilidade só pode ser usada quando o jogador tiver dois pontos de vida ou menos. | Regra de negócio |
| Recursos de acessibilidade | O jogo possui recursos como narração, sons, músicas e configurações de acessibilidade. | Requisito de acessibilidade |

---

# Construção do Diagrama

## Ator

**Jogador**

## Casos de uso

- Selecionar fase
- Enfrentar vilão
- Responder charada
- Utilizar habilidade
- Receber dica
- Acessar modo de treinamento
- Estudar conceitos
- Selecionar tema de estudo
- Consultar conteúdo
- Configurar recursos de acessibilidade

---

## Relacionamentos

### Selecionar fase

**Jogador → Selecionar fase**

### Enfrentar vilão

**Jogador → Enfrentar vilão**

**Enfrentar vilão** `<<include>>` **Responder charada**

### Utilizar habilidade

**Jogador → Utilizar habilidade**

**Utilizar habilidade** `<<extend>>` **Enfrentar vilão**

**Utilizar habilidade** `<<include>>` **Receber dica**

### Acessar modo de treinamento

**Jogador → Acessar modo de treinamento**

### Estudar conceitos

**Jogador → Estudar conceitos**

**Estudar conceitos → Selecionar tema de estudo**

**Estudar conceitos → Consultar conteúdo**

### Configurar recursos de acessibilidade

**Jogador → Configurar recursos de acessibilidade**

---

## Regra de negócio

A habilidade de receber uma dica só pode ser utilizada uma vez por batalha e quando o jogador possuir dois pontos de vida ou menos.

---

# Matriz de Rastreabilidade

| ID | Requisito do artigo | Caso de uso correspondente | No diagrama? |
|---|---|---|---|
| RF01 | O software permite selecionar uma fase. | Selecionar fase | Sim |
| RF02 | O software permite selecionar a opção de tutorial. | Acessar modo de treinamento | Sim |
| RF03 | O software permite selecionar a opção de estudar conceitos. | Estudar conceitos | Sim |
| RF04 | O software permite escolher um tema para estudar. | Selecionar tema de estudo | Sim |
| RF05 | O software permite consultar o conteúdo do tema selecionado. | Consultar conteúdo | Sim |

---

# CHECKLIST

- Os atores representam papéis externos ao sistema. — OK
- Os casos de uso foram escritos com verbo no infinitivo. — OK
- A fronteira do sistema está identificada. — OK
- Cada associação representa uma interação real. — OK
- O `<<include>>` representa um comportamento obrigatório e reutilizado. — OK
- O `<<extend>>` representa um comportamento opcional ou condicionado. — OK
- As regras de negócio não foram representadas incorretamente como atores. — OK
- Os requisitos selecionados estão rastreados no diagrama. — OK
- Pelo menos uma necessidade de acessibilidade foi considerada. — OK
- O diagrama está legível e sem elementos desconectados. — OK
