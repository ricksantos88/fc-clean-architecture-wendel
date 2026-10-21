# FC Clean Architecture - Desafio Clean Architecture: API de Listagem de Produtos

Projeto desenvolvido no curso Full Cycle - Clean Architecture.

## Tecnologias
- Node.js & TypeScript
- Express
- Sequelize & SQLite in-memory
- Supertest & Jest
- jstoxml

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
