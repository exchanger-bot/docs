## Logs API

### Create

- **[POST]** `/api/v1/log` — Создать новую запись в БД логов.


***Request***

```json
{
    "service": 200,
    "module": "db",
    "info": "some error text"
}
```

***Response***

```json
{
    "id": 11,
    "username": null,
    "info": "some error text",
    "service": 200,
    "module": "db",
    "created_at": "2022-01-15T15:09:31.28989Z"
}
```

<hr>

### Selection

#### Query Params

- `service` — Параметр фильтрации по номеру сервиса.
- `username` — Параметр фильтрации по имени пользователя.
- `date_from` — Параметр фильтрации поиск начиная с указанной даты.
- `date_to` — Параметр фильтрации поиск заканчивая указанной датой.

- Если не указан параметр `date_from` по умолчанию берется дата `2020-01-01T00:00:00.00000000`.
- Если не указан параметр `date_to` по умолчанию берется текущая дата.


- **[GET]** `/api/v1/logs` — Получить выборку логов с учетом указанных параметров фильтрации.

***Header***

```json
{
    "Authorization": "Bearer <token>"
}
```

***Response***

```json
{
    "current_page": 1,
    "data": [],
    "last_page": 2,
    "limit": 15,
    "total": 1
}
```

<hr>

## Selection delete

- **[DELETE]** `/api/v1/logs` — Удалить выборку логов с учетом указанных параметров.

#### Query Params

- `date_from` — Удалить начиная с указанной даты.
- `date_to` — Удалить заканчивая указанной датой.

- Если не указан параметр `date_from` по умолчанию берется дата `2020-01-01T00:00:00.00000000`.
- Если не указан параметр `date_to` по умолчанию берется текущая дата.

***Header***

```json
{
    "Authorization": "Bearer <token>"
}
```

***Response***
```json
[]
```

Если было удалено записей > 0, возвращается массив удаленных записей.

<hr>

## Delete

- **[DELETE]** `/api/v1/log/:id` — Удалить одну запись лога.

***Header***

```json
{
    "Authorization": "Bearer <token>"
}
```

***Response***

```json
{
    "id": 11,
    "username": null,
    "info": "some error text",
    "service": 200,
    "module": "db",
    "created_at": "2022-01-15T15:09:31.28989Z"
}
```