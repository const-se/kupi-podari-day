# Auth

## /signin

Метод: `POST`

Параметры:

- `username: string`
- `password: string`

Ответ:

```json
{
  "access_token": "..."
}
```

## /signup

Метод: `POST`

Параметры:

- `username: string`
- `about: string`
- `avatar?: string`
- `email: string`
- `password: string`

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
