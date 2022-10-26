# json-server-base

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento de API's.

<hr>

## Endpoints

Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 3 endpoints que podem ser utilizados para cadastro e 2 endpoints que podem ser usados para login.

<br>

## Rotas que não precisam de autenticação

<hr>
<br>

<h2 align="center">Cadastro de Usuário</h2>
<hr>

`POST /signup - FORMATO DA REQUISIÇÃO`

```json
{
   "email": "thomas@mail.com",
   "password": "Teste1234",
   "name": "Thomas"
}
```

<br>

Caso dê tudo certo, a resposta será assim:

`POST /signup - FORMATO DA RESPOSTA - STATUS 201`

```json
{
   "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRob21hc0BtYWlsLmNvbSIsImlhdCI6MTY2NjY1MDA4MywiZXhwIjoxNjY2NjUzNjgzLCJzdWIiOiIyIn0.7D9AmzeMPzCDZSoKhUuhFRjtBIqJT8oXUVCyA4hIqMc",
   "user": {
      "email": "thomas@mail.com",
      "name": "Thomas",
      "id": 2
   }
}
```

<br>
<h2 align="center">Possíveis erros</h2>
<hr>

email existente:

`POST /signup - FORMATO DA RESPOSTA - STATUS 400`

```json
"Email already exists"
```

<br>

faltou adicionar email ou senha:

`POST /signup - FORMATO DA RESPOSTA - STATUS 400`

```json
"Email and password are required"
```

<br>
<h2 align="center">Login</h2>
<hr>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
   "email": "thomas@mail.com",
   "password": "Teste1234"
}
```

<br>

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 200`

```json
{
   "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRob21hc0BtYWlsLmNvbSIsImlhdCI6MTY2NjY1MDExMSwiZXhwIjoxNjY2NjUzNzExLCJzdWIiOiIyIn0.mVXA5yjtVZ-koCblvvQoOJzJHCDLTA4FA1OrfyR8Mkk",
   "user": {
      "email": "thomas@mail.com",
      "name": "Thomas",
      "id": 2
   }
}
```

<br>
<h2 align="center">Possíveis erros</h2>
<hr>

senha errada:

`POST /login - FORMATO DA RESPOSTA - STATUS 400`

```json
"Incorrect password"
```

<br>

email errado:

`POST /login - FORMATO DA RESPOSTA - STATUS 400`

```json
"Cannot find user"
```

<br>
<h2 align="center">Listar livros gratuitos</h2>
<hr>

`GET /books-free - FORMATO DA RESPOSTA - STATUS 200`

```json
[
   {
      "title": "Manual dos Jovens Estressados",
      "author": "Augusto Cury",
      "userId": 2,
      "id": 1
   },
   {
      "title": "A raiva não educa. A calma educa",
      "author": "Maya Eigenmann",
      "userId": 2,
      "id": 2
   }
]
```

<br>

## Rotas que precisam de autenticação

<hr>

<br>
<h2 align="center">Listar livros pagos</h2>
<hr>

`GET /books-premium - FORMATO DA RESPOSTA - STATUS 200`

```json
[
   {
      "title": "Doutor Sono",
      "author": "Stephen King",
      "userId": 2,
      "id": 1
   },
   {
      "title": "O Cérebro da Criança",
      "author": "Daniel J. Siegel e Tina Payne Bryson",
      "userId": 2,
      "id": 2
   }
]
```

<br>
<h2 align="center">Listar todos os livros de um único usuário</h2>
<hr>

`GET /users/{id do usuário}?_embed=books-free&_embed=books-premium - FORMATO DA RESPOSTA - STATUS 200`

```json
{
   "email": "thomas@mail.com",
   "password": "$2a$10$TI3hrcWp9sgo4XppnMbXS.OqrFN1.nPRG00Nbhg.MGs7HPtgkW9Ki",
   "name": "Thomas",
   "id": 2,
   "books-free": [
      {
         "title": "Manual dos Jovens Estressados",
         "author": "Augusto Cury",
         "userId": 2,
         "id": 1
      },
      {
         "title": "A raiva não educa. A calma educa",
         "author": "Maya Eigenmann",
         "userId": 2,
         "id": 2
      }
   ],
   "books-premium": [
      {
         "title": "Doutor Sono",
         "author": "Stephen King",
         "userId": 2,
         "id": 1
      },
      {
         "title": "O Cérebro da Criança",
         "author": "Daniel J. Siegel e Tina Payne Bryson",
         "userId": 2,
         "id": 2
      }
   ]
}
```

<br>
<h2 align="center">Criar livro pago ou gratis</h2>
<hr>

`POST /books-premium - FORMATO DA REQUISIÇÃO` <br>
`POST /books-free - FORMATO DA REQUISIÇÃO`

```json
{
	"title": "Manual dos Jovens Estressados",
	"author": "Augusto Cury",
	"userId": {"id do usuário logado"}
}
```

<br>

Caso dê tudo certo, a resposta será assim:

`POST /books-premium - FORMATO DA RESPOSTA - STATUS 201` <br>
`POST /books-free - FORMATO DA RESPOSTA - STATUS 201`

```json
{
   "title": "Manual dos Jovens Estressados",
   "author": "Augusto Cury",
   "userId": 2,
   "id": 2
}
```

<br>
<h2 align="center">Remover livro pago ou gratis</h2>
<hr>

`DELETE /books-premium/{id do livro}` <br>
`DELETE /books-free/{id do livro}`

```json
Não é necessário um corpo da requisição.
```
