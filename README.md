# Sistema de Agendamento de Partidas de Tênis 🎾

> Projeto desenvolvido para a disciplina de Engenharia de Software 2, do curso de Sistemas de Informação da Universidade Federal de Ouro Preto (UFOP).

---

> # Sprint 1: Definição do Modelo de Processo e Especificação de Requisitos

### 1. **Modelo de Processo**

O projeto será desenvolvido utilizando um modelo de processo **ágil**, com foco em entregas incrementais e iterativas. O trabalho será dividido em **3 sprints**, conforme solicitado, e cada sprint terá um conjunto de tarefas específicas.

#### Atividades do Sprint 1:

- **Definição do escopo do projeto**: Definir o que o sistema de agendamento de partidas de tênis fará.
- **Especificação de requisitos**: Listar os requisitos funcionais e não funcionais.
- **Definição de tecnologias**: Escolha das tecnologias que serão utilizadas no projeto.
- **Cronograma**: Estabelecimento de prazos para cada atividade.

#### Cronograma:

- **Semana 1**: Definição do escopo, especificação de requisitos e escolha das tecnologias.
- **Semana 2**: Criação da documentação e preparação do ambiente de desenvolvimento.

---

### 2. **Especificação de Requisitos**

#### Requisitos Funcionais:

1. **Cadastro e Autenticação de Usuários**:

   - Os usuários devem poder se cadastrar no sistema fornecendo nome, e-mail e senha.
   - Os usuários devem poder fazer login no sistema utilizando e-mail e senha.
   - O sistema deve validar os dados de entrada (e-mail válido, senha segura, etc.).

2. **Agendamento de Partidas**:

   - Os usuários devem poder agendar partidas de tênis, informando data, hora, local e adversário.
   - O sistema deve permitir que os usuários convidem outros jogadores para a partida.
   - O sistema deve enviar notificações aos jogadores convidados.

3. **Visualização de Partidas Agendadas**:

   - Os usuários devem poder visualizar todas as partidas agendadas em um calendário ou lista.
   - O sistema deve permitir que os usuários confirmem ou cancelem sua participação em uma partida.

4. **Histórico de Partidas**:

   - O sistema deve manter um histórico de partidas jogadas, incluindo data, hora, local e participantes.
   - Os usuários devem poder visualizar o histórico de partidas.

5. **Perfil de Usuário**:
   - Os usuários devem poder editar seu perfil, incluindo informações como nome, e-mail e foto.
   - O sistema deve permitir que os usuários alterem sua senha.

#### Requisitos Não Funcionais:

1. **Desempenho**:

   - O sistema deve ser capaz de lidar com até 1000 usuários simultaneamente sem degradação significativa do desempenho.

2. **Segurança**:

   - O sistema deve garantir que as senhas dos usuários sejam armazenadas de forma segura (hash + salt).
   - O sistema deve implementar autenticação baseada em tokens (JWT) para proteger as rotas da API.

3. **Usabilidade**:

   - A interface do usuário deve ser intuitiva e fácil de usar, com um tempo de aprendizado mínimo.
   - O sistema deve ser responsivo e funcionar bem em dispositivos móveis e desktops.

4. **Disponibilidade**:
   - O sistema deve estar disponível 99% do tempo, com um tempo de inatividade máximo de 1 hora por mês.

---

### 3. **Tecnologias Utilizadas**

#### Frontend:

- **Vue.js**: Framework JavaScript para construção da interface do usuário.
- **Vite**: Ferramenta de build rápida para Vue.js.
- **Tailwind CSS**: Framework CSS utilitário para estilização rápida e responsiva.
- **PrimeVue**: Biblioteca de componentes UI para Vue.js, com componentes prontos para uso.

#### Backend:

- **Spring Boot**: Framework Java para construção de APIs RESTful.
- **Spring Security**: Para implementação de autenticação e autorização.
- **JWT (JSON Web Tokens)**: Para autenticação segura entre frontend e backend.

#### Banco de Dados:

- **MongoDB**: Banco de dados NoSQL para armazenamento de dados dos usuários, partidas e histórico.

#### Outras Ferramentas:

- **Axios**: Para fazer chamadas HTTP da aplicação Vue.js para o backend.
- **Postman**: Para testar as APIs do backend durante o desenvolvimento.
- **Git**: Para controle de versão do código.

---



### 6. **Como Executar o Projeto**

#### Frontend:

1. Instale as dependências:
   ```bash
   npm install
   ```
