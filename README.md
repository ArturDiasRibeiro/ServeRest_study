# Testes de API - ServeRest (Postman)

Projeto de estudos e prática de testes funcionais e automatizados de API REST utilizando a API pública [ServeRest](https://serverest.dev).

## Cenários Cobertos (CRUD de Usuários)
- **GET `/usuarios`**: Validação de status `200 OK` e estrutura da lista retornada.
- **POST `/usuarios`**: Criação de usuário (`201 Created`), captura dinâmica do `_id` via variável de coleção (`userId`) e validação de regra de negócio para e-mail duplicado (`400 Bad Request`).
- **PUT `/usuarios/{{userId}}`**: Atualização de dados cadastrais (`200 OK`).
- **DELETE `/usuarios/{{userId}}`**: Exclusão do registro criado para limpeza de massa de dados (`200 OK`) e validação de comportamento em exclusão repetida.

## Como Executar
1. Importe o ficheiro `.json` da collection no **Postman**.
2. Execute a collection completa através do **Collection Runner** para validar o fluxo encadeado de ponta a ponta.
