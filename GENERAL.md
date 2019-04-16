# API Уведомления от других модулей

| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить уведомления | [GET] /api/v1/notifications/getNotifications | offset (default 0), limit (default 40) | Список [Notification](GENERAL.md#notification) |
| Пометить как прочитанное | [POST] /api/v1/notifications/markAsRead | id | bool |
| Пометить как прочитанное | [POST] /api/v1a/notifications/markAsRead | ids - список id | bool |
| Пометить как полученное | [POST] /api/v1/notifications/markAsReceived | ids - список id | bool |
| Получить новые уведомления | [GET] /api/v1/notifications/getUpdates | - | Список [Notification](GENERAL.md#notification) |
| Получить новые уведомления | [GET] /api/async/notifications/getUpdates (longpoll) | - | Список [Notification](GENERAL.md#notification) |

# API для регистрации FCM
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Регистрация токена FCM | [POST] /api/v1/auth/tokenRegistry | token | ResponseStatus 200 |
| Обновление токена FCM | [POST] /api/v1/auth/tokenUpdate | token | ResponseStatus 200 |

# API загрузка и скачивание файлов
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Скачивание файла | [GET] /api/v1/file/download | fileCode | file |
| Скачивание файла | [GET] /api/v1/file/{storageFileCode} | - | file |
| Загрузка файла | [POST] /api/v1/file/uploadFile | file (multipart/form-data) | [UploadFile](GENERAL.md#uploadfile) |

# API общее
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить список модулей | [GET] /api/v1/getAccessibleModules | - | Список [Module](GENERAL.md#Module) |
| Получить серверное время | [GET] /api/v1/getServerTimestamp | clientTime | [ServerTimestamp](GENERAL.md#servertimestamp) |
| Получить пользовательские настройки | [GET] /api/v1/account/getUserSettings | - | Список [UserSetting](GENERAL.md#usersetting) |
| Установить пользовательские настройки | [POST] /api/v1/account/setUserSettings | Список [UserSetting](GENERAL.md#usersetting) | bool |
| Сменить пароль | [POST] /api/v1/account/changePassword | [RequestChangePassword](GENERAL.md#requestchangepassword) | bool |

## Notification
```
{
  id: int, // id
  moduleCode: string, // код модуля
  type: string, // тип
  text: string, // текст уведомления
  url: string, // ссылка
  status: string, // cтатус
  createdAt: timestamp, // дата и время создания
}
```
## Module
```
{
  moduleCode: string, // код модуля
  moduleName: string, // наименование модуля
  url: string, // ссылка
}
```
## ServerTimestamp
```
{
  serverTimestamp: long, // timestamp
  diff: long // разница
}
```
```javascript
export const ntp = (t0, t1, t2, t3) => ({
  roundtripdelay: (t3 - t0) - (t2 - t1),
  offset: ((t1 - t0) + (t2 - t3)) / 2
});
getServerTimestamp(clientTimestamp)
.then(payload => ntp(clientTimestamp, payload.serverTimestamp, payload.serverTimestamp, Date.now()))
.then(ntp => {
  console.log('NTP delay:', ntp.roundtripdelay, 'NTP offset:', ntp.offset, 'corrected: ', (new Date(clientTimestamp + ntp.offset)));
});
// http://stackoverflow.com/a/22969338
```
## UserSetting
```
{
  name: string, // имя настройки
  value: string, // значение
}
```
## RequestChangePassword
```
{
  oldPassword: string, // старый пароль
  newPassword: string // новый пароль
}
```
## UploadFile
```
{
  code: string, // код файла
  name: string, // наименование
  size: long // размер
}
```
