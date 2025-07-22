# Documentação da API FastAPI

## Descrição geral

O código fornece uma API RESTful simples construída com FastAPI e Pydantic. O objetivo desta API é permitir a criação e leitura de 'itens'. Cada 'item' consiste em três propriedades: nome, descrição e preço.

## Dependências

- FastAPI
- Pydantic

Instale as dependências usando o pip:

```bash
pip install fastapi[all]
pip install pydantic
```

## Parâmetros e tipos

### Classe Item

A classe Item é um modelo Pydantic que define a estrutura de um 'item'. Consiste em três campos:

- `name`: Nome do item. Deve ser uma string.
- `description`: Descrição do item. Deve ser uma string.
- `price`: Preço do item. Deve ser um número flutuante.

### Endpoints

- POST `/items/`: Cria um novo item. Aceita um objeto 'item' no corpo da solicitação.
- GET `/items/`: Retorna uma lista de todos os itens.
- GET `/items/{item_id}`: Retorna um item específico. Aceita um `item_id` como parâmetro de caminho.

## Exemplos de uso

### Criando um item

```bash
curl -X POST "http://localhost:8000/items/" -H "accept: application/json" -H "Content-Type: application/json" -d "{\"name\":\"Item1\",\"description\":\"This is an item\",\"price\":10.5}"
```

### Lendo todos os itens

```bash
curl -X GET "http://localhost:8000/items/" -H "accept: application/json"
```

### Lendo um item específico

```bash
curl -X GET "http://localhost:8000/items/0" -H "accept: application/json"
```

## Notas importantes

- A API não persiste os itens. Ou seja, se o servidor for reiniciado, todos os itens serão perdidos.
- O `item_id` é baseado no índice do item na lista de itens. Portanto, não é uma identificação única ou persistente.

## Execução

Para executar o servidor localmente, você pode usar o comando uvicorn:

```bash
uvicorn main:app --reload
```

Onde `main` é o nome do seu arquivo Python.

Visite `http://localhost:8000/docs` no navegador para ver a documentação interativa da API Swagger.