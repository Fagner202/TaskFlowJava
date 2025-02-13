# TaskFlow - Gerenciador de Tarefas

## 📌 Introdução
O **TaskFlow** é uma aplicação web desenvolvida em Java com Spring Boot para gerenciar tarefas de forma eficiente. Ele permite que usuários criem, editem e excluam tarefas, além de fornecer autenticação para controle de acesso.

## 🚀 Tecnologias Utilizadas
- **Back-end**: Java com Spring Boot
- **Front-end**: Thymeleaf
- **Banco de Dados**: PostgreSQL
- **Gerenciador de Dependências**: Maven ou Gradle
- **Servidor de Aplicação**: A definir conforme necessidade

## 🏛 Arquitetura do Sistema
O sistema segue o padrão **MVC (Model-View-Controller)**:
- **Model**: Representa as entidades do sistema (ex.: `Task.java`).
- **View**: Responsável pela interface do usuário, utilizando Thymeleaf.
- **Controller**: Gerencia as requisições HTTP e intermedia entre Model e View.

## 📌 Funcionalidades Principais
- Cadastro de usuários com autenticação.
- CRUD de tarefas (Criar, Ler, Atualizar, Excluir).
- Filtragem e ordenação de tarefas.
- Notificação de prazos de tarefas.

## 🔄 Casos de Uso
1. **Usuário se cadastra e faz login.**
2. **Usuário cria uma nova tarefa informando título, descrição e prazo.**
3. **Usuário pode editar ou excluir suas tarefas.**
4. **Usuário visualiza uma lista de tarefas filtradas por status (pendente, concluída, etc.).**

## 🗃 Estrutura do Banco de Dados
Abaixo está o modelo inicial do banco de dados:

### **Tabela: users**
| ID | Nome | Email | Senha |
|----|------|-------|-------|
| 1  | João  | joao@email.com | hash123 |

### **Tabela: tasks**
| ID | Usuário_ID | Título | Descrição | Status | Prazo |
|----|------------|---------|------------|--------|-------|
| 1  | 1          | Estudar Java | Praticar Spring Boot | Pendente | 2025-03-01 |

## 🔗 APIs e Endpoints
A aplicação oferecerá os seguintes endpoints:

### **Usuários**
- `POST /register` - Cadastro de usuário
- `POST /login` - Autenticação

### **Tarefas**
- `GET /tasks` - Lista todas as tarefas do usuário
- `POST /tasks` - Cria uma nova tarefa
- `PUT /tasks/{id}` - Atualiza uma tarefa
- `DELETE /tasks/{id}` - Remove uma tarefa

## 📌 Como Executar o Projeto
1. Clone este repositório: `git clone https://github.com/seu-repositorio/taskflow.git`
2. Configure o banco de dados PostgreSQL.
3. Execute o projeto com `mvn spring-boot:run` ou `./gradlew bootRun`.
4. Acesse a aplicação em `http://localhost:8080`.

## 📌 Contribuição
Se quiser contribuir, sinta-se à vontade para abrir issues e pull requests! 🎉

## 📄 Licença
Este projeto está sob a licença MIT.

