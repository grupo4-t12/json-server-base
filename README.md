# "Fake-API" criada para o Projeto Front-End do Módulo 3 da Kenzie Academy Brasil (Grupo 4)

Fizemos um "fork" do repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Projetos Front-end (https://github.com/Kenzie-Academy-Brasil-Developers/json-server-base).

## Endpoints que não precisam de autenticação

Não é necessário passar um token para realizar uma requisição bem sucedida nos seguintes endpoints:

### Cadastro

POST /register

{
"email": "exemplo@mail.com",
"password": "Exemplo123"
}

Segundo a documentação do JSON-Server-Auth (https://www.npmjs.com/package/json-server-auth), os endpoints POST /signup e POST /users também podem ser utilizados para a realização do cadastro.

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.

### Login

POST /login

{
"email": "exemplo@mail.com",
"password": "Exemplo123"
}

Resposta da API:

{
"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6Im1hdGhldXNAbWFpbC5jb20iLCJpYXQiOjE2NjE4MzcxMTAsImV4cCI6MTY2MTg0MDcxMCwic3ViIjoiMiJ9.TUdRPgJbZK93ZRSIYs4esiLSR8kFzW6nBtoMk1cjYYM",
"user": {
"email": "exemplo@mail.com",
"id": 2
}
}

Segundo a documentação do JSON-Server-Auth, o endpoint POST /signin também pode ser utilizado para a realização do login, o usuário precisa estar
cadastrado na lista de users.

### Users

GET /users

Não é necessário passar um body, a resposta será uma lista contendo todos os usuários cadastrados.

### Listagem de Pets

GET /pets

Não é necessário passar um body, a resposta será uma lista contendo todos os pets cadastrados.

É possível aplicar um filtro para listar apenas os pets pertencentes a algum usuário específico, fazemos isso utilizando o ID do usuário:

GET /pets?userId={userId}

## Endpoints que precisam de autenticação

É necessário passar um token para realizar uma requisição bem sucedida nos seguintes endpoints:

### Cadastro de Pets

POST /pets

{
"name": "Dodó",
"animal": "raposa",
"userId": 2
}

Resposta da API:

{
"name": "Dodó",
"animal": "raposa",
"userId": 2,
"id": 5
}

É necessário passar o "userId", é o ID do usuário cadastrado na API que é dono do pet.

### Edição de Pets

PATCH /pets/{id}

{
"name": "Toby"
}

É possível usar esse endpoint para editar as informações de um pet já cadastrado, no exemplo acima, o nome do pet está sendo atualizado.

### Exclusão de Pets

DELETE /pets/{id}

Não é necessário passar um body, o pet com id correspondente será removido da API.
