# Сущности

## User

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

## Wish

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

## Wishlist

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

## Offer

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
