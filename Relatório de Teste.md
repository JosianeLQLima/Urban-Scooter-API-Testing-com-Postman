# Caso de Teste 032 – Validação do campo `password` contendo caracteres especiais

## Objetivo

Verificar se a API impede a criação de um entregador quando o campo **`password`** contém caracteres especiais.

---

## Informações do Teste

| Campo             | Valor                  |
| ----------------- | ---------------------- |
| **ID**            | CT-032                 |
| **Endpoint**      | `POST /api/v1/courier` |
| **Método HTTP**   | `POST`                 |
| **Ferramenta**    | Postman                |
| **Tipo de Teste** | Teste Negativo         |
| **Status**        | ❌ Reprovado            |

---

## Pré-condições

* A API Urban Scooter deve estar disponível.
* O endpoint **`POST /api/v1/courier`** deve estar acessível.

---

## Dados de Teste

### Corpo da Requisição

```json
{
    "login": "Carlos",
    "firstName": "Pedro",
    "password": "12#4"
}
```

---

## Passos para Execução

1. Abrir o Postman.
2. Criar uma requisição **POST** para o endpoint **`/api/v1/courier`**.
3. Adicionar o cabeçalho:

```text
Content-Type: application/json
```

4. Enviar o corpo da requisição.
5. Verificar o código de status e o corpo da resposta.

---

## Resultado Esperado

A API deve rejeitar a criação do entregador quando o campo **`password`** contém caracteres especiais.

**Status esperado:**

```text
400 Bad Request
```

**Resposta esperada:**

```json
{
    "message": "Não há dados suficientes para criar uma conta"
}
```

---

## Resultado Obtido

A API aceitou a criação do entregador com o campo **`password`** contendo caracteres especiais, retornando:

```text
201 Created
```

O usuário foi cadastrado com sucesso, mesmo utilizando a senha **"12#4"**, que não atende à regra de negócio.

---

## Resultado do Teste

**❌ REPROVADO**

A API não valida corretamente o campo **`password`**, permitindo caracteres especiais em um campo que deveria aceitar apenas dígitos numéricos.

---

## Evidências

* Resposta da API no Postman.
* Código HTTP retornado: **201 Created**.
* Payload utilizado durante a execução do teste.

