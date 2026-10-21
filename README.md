# FC Clean Architecture - Desafio Clean Architecture: Notification Pattern na Entidade Product

Projeto desenvolvido no curso Full Cycle - Clean Architecture.

## Tecnologias e Padrões
- Node.js & TypeScript
- Express
- Sequelize & SQLite in-memory
- Supertest & Jest
- Yup (Validação)
- **Notification Pattern** (acumulação de erros de domínio)

---

## Como executar

### 1. Instalação das dependências
```bash
npm install
```

### 2. Executar a aplicação
Para iniciar o servidor de desenvolvimento:
```bash
npm run dev
```
O servidor inicializará por padrão na porta `3000` (ou na porta configurada via `.env`).

---

## Notification Pattern na Entidade Product

A entidade `Product` foi refatorada para herdar de `Entity` e utilizar o **Notification Pattern**:
- As regras de validação são processadas via `ProductYupValidator` e instanciadas por `ProductValidatorFactory`.
- O validador não interrompe o fluxo no primeiro erro encontrado (`abortEarly: false`), acumulando todas as violações na propriedade `notification` com o contexto `product`.
- Caso haja erros acumulados, um `NotificationError` é lançado consolidando todas as mensagens (ex: `product: Name is required,product: Price must be greater than zero`).

---

## Endpoints

### Produto (`/product`)

- **POST `/product`**
  Cria um novo produto.
  - **Body (JSON):**
    ```json
    {
      "name": "Product 1",
      "price": 100
    }
    ```
  - **Status:** `200 OK`

- **GET `/product`**
  Lista todos os produtos cadastrados.
  - **JSON (`Accept: application/json` ou padrão):**
    ```json
    {
      "products": [
        {
          "id": "uuid",
          "name": "Product 1",
          "price": 100
        }
      ]
    }
    ```
  - **XML (`Accept: application/xml`):**
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <products>
      <product>
        <id>uuid</id>
        <name>Product 1</name>
        <price>100</price>
      </product>
    </products>
    ```

---

## Como rodar os testes

Para executar todos os testes da aplicação (unitários, de integração e End-to-End):
```bash
npm test
```
