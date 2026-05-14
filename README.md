# Projeto Pizzaria 🍕

Sistema full stack para gerenciamento de pedidos de uma pizzaria, desenvolvido com Node.js, React, Next.js, React Native, TypeScript e Prisma.

O projeto simula uma aplicação real de atendimento para pizzarias/restaurantes, permitindo o cadastro de usuários, autenticação, gerenciamento de categorias e produtos, criação de pedidos por mesa, adição e remoção de itens e acompanhamento dos pedidos até sua finalização.

Este projeto foi desenvolvido com base no projeto **Sujeito Pizzaria**, do curso **Projeto Completo NodeJS, React, React Native, TypeScript**, ministrado por Matheus Fraga na Udemy, com o objetivo de praticar uma aplicação completa envolvendo backend, frontend web e mobile.

---

## Demonstração

Aplicação web publicada:

```text
https://projeto-pizzaria.vercel.app
```

API utilizada pelo frontend:

```text
https://api-projetopizza.onrender.com
```

---

## Sobre o projeto

O **Projeto Pizzaria** é uma aplicação full stack dividida em três partes principais:

- **Backend:** API REST responsável por autenticação, regras de negócio, cadastro de produtos, categorias e controle dos pedidos.
- **Frontend:** painel web administrativo, usado para login, cadastro, gerenciamento de categorias, produtos e visualização de pedidos.
- **Mobile:** aplicação mobile voltada para o uso operacional, permitindo que pedidos sejam criados e enviados de forma mais prática no atendimento.

A proposta do sistema é representar o fluxo básico de uma pizzaria: o usuário acessa o sistema, cadastra categorias e produtos, registra pedidos por mesa, adiciona itens ao pedido e acompanha os pedidos enviados até a finalização.

---

## Funcionalidades

### Autenticação

O sistema possui cadastro e login de usuários. Após o login, o usuário recebe um token de autenticação, utilizado para acessar as rotas protegidas da aplicação.

Funcionalidades relacionadas:

- Cadastro de usuário.
- Login com e-mail e senha.
- Autenticação via JWT.
- Proteção de rotas no backend.
- Controle de sessão no frontend.

---

### Categorias

O painel permite cadastrar e listar categorias de produtos. As categorias servem para organizar o cardápio, por exemplo: pizzas, bebidas, sobremesas ou outros tipos de itens.

Funcionalidades relacionadas:

- Cadastro de categorias.
- Listagem de categorias.
- Associação de produtos a uma categoria.

---

### Produtos

O sistema permite cadastrar produtos com nome, preço, descrição, categoria e imagem. As imagens são enviadas para o backend usando upload de arquivos.

Funcionalidades relacionadas:

- Cadastro de produto.
- Upload de imagem do produto.
- Associação do produto a uma categoria.
- Listagem de produtos por categoria.

---

### Pedidos

A aplicação permite criar pedidos relacionados a uma mesa, adicionar produtos ao pedido, remover itens, enviar o pedido para preparo e finalizar pedidos.

Funcionalidades relacionadas:

- Criação de pedido por mesa.
- Adição de itens ao pedido.
- Remoção de itens do pedido.
- Envio do pedido.
- Listagem de pedidos abertos.
- Visualização dos detalhes de um pedido.
- Finalização de pedido.

---

## Tecnologias utilizadas

### Backend

- Node.js
- Express
- TypeScript
- Prisma ORM
- PostgreSQL
- JWT para autenticação
- BcryptJS para criptografia de senhas
- Multer para upload de imagens
- CORS
- Dotenv

### Frontend Web

- React
- Next.js
- TypeScript
- Axios
- Sass/SCSS
- Nookies
- React Toastify
- React Icons
- JWT Decode

### Mobile

- React Native
- Expo
- TypeScript
- Axios
- React Navigation
- Async Storage

---

## Estrutura do projeto

```text
Projeto_pizzaria/
├── backend/
│   ├── prisma/
│   │   ├── migrations/
│   │   └── schema.prisma
│   ├── src/
│   │   ├── config/
│   │   ├── controllers/
│   │   ├── middlewares/
│   │   ├── prisma/
│   │   ├── services/
│   │   ├── routes.ts
│   │   └── server.ts
│   ├── package.json
│   └── tsconfig.json
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── contexts/
│   │   ├── pages/
│   │   ├── services/
│   │   └── utils/
│   ├── styles/
│   ├── package.json
│   └── tsconfig.json
│
├── mobile/
│   ├── src/
│   │   ├── contexts/
│   │   ├── pages/
│   │   ├── routes/
│   │   └── services/
│   ├── package.json
│   └── tsconfig.json
│
└── README.md
```

---

## Modelagem do banco de dados

O banco de dados foi modelado com Prisma e PostgreSQL. As principais entidades da aplicação são:

### User

Representa o usuário do sistema, responsável por acessar o painel e utilizar as funcionalidades protegidas.

Campos principais:

- `id`
- `name`
- `email`
- `password`
- `created_at`
- `updated_at`

### Category

Representa uma categoria de produtos.

Campos principais:

- `id`
- `name`
- `created_at`
- `updated_at`

Relacionamento:

- Uma categoria pode possuir vários produtos.

### Product

