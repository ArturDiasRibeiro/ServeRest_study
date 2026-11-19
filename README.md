# Testes de API e CI/CD - ServeRest

Suíte de testes automatizados de API REST utilizando **Postman**, **Newman** e **GitHub Actions**, validando fluxos completos na API pública [ServeRest](https://serverest.dev).

## Tecnologias Utilizadas
- **Postman**: Criação da collection, variáveis dinâmicas (`{{$randomInt}}`, `{{$randomEmail}}`), encadeamento de requisições e asserções em JavaScript.
- **Newman**: Execução da suíte de testes via linha de comando (CLI).
- **GitHub Actions**: Pipeline de Integração Contínua (CI) executado automaticamente a cada `push` ou `pull_request` na branch `main`.

## Cenários Cobertos

### 1. Autenticação (`/login`)
- **POST `/login`**: Autenticação de usuário administrador (`200 OK`) e captura dinâmica do token JWT (`authToken`) para autorização das rotas protegidas.

### 2. Usuários (`/usuarios`)
- **GET `/usuarios`**: Validação de status `200 OK` e estrutura da lista retornada.
- **POST `/usuarios`**: Cadastro de usuário (`201 Created`) com captura automática do `_id` (`userId`).
- **PUT `/usuarios/{{userId}}`**: Atualização cadastral com dados dinâmicos para evitar colisão na base compartilhada.
- **DELETE `/usuarios/{{userId}}`**: Exclusão do registro para limpeza de massa de dados (`200 OK`).

### 3. Produtos (`/produtos`)
- **POST `/produtos`**: Criação de produto autenticado via Bearer Token (`201 Created`), captura dinâmica do `productId` e validação de bloqueio sem token (`401 Unauthorized`).
- **GET `/produtos`**: Listagem de produtos (`200 OK`).
- **DELETE `/produtos/{{productId}}`**: Exclusão do produto criado (`200 OK`) garantindo a idempotência da suíte.

## Como Executar Localmente

1. Clone o repositório e acesse a pasta do projeto:
   ```bash
   git clone [https://github.com/ArturDiasRibeiro/ServeRest_study.git](https://github.com/ArturDiasRibeiro/ServeRest_study.git)
   cd ServeRest_study
