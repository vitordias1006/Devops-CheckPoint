  Gerencia Livros API — Book Management

API REST para gerenciamento de livros, desenvolvida com Spring Boot e hospedada em máquina virtual na Azure.

  Índice
Visão Geral
Tecnologias
Endereço da API
Endpoints
Executando na VM (Azure)
Build Local
Autor
  Visão Geral

A Gerencia Livros API é uma aplicação backend RESTful desenvolvida para o gerenciamento de livros. Permite cadastrar e listar livros com informações como título, autor, data de lançamento, sinopse e editora.

A aplicação está hospedada em uma máquina virtual na Azure e pode ser acessada via IP público.

Este projeto foi desenvolvido como parte de um trabalho acadêmico com foco em práticas de deploy, execução em ambiente cloud e testes via terminal utilizando curl.

  Tecnologias
Tecnologia	Versão	Descrição
Java	21	Linguagem principal
Spring Boot	3.x	Framework REST
MySQL	8.0	Banco de dados relacional
Azure VM	—	Hospedagem da aplicação
Maven	Wrapper	Build e dependências
  Endereço da API
http://40.120.24.82:8080/books


A aplicação precisa estar rodando na VM para responder.

  Endpoints
  GET /books — Listar livros

Retorna todos os livros cadastrados.

curl http://40.120.24.82:8080/books


Resposta esperada:
Array JSON com os livros.

  POST /books — Cadastrar livro

Cria um novo livro no sistema.

curl -X POST http://40.120.24.82:8080/books \
-H "Content-Type: application/json" \
-d '{
  "title": "Penseés",
  "releaseDate": "1644-06-04",
  "synopsis": "Just a human going through life experiencing every moment while always pondering about it",
  "author": "Blaise Pascal",
  "publisher": "PascalBooksDOTCOM"
}'

  Body da requisição
Campo	Tipo	Descrição
title	string	Título do livro
releaseDate	string	Data de lançamento (YYYY-MM-DD)
synopsis	string	Descrição do livro
author	string	Autor
publisher	string	Editora
  Executando na VM (Azure)

Acesse sua VM via SSH e execute:

1. Subir a aplicação
nohup java -jar gerencia-livros-0.0.1-SNAPSHOT.jar > log.txt 2>&1 &

2. Ver logs
tail -f log.txt

3. Testar localmente
curl http://localhost:8080/books

4. Testar via IP público
curl http://40.120.24.82:8080/books

5. Parar aplicação
pkill -f gerencia-livros

  Build Local
Windows
.\mvnw clean package

Linux / macOS
./mvnw clean package

Arquivo gerado:

target/gerencia-livros-0.0.1-SNAPSHOT.jar

Depois é só subir pra VM e rodar.

 Autor

Vitor Dias

Projeto acadêmico desenvolvido para disciplina de DevOps.
