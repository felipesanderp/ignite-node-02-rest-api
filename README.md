# Transactions API

Essa aplicação simula operações de transações de débito ou crédito que um usuário pode fazer.

## :rocket: Tecnologias

- [Node.js](https://nodejs.org/en)
- [Fastify](https://fastify.dev/)
- [Knex.js](https://knexjs.org/)
- [Zod](https://zod.dev/)
- [TypeScript](https://www.typescriptlang.org)
- [Vitest](https://vitest.dev/)
  
## :twisted_rightwards_arrows: Rotas

A aplicação conta com 4 rotas, descritas abaixo:

`GET /transactions`: Essa rota retorna todas as transações do usuário. Utiliza do **sessionId** presente nos *cookies* da aplicação para retornar somente as transações do usuário.

`GET /transactions/:id`: Essa rota recebe como parâmetro o *id* de uma transação e retorna informações sobre ela. Também utiliza do sessionId presente nos *cookies* para identificar que a transação pertence ao usuário.

`GET /transactions/summary` 

<details>
<summary>Requisitos</summary>

## RF

- [x] O usuário deve poder criar uma nova transação;
- [x] O usuário deve poder obter um resumo da sua conta;
- [x] O usuário deve poder listar todas as transações que já ocorreram;
- [x] O usuário deve poder visualizar uma transação única;

## RN

- [x] A transação pode ser do tipo crédito que somará ao valor total, ou débito subtrairá;
- [x] Deve ser possível identificarmos o usuário entre as requisições;
- [x] O usuário só pode visualizar transações o qual ele criou;
</details>