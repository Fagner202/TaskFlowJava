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



# README - Configuração do Ambiente para Aplicação Java com Spring Boot

Este guia descreve os passos necessários para configurar um ambiente de desenvolvimento para uma aplicação Java utilizando Spring Boot, PostgreSQL e Docker.

## 1. Instalação do Java
```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
java -version
```
### Explicação:
- `sudo apt update`: Atualiza a lista de pacotes disponíveis no sistema.
- `sudo apt install openjdk-17-jdk -y`: Instala o JDK (Java Development Kit) versão 17 sem solicitar confirmação.
- `java -version`: Verifica se o Java foi instalado corretamente.

---

## 2. Instalação do Maven e Gradle
```bash
sudo apt install maven -y
mvn -version
sudo apt install gradle -y
gradle -v
```
### Explicação:
- `sudo apt install maven -y`: Instala o Maven, gerenciador de dependências e build para Java.
- `mvn -version`: Verifica a instalação do Maven.
- `sudo apt install gradle -y`: Instala o Gradle, alternativa ao Maven para gerenciamento de dependências e build.
- `gradle -v`: Verifica a instalação do Gradle.

---

## 3. Configuração do Banco de Dados PostgreSQL com Docker
```bash
docker run --name postgres-db -e POSTGRES_USER=admin -e POSTGRES_PASSWORD=admin -e POSTGRES_DB=taskflow -p 5432:5432 -d postgres
docker ps
```
### Explicação:
- `docker run --name postgres-db`: Cria e executa um contêiner Docker chamado `postgres-db`.
- `-e POSTGRES_USER=admin -e POSTGRES_PASSWORD=admin`: Define o usuário e senha do banco de dados.
- `-e POSTGRES_DB=taskflow`: Cria um banco de dados chamado `taskflow`.
- `-p 5432:5432`: Mapeia a porta do PostgreSQL no contêiner para a máquina local.
- `-d postgres`: Executa o contêiner em segundo plano usando a imagem oficial do PostgreSQL.
- `docker ps`: Lista os contêineres em execução para verificar se o banco foi iniciado corretamente.

---

## 4. Criação do Projeto Spring Boot
```bash
curl -L -G https://start.spring.io/starter.zip \
  -d dependencies=web,thymeleaf,data-jpa,postgresql \
  -d type=maven-project \
  -d language=java \
  -d bootVersion=3.3.0 \
  -d baseDir=taskflow \
  -o taskflow.zip && unzip -o taskflow.zip && rm taskflow.zip
```
### Explicação:
- `curl -L -G https://start.spring.io/starter.zip`: Baixa um template de projeto Spring Boot.
- `-d dependencies=web,thymeleaf,data-jpa,postgresql`: Inclui dependências para desenvolvimento web, Thymeleaf, JPA e PostgreSQL.
- `-d type=maven-project`: Define o tipo do projeto como um projeto Maven.
- `-d language=java`: Define a linguagem do projeto como Java.
- `-d bootVersion=3.3.0`: Define a versão do Spring Boot a ser usada.
- `-d baseDir=taskflow`: Define o nome da pasta do projeto.
- `-o taskflow.zip`: Salva o arquivo ZIP com o projeto.
- `unzip -o taskflow.zip && rm taskflow.zip`: Extrai os arquivos do projeto e remove o ZIP.

---

## 5. Configuração do Banco de Dados no Spring Boot
Adicione as seguintes configurações no arquivo `application.properties`:
```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/taskflow
spring.datasource.username=admin
spring.datasource.password=admin
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
```
### Explicação:
- `spring.datasource.url`: Define a URL de conexão com o PostgreSQL.
- `spring.datasource.username` e `spring.datasource.password`: Define o usuário e senha do banco de dados.
- `spring.jpa.hibernate.ddl-auto=update`: Atualiza automaticamente o esquema do banco de dados conforme as entidades.
- `spring.jpa.properties.hibernate.dialect`: Define o dialeto do Hibernate para PostgreSQL.

---

## 6. Executando a Aplicação
```bash
mvn spring-boot:run
```
Ou, se estiver usando Gradle:
```bash
./gradlew bootRun
```
Acesse a aplicação no navegador:
```bash
http://localhost:8080
```
### Explicação:
- `mvn spring-boot:run`: Inicia a aplicação usando o Maven.
- `./gradlew bootRun`: Inicia a aplicação usando o Gradle.
- `http://localhost:8080`: URL onde a aplicação estará disponível.

---

## Conclusão
Este guia cobre a instalação das ferramentas necessárias, configuração do PostgreSQL no Docker, criação do projeto Spring Boot e inicialização da aplicação. Agora, o ambiente está pronto para desenvolvimento!