2. Execute o servidor de desenvolvimento:
   ```bash
   npm run dev
   ```

#### Backend:

1. Configure o arquivo `application.properties` com as credenciais do MongoDB.
2. Execute o projeto Spring Boot:
   ```bash
   ./mvnw spring-boot:run
   ```

---

> # Sprint 2: Detalhamento de Requisitos e Projeto Arquitetural

### 0. **Estrutura do Projeto**

#### Frontend (Vue.js):

- **Estrutura de Pastas**:
  ```
  src/
  ├── assets/           # Arquivos estáticos (imagens, fonts, etc.)
  ├── components/       # Componentes reutilizáveis
  ├── config/           # Configurações da API 
  ├── views/            # Páginas da aplicação
  ├── router/           # Configuração de rotas (Vue Router)
  ├── store/            # Gerenciamento de estado (Vuex ou Pinia)
  ├── services/         # Serviços para chamadas à API (Axios)
  └── App.vue           # Componente principal
  ```

#### Backend (Spring Boot):

- **Estrutura de Pastas**:
  ```
  src/
  ├── main/
  │   ├── java/
  │   │   └── com/
  │   │       └── agendamentotenis/
  │   │           ├── controller/    # Controladores das APIs
  │   │           ├── model/         # Entidades do banco de dados
  │   │           ├── repository/    # Repositórios para acesso ao MongoDB
  │   │           ├── service/       # Lógica de negócio
  │   │           └── security/      # Configurações de segurança (JWT)
  │   └── resources/
  │       └── application.properties # Configurações do Spring Boot
  └── test/                          # Testes unitários e de integração
  ```

---


### 1. **Detalhamento dos Requisitos Funcionais**

### Histórias de Usuário:

As histórias de usuário ajudam a descrever as funcionalidades do sistema do ponto de vista do usuário. Abaixo estão algumas histórias de usuário para o sistema de agendamento de partidas de tênis:

1. **Cadastro e Autenticação**:

   - **Como** um novo usuário,
   - **Eu quero** me cadastrar no sistema fornecendo nome, e-mail e senha,
   - **Para que** eu possa acessar as funcionalidades do sistema.

   - **Como** um usuário cadastrado,
   - **Eu quero** fazer login no sistema utilizando meu e-mail e senha,
   - **Para que** eu possa agendar e visualizar partidas.

2. **Agendamento de Partidas**:

   - **Como** um usuário logado,
   - **Eu quero** agendar uma partida de tênis informando data, hora, local e adversário,
   - **Para que** eu possa organizar minhas partidas.

   - **Como** um usuário logado,
   - **Eu quero** convidar outros jogadores para uma partida,
   - **Para que** eles possam confirmar ou recusar o convite.

3. **Visualização de Partidas**:

   - **Como** um usuário logado,
   - **Eu quero** visualizar todas as partidas agendadas em um calendário ou lista,
   - **Para que** eu possa gerenciar minhas partidas.

   - **Como** um usuário logado,
   - **Eu quero** confirmar ou cancelar minha participação em uma partida,
   - **Para que** eu possa manter minha agenda atualizada.

4. **Histórico de Partidas**:

   - **Como** um usuário logado,
   - **Eu quero** visualizar o histórico de partidas jogadas,
   - **Para que** eu possa acompanhar meu desempenho ao longo do tempo.

5. **Perfil de Usuário**:

   - **Como** um usuário logado,
   - **Eu quero** editar meu perfil, incluindo nome, e-mail e foto,
   - **Para que** eu possa manter minhas informações atualizadas.

   - **Como** um usuário logado,
   - **Eu quero** alterar minha senha,
   - **Para que** eu possa garantir a segurança da minha conta.

---

> ### Cenários de Teste:

Aqui estão alguns cenários de teste para validar as funcionalidades descritas nas histórias de usuário:

1. **Cadastro de Usuário**:

   - **Dado** que o usuário está na página de cadastro,
   - **Quando** ele preenche os campos de nome, e-mail e senha corretamente,
   - **Então** o sistema deve criar uma nova conta e redirecionar o usuário para a página de login.

2. **Login de Usuário**:

   - **Dado** que o usuário está na página de login,
   - **Quando** ele insere um e-mail e senha válidos,
   - **Então** o sistema deve autenticar o usuário e redirecioná-lo para a página inicial.

