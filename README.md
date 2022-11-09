# Pro Support API

Repositório base da API do projeto Pro Support Technology.

## Uso da API

Após o clone utilizar o comando "yarn" no terminal para que todas as dependências sejam instaladas. <br/>
Para rodar a API localmente utiliza-se o comando "yarn start".

## Endpoints

### Cadastro

POST/users = realiza o cadastro

### Login

POST/signin = executa o login

### Rotas relacionadas ao usuário comum

GET/questions?\_embed=responses = lista todas as perguntas; </br>
POST/questions = cria uma pergunta </br>
PATCH/questions/{id da pergunta} = editar pergunta </br>
DELETE/questions/{id da pergunta} = deletar pergunta </br>
GET/users/{id do usuário logado} = buscar informações do usuário </br>
PATCH/users/{id do usuário logado} = alterar dados do usuário </br>

### Rotas relacionadas ao usuário Admin

POST/responses = adiciona uma resposta a uma pergunta </br>
PATCH/responses/{id da pergunta} = editar resposta </br>
DELETE/responses/{id da resposta} = deletar resposta </br>
DELETE/questions/{id da pergunta} = deletar pergunta </br>
GET/users = lista todos os usuários cadastrados </br>
GET/users/{id do usuário logado} = buscar informações do usuário </br>
PATCH/users/{id do usuário logado} = alterar dados do usuário </br>
DELETE/users/{id de usuário} = deletar conta de algum usuário </br>

## Links

Para o maior entendimento do funcionamento da API e de seus endpoints consulte a documentação oficial: https://pro-support-doc.vercel.app/
