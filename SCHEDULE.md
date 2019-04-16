# API Расписание занятий
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить расписание занятий на основе электронных журналов | [GET] /api/v1/schedule/getSchedule | - | Список [ScheduleLesson](SCHEDULE.md#schedulelesson) |
| Получить расписание занятий на основе расписания с портала | [GET] /api/v1/schedule/getSchedule2 | - | Список [ScheduleLesson](SCHEDULE.md#schedulelesson) |
| Получить номер текущей недели | [GET] /api/v1/schedule/getStudyWeek | - | int |
## ScheduleLesson
```
{
  id: int,
  journalId: int, // id журнала
  subject: Subject, // дисциплина
  weekday: int, // день недели 0-понедельник, null - на обоих неделях для /api/v1/schedule/getSchedule2
  weekNumber: int, // 0 первая неделя
  lessonNumber: int, // 0 первая пара
  burdenType: string, // тип лекция практика лаба
  auditorium: string, // аудитория
  groups: string[], // группы
  teacher: string, // препод
}
```
## Subject
```
{
  id: int,
  code: string, // код дисциплины
  name: string, // наименование
  shortName: string, // краткое наименование
  complexityZet: double, // трудоемкость ЗЕТ
  complexityTotal: int, // трудоемкость в часах
  type: string, // тип дисциплины
}
```
