# API Сообщения
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить диалоги | [GET] /api/v2/messenger/getDialogs | - | [Dialogs](MESSENGER.md#dialogs) |
| Создать чат | [POST] /api/v2/messenger/createChat | [RequestCreateChat](MESSENGER.md#requestcreatechat) | [Dialogs](MESSENGER.md#dialogs) |
| Изменить название чата | [POST] /api/v2/messenger/editChatTitle | [RequestEditChatTitle](MESSENGER.md#requesteditchattitle) | bool |
| Добавить пользователя в чат | [POST] /api/v2/messenger/addChatUser | [RequestAddChatUser](MESSENGER.md#requestaddchatuser) | [ChatParcipantAdd](MESSENGER.md#chatparcipantadd) |
| Удалить пользователя из чата | [POST] /api/v2/messenger/removeChatUser | [RequestRemoveChatUser](MESSENGER.md#requestremovechatuser) | bool |
| Обновить настройки уведомлений | [POST] /api/v2/messenger/updateNotifySettings | [RequestUpdateNotifySettings](MESSENGER.md#requestupdatenotifysettings) | bool |
| Получить информацию о чате | [GET] /api/v2/messenger/getChatFull | id | [ChatFull](MESSENGER.md#chatfull) |
| Получить информацию о пользователе | [GET] /api/v2/messenger/getUserFull | id | [UserFull](MESSENGER.md#userfull) |
| Получить сообщения | [GET] /api/v2/messenger/getMessages | id - список id сообщений | Список [Message](MESSENGER.md#message)|
| Получить историю сообщений | [GET] /api/v2/messenger/getHistory | peerId, offset (default 0), limit (default 25) | [Messages](MESSENGER.md#messages) |
| Отметить сообщение как прочитанное | [POST] /api/v2/messenger/readHistory | [RequestReadMessages](MESSENGER.md#requestreadmessages) | bool |
| Отправить сообщение | [POST] /api/v2/messenger/sendMessage | [RequestSendMessage](MESSENGER.md#requestsendmessage) | [SentMessage](MESSENGER.md#sentmessage) |
| Получить список пользователей, прочитавших сообщение | [GET] /api/v2/messenger/getViewedUsers | msgId - id сообщения | Список [User](MESSENGER,md#user) |
| Получить новые сообщения в диалоге | [GET] /api/v2/messenger/getDialogUpdates | peerId, lastMessageId | [Messages](MESSENGER.md#messages) |
| Получить новые сообщения в диалоге | [GET] /api/v2/messenger/getGlobalUpdates | time | [Dialogs](MESSENGER.md#dialogs) |
| Получить новые сообщения (longpoll) | [GET] /api/async/messenger/getDialogUpdates | peerId, lastMessageId | [Messages](MESSENGER.md#messages) |
| Получить новые сообщения (longpoll) | [GET] /api/async/messenger/getGlobalUpdates | time | [Dialogs](MESSENGER.md#dialogs) |
| Получить информацию о пользователе | [GET] /api/v1/users/getUser | id | [User](MESSENGER.md#user) |
| Получить информацию о пользователях | [GET] /api/v1/users/getUsers | ids | Список [User](MESSENGER.md#user) |
| Получить корневые группы пользователей | [GET] /api/v1/users/getUserGroupsRoot | - | Список [UserGroup](MESSENGER.md#usergroup) |
| Получить подгруппы группы пользователей | [GET] /api/v1/users/getSubgroups | id | [Subgroups](MESSENGER.md#subgroups) |
| Получить группы техподдержки | [GET] /api/v1/users/getSupport | - | Список [UserGroup](MESSENGER.md#usergroup) |
| Поиск пользователей | [GET] /api/v1/users/findUsers | query, offset (default 0), limit (default 100) | Список [User](MESSENGER.md#user) |

#### RequestAddChatUser
```
{
  chatId: int, // id чата
  user: AbsInputUser, // пользователь
}
```
#### RequestCreateChat
```
{
  type: string, // тип
  name: string, // наименование
  users: string[], // пользователи
  message: string, // первое сообщение
  attachments: string[], // вложения
  context: string, // контекст
}
```
#### RequestEditChatTitle
```
{
  chatId: int, // id чата
  title: string, // новое наименование
}
```
#### RequestReadMessages
```
{
  peer: AbsPeer, // пользователь/чат
  maxId: int, // max id сообщения в диалоге
}
```
#### RequestRemoveChatUser
```
{ 
  chatId: int, // id чата
  user: AbsInputUser, // пользователь/чат
}
```
#### RequestSendMessage
```
{
  peer: AbsPeer, // пользователь/чат
  message: string, // текст сообщения
  replyToId: int, // id сообщения
  attachments: string[], // вложения
  context: string, // контекст
}
```
#### RequestUpdateNotifySettings
```
{
  peer: AbsPeer, // пользователь/чат
  notify: boolean, 
}
```
#### Attachment
```
{
  id: int, // id 
  type: string, // тип
  fileCode: string, // код файла
  fileName: string, // наименование
  fileSize: long, // размер
}
```
#### Chat
```
{
  id: int, // id чата
  type: string, // тип (ANNOUNCEMENT, CHAT, SUPPORT)
  name: string, // наименование 
  description: string, // описание
  context: string, // контекст
  participantsCount: int, // кол-во участников
  date: timestamp, // дата и время создания
  flags: int // 0x1-создатель 0x2-админ
}
```
#### ChatFull
```
{
  chat: Chat, // чат
  notifySettings: bool, // уведомления
  participants: ChatParticipant[], // участники чата
  users: AbsUser[] // пользователи
}
```
#### ChatParticipant
```
{
  id: string // id 
  type: string // тип
  invitedBy: string // кем приглашен
  date: timestamp // дата приглашения
  flags: int // 0x1-создатель 0x2-админ
}
```
#### ChatParticipantAdd
```
{
  participant: ChatParticipant, // участник чата
  user: AbsUser // пользователь/чат
}
```
#### Dialog
```
{
  peerId: AbsPeer, // пользователь/чат
  lastMessageId: long, // id последнего сообщения
  unreadCount: int, // кол-во непрочитанных сообщений
  notifySettings: bool, // уведомления
  type: string // тип
}
```
#### Dialogs
```
{
  dialogs: Dialog[], // диалоги
  messages: Message[], // сообщения
  chats: Chat[], // чаты
  users: AbsUser[], // пользователи
}
```
#### AbsInputUser {}
#### InputUser: [AbsInputUser](MESSENGER.md#absinputuser)
```
{
  userId: string // id пользователя
}
```
#### InputUserGroup: [AbsInputUser](MESSENGER.md#absinputuser)
```
{
  userGroupId: string // id группы
}
```
#### AbsMessage
```
{
  id: int // id сообщения
}
```
#### Message: [AbsMessage](MESSENGER.md#absmessage)
```
{
  id: int, // id сообщения
  type: int,  // тип
  context: string,  // контекст
  from: string;,  // от кого id пользователя
  peerId: AbsPeer,  // получатель
  message: string, // текст сообщения
  date: timestamp, // дата и время отправления
  flags: int, // 0x1-отправлено пользователем 0x2-прочитано
  views: int, // количество просмотров
  replyToMsgId: int, // ответ на сообщение
  attachments: Attachment[] // вложения
}
```
#### MessageService: [AbsMessage](MESSENGER.md#absmessage)
```
{
  id: int, // id сообщения
  type: int, // тип
  context: string, // контекст
  from: string, // от кого id пользователя
  peerId: AbsPeer, // получатель 
  date: timestamp, // дата и время отправления
  flags: int, // 0x1-отправлено пользователем 0x2-прочитано
  action: AbsMessageAction, // действие
}
```
#### AbsMessageAction {}
#### MessageActionChatAddUser: [AbsMessageAction](MESSENGER.md#absmessageaction)
```
{
  users: string[], // добавленные пользователи
}
```
#### MessageActionChatDeleteUser: [AbsMessageAction](MESSENGER.md#absmessageaction)
```
{
  userId: string, // удаленный пользователь
}
```
#### MessageActionChatEditTitle: [AbsMessageAction](MESSENGER.md#absmessageaction)
```
{
  title: string, // новое наименование чата
}
```
#### Messages
```
{
  messages: Message[], // сообщения
  chats: Chat[], // чаты
  users: User[], // пользователи
}
```
#### AbsPeer {}
#### PeerChat: [AbsPeer](MESSENGER.md#abspeer)
```
{
  chatId: int // id чата
}
```
#### PeerUser: [AbsPeer](MESSENGER.md#abspeer)
```
{
  userId: string, // id пользователя
}
```
#### SentMessage
```
{
  id: int,
  date: timestamp 
}
```
#### Subgroups
```
{
  groups: UserGroup[], // группы
  users: User[] // пользователи
}
```
#### AbsUser
```
{
  id: string
}
```
#### User: [AbsUser](MESSENGER.md#absuser)
```
{
  id: string, // id пользователя
  lastName: string, // фамилия
  firstName: string, // имя
  patronymic: string, // отчество
  sex: string, // пол (M/F)
  photo: string, // код файла
  information: string, // информация (должность / группа)
}
```
#### UserGroup: [AbsUser](MESSENGER.md#absuser)
```
{
  id: string, // id пользователя
  name: string, // наименование группы
  shortName: string, // краткое наименование
  usersCount: int // количество участников
}
```
#### UserFull
```
{
  user: AbsUser, // пользователь
  notifySettings: bool // уведомления
}
```