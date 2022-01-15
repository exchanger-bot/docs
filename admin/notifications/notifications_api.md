## Notifications API

### Create

При создании уведомления в NSQ записывается очередь сообщений которая будет отправленна всем менеджерам.


- **[POST]** `/api/v1/admin/notification` — создать новое уведомление

#### 854

Все изображения полученные от пользователя сохраняются в папку `tmp`

***Request***

```json
{
    "type": 854,
    "meta_data": {
        "card_verification": {
            "code": 245335,
            "user_card": "5559494130410854",
            "img_path": "tmp/I0HuKc_2021-12-12T16:33:29.26685161.png"
        },
        "ex_action_cancel": {
            "ex_from": null,
            "ex_to": null
        }
    },
    "user": {
        "chat_id": 3546223,
        "username": "I0HuKc"
    }

```

***Response***

```json
{
    "id": 8,
    "type": 854,
    "status": 1,
    "meta_data": {
        "code": 245335,
        "user_card": "5559494130410854",
        "img_path": "tmp/I0HuKc_2021-12-12T16:33:29.26685161.png"
    },
    "user": {
        "chat_id": 3546223,
        "username": "I0HuKc"
    },
    "created_at": "2021-12-13T11:57:10.809798Z",
    "updated_at": "2021-12-13T11:57:10.809798Z"
}
```

#### 855

***Request***

```json
{
    "type": 855,
    "meta_data": {
        "ex_action_cancel": {
            "ex_from": "BTC",
            "ex_to": "ETH"
        }
    },
    "user": {
        "chat_id": 3546223,
        "username": "I0HuKc"
    }

```

<hr>

### Selection

Получить срез нужного участка данных из БД `notifications`

- **[GET]** `/api/v1/admin/notifications?page=1&limit=15` — Получить нужную выборку записей 

API путь указан с значениями по умолчанию для параметров запроса, т.е. если явно не указать параметры и их значения для параметра `page` автоматически на сервере будет установленно значение **1**, для параметра `limit` значение **15**. 

Это сделано для того , чтобы при простом переходе по ссылке `/api/v1/admin/notifications` все выполнялось автоматически и не нужно было указывать длинную ссылку. 

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
    "limit": 15
}
```

<hr>

### Update

- **[PUT]** `/api/v1/admin/notification/:id` — обновить статус уведомления


***Header***

```json
{
    "Authorization": "Bearer <token>"
}
```


***Request***

```json
{
    "id": 2,
    "type": 854,
    "status": 2,
    "user": {
        "chat_id": 3546223,
        "username": "I0HuKc"
    }
}
```


***Response***

```json
{
    "id": 2,
    "type": 854,
    "status": 2,
    "meta_data": {
        "code": 691156,
        "user_card": "5559494130410854",
        "img_path": null
    },
    "user": {
        "chat_id": 524164407,
        "username": "I0HuKc"
    },
    "created_at": "2021-12-12T19:24:10.156095Z",
    "updated_at": "2021-12-13T10:16:59.499637Z"
}
```

<hr>

### Delete

- **[DELETE]** `/api/v1/admin/notification/:id` — удалить уведомление

***Header***

```json
{
    "Authorization": "Bearer <token>"
}
```


***Request***

```json
{
    "id": 2,
    "type": 854,
    "status": 2,
    "user": {
        "chat_id": 3546223,
        "username": "I0HuKc"
    }
}
```


***Response***

```json
{
    "id": 2,
    "type": 854,
    "status": 2,
    "meta_data": {
        "code": 691156,
        "user_card": "5559494130410854",
        "img_path": null
    },
    "user": {
        "chat_id": 524164407,
        "username": "I0HuKc"
    },
    "created_at": "2021-12-12T19:24:10.156095Z",
    "updated_at": "2021-12-13T10:16:59.499637Z"
}
```

<hr>

### Count new notifications

- **[GET]** `/api/v1/admin/notifications/check` — получить количество новых уведомлений


***Response***

```json
{
    "new_notifications": 6
}
```