3. **Agendamento de Partida**:

   - **Dado** que o usuário está logado,
   - **Quando** ele agenda uma partida informando data, hora, local e adversário,
   - **Então** o sistema deve salvar a partida e enviar notificações aos jogadores convidados.

4. **Visualização de Partidas Agendadas**:

   - **Dado** que o usuário está logado,
   - **Quando** ele acessa a página de partidas agendadas,
   - **Então** o sistema deve exibir todas as partidas agendadas em um calendário ou lista.

5. **Confirmação de Participação**:
   - **Dado** que o usuário recebeu um convite para uma partida,
   - **Quando** ele confirma sua participação,
   - **Então** o sistema deve atualizar o status da partida e notificar o organizador.

---

### 2. **Projeto Arquitetural**

### Diagrama de Classes:

O diagrama de classes descreve as principais entidades do sistema e seus relacionamentos. Aqui está uma visão geral das classes principais:

Claro! Vou criar um **Diagrama de Classes UML** para o backend do seu sistema de agendamento de partidas de tênis, considerando as principais entidades e seus relacionamentos. O backend será desenvolvido em **Spring Boot**, e as classes principais serão:

1. **User**: Representa os usuários do sistema.
2. **Match**: Representa as partidas de tênis.
3. **Notification**: Representa as notificações enviadas aos usuários.
4. **Authentication**: Responsável pela autenticação e autorização (JWT).

Aqui está o **Diagrama de Classes UML**:

```plaintext
+-------------------+       +-------------------+       +-------------------+
|      User         |       |      Match        |       |  Notification     |
+-------------------+       +-------------------+       +-------------------+
| - id: String      |       | - id: String      |       | - id: String      |
| - name: String    |       | - date: LocalDate |       | - message: String |
| - email: String   |       | - time: LocalTime |       | - recipient: User |
| - password: String|       | - location: String|       +-------------------+
+-------------------+       | - players: List<User>     |                   |
| + getters/setters |       +-------------------+       | + getters/setters |
| + authenticate()  |       | + getters/setters |       +-------------------+
| + updateProfile() |       | + scheduleMatch() |
+-------------------+       | + invitePlayer()  |
                            +-------------------+

+-------------------+
|  Authentication   |
+-------------------+
| - token: String   |
| - user: User      |
+-------------------+
| + generateToken() |
| + validateToken() |
+-------------------+
```

### Explicação das Classes:

1. **User**:

   - **Atributos**:
     - `id`: Identificador único do usuário.
     - `name`: Nome do usuário.
     - `email`: E-mail do usuário (usado para login).
     - `password`: Senha do usuário (armazenada de forma segura com hash).
   - **Métodos**:
     - `authenticate()`: Método para autenticar o usuário (verificar e-mail e senha).
     - `updateProfile()`: Método para atualizar as informações do perfil do usuário.

2. **Match**:

   - **Atributos**:
     - `id`: Identificador único da partida.
     - `date`: Data da partida.
     - `time`: Hora da partida.
     - `location`: Local onde a partida será realizada.
     - `players`: Lista de usuários participantes da partida.
   - **Métodos**:
     - `scheduleMatch()`: Método para agendar uma nova partida.
     - `invitePlayer()`: Método para convidar um jogador para a partida.

3. **Notification**:

   - **Atributos**:
     - `id`: Identificador único da notificação.
     - `message`: Mensagem da notificação.
     - `recipient`: Usuário que recebe a notificação.
   - **Métodos**:
     - `getters/setters`: Métodos para acessar e modificar os atributos.

4. **Authentication**:
   - **Atributos**:
     - `token`: Token JWT gerado para autenticação.
     - `user`: Usuário associado ao token.
   - **Métodos**:
     - `generateToken()`: Método para gerar um token JWT após o login.
     - `validateToken()`: Método para validar o token JWT em requisições subsequentes.

### Relacionamentos:

- **User** e **Match**: Um usuário pode agendar várias partidas (`User` -> `Match`), e uma partida pode ter vários jogadores (`Match` -> `User`).
- **User** e **Notification**: Um usuário pode receber várias notificações (`User` -> `Notification`).
- **Authentication** e **User**: A autenticação está associada a um usuário (`Authentication` -> `User`).

---

### Como Ficaria no Spring Boot:

No Spring Boot, essas classes seriam implementadas da seguinte forma:

#### Classe `User`:

```java
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private String id;

    private String name;
    private String email;
    private String password;

    @OneToMany(mappedBy = "organizer")
    private List<Match> matches;

    // Getters e Setters
}
```

