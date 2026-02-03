# 🍕 FastAPI Restaurant Order System | Sistema de Pedidos de Restaurante

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.128.0-green.svg)](https://fastapi.tiangolo.com)
[![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-2.0-red.svg)](https://www.sqlalchemy.org)

[🇧🇷 Português](#português) | [🇺🇸 English](#english)

---

## 🇧🇷 Português

### 📝 Sobre o Projeto

Este é um projeto de portfólio desenvolvido durante meus estudos de APIs RESTful com FastAPI. O sistema simula o backend completo de um restaurante, incluindo autenticação de usuários, gerenciamento de pedidos e itens.

**Objetivo:** Demonstrar conhecimentos práticos em desenvolvimento de APIs, autenticação JWT, modelagem de banco de dados e boas práticas de desenvolvimento backend.

### ✨ Funcionalidades

#### 🔐 Autenticação
- Cadastro de usuários com senha criptografada (bcrypt)
- Sistema de login com JWT (JSON Web Token)
- Tokens de acesso e refresh
- Autenticação OAuth2

#### 📦 Gerenciamento de Pedidos
- Criar novos pedidos
- Adicionar/remover itens do pedido
- Cancelar pedidos
- Finalizar pedidos
- Visualizar pedidos (individual e lista completa)
- Cálculo automático de preços
- Sistema de permissões (usuário/admin)

### 🛠️ Tecnologias Utilizadas

- **FastAPI** - Framework web moderno e rápido
- **SQLAlchemy** - ORM para manipulação do banco de dados
- **Alembic** - Migrações de banco de dados
- **SQLite** - Banco de dados (desenvolvimento)
- **Pydantic** - Validação de dados
- **JWT (python-jose)** - Autenticação e autorização
- **Passlib + bcrypt** - Criptografia de senhas
- **Python-dotenv** - Gerenciamento de variáveis de ambiente

### 📊 Estrutura do Banco de Dados

```
usuarios (Users)
├── id (PK)
├── nome
├── email
├── senha (encrypted)
├── ativo
└── admin

pedidos (Orders)
├── id (PK)
├── status (PENDENTE/CANCELADO/FINALIZADO)
├── usuario (FK)
└── preco

itens_pedido (Order Items)
├── id (PK)
├── quantidade
├── sabor
├── tamanho
├── preco_unitario
└── pedido (FK)
```

### 🚀 Como Executar

1. **Clone o repositório**
```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
```

2. **Crie um ambiente virtual**
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

3. **Instale as dependências**
```bash
pip install -r requirements.txt
```

4. **Configure as variáveis de ambiente**

Crie um arquivo `.env` na raiz do projeto:
```env
SECRET_KEY=sua_chave_secreta_aqui
ALGORITHM=HS256
ACESS_TOKEN_EXPIRE_MINUTES=30
```

5. **Execute as migrações**
```bash
alembic upgrade head
```

6. **Inicie o servidor**
```bash
uvicorn main:app --reload
```

7. **Acesse a documentação interativa**
- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`

### 📚 Endpoints Principais

#### Autenticação (`/auth`)
- `POST /auth/criar_conta` - Criar nova conta
- `POST /auth/login` - Login (retorna tokens JWT)
- `POST /auth/login-form` - Login via formulário OAuth2
- `GET /auth/refresh` - Renovar token de acesso

#### Pedidos (`/pedidos`)
- `POST /pedidos/pedido` - Criar novo pedido
- `POST /pedidos/pedido/adicionar-item/{id_pedido}` - Adicionar item
- `POST /pedidos/pedido/remover-item/{id_item_pedido}` - Remover item
- `POST /pedidos/pedido/cancelar/{id_pedido}` - Cancelar pedido
- `POST /pedidos/pedido/finalizar/{id_pedido}` - Finalizar pedido
- `GET /pedidos/pedido/{id_pedido}` - Visualizar pedido específico
- `GET /pedidos/listar` - Listar todos (apenas admin)
- `GET /pedidos/listar/pedidos-usuario` - Listar pedidos do usuário

### 🎓 Aprendizados

Este projeto me permitiu desenvolver e consolidar conhecimentos em:
- Arquitetura REST API
- Autenticação e autorização com JWT
- ORM e modelagem de banco de dados
- Validação de dados com Pydantic
- Tratamento de exceções e erros HTTP
- Documentação automática de APIs
- Boas práticas de segurança (criptografia, tokens)

### 📄 Licença

Este é um projeto educacional desenvolvido para fins de portfólio.

---

## 🇺🇸 English

### 📝 About the Project

This is a portfolio project developed during my studies of RESTful APIs with FastAPI. The system simulates a complete restaurant backend, including user authentication, order management, and items.

**Goal:** Demonstrate practical knowledge in API development, JWT authentication, database modeling, and backend development best practices.

### ✨ Features

#### 🔐 Authentication
- User registration with encrypted passwords (bcrypt)
- Login system with JWT (JSON Web Token)
- Access and refresh tokens
- OAuth2 authentication

#### 📦 Order Management
- Create new orders
- Add/remove items from orders
- Cancel orders
- Complete orders
- View orders (individual and complete list)
- Automatic price calculation
- Permission system (user/admin)

### 🛠️ Technologies Used

- **FastAPI** - Modern and fast web framework
- **SQLAlchemy** - ORM for database manipulation
- **Alembic** - Database migrations
- **SQLite** - Database (development)
- **Pydantic** - Data validation
- **JWT (python-jose)** - Authentication and authorization
- **Passlib + bcrypt** - Password encryption
- **Python-dotenv** - Environment variables management

### 📊 Database Structure

```
usuarios (Users)
├── id (PK)
├── nome (name)
├── email
├── senha (password - encrypted)
├── ativo (active)
└── admin

pedidos (Orders)
├── id (PK)
├── status (PENDING/CANCELLED/COMPLETED)
├── usuario (user - FK)
└── preco (price)

itens_pedido (Order Items)
├── id (PK)
├── quantidade (quantity)
├── sabor (flavor)
├── tamanho (size)
├── preco_unitario (unit_price)
└── pedido (order - FK)
```

### 🚀 How to Run

1. **Clone the repository**
```bash
git clone https://github.com/your-username/your-repository.git
cd your-repository
```

2. **Create a virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure environment variables**

Create a `.env` file in the project root:
```env
SECRET_KEY=your_secret_key_here
ALGORITHM=HS256
ACESS_TOKEN_EXPIRE_MINUTES=30
```

5. **Run migrations**
```bash
alembic upgrade head
```

6. **Start the server**
```bash
uvicorn main:app --reload
```

7. **Access interactive documentation**
- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`

### 📚 Main Endpoints

#### Authentication (`/auth`)
- `POST /auth/criar_conta` - Create new account
- `POST /auth/login` - Login (returns JWT tokens)
- `POST /auth/login-form` - Login via OAuth2 form
- `GET /auth/refresh` - Refresh access token

#### Orders (`/pedidos`)
- `POST /pedidos/pedido` - Create new order
- `POST /pedidos/pedido/adicionar-item/{id_pedido}` - Add item
- `POST /pedidos/pedido/remover-item/{id_item_pedido}` - Remove item
- `POST /pedidos/pedido/cancelar/{id_pedido}` - Cancel order
- `POST /pedidos/pedido/finalizar/{id_pedido}` - Complete order
- `GET /pedidos/pedido/{id_pedido}` - View specific order
- `GET /pedidos/listar` - List all (admin only)
- `GET /pedidos/listar/pedidos-usuario` - List user's orders

### 🎓 Learning Outcomes

This project allowed me to develop and consolidate knowledge in:
- REST API architecture
- Authentication and authorization with JWT
- ORM and database modeling
- Data validation with Pydantic
- Exception handling and HTTP errors
- Automatic API documentation
- Security best practices (encryption, tokens)

### 📄 License

This is an educational project developed for portfolio purposes.

---

**Made with ❤️ for learning and demonstration purposes**
