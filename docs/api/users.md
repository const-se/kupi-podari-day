# Users

## /users/me

Метод: `GET`

Ответ:

```json
{
  "id": 123,
  "createdAt": "...",
  "updatedAt": "...",
  "username": "...",
  "about": "...",
  "avatar": "...",
  "email": "..."
}
```

---

Метод: `PATCH`

Параметры:

- `avatar?: string`
- `about?: string`
- `email?: string`
- `password? string`
- `username?: string`

Ответ:

```json
{
  "id": 123,
  "createdAt": "...",
  "updatedAt": "...",
  "username": "...",
  "about": "...",
  "avatar": "...",
  "email": "..."
}
```

## /users/me/wishes

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

## /users/:username

Метод: `GET`

Ответ:

```json
{
  "id": 123,
  "createdAt": "...",
  "updatedAt": "...",
  "username": "...",
  "about": "...",
  "avatar": "..."
}
```

## /users/:username/wishes

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

## /users/find

Метод: `POST`

Параметры:

- `query: string`

Ответ:

```json
[
  {
    "id": 123,
    "createdAt": "...",
    "updatedAt": "...",
    "username": "...",
    "about": "...",
    "avatar": "..."
  },
  ...
]
```