#### Classe `Match`:

```java
@Entity
public class Match {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private String id;

    private LocalDate date;
    private LocalTime time;
    private String location;

    @ManyToMany
    private List<User> players;

    // Getters e Setters
}
```

#### Classe `Notification`:

```java
@Entity
public class Notification {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private String id;

    private String message;

    @ManyToOne
    private User recipient;

    // Getters e Setters
}
```

#### Classe `Authentication`:

```java
public class Authentication {
    private String token;
    private User user;

    // Getters e Setters
}
```

---

#### Diagrama de Componentes:

O **Diagrama de Componentes** mostra como o frontend (Vue.js), o backend (Spring Boot) e o banco de dados (MongoDB) interagem entre si. Aqui está uma visão geral:

- **Frontend (Vue.js)**: Responsável pela interface do usuário e interação com o backend.
- **Backend (Spring Boot)**: Responsável pela lógica de negócio, autenticação e acesso ao banco de dados.
- **Database (MongoDB)**: Armazena os dados dos usuários, partidas e notificações.

Aqui está o **Diagrama de Componentes UML**:

```plaintext
+-------------------+       +-------------------+       +-------------------+
|   Frontend        |       |   Backend         |       |   MongoDB         |
|  (Vue.js)         |       |  (Spring Boot)    |       |  (Database)       |
+-------------------+       +-------------------+       +-------------------+
| - User Interface  |       | - Controllers     |       | - Users           |
| - Components      |       | - Services        |       | - Matches         |
| - Router          |       | - Repositories    |       | - Notifications   |
| - State Management|       | - Security (JWT)  |       +-------------------+
+-------------------+       +-------------------+
|                   |       |                   |
|  <<HTTP>>         |<----->|  <<HTTP>>         |<----->|  <<Database>>     |
|  (API Calls)      |       |  (API Endpoints)  |       |  (CRUD Operations)|
+-------------------+       +-------------------+       +-------------------+
```

### Explicação dos Componentes:

1. **Frontend (Vue.js)**:

   - **User Interface**: Responsável pela interface gráfica do usuário, construída com Vue.js, Vite, Tailwind CSS e PrimeVue.
   - **Components**: Componentes reutilizáveis que compõem a interface (ex: formulários, listas, calendário).
   - **Router**: Gerencia as rotas da aplicação (ex: navegação entre páginas).
   - **State Management**: Gerencia o estado global da aplicação (ex: dados do usuário logado, partidas agendadas).
   - **HTTP (API Calls)**: Faz chamadas HTTP para o backend (Spring Boot) usando Axios.

2. **Backend (Spring Boot)**:

   - **Controllers**: Recebe as requisições HTTP do frontend e as direciona para os serviços apropriados.
   - **Services**: Contém a lógica de negócio do sistema (ex: agendamento de partidas, autenticação de usuários).
   - **Repositories**: Responsável pela interação com o banco de dados (MongoDB) para operações CRUD.
   - **Security (JWT)**: Gerencia a autenticação e autorização dos usuários usando JWT (JSON Web Tokens).
   - **HTTP (API Endpoints)**: Expõe endpoints RESTful para o frontend consumir.

3. **MongoDB (Database)**:
   - **Users**: Armazena os dados dos usuários (nome, e-mail, senha, etc.).
   - **Matches**: Armazena os dados das partidas agendadas (data, hora, local, jogadores).
   - **Notifications**: Armazena as notificações enviadas aos usuários (mensagem, destinatário).

### Interações entre Componentes:

1. **Frontend -> Backend**:

   - O frontend faz chamadas HTTP (usando Axios) para os endpoints do backend (Spring Boot).
   - Exemplo: Quando o usuário agenda uma partida, o frontend envia uma requisição POST para o backend com os dados da partida.

2. **Backend -> MongoDB**:

   - O backend (Spring Boot) interage com o banco de dados MongoDB para realizar operações CRUD (Create, Read, Update, Delete).
   - Exemplo: Quando uma partida é agendada, o backend salva os dados da partida no MongoDB.

3. **Backend -> Frontend**:
   - O backend processa as requisições do frontend e retorna respostas HTTP (ex: dados das partidas agendadas, confirmação de autenticação).
   - Exemplo: Quando o usuário faz login, o backend retorna um token JWT para o frontend, que é armazenado no estado global da aplicação.

---

#### Diagrama de Sequência:

