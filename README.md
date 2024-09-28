# Spring Boot JWT Authentication

Este projeto implementa autenticação e autorização usando JSON Web Tokens (JWT) com Spring Boot. Ele segue a arquitetura Model-View-Controller (MVC).

## Tecnologias Utilizadas

- **Spring Boot** (versão 3.x)
- **JWT** (versão 0.12.6)
- **Spring Security**
- **Lombok**
- **H2 Database** (para testes de banco de dados)
- **Maven** (para gerenciamento de dependências)

## Funcionalidades

- Autenticação de usuários usando JWT.
- Proteção de rotas com filtros de autorização JWT.
- Geração de tokens JWT após login bem-sucedido.
- Verificação automática de validade de tokens.
- Exemplo de configuração de segurança personalizada, permitindo acesso somente às páginas do banco H2.

## Como Executar o Projeto

### Pré-requisitos

Certifique-se de que você tenha instalado o seguinte:

- [JDK 17+]
- [Maven]


### Rotas
- **Rota pública** - `/api/test/all` - Conteúdo público para teste sem necessidade de autenticação.
- `/api/auth/signin` - Endpoint para autenticação (requer usuário e senha).
- `/api/auth/signup` - Endpoint para registrar novos usuários.
- **Rotas protegidas** - Qualquer rota protegida requer um token JWT no cabeçalho `Authorization: Bearer <TOKEN>`.

### Para testes, executar primeiro no banco os seguintes inserts:

INSERT INTO roles(name) VALUES('ROLE_USER');  
INSERT INTO roles(name) VALUES('ROLE_MODERATOR');  
INSERT INTO roles(name) VALUES('ROLE_ADMIN');  

## Exemplos de Requisições

### Registro de Usuário

POST /api/auth/signup  
Content-Type: application/json  

{  
  "username": "novousuario",  
  "password": "senhaforte",  
  "email": "email@email.com",  
  "role": ["user", "mod", "admin"]  
}

### Login de Usuário

POST /api/auth/signin  
Content-Type: application/json  

{  
  "username": "novousuario",  
  "password": "senhaforte"  
}  

**Resposta (JWT Token):**  

{  
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."  
}  

## Acessando Rotas Protegidas  
Para acessar qualquer rota protegida, envie o JWT no cabeçalho da requisição:  

GET /api/test/user  
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...


