# الصاق افزونه کاربر

| CREATE USER ADDON |                   |
|-------------------|-------------------|
| API Permissions   | USER_ADDON_CREATE |
| OAuth Permissions | USER_ADDON_CREATE |
| Rate Limit        | Unlimited         |


## ریکوئست

```http request
POST https://api.divar.ir/v2/open-platform/addons/user/{{phone}}
x-access-token: {{access-token}}
x-api-key: {{api-key}}

{
    "widgets": [

    ],
    "phone": "09991234567",
    "categories": [],
    "ticket_uuid": "812d56e6-e44d-45e7-8932-f9acbd416999",
    "cost": 124000,
    "semantic": {
        "identity_verification_result": "FACE_AND_ID_MATCHED"
    }
}
```

| Field                | Type     | Example                                | Description                                                                                             |
|----------------------|----------|----------------------------------------|---------------------------------------------------------------------------------------------------------|
| widgets              | array    | []                                     | مشاهده [ویجت‌های کنار دیوار](../widgets)                                                                |
| notes                | string   | "note"                                 | یادداشت دلخواه برای شما حداکثر یک کیلوبایت                                                              |
| phone                | string   | "09991234567"                          | آیدی کاربر متقاضی افزونه کاربر                                                                          |
| categories           | []string | []                                     | لیست دسته‌بندی‌هایی که افزونه روی آگهی‌های آن دسته‌ها به شکل خودکار الصاق گردد                          |
| ticket_uuid          | string   | "812d56e6-e44d-45e7-8932-f9acbd416999" | مشاهده [بلیط پرداخت](../payment-ticket)                                                                 |
| cost    | int32    | 124000                                 | هزینه انجام خدمت به ریال                                                                                |
| semantic             | object   | {}                                     | [اطلاعات معنایی](semantic.md)                                                                           |

> - داشتن اکسس توکن با درسترسی مربوطه برای الصاق این نوع افزونه الزامی است
> - برای الصاق افزونه‌آگهی روی همه دسته‌هایی که اپ مربوطه در آن نمایش داده می‌شود، کافیست لیست دسته‌بندی‌ها را خالی بگذارید.

## ریسپانس

```json
{
    "id": "812d56e6-e44d-45e7-8932-f9acbd416999"
}
```

# حذف افزونه کاربر

برای حذف افزونه کاربر میتوان از ریکوئست زیر استفاده نمود:

```http request
DELETE https://api.divar.ir/v1/open-platform/addons/user/{{id}}
x-api-key: {{api-key}}
```

با در دست داشتن آیدی (uuid) افزونه کاربر متناظر میتوانید اقدام به حذف آن نمائید.