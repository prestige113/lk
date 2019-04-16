# Личный кабинет
- [Профиль сотрудника](PROFILE.md)
- [Портфолио студента](STUDENTPROFILE.md)
- [Расписание занятий](SCHEDULE.md)
- [Сообщения](MESSENGER.md)
- [Электронные журналы](JOURNALS.md)
- [Задачи](TASKS.md)
- [Уведомления, FCM, настройки пользователя, файлы](GENERAL.md)

## Физ. модель БД
```common/powerdesigner_files/15_personal_office_employees/personal_office.pdm```

## Выполнение задач по расписанию (job'ы)
- *__ActualizeExternalTasksJob__* - Создание задач на основе внешних источников (Успеваемость), выполняется каждый час.
- *__DepartmentBasedGroupsActualizationJob__* - Актуализация групп пользователей на основе подразделений, выполняется каждый час.
- *__EmployeeUsersActualizationJob__* - Актуализация пользователей работников университета, выполняется каждый час.
- *__StudentUsersActualizationJob__* - Актуализация пользователей студентов университетат, выполняется каждый час.
- *__NotificationJob__* - Рассылка push-уведомлений для Google FCM


## Личный кабинет web-клиент
- [Webpack](https://webpack.js.org/) - сборка проекта
- [ReactJS](https://reactjs.org/)
- [React Redux](https://redux.js.org/) - управление состоянием приложения
- [React Router](https://github.com/ReactTraining/react-router) - роутинг
- [redux-form](https://github.com/erikras/redux-form) - работа с формами
- [axios](https://github.com/axios/axios) - http client

Сборка проекта
```bash
yarn web-prod-teacher — js-bundle для преподавателя
yarn web-prod-employee — js-bundle для работника
yarn web-prod-student — js-bundle для студента
```
Сгенерированые файлы (web/resources/) скопировать в папку webapp, обновить index.jspx