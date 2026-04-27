#  Gerencia Livros API --- Book Management

API REST para gerenciamento de livros, desenvolvida com Spring Boot e
hospedada em máquina virtual na Azure.

------------------------------------------------------------------------

##  Índice

-   Visão Geral\
-   Tecnologias\
-   Endereço da API\
-   Endpoints\
-   Executando na VM (Azure)\
-   Build Local\
-   Status do Projeto\
-   Autor

------------------------------------------------------------------------

##  Visão Geral

A **Gerencia Livros API** é uma aplicação backend RESTful desenvolvida
para o gerenciamento de livros. Permite cadastrar e listar livros com
informações como título, autor, data de lançamento, sinopse e editora.

A aplicação está hospedada em uma máquina virtual na Azure e pode ser
acessada via IP público.

Este projeto foi desenvolvido como parte de um trabalho acadêmico com
foco em práticas de deploy, execução em ambiente cloud e testes via
terminal utilizando `curl`.

------------------------------------------------------------------------

##  Tecnologias

  Tecnologia    Versão    Descrição
  ------------- --------- ---------------------------
  Java          21        Linguagem principal
  Spring Boot   3.x       Framework REST
  MySQL         8.0       Banco de dados relacional
  Azure VM      ---       Hospedagem da aplicação
  Maven         Wrapper   Build e dependências

------------------------------------------------------------------------

##  Endereço da API

http://40.120.24.82:8080/books

> A aplicação precisa estar rodando na VM para responder.

------------------------------------------------------------------------

## 📡 Endpoints

###  GET /books --- Listar livros

``` bash
curl http://40.120.24.82:8080/books
```

------------------------------------------------------------------------

###  POST /books --- Cadastrar livro

``` bash
curl -X POST http://40.120.24.82:8080/books \
-H "Content-Type: application/json" \
-d '{
  "title": "livro",
  "releaseDate": "2000-06-04",
  "synopsis": "sinopse",
  "author": "autor",
  "publisher": "editora"
}'
```

------------------------------------------------------------------------

## ☁️ Executando na VM (Azure)

``` bash
nohup java -jar gerencia-livros-0.0.1-SNAPSHOT.jar > log.txt 2>&1 &
```

Ver logs:

``` bash
tail -f log.txt
```

Testar:

``` bash
curl http://localhost:8080/books
```

------------------------------------------------------------------------

##  Build Local

``` bash
./mvnw clean package
```

------------------------------------------------------------------------

##  Status do Projeto

-   API funcionando na Azure\
-   Endpoint GET operacional\
-   Endpoint POST operacional\
-   Deploy via JAR concluído

------------------------------------------------------------------------

##  Autor

Vitor Dias
