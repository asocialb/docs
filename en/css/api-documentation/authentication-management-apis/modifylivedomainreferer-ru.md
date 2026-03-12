Источник (EN): [modifylivedomainreferer.md](./modifylivedomainreferer.md)

# ModifyLiveDomainReferer

## 1. Описание API

Доменное имя для API-запроса: live.tencentcloudapi.com.

Данный API используется для настройки белого/чёрного списка referer для домена прямой трансляции.
Информация о referer включается в HTTP-запросы. После включения конфигурации referer прямые трансляции, использующие RTMP или WebRTC для воспроизведения, не будут проверять referer и могут воспроизводиться в обычном режиме. Для того чтобы конфигурация referer действовала, рекомендуется использовать протокол HTTP-FLV или HLS для воспроизведения.

Максимум 20 запросов в секунду для данного API.

Рекомендуем использовать API Explorer

Попробовать

API Explorer предоставляет широкий набор возможностей, включая онлайн-вызов, аутентификацию подписи, генерацию кода SDK и быстрый поиск API. Он позволяет просматривать запрос, ответ и автоматически сгенерированные примеры.

## 2. Входные параметры

Следующий список параметров запроса содержит только параметры API-запроса и некоторые общие параметры. Полный список общих параметров см. в разделе [Общие параметры запроса](https://intl.cloud.tencent.com/document/api/267/30763).

| Имя параметра | Обязательный | Тип | Описание |
| --- | --- | --- | --- |
| Action | Да | String | [Общие параметры](https://intl.cloud.tencent.com/document/api/267/30763). Значение для данного API: ModifyLiveDomainReferer. |
| Version | Да | String | [Общие параметры](https://intl.cloud.tencent.com/document/api/267/30763). Значение для данного API: 2018-08-01. |
| Region | Нет | String | [Общие параметры](https://intl.cloud.tencent.com/document/api/267/30763). Данный параметр не требуется для этого API. |
| DomainName | Да | String | Доменное имя воспроизведения |
| Enable | Да | Integer | Включить ли аутентификацию белого/чёрного списка referer для текущего доменного имени |
| Type | Да | Integer | Тип списка. Допустимые значения: `0` (чёрный список), `1` (белый список) |
| AllowEmpty | Да | Integer | Разрешить ли пустой referer. Допустимые значения: `0` (нет), `1` (да) |
| Rules | Да | String | Список referer. Элементы разделяются точкой с запятой (;). |

## 3. Выходные параметры

| Имя параметра | Тип | Описание |
| --- | --- | --- |
| RequestId | String | Уникальный идентификатор запроса, возвращаемый с каждым запросом. RequestId необходим для локализации проблемы. |

## 4. Пример

### Пример 1. Пример запроса

#### Пример входных данных

```
https://live.tencentcloudapi.com/?Action=ModifyLiveDomainReferer
&DomainName=5000.liveplay.myqcloud.com
&Enable=1
&Type=0
&AllowEmpty=1
&Rules=aaa.com;bbb.com
&<Common request parameters>
```

#### Пример выходных данных

```
{
    "Response": {
        "RequestId": "8e50cdb5-56dc-408b-89b0-31818958d424"
    }
}
```

## 5. Ресурсы для разработчиков

### SDK

TencentCloud API 3.0 включает SDK, поддерживающие различные языки программирования, для упрощения вызова API.

Tencent Cloud SDK 3.0 for Python
Tencent Cloud SDK 3.0 for Java
Tencent Cloud SDK 3.0 for PHP
Tencent Cloud SDK 3.0 for Go
Tencent Cloud SDK 3.0 for Node.js
Tencent Cloud SDK 3.0 for .NET
Tencent Cloud SDK 3.0 for C++

### Интерфейс командной строки

Tencent Cloud CLI 3.0

## 6. Коды ошибок

Ниже перечислены только коды ошибок, связанные с бизнес-логикой API. Другие коды ошибок см. в разделе [Общие коды ошибок](https://intl.cloud.tencent.com/document/api/267/30851#common-error-codes).

| Код ошибки | Описание |
| --- | --- |
| InternalError | Внутренняя ошибка. |
| InternalError.ConnectDbError | Ошибка подключения к базе данных. |
| InternalError.DBError | Ошибка выполнения запроса к БД. |
| InternalError.DomainNotExist | Доменное имя не существует. |
| InvalidParameter | Недопустимый параметр. |
| InvalidParameterValue | Недопустимое значение параметра. |
| MissingParameter | Отсутствует параметр. |
| ResourceNotFound.DomainNotExist | Доменное имя не существует или не совпадает. |
| ResourceNotFound.ForbidService | Вы заблокированы. |
| ResourceNotFound.FreezeService | Сервис приостановлен. |
| ResourceNotFound.StopService | Сервис приостановлен из-за задолженности на счёте. Пожалуйста, пополните баланс для активации сервиса. |
| ResourceNotFound.UserDisableService | Вы отключили сервис. |


---
*Source: [https://www.tencentcloud.com/document/product/267/40610](https://www.tencentcloud.com/document/product/267/40610)*
