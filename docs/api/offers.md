# Offers

## /offers

Метод: `GET`

Ответ:

```json
[
  {
    "id": 123,
    "createdAt": "...",
    "updatedAt": "...",
    "amount": "...",
    "hidden": true
  },
  ...
]
```

---

Метод: `POST`

Параметры:

- `amount: number`
- `hidden: boolean`
- `itemId: number`

Ответ:

```json
{
  "id": 123,
  "createdAt": "...",
  "updatedAt": "...",
  "amount": "...",
  "hidden": true
}
```

## /offers/:id

Метод: `GET`

Ответ:

```json
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
  },
  "item": {
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
}
```
