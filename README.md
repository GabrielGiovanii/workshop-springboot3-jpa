<h1 align="center">Projeto Web services com Spring Boot e JPA / Hibernate</h1>

## Sobre o Projeto
Este projeto faz parte do Curso "Java COMPLETO - Programação Orientada a Objetos + Projetos", ministrado pelo Professor Dr. Nelio Alves na plataforma Udemy. 
O objetivo do projeto é introduzir os alunos ao desenvolvimento de Web services com Spring Boot e JPA / Hibernate.

## Tecnologias Utilizadas
* [JavaSE 17](https://docs.oracle.com/en/java)
* [Spring Boot 3](https://docs.spring.io/spring-boot/docs/current/reference/html)
* [Apache Tomcat](https://tomcat.apache.org/tomcat-8.5-doc/index.html)
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
          "name": "Maria Brown",
          "email": "maria@gmail.com",
          "phone": "988888888",
          "password": "123456"
      },
      {
          "id": 2,
          "name": "Alex Green",
          "email": "alex@gmail.com",
          "phone": "977777777",
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
        "name": "Maria Brown",
        "email": "maria@gmail.com",
        "phone": "988888888",
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

- Category
  - Listar Categories
  ```
  Get: localhost:8080/categories
  
  Corpo da Resposta:
  [
      {
          "id": 1,
          "name": "Electronics"
      },
      {
          "id": 2,
          "name": "Books"
      },
      {
          "id": 3,
          "name": "Computers"
      }
  ]
  ```
  - Listar User por id
  ```
  Get: localhost:8080/categories/{id}
  
  Corpo da Resposta:
    {
        "id": 1,
        "name": "Electronics"
    }
  ```

- Product
  - Listar Products
  ```
  Get: localhost:8080/products
  
  Corpo da Resposta:
  [
      {
          "id": 1,
          "name": "The Lord of the Rings",
          "description": "Lorem ipsum dolor sit amet, consectetur.",
          "price": 90.5,
          "imgUrl": "",
          "categories": [
              {
                  "id": 2,
                  "name": "Books"
              }
          ]
      },
      {
          "id": 2,
          "name": "Smart TV",
          "description": "Nulla eu imperdiet purus. Maecenas ante.",
          "price": 2190.0,
          "imgUrl": "",
          "categories": [
              {
                  "id": 1,
                  "name": "Electronics"
              },
              {
                  "id": 3,
                  "name": "Computers"
              }
          ]
      }
  ]
  ```
  - Listar Product por id
  ```
  Get: localhost:8080/products/{id}
  
  Corpo da Resposta:
      {
          "id": 1,
          "name": "The Lord of the Rings",
          "description": "Lorem ipsum dolor sit amet, consectetur.",
          "price": 90.5,
          "imgUrl": "",
          "categories": [
              {
                  "id": 2,
                  "name": "Books"
              }
          ]
      }
  ```

- Order
  - Listar Orders
  ```
  Get: localhost:8080/orders
  
  Corpo da Resposta:
  [
      {
          "id": 1,
          "moment": "2019-06-20T19:53:07Z",
          "orderStatus": "PAID",
          "client": {
              "id": 1,
              "name": "Maria Brown",
              "email": "maria@gmail.com",
              "phone": "988888888",
              "password": "123456"
          },
          "items": [
              {
                  "quantity": 2,
                  "price": 90.5,
                  "product": {
                      "id": 1,
                      "name": "The Lord of the Rings",
                      "description": "Lorem ipsum dolor sit amet, consectetur.",
                      "price": 90.5,
                      "imgUrl": "",
                      "categories": [
                          {
                              "id": 2,
                              "name": "Books"
                          }
                      ]
                  },
                  "subTotal": 181.0
              },
              {
                  "quantity": 1,
                  "price": 1250.0,
                  "product": {
                      "id": 3,
                      "name": "Macbook Pro",
                      "description": "Nam eleifend maximus tortor, at mollis.",
                      "price": 1250.0,
                      "imgUrl": "",
                      "categories": [
                          {
                              "id": 3,
                              "name": "Computers"
                          }
                      ]
                  },
                  "subTotal": 1250.0
              }
          ],
          "payment": {
              "id": 1,
              "moment": "2019-06-20T21:53:07Z"
          },
          "total": 1431.0
      },
      {
          "id": 2,
          "moment": "2019-07-21T03:42:10Z",
          "orderStatus": "WAITING_PAYMENT",
          "client": {
              "id": 2,
              "name": "Alex Green",
              "email": "alex@gmail.com",
              "phone": "977777777",
              "password": "123456"
          },
          "items": [
              {
                  "quantity": 2,
                  "price": 1250.0,
                  "product": {
                      "id": 3,
                      "name": "Macbook Pro",
                      "description": "Nam eleifend maximus tortor, at mollis.",
                      "price": 1250.0,
                      "imgUrl": "",
                      "categories": [
                          {
                              "id": 3,
                              "name": "Computers"
                          }
                      ]
                  },
                  "subTotal": 2500.0
              }
          ],
          "payment": null,
          "total": 2500.0
      }
  ]
  ```
  - Listar Order por id
  ```
  Get: localhost:8080/orders/{id}
  
  Corpo da Resposta:
      {
          "id": 1,
          "moment": "2019-06-20T19:53:07Z",
          "orderStatus": "PAID",
          "client": {
              "id": 1,
              "name": "Maria Brown",
              "email": "maria@gmail.com",
              "phone": "988888888",
              "password": "123456"
          },
          "items": [
              {
                  "quantity": 2,
                  "price": 90.5,
                  "product": {
                      "id": 1,
                      "name": "The Lord of the Rings",
                      "description": "Lorem ipsum dolor sit amet, consectetur.",
                      "price": 90.5,
                      "imgUrl": "",
                      "categories": [
                          {
                              "id": 2,
                              "name": "Books"
                          }
                      ]
                  },
                  "subTotal": 181.0
              },
              {
                  "quantity": 1,
                  "price": 1250.0,
                  "product": {
                      "id": 3,
                      "name": "Macbook Pro",
                      "description": "Nam eleifend maximus tortor, at mollis.",
                      "price": 1250.0,
                      "imgUrl": "",
                      "categories": [
                          {
                              "id": 3,
                              "name": "Computers"
                          }
                      ]
                  },
                  "subTotal": 1250.0
              }
          ],
          "payment": {
              "id": 1,
              "moment": "2019-06-20T21:53:07Z"
          },
          "total": 1431.0
      }
  ```
  
## Estudante
### [Gabriel Giovani](https://www.linkedin.com/in/gabriel-giovanii)

## Autor
### [Nélio Alves](https://www.linkedin.com/in/nelio-alves)
