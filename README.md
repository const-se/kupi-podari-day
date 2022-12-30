# КупиПодариДай

## Оглавление

- [Сущности](#сущности)
  - [User](#user)
  - [Wish](#wish)
  - [Wishlist](#wishlist)
  - [Offer](#offer)
- [Связи сущностей](#связи-сущностей)
- [API](#api)
  - [Auth](#auth)
    - [/signin](#signin)
    - [/signup](#signup)
  - [Users](#users)
    - [/users/me](#usersme)
    - [/users/me/wishes](#usersmewishes)
    - [/users/:username](#usersusername)
    - [/users/:username/wishes](#usersusernamewishes)
    - [/users/find](#usersfind)
  - [Wishes](#wishes)
    - [/wishes](#wishes-1)
    - [/wishes/last](#wisheslast)
    - [/wishes/top](#wishestop)
    - [/wishes/:id](#wishesid)
    - [/wishes/:id/copy](#wishesidcopy)
  - [Wishlists](#wishlists)
    - [/wishlistlists](#wishlistlists)
    - [/wishlistlists/:id](#wishlistlistsid)

## Сущности

### User

Свойства сущности и их особенности:

- **id:** `number`
  - Первичный ключ
- **createdAt:** `Date`
  - Дата создания
- **updatedAt:** `Date`
  - Дата обновления
- **username:** `string`
  - Строка
  - Уникальное значение
  - Длина строки от 2 до 30 символов
- **about:** `string`
  - Строка
  - Опциональное значение
  - Длина строки от 2 до 200 символов
  - Значение по умолчанию: `Пока ничего не рассказал о себе`
- **avatar:** `string`
  - URL
  - Опциональное значение
  - Значение по умолчанию: `https://i.pravatar.cc/300`
- **email:** `string`
  - E-mail
  - Уникальное значение
  - По умолчанию не включается в выборку
- **password:** `string`
  - Строка
  - Свойство скрыто
  - По умолчанию не включается в выборку
- **wishes:** `Wish[]`
  - Связь `User <-(1:X)-> Wish.owner`
- **offers:** `Offer[]`
  - Связь `User <-(1:X)-> Offer.user`
- **wishlists:** `Wishlist[]`
  - Связь `User <-(1:X)-> Wishlist.owner`

### Wish

Свойства сущности и их особенности:

- **id:** `number`
  - Первичный ключ
- **createdAt:** `Date`
  - Дата создания
- **updatedAt:** `Date`
  - Дата обновления
- **name:** `string`
  - Строка
  - Длина строки от 1 до 250 символов
- **link:** `string`
  - URL
- **image:** `string`
  - URL
- **price:** `number`
  - Положительное значение
- **raised:** `number`
  - Положительное значение
  - Значение по умолчанию: `0`
- **owner:** `User`
  - Связь `Wish <-(X:1)-> User.wishes`
- **description:** `string`
  - Строка
  - Длина строки от 1 до 1024 символов
- **offers:** `Offer[]`
  - Связь `Wish <-(1:X)-> Offer.item`
- **copied:** `number`
  - Положительное значение
  - Значение по умолчанию: `0`

### Wishlist

Свойства сущности и их особенности:

- **id:** `number`
  - Первичный ключ
- **createdAt:** `Date`
  - Дата создания
- **updatedAt:** `Date`
  - Дата обновления
- **name:** `string`
  - Строка
  - Длина строки от 1 до 250 символов
- **description:** `string`
  - Строка
  - Длина строки от 0 до 1500 символов
- **image:** `string`
  - URL
- **items:** `Wish[]`
  - Связь `Wishlist <-(X:X)-> Wish` (односторонняя)
- **owner:** `User`
  - Связь `Wishlist <-(X:1)-> User.wishlists`

### Offer

Свойства сущности и их особенности:

- **id:** `number`
  - Первичный ключ
- **createdAt:** `Date`
  - Дата создания
- **updatedAt:** `Date`
  - Дата обновления
- **user:** `User`
  - Связь `Offer <-(X:1)-> User.offers`
- **item:** `Wish`
  - Связь `Offer <-(X:1)-> Wish.offers`
- **amount:** `number`
  - Положительное значение
- **hidden:** `boolean`
  - Значение по умолчанию: `false`

## Связи сущностей

См. [схему в Miro](https://miro.com/app/board/uXjVP2Z2WoM=/?share_link_id=816464723629)

## API

### Auth

#### /signin

Метод: `POST`

Параметры:

- `username`
- `password`

Ответ:

    {
      "access_token": "..."
    }

#### /signup

Метод: `POST`

Параметры:

- `username`
- `about`
- `avatar` (опциональный)
- `email`
- `password`

Ответ:

    {
      "id": 123,
      "createdAt": "...",
      "updatedAt": "...",
      "username": "...",
      "about": "...",
      "avatar": "...",
      "email": "..."
    }

### Users

#### /users/me

Метод: `GET`

Ответ:

    {
      "id": 123,
      "createdAt": "...",
      "updatedAt": "...",
      "username": "...",
      "about": "...",
      "avatar": "...",
      "email": "..."
    }

---

Метод: `PATCH`

Параметры:

- `avatar` (опциональный)
- `about` (опциональный)
- `email` (опциональны)
- `password` (опциональный)
- `username` (опциональный)

Ответ:

    {
      "id": 123,
      "createdAt": "...",
      "updatedAt": "...",
      "username": "...",
      "about": "...",
      "avatar": "...",
      "email": "..."
    }

#### /users/me/wishes

Метод: `GET`

Ответ:

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

#### /users/:username

Метод: `GET`

Ответ:

    {
      "id": 123,
      "createdAt": "...",
      "updatedAt": "...",
      "username": "...",
      "about": "...",
      "avatar": "..."
    }

#### /users/:username/wishes

Метод: `GET`

Ответ:

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

#### /users/find

Метод: `POST`

Параметры:

- `query`

Ответ:

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

### Wishes

#### /wishes

Метод: `POST`

Параметры:

- `name`
- `link`
- `image`
- `price`
- `description`

Ответ:

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

#### /wishes/last

Метод: `GET`

Ответ:

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

#### /wishes/top

Метод: `GET`

Ответ:

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

#### /wishes/:id

Метод: `GET`

Ответ:

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

---

Метод: `PATCH`

Параметры:

- `name`
- `link`
- `image`
- `price`
- `description`

Ответ:

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

---

Метод: `DELETE`

Ответ:

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

#### /wishes/:id/copy

Метод: `POST`

Ответ:

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

### Wishlists

#### /wishlistlists

Метод: `GET`

Ответ:

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

---

Метод: `POST`

Параметры:

- `name`
- `description`
- `image`
- `itemsId`

Ответ:

    {
      "id": 123,
      "createdAt": "...",
      "updatedAt": "...",
      "name": "...",
      "description": "...",
      "image": "..."
    }

#### /wishlistlists/:id

Метод: `GET`

Ответ:

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

---

Метод: `PATCH`

Параметры:

- `name`
- `description`
- `image`
- `itemsId`

Ответ:

    {
      "id": 123,
      "createdAt": "...",
      "updatedAt": "...",
      "name": "...",
      "description": "...",
      "image": "..."
    }

---

Метод: `DELETE`

Ответ:

    {
      "id": 123,
      "createdAt": "...",
      "updatedAt": "...",
      "name": "...",
      "description": "...",
      "image": "..."
    }