O diagrama de sequência mostra a interação entre os componentes do sistema durante uma operação específica, como o **agendamento de uma partida**. Vamos considerar a interação entre o **Frontend (Vue.js)**, o **Backend (Spring Boot)** e o **Banco de Dados (MongoDB)**.

Aqui está o **Diagrama de Sequência UML**:

```plaintext
+-------------------+       +-------------------+       +-------------------+
|   Frontend        |       |   Backend         |       |   MongoDB         |
|  (Vue.js)         |       |  (Spring Boot)    |       |  (Database)       |
+-------------------+       +-------------------+       +-------------------+
|                   |       |                   |       |                   |
|  Usuário          |       |  Controller       |       |  Database         |
|                   |       |  Service          |       |                   |
|                   |       |  Repository       |       |                   |
+-------------------+       +-------------------+       +-------------------+
|                   |       |                   |       |                   |
| 1. Agendar Partida|       |                   |       |                   |
|------------------>|       |                   |       |                   |
|                   | 2. Validação dos dados   |       |                   |
|                   |------------------>|       |       |                   |
|                   |                   | 3. Salvar partida no banco        |
|                   |                   |------------------>|               |
|                   |                   |                   | 4. Persistir   |
|                   |                   |                   | dados no MongoDB|
|                   |                   |<------------------|               |
|                   | 5. Retornar resposta   |       |                   |
|                   |<------------------|       |       |                   |
| 6. Exibir mensagem|       |                   |       |                   |
|<------------------|       |                   |       |                   |
|                   |       |                   |       |                   |
+-------------------+       +-------------------+       +-------------------+
```

### Explicação do Diagrama de Sequência:

1. **Usuário no Frontend (Vue.js)**:

   - O usuário preenche o formulário de agendamento de partida no frontend (Vue.js) e clica em "Agendar".
   - O frontend envia uma requisição HTTP (POST) para o backend (Spring Boot) com os dados da partida (data, hora, local, jogadores).

2. **Backend (Spring Boot)**:

   - **Controller**: Recebe a requisição do frontend e a repassa para o **Service**.
   - **Service**: Valida os dados da partida (ex: verifica se a data e hora são válidas, se os jogadores existem, etc.).
   - **Repository**: Se os dados forem válidos, o **Service** solicita ao **Repository** que salve a partida no banco de dados.

3. **Banco de Dados (MongoDB)**:

   - O **Repository** interage com o banco de dados MongoDB para persistir os dados da partida.
   - Após a persistência, o banco de dados retorna uma confirmação para o **Repository**.

4. **Backend (Spring Boot)**:

   - O **Repository** retorna a confirmação para o **Service**.
   - O **Service** retorna uma resposta de sucesso para o **Controller**.
   - O **Controller** retorna uma resposta HTTP (ex: status 200 OK) para o frontend.

5. **Frontend (Vue.js)**:
   - O frontend recebe a resposta do backend e exibe uma mensagem de sucesso para o usuário (ex: "Partida agendada com sucesso!").

---

### Detalhamento das Interações:

#### 1. **Frontend -> Backend (Requisição HTTP)**:

- O frontend envia uma requisição POST para o backend com os dados da partida.
- Exemplo de requisição:
  ```json
  POST /api/matches
  {
    "date": "2024-03-30",
    "time": "15:00",
    "location": "Quadra Central",
    "players": ["user1@example.com", "user2@example.com"]
  }
  ```

#### 2. **Backend (Validação dos Dados)**:

- O **Service** valida os dados da partida:
  - Verifica se a data e hora são válidas.
  - Verifica se os jogadores existem no banco de dados.
  - Verifica se o local está disponível.

#### 3. **Backend -> MongoDB (Persistência dos Dados)**:

- O **Repository** salva a partida no banco de dados MongoDB.
- Exemplo de documento salvo no MongoDB:
  ```json
  {
    "_id": "12345",
    "date": "2024-03-30",
    "time": "15:00",
    "location": "Quadra Central",
    "players": ["user1@example.com", "user2@example.com"]
  }
  ```

#### 4. **Backend -> Frontend (Resposta HTTP)**:

- O backend retorna uma resposta de sucesso para o frontend.
- Exemplo de resposta:
  ```json
  {
    "status": "success",
    "message": "Partida agendada com sucesso!"
  }
  ```

#### 5. **Frontend (Exibição da Mensagem)**:

- O frontend exibe uma mensagem de sucesso para o usuário, confirmando que a partida foi agendada.

---
