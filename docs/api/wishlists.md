# Wishlists

## /wishlistlists

Метод: `GET`

Ответ:

```json
[
  {
    "id": 123,
    "createdAt": "...",
    "updatedAt": "...",
    "name": "...",
    "description": "...",
    "image": "...",
    "owner": {
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
```

---

Метод: `POST`

Параметры:

- `name: string`
- `description: string`
- `image: string`
- `itemsId: number[]`

Ответ:

```json
{
  "id": 123,
  "createdAt": "...",
  "updatedAt": "...",
  "name": "...",
  "description": "...",
  "image": "..."
}
```

## /wishlistlists/:id

Метод: `GET`

Ответ:

```json
[
  {
    "id": 123,
    "createdAt": "...",
    "updatedAt": "...",
    "name": "...",
    "description": "...",
    "image": "...",
    "owner": {
      "id": 123,
      "createdAt": "...",
      "updatedAt": "...",
      "username": "...",
      "about": "...",
      "avatar": "..."
    },
    "items": [
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
  },
  ...
]
```

---

Метод: `PATCH`

Параметры:

- `name: string`
- `description: string`
- `image: string`
- `itemsId: number[]`

Ответ:

```json
{
  "id": 123,
  "createdAt": "...",
  "updatedAt": "...",
  "name": "...",
  "description": "...",
  "image": "..."
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
  "description": "...",
  "image": "..."
}
```
