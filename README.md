# Transactions API

Essa aplicação simula operações de transações de débito (saída) ou crédito (entrada) de um usuário.

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

`GET /transactions/summary`: Essa rota retorna o resumo das transações efetuadas. Retorna um objeto no seguinte formato: 
```js 
{
  "summary": { 
      "amount": number 
    }
}
```
O *amount* é somado a partir do tipo das transações cadastradas no banco de dados, explicadas na rota seguinte.

`POST /transactions`: Essa rota é responsável por cadastrar novas transações no banco de dados e definir o *cookie* **sessionId**. É obrigatório passar os seguintes dados no corpo da requisição, para que uma transação seja criada com sucesso: `title`: Título da transação; `amount`: A quantia da transação; `type`: Tipo da transação, pode ser *debit* ou *credit*. Quando passada como *debit*, o `amount` da transação será cadastrada no banco de dados como negativa, simulando uma saída. Quando cadastrada como *credit*, o `amount` será cadastrado como um número positivo, simulando uma entrada.

<details>
<summary>Executando a aplicação</summary>

### :information_source: Executando a aplicação

Abaixo segue as instruções para rodar a aplicação:

**1º** Comece clonando este repositório:
```bash 
git clone https://github.com/felipesanderp/ignite-node-02-rest-api.git
```

**2º** Acesse a pasta do projeto em um terminal de preferência própria:
```bash 
cd ignite-node-02-rest-api
```

**3º** Instale as dependências do projeto, com um gerenciador de pacotes de preferência própria (aqui estou utilizando o *npm*):
```bash 
npm install
```

**4º** Após terminar de instalar as dependências, execute

</details>

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