<h1 align="center">Projeto Web services com Spring Boot e JPA / Hibernate</h1>

## Sobre o Projeto
Este projeto faz parte do Curso "Java COMPLETO - Programação Orientada a Objetos + Projetos", ministrado pelo Professor Dr. Nelio Alves na plataforma Udemy. 
O objetivo do projeto é introduzir os alunos ao desenvolvimento de Web services com Spring Boot e JPA / Hibernate.

## Tecnologias Utilizadas
* [JavaSE 17](https://docs.oracle.com/en/java)
* [Spring Boot 3](https://docs.spring.io/spring-boot/docs/current/reference/html)
* [JPA](https://docs.oracle.com/javaee/6/tutorial/doc/bnbpz.html)
* [Hibernate](https://hibernate.org/orm/documentation/6.2)
* [Maven](https://maven.apache.org/what-is-maven.html)
* [Postman](https://learning.postman.com/docs/publishing-your-api/documenting-your-api)
  
## Práticas Adotadas
* Implementação de modelos de domínio em Java.
* Estruturação de camadas lógicas, incluindo resource, service e repository.
* Utilização de bancos de dados H2 para ambiente de teste.
* Realização de operações CRUD (Create, Retrieve, Update, Delete).
* Manipulação e tratamento de exceções.
* Uso de anotações e configurações específicas do Spring Boot e JPA.
* Exploração de conceitos de programação orientada a objetos em um contexto prático.

# Como executar
- Clone o projeto
```
git clone https://github.com/GabrielGiovanii/workshop-springboot3-jpa.git
```
- Abra o projeto na sua IDE, exemplo:  IntelliJ IDEA ou Eclipse
- Execute o projeto, porta local:
```
localhost:8080
```

## Modelo de Domínio
![modelo de dominio](https://github.com/GabrielGiovanii/workshop-springboot3-jpa/assets/115679464/26fabaaf-b247-4037-aca6-956732e07502)
  
## API Endpoints
- User
  - Listar Users
  ```
  Get: localhost:8080/users
  
  Corpo da Resposta:
  [
      {
          "id": 1,
          "name": "Bob Brown",
          "email": "bob@gmail.com",
          "phone": "977557755",
          "password": "123456"
      },
      {
          "id": 2,
          "name": "Maria Brown",
          "email": "mariagmail.com",
          "phone": "977557755",
          "password": "123456"
      }
  ]
  ```
  - Listar User por id
  ```
  Get: localhost:8080/users/{id}
  
  Corpo da Resposta:
      {
          "id": 1,
          "name": "Bob Brown",
          "email": "bob@gmail.com",
          "phone": "977557755",
          "password": "123456"
      }
  ```
  
  - Criar User
  ```
  Post: localhost:8080/users
  
  Corpo solicitado:
      {
          "name": "Maria Brown",
          "email": "mariagmail.com",
          "phone": "977557755",
          "password": "123456"
      }
  ```
  
  - Atualizar User
  ```
  Put: localhost:8080/users/{id}
  
  Corpo solicitado:
      {
          "name": "Bob Brown",
          "email": "bob@gmail.com",
          "phone": "977557755"
      }
  ```
  
  - Deletar User
  ```
  Delete: localhost:8080/users/{id}
  ```
  
## Estudante
### [Gabriel Giovani](https://www.linkedin.com/in/gabriel-giovanii)

## Autor
### [Nélio Alves](https://www.linkedin.com/in/nelio-alves)
