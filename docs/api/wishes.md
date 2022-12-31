# Wishes

## /wishes

Метод: `POST`

Параметры:

- `name: string`
- `link: string`
- `image: string`
- `price: number`
- `description: string`

Ответ:

```json
{
  "id": 123,
  "createdAt": "...",
  "updatedAt": "...",
  "name": "...",
  "link": "...",
  "image": "...",
  "price": 100,
  "raised": 50,
  "description": "...",
  "copied": 0
}
```

## /wishes/last

Метод: `GET`

Ответ:

```json
[
  {
    "id": 123,
    "createdAt": "...",
    "updatedAt": "...",
    "name": "...",
    "link": "...",
    "image": "...",
    "price": 100,
    "raised": 50,
    "description": "...",
    "copied": 0
  },
  ...
]
```

## /wishes/top

Метод: `GET`

Ответ:

```json
[
  {
    "id": 123,
    "createdAt": "...",
    "updatedAt": "...",
    "name": "...",
    "link": "...",
    "image": "...",
    "price": 100,
    "raised": 50,
    "description": "...",
    "copied": 0
  },
  ...
]
```

## /wishes/:id

Метод: `GET`

Ответ:

```json
{
  "id": 123,
  "createdAt": "...",
  "updatedAt": "...",
  "name": "...",
  "link": "...",
  "image": "...",
  "price": 100,
  "raised": 50,
  "description": "...",
  "copied": 0,
  "owner": {
    "id": 123,
    "createdAt": "...",
    "updatedAt": "...",
    "username": "...",
    "about": "...",
    "avatar": "..."
  },
  "offers": [
    {
      "id": 123,
      "createdAt": "...",
      "updatedAt": "...",
      "amount": "...",
      "hidden": true,
      "user": {
        "id": 123,
        "createdAt": "...",
        "updatedAt": "...",
        "username": "...",
        "about": "...",
        "avatar": "..."
      }
    },
    ...
  ]
}
```

---

Метод: `PATCH`

Параметры:

- `name: string`
- `link: string`
- `image: string`
- `price: number`
- `description: string`

Ответ:

```json
{
  "id": 123,
  "createdAt": "...",
  "updatedAt": "...",
  "name": "...",
  "link": "...",
  "image": "...",
  "price": 100,
  "raised": 50,
  "description": "...",
  "copied": 0
}
```

---

Метод: `DELETE`

Ответ:

```json
{
  "id": 123,
  "createdAt": "...",
  "updatedAt": "...",
  "name": "...",
  "link": "...",
  "image": "...",
  "price": 100,
  "raised": 50,
  "description": "...",
  "copied": 0
}
```

## /wishes/:id/copy

Метод: `POST`

Ответ:

```json
{
  "id": 123,
  "createdAt": "...",
  "updatedAt": "...",
  "name": "...",
  "link": "...",
  "image": "...",
  "price": 100,
  "raised": 50,
  "description": "...",
  "copied": 0
}
```
