# API Задачи
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить задачи | [GET] /api/v1/tasks/getTasks | id, ids, name, types, sources, startDate, endDate, status | Список [Task](TASKS.md#Task) |
| Создать задачу | [POST] /api/v1/tasks/createTask | [RequestTask](TASKS.md#requesttask) | id |
| Обновить задачу | [PUT] /api/v1/tasks/updateTask | [RequestTask](TASKS.md#requesttask) | [Task](TASKS.md#Task) |
| Удалить задачу | [DELETE] /api/v1/tasks/deleteTask | id | ResponseStatus 204 |
| Очистить корзину | [POST] /api/v1/tasks/clearTrash | - | bool |
| Изменить статус | [POST] /api/v1/tasks/changeStatus | [RequestChangeTaskStatus](TASKS.md#requestchangetaskstatus) | [Task](TASKS.md#Task) |
| Изменить приоритет | [POST] /api/v1/tasks/changePriority | [RequestChangeTaskPriority](TASKS.md#requestchangetaskpriority) | [Task](TASKS.md#Task) |
| Создать чат на основе задачи | [POST] /api/v1/tasks/createChat | id | id чата |

## Task
```
{
  taskId: int,
  name: string, // наименование 
  description: string, // описание
  addInfo: string, // доп. информация
  location: string, // место
  type: string, // EDU - Учебная деятельность, EDU_M - Учебно-методическая деятельность, SCIENCE - Научная деятельность, SCIENCE_M - Научно-методическая деятельность, ORGANIZATION - Организационная деятельность
  startTime: timestamp, //
  endTime: timestamp, //
  allDay: boolean, // на весь день
  priority: int, // приоритет
  source: string, // IPW - Индивидуальный план работы, PROGRESS - Журнал успеваемости, EVENTS - Мероприятия
  externalKey: string, //
  linkedChatId: int, // связанный чат
  linkedTasks: int[], // связанные задачи
  members: TaskMember[], // участники
  role: string, // OWNER - Владелец - создатель, PERFORMER - Исполнитель, FOLLOWER - Подписчик
  assignedAt: timestamp, //
  assignedBy: string, //
  status: string, // статус
  completeTime: timestamp, //
  creationTime: timestamp, //
  modificationTime: timestamp //
}
```
## RequestTask
```
{
  taskId: int,
  name: string,
  description: string,
  type: string, // EDU - Учебная деятельность, EDU_M - Учебно-методическая деятельность, SCIENCE - Научная деятельность, SCIENCE_M - Научно-методическая деятельность, ORGANIZATION - Организационная деятельность
  startTime: timestamp,
  endTime: timestamp,
  allDay: bool,
  priority: int,
  location: string,
  status: string,
}
```
## TaskMember
```
{
  userId: string,
  userRole: string, // OWNER - Владелец - создатель, PERFORMER - Исполнитель, FOLLOWER - Подписчик
  assignedAt: timestamp,
  assignedBy: string,
}
```
## RequestChangeTaskPriority
```
{
  taskId: int,
  priority: int,
}
```
## RequestChangeTaskStatus
```
{
  taskId: int,
  status: string,
}
```
