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

**3º** Ainda no terminal, instale as dependências do projeto, com um gerenciador de pacotes de preferência própria (aqui estou utilizando o *npm*):
```bash 
npm install
```
**4º** Agora, copie o arquivo `.env.example` na raiz do projeto:
```bash 
cp .env.example .env
``` 
Um novo arquivo deverá aparecer na raiz do projeto. Você deverá abri-lo utilizando um editor de texto ou código de sua preferência, como o Visual Studio Code e preencher as duas variáveis ambiente `DATABASE_URL` e `DATABASE_CLIENT`. Essas duas variáveis podem variar de acordo com o tipo do banco de dados escolhido: se escolher utilizar o SQLite, o `DATABASE_CLIENT` deverá ser preenchido com *"sqlite"* e a `DATABASE_URL` com algo como *"./db/app.db"*. Se escolher utilizar o PostgreSQL, o `DATABASE_CLIENT` deverá ser preenchido com *"pg"* e o `DATABASE_URL` com uma *string* de conexão do PostgreSQL aceita pelo Knex.js.

**5º** Após terminar de instalar as dependências e configurar as variáveis ambiente, execute o comando abaixo no terminal para realizar as *migrations*, isto é, criar as tabelas no banco de dados:
```bash 
npm run knex migrate:latest
```
Uma mensagem de sucesso deverá aparecer no seu terminal, como `Batch 1 run: 2 migrations`

**6º** Agora, é só executar a aplicação e testa-lá em uma ferramenta cliente de API's, como o [Insomnia](https://insomnia.rest/):
```bash 
npm run dev
```
A aplicação será executada na porta `3333`. Se acontecer algum erro de conflito nesta porta, você poderá modifica-lá no arquivo `index.ts` da pasta `env` ou parar a aplicação que já está utilizando essa porta.

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