# json-server-base

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth para ser usada no desenvolvimento da API de cursos.

## Endpoints

Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 3 endpoints que podem ser utilizados para cadastro e 2 endpoints que podem ser usados para login. Adicionalmente há 2 endpoints para iniciar, contendo a lista de cursos e a lista de disciplinas.

## Cadastro

POST /register <br/>
POST /signup <br/>
POST /users <br/><br/>
Formato da requisição:

```json
{
  "email": "kenzinho@mail.com",
  "password": "123456",
  "name": "Kenzinho",
  "age": 38
}
```

Formato da resposta:

```json
{
  "email": "kenzinho@mail.com",
  "password": "$2a$10$YQiiz0ANVwIgpOjYXPxc0O9H2XeX3m8OoY1xk7OGgxTnOJnsZU7FO",
  "name": "Kenzinho",
  "age": 38,
  "id": 1
}
```

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.

## Login

POST /login <br/>
POST /signin <br/><br/>
Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"

Formato da requisição:

```json
{
  "email": "kenzinho@mail.com",
  "password": "123456",
  "name": "Kenzinho",
  "age": 38
}
```

Formato da resposta:

```json
{
  "email": "kenzinho@mail.com",
  "password": "$2a$10$YQiiz0ANVwIgpOjYXPxc0O9H2XeX3m8OoY1xk7OGgxTnOJnsZU7FO",
  "name": "Kenzinho",
  "age": 38,
  "id": 1
}
```

## Curso

Quando logado, você cria seu curso para poder ter acesso à quais disciplinas quer adicionar

### Ver todos os cursos:

GET /courses <br/><br/>
Formato da resposta:

```json
[
  {
    "course_name": "front end developer",
    "course_description": "developing for the future",
    "id": 1
  },
  {
    "course_name": "backend end developer",
    "course_description": "backing to the future",
    "id": 2
  }
]
```

### Adicionar curso:

POST /courses <br/><br/>
Formato de envio do JSON:

```json
{
  "course_name": "backend end developer",
  "course_description": "backing to the future",
  "userId: 2"
}
```

Formato da resposta:

```json
{
  "course_name": "backend end developer",
  "course_description": "backing to the future",
  "userId: 2"
  "id": 3
}
```

### Atualizar curso:

PATCH /courses/:course_id <br/><br/>
Formato de envio do JSON:

```json
{
  "course_description": "new description"
}
```

Formato da resposta:

```json
{
  "course_description": "new description"
}
```

### Excluir cursos:

DELETE /courses/:course_id <br/>
Nota: não é necessário um corpo da requisição (JSON)

## Disciplina

Quando logado, você cria sua disciplinas para poder associar aos cursos (você também pode consultar todas as disciplinas mesmo não logado)

### Ver todas as disciplinas:

GET /disciplinas <br/><br/>
Formato da resposta:

```json
[
  {
    "discipline_name": "react",
    "discipline_description": "create interfaces",
    "id": 1
  },
  {
    "discipline_name": "node",
    "discipline_description": "build scalable applications",
    "id": 2
  }
]
```

### Adicionar disciplina:

POST /disciplinas <br/><br/>
Formato de envio do JSON:

```json
{
  "discipline_name": "react",
  "discipline_description": "create interfaces"
}
```

Formato da resposta:

```json
{
  "discipline_name": "react",
  "discipline_description": "create interfaces",
  "id": 1
}
```

### Atualizar disciplina:

PATCH /disciplinas/:discipline_id <br/><br/>
Formato de envio do JSON:

```json
{
  "discipline_description": "new description"
}
```

Formato da resposta:

```json
{
  "discipline_description": "new description"
}
```

### Excluir disciplinas:

DELETE /disciplinas/:discipline_id <br/>
Nota: não é necessário um corpo da requisição (JSON)