Representa um produto cadastrado no cardápio.

Campos principais:

- `id`
- `name`
- `price`
- `description`
- `banner`
- `category_id`
- `created_at`
- `updated_at`

Relacionamento:

- Um produto pertence a uma categoria.
- Um produto pode estar presente em vários itens de pedido.

### Order

Representa um pedido feito por uma mesa.

Campos principais:

- `id`
- `table`
- `status`
- `draft`
- `name`
- `created_at`
- `updated_at`

Relacionamento:

- Um pedido pode possuir vários itens.

### Item

Representa um item dentro de um pedido.

Campos principais:

- `id`
- `amount`
- `order_id`
- `product_id`
- `created_at`
- `updated_at`

Relacionamento:

- Um item pertence a um pedido.
- Um item está associado a um produto.

---

## Rotas principais da API

### Usuários

```http
POST /users
POST /session
GET /me
```

### Categorias

```http
POST /category
GET /category
```

### Produtos

```http
POST /product
GET /category/product
```

### Pedidos

```http
POST /order
DELETE /order
POST /order/add
DELETE /order/remove
PUT /order/send
GET /orders
GET /order/detail
PUT /order/finish
```

---

## Como executar o projeto localmente

Antes de começar, é necessário ter instalado:

- Node.js
- Yarn ou npm
- PostgreSQL
- Expo CLI, caso deseje executar o app mobile

---

## Clonando o repositório

```bash
git clone https://github.com/MarioViniciusBC/Projeto_pizzaria.git
cd Projeto_pizzaria
```

---

## Configurando o backend

Acesse a pasta do backend:

```bash
cd backend
```

Instale as dependências:

```bash
yarn
```

Crie um arquivo `.env` na pasta `backend` com as variáveis necessárias:

```env
DATABASE_URL="postgresql://usuario:senha@localhost:5432/nome_do_banco"
SHADOW_DATABASE_URL="postgresql://usuario:senha@localhost:5432/nome_do_banco_shadow"
JWT_SECRET="sua_chave_secreta"
```

Execute as migrations do Prisma:

```bash
yarn prisma migrate dev
```

Gere o client do Prisma:

```bash
yarn prisma generate
```

Inicie o servidor:

```bash
yarn dev
```

Por padrão, a API roda em:

```text
http://localhost:3333
```

---

## Configurando o frontend

Em outro terminal, acesse a pasta do frontend:

```bash
cd frontend
```

Instale as dependências:

```bash
yarn
```

No arquivo de configuração da API, ajuste a `baseURL` caso queira usar o backend local:

```ts
baseURL: 'http://localhost:3333'
```

Depois, inicie o projeto:

```bash
yarn dev
```

O frontend ficará disponível em:

```text
http://localhost:3000
```

---

## Configurando o mobile

Em outro terminal, acesse a pasta do mobile:

```bash
cd mobile
```

Instale as dependências:

```bash
yarn
```

Inicie o Expo:

```bash
yarn start
```

Também é possível executar diretamente em Android, iOS ou web:

```bash
yarn android
yarn ios
yarn web
```

Caso esteja usando a API local, lembre-se de ajustar a URL da API no projeto mobile. Em dispositivos físicos, normalmente não se usa `localhost`, mas sim o IP da máquina na rede local.

Exemplo:

```text
http://192.168.0.10:3333
```

---

## Fluxo básico de uso

1. O usuário cria uma conta ou faz login.
2. O sistema autentica o usuário e salva o token.
3. O usuário cadastra categorias.
4. O usuário cadastra produtos associados às categorias.
5. Um pedido é criado para uma mesa.
6. Produtos são adicionados ao pedido.
7. O pedido é enviado para preparo.
8. O painel lista os pedidos abertos.
9. O pedido pode ser visualizado em detalhes.
10. O pedido é finalizado.

---

## Aprendizados do projeto

Este projeto foi importante para praticar conceitos essenciais de desenvolvimento full stack, como:

- Criação de API REST com Node.js e Express.
- Organização do backend em controllers, services, middlewares e rotas.
- Autenticação com JWT.
- Criptografia de senhas.
- Upload de arquivos.
- Integração com banco de dados usando Prisma.
- Modelagem de entidades e relacionamentos.
- Consumo de API no frontend e no mobile.
- Uso de SSR e controle de autenticação no Next.js.
- Gerenciamento de sessão com cookies.
- Navegação e autenticação em aplicação mobile.
- Organização de um projeto com múltiplas aplicações no mesmo repositório.

---

## Possíveis melhorias futuras

Algumas melhorias que poderiam ser implementadas futuramente:

- Tela pública de cardápio para clientes.
- Controle de permissões por tipo de usuário.
- Painel com métricas de vendas.
- Histórico de pedidos finalizados.
- Filtro de pedidos por status.
- Cadastro de adicionais e tamanhos de pizza.
- Integração com pagamentos.
- Testes automatizados.
- Docker para facilitar a configuração do ambiente.
- Documentação da API com Swagger ou Insomnia/Postman.

---

## Autor

Desenvolvido por **Mário Vinícius**.

GitHub:

```text
https://github.com/MarioViniciusBC
```

---

## Licença

Este projeto está sob a licença MIT.
