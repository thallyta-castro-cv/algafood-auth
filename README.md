# Authorization Server - AlgaFood API

Este é um **Authorization Server** desenvolvido com **Spring Security OAuth2**, usando **Java 17** e **Spring Boot 2.7.4**. Ele é parte de uma aplicação maior, o projeto **AlgaFood API**, que atua como **Resource Server**. Este projeto tem o objetivo didático de entender o funcionamento da **autenticação** e **autorização** com OAuth2 em um cenário legado, já que o Spring mudou recentemente a abordagem para o gerenciamento de Authorization Servers.

## Objetivo

O projeto tem como principal objetivo:

- Prover um Authorization Server que emite tokens OAuth2 para proteger APIs da AlgaFood.
- Servir como uma referência para **gerenciamento de Authorization Server** em projetos legados que ainda utilizam **Spring Security OAuth2**.
- Auxiliar no entendimento do fluxo de autenticação e autorização com **OAuth2**.
- Facilitar a transição futura para as novas versões do Spring Authorization Server.

## Tecnologias Utilizadas

- **Java 17**
- **Spring Boot 2.7.4**
- **Spring Security OAuth2**
- **JWT (JSON Web Tokens)** para autenticação e autorização
- **Maven** como ferramenta de build

## Estrutura do Projeto

O projeto é composto pelos seguintes módulos:

1. **Authorization Server**: Responsável pela emissão e validação dos tokens.
2. **Resource Server (AlgaFood API)**: Uma API protegida que utiliza os tokens gerados pelo Authorization Server.

## Funcionalidades

- **Autenticação**: Gera tokens de acesso (Access Tokens) baseados no protocolo OAuth2.
- **Autorização**: Protege recursos utilizando escopos e roles associadas ao token.
- **Suporte a múltiplos Grant Types**:
  - Authorization Code
  - Password Credentials (somente para fins de teste)
  - Client Credentials
- **Armazenamento de Tokens**: Armazena os tokens em memória, mas pode ser facilmente configurado para armazenar tokens em um banco de dados externo.

## Fluxo de Autenticação

1. O cliente (ex: uma aplicação frontend) faz uma requisição para o **Authorization Server** solicitando um token de acesso.
2. O **Authorization Server** autentica o cliente e emite um **Access Token**.
3. O cliente utiliza esse **Access Token** para acessar recursos protegidos na **AlgaFood API** (Resource Server).
4. A **AlgaFood API** valida o token e, se for válido, permite o acesso ao recurso solicitado.

## Como Executar o Projeto

### Pré-requisitos

- **Java 17**
- **Maven**

### Passos para execução:

1. Instale as dependências e execute o projeto:

   ```bash
   mvn clean install
   mvn spring-boot:run
   ```
2. A aplicação será iniciada em http://localhost:8081.

## Endpoints

- `/oauth/token`: Endpoint para obtenção de tokens de acesso.

### Exemplo de Requisição para Obtenção de Token

```bash
curl -X POST \
  http://localhost:8080/oauth/token \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'grant_type=password&username=admin&password=admin&client_id=algafood-client&client_secret=algafood-secret'
```

# Autor
<b>Thallyta Macedo Carvalho de Castro</b>

Linkedin: https://www.linkedin.com/in/thallyta-castro/

Medium: https://medium.com/@thallyta-castro-cv

email: thallytacastro.dev@gmail.com
