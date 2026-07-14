# Bug Report

## Título

**POST /api/v1/courier - Está sendo possível criar entregador com `password` contendo caracteres especiais na requisição**

## Descrição do Bug

O bug ocorre no endpoint **POST /api/v1/courier** da API do Urban Scooter. Ao enviar uma requisição para criar um entregador com o campo **`password`** contendo caracteres especiais, a API permite a criação da conta, mesmo que a regra de negócio determine que a senha deve conter apenas dígitos numéricos.

---

## Ambiente

* **Aplicação:** Urban Scooter API
* **Ferramenta:** Postman
* **Método HTTP:** `POST`
* **Endpoint:** `/api/v1/courier`
* **Content-Type:** `application/json`

---

## Passos para Reproduzir

### Requisição JSON

```json
{
  "login": "Carlos",
  "firstName": "Pedro",
  "password": "12#4"
}
```

### cURL

```bash
curl --location 'https://cnt-bd423384-768f-4532-a8f2-d3c6cf270d18.containerhub.tripleten-services.com/api/v1/courier' \
--header 'Content-Type: application/json' \
--data-raw '{
    "login":"Carlos",
    "firstName":"Pedro",
    "password":"12#4"
}'
```

---

## Resultado Esperado

A API deve validar o campo **`password`** e rejeitar valores que contenham caracteres especiais.

**Status Code:** `400 Bad Request`

```json
{
  "message": "Não há dados suficientes para criar uma conta"
}
```

---

## Resultado Atual

A API aceita a criação do entregador com o campo **`password`** contendo caracteres especiais, retornando **201 Created** e cadastrando a conta, mesmo que o valor informado (`12#4`) não atenda à regra de negócio.

---

## Severidade

**Alta** – Permite o cadastro de usuários com dados que violam as regras de validação da aplicação.

## Prioridade

**Alta**

## Evidência

* Captura de tela da resposta no Postman.
* Coleção do Postman contendo a requisição.
