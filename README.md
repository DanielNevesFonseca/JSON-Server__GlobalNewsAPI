<h1 align="center">
  Global News - API
</h1>

<p align="center">
  <a href="#endpoints">Endpoints</a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</p>

A API tem um total de 13 endpoints, sendo em volta principalmente do usuário (dev) - podendo cadastrar seu perfil, tecnologias que estuda e trabalhos realizados. <br/>

A url base da API é https://kenzie-feed-api.onrender.com/

## Rotas que não precisam de autenticação

<h2 align ='center'> Listagem de posts </h2>

Nessa aplicação o usuário sem fazer login ou se cadastrar pode ver os produtos já cadastrados na plataforma, na API podemos acessar a lista dessa forma:

`GET /posts?_embed=likes - FORMATO DA RESPOSTA - STATUS 200`

```json
[
  {
    "title": "5 lugares para viajar nas próximas férias de verão",
    "description": "At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque corrupti quos dolores et quas molestias excepturi sint occaecati cupiditate non provident, similique sunt in culpa qui officia deserunt mollitia animi, id est laborum et dolorum fuga. Et harum quidem rerum facilis est et expedita distinctio. Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil impedit quo minus id quod maxime placeat facere possimus, omnis voluptas assumenda est, omnis dolor repellendus. Temporibus autem quibusdam et aut officiis debitis aut rerum necessitatibus saepe eveniet ut et voluptates repudiandae sint et molestiae non recusandae. Itaque earum rerum hic tenetur a sapiente delectus, ut aut reiciendis voluptatibus maiores alias consequatur aut perferendis doloribus asperiores repellat.",
    "owner": "Roberto Silva",
    "userId": 1,
    "id": 2,
    "image": "https://res.cloudinary.com/dsbkp5841/image/upload/v1688391686/Rectangle_4_lvbqtd.jpg"
    "likes": []
  }
]
```

Também é possível acessar um produto específico passando o id para rota:

`GET /posts/:id?_embed=likes - FORMATO DA RESPOSTA - STATUS 200`
```json
{
  "title": "5 lugares para viajar nas próximas férias de verão",
  "description": "At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque corrupti quos dolores et quas molestias excepturi sint occaecati cupiditate non provident, similique sunt in culpa qui officia deserunt mollitia animi, id est laborum et dolorum fuga. Et harum quidem rerum facilis est et expedita distinctio. Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil impedit quo minus id quod maxime placeat facere possimus, omnis voluptas assumenda est, omnis dolor repellendus. Temporibus autem quibusdam et aut officiis debitis aut rerum necessitatibus saepe eveniet ut et voluptates repudiandae sint et molestiae non recusandae. Itaque earum rerum hic tenetur a sapiente delectus, ut aut reiciendis voluptatibus maiores alias consequatur aut perferendis doloribus asperiores repellat.",
  "owner": "Roberto Silva",
  "userId": 1,
  "id": 2,
  "image": "https://res.cloudinary.com/dsbkp5841/image/upload/v1688391686/Rectangle_4_lvbqtd.jpg",
  "likes": []
}
```

<h2 align ='center'> Criação de usuário </h2>

`POST /users - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "johndoe@email.com",
  "password": "123456",
  "name": "John Doe",
}
```

Caso dê tudo certo, a resposta será assim:

`POST /users - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImpvaG5kb2VAZW1haWwuY29tIiwiaWF0IjoxNjg3ODA4MTYzLCJleHAiOjE2ODc4MTE3NjMsInN1YiI6IjMifQ.nWj1gqD4t3x00UTQvfFiK-PQjcgSpzbGeHknpncgC9E",
  "user": {
    "email": "johndoe@email.com",
    "name": "John Doe",
    "id": 3
  }
}
```


<h2 align = "center"> Login </h2>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "johndoe@email.com",
  "password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImpvaG5kb2VAZW1haWwuY29tIiwiaWF0IjoxNjg3ODA4MTYzLCJleHAiOjE2ODc4MTE3NjMsInN1YiI6IjMifQ.nWj1gqD4t3x00UTQvfFiK-PQjcgSpzbGeHknpncgC9E",
  "user": {
    "email": "johndoe@email.com",
    "name": "John Doe",
    "id": 3
  }
}
```

## Rotas que necessitam de autorização

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}


<h2 align ='center'> Cadastrar post </h2>

`POST /posts - FORMATO DA REQUISIÇÃO`

```json
{
  "title": "4 lugares para viajar nas próximas férias de verão",
  "description": "At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque corrupti quos dolores et quas molestias excepturi sint occaecati cupiditate non provident, similique sunt in culpa qui officia deserunt mollitia animi, id est laborum et dolorum fuga. Et harum quidem rerum facilis est et expedita distinctio. Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil impedit quo minus id quod maxime placeat facere possimus, omnis voluptas assumenda est, omnis dolor repellendus. Temporibus autem quibusdam et aut officiis debitis aut rerum necessitatibus saepe eveniet ut et voluptates repudiandae sint et molestiae non recusandae. Itaque earum rerum hic tenetur a sapiente delectus, ut aut reiciendis voluptatibus maiores alias consequatur aut perferendis doloribus asperiores repellat.",
  "owner": "Roberto Silva",
  "userId": 1,
  "image": "https://res.cloudinary.com/dsbkp5841/image/upload/v1688391686/Rectangle_4_lvbqtd.jpg"
}
```

<h2 align ='center'> Atualizar post </h2>

`PUT /posts/:id - FORMATO DA REQUISIÇÃO`

```json
{
  "title": "4 lugares para viajar nas próximas férias de verão",
  "description": "At vero eos et accusamus et iusto odio dignissimos ducimus qui blanditiis praesentium voluptatum deleniti atque corrupti quos dolores et quas molestias excepturi sint occaecati cupiditate non provident, similique sunt in culpa qui officia deserunt mollitia animi, id est laborum et dolorum fuga. Et harum quidem rerum facilis est et expedita distinctio. Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil impedit quo minus id quod maxime placeat facere possimus, omnis voluptas assumenda est, omnis dolor repellendus. Temporibus autem quibusdam et aut officiis debitis aut rerum necessitatibus saepe eveniet ut et voluptates repudiandae sint et molestiae non recusandae. Itaque earum rerum hic tenetur a sapiente delectus, ut aut reiciendis voluptatibus maiores alias consequatur aut perferendis doloribus asperiores repellat.",
  "owner": "Roberto Silva",
  "userId": 1,
  "image": "https://res.cloudinary.com/dsbkp5841/image/upload/v1688391686/Rectangle_4_lvbqtd.jpg"
}
```

Também é possível deletar um post, utilizando este endpoint:

`DELETE /posts/:id`

```
Não é necessário um corpo da requisição.
```

Like em um post:

`POST /likes`

```json
{
  "userId": 1,
  "postId": 2
}
```

Deslike em um post:

`DELETE /likes/:id`

```
Não é necessário um corpo da requisição.
```
