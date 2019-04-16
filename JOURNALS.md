# API Электронные журналы студента
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить виды контрольных испытаний | [GET] /api/v1/general/journal/getControlTypes | - | Список [ControlType](STUDENTPROFILE.md#controltype) |
| Получить журналы | [GET] /api/v1/student/journal/getJournals | journalId | [StudentJournal](JOURNALS.md#studentjournal) |
| Получить план расписания занятий | [GET] /api/v1/student/journal/getSchedulePlans | journalId | [SchedulePlan](JOURNALS.md#scheduleplan) |
| Получить план занятий | [GET] /api/v1/student/journal/getLessonPlans | journalId | [StudentLessonPlan](JOURNALS.md#studentlessonplan) |
| Получить преподавателей | [GET] /api/v1/student/journal/getTeachers | journalId | Список [Employee](JOURNALS.md#employee) |

# API Электронные журналы преподаватель
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить виды контрольных испытаний | [GET] /api/v1/general/journal/getControlTypes | - | Список [ControlType](STUDENTPROFILE.md#controltype) |
| Установить отметку о посещении | [POST] /api/v1/employee/journal/setAttendance | [RequestSetAttendance](JOURNALS.md#requestsetattendance) | boolean |
| Установить оценку за КИ | [POST] /api/v1/employee/journal/setAttestation | [CurrentAttestation](JOURNALS.md#currentattestation), chatFiles: string[] | [CurrentAttestation](JOURNALS.md#currentattestation) |
| Удалить оценку за КИ | [POST] /api/v1/employee/journal/removeAttestation | [RequestRemoveAttestation](JOURNALS.md#requestremoveattestation) | boolean |
| Получить промежуточную аттестацию | [GET] /api/v1/employee/journal/getIntermediateProgress | journalId | boolean |
| Установить промежуточную аттестацию | [POST] /api/v1/employee/journal/saveIntermediateProgress | [IntermediateProgress](JOURNALS.md#intermediateprogress) | boolean |
| Удалить промежуточную аттестацию | [DELETE] /api/v1/employee/journal/removeIntermediateProgress | id, accessCode | boolean |
| Получить журналы | [GET] /api/v1/employee/journal/getJournals | journalId | Список [Journal](JOURNALS.md#journal) | 
| Получить студентов | [GET] /api/v1/employee/journal/getStudents | journalId | Список [Student](JOURNALS.md#student) | 
| Получить план расписания занятий | [GET] /api/v1/employee/journal/getSchedulePlans | journalId | Список [SchedulePlan](JOURNALS.md#journal) |
| Получить план занятий | [GET] /api/v1/employee/journal/getLessonPlans | journalId | Список [SchedulePlanLesson](JOURNALS.md#scheduleplanlesson) |
| Получить контрольные испытания | [GET] /api/v1/employee/journal/getControls | journalId | Список [ScheduleControl](JOURNALS.md#schedulecontrol) |
| Получить текущую аттестацию | [GET] /api/v1/employee/journal/getAttestations | journalId, gradeSystem | Список [CurrentAttestation](JOURNALS.md#currentattestation)| 
| Установить дату занятия | [POST] /api/v1/employee/journal/setScheduleFactDate | [RequestSetScheduleFactDate](JOURNALS.md#requestsetschedulefactdate) | boolean | 
| Получить файлы по контексту | [GET] /api/v1/employee/journal/getStudentFiles | chatContext, studentCode |Список [Attachment](MESSENGER.md#attachment) |
| Получить преподавателей | [GET] /api/v1/employee/journal/getTeachers | journalId | Список [Employee](JOURNALS.md#employee) |

## StudentJournal
```
{
  id: int, // id
  subject: Subject, // дисциплина
  year: string, // год
  block: int, // блок
  status: string, // статус
  controlType: ControlType, // тип контроля
  rating: StudentRating, // рейтинг
}
```
## StudentLessonPlan
```
{
  journalId: int,
  schedulePlanLessonId: int, 
  scheduleId: int,
  plannedDate: timestamp, // запланированная дата
  factDate: timestamp, // дата по факту
  type: string, // тип
  burdenType: string, // лекция/практика
  number: int, // номер
  absent: bool, // отсутствовал на паре
  teacherCode: string, // код преподавателя
  controls: ScheduleControl[], // контрольные испытания
  modules: ScheduleModule[], // модули
  grades: CurrentAttestation[] // оценки
}
```
## SchedulePlan
```
{
  schedulePlanId: int,
  journalId: int,
  weekday: int, // номер дня недели
  weekNumber: int, // номер недели
  lessonNumber: int, // номер занятия
  burdenType: string, // тип нагрузки
  status: string, // статус
  creationTime: timestamp,
  teacherCode: string, // код преподавателя
  auditoriumCode: string, // код аудиториии
  auditoriumName: string, // наименование аудитории
  groups: JournalGroup[] // группы
}
```
## ScheduleControl
```
{
  id: int, //
  code: string, // код
  name: string, // наименование
  typeCode: string, //
  maxScore: float, // максибалл
  weight: float, // вес КИ
  journalId: int, // журнал
  type: string // тип (текущая, промежуточная)
}
```
## ScheduleModule
```
{
  id: int, //
  code: string, // код
  name: string // наименование
}
```
## CurrentAttestation
```
{
  currentAttestationId: int, //
  schedulePlanLessonId: int, //
  scheduleControlId: int, //
  studentCode: string, // код студента
  gradeDate: date, // дата оценки
  grade: string, // оценка
  gradePercentage: float, // процент
  gradeSystemCode: string, // система оценивания
  teacherCode: string, // код преподавателя
  attestationFiles: AttestationFile[], // файлы
  archivedBy: string, // 
  archivedDate: timestamp, //
  creationTime: timestamp //
}
```
## JournalGroup
```
{
  journalGroupId: int, //
  higherJournalGroupId: int, // id группы для подгруппы
  groupInfoId: string, // id группы из контингента
  groupName: string, // наименование группы
  journalId: int, // журнал
  studentCodes: string[] // коды студентов
}
```
## Employee
```
{
  code: string, // код
  info: string // ФИО должность
}
```

## RequestSetAttendance
```
{
  schedulePlanLessonId: int, // id 
  studentCode: string, // код студента
  accessCode: string, // код преподавателя
  absent: boolean, // посещение
}
```

## RequestRemoveAttestation
```
{
  attestationId: int, // id 
  accessCode: string, // код преподавателя
}
```

## IntermediateProgress
```
{
  intermediateProgressId: int, //
  journalId: int, // id журнала
  studentCode: string, // код студента
  grade: string, // оценка
  gradePercentage: int, // система оценивания

  increaseReason: string, // причина повышения оценки
  attestationType: string, // тип аттестации
  teacherCode: string, // код преподавателя

  status: string, // статус
  archivedBy: string, //
  archivedDate: timestamp, //
  creationTime: timestamp, //
}
```

## Journal
```
{
  id: int, // id журнала
  subject: Subject, // дисциплина
  year: string, // год
  block: int, // блок
  status: string, // статус
  eduFormCode: string, // код формы обучения
  eduFormAccelerated: boolean, // 
  controlType: ControlTypeBean, // тип контроля (экзамен, дифф зачет и т.п)
  pollingWeight: float, // вес опросов на паре
  courseActivity: boolean, // есть КР/КП
  maxScore: float, // макс. кол-во баллов
  mainTeacherCode: string, // код преподавателя
  journalGroups: JournalGroup[], // группы
}
```

## Student
```
{
  studentCode: string, // код студента
  groupInfoId: string, // код группы
  lastname: string, // фамилия
  firstname: string, // имя 
  patronymic: string, // отчество
  sex: string, // пол (F/M)
  photoFileCode: string, // код файла 
  standardCode: string, // код стандарта обучения
  startYear: int, // год начала обучения
  studentStatus: string, // статус
  chairDepartmentCode: string, // код кафедры
  directionProfileCode: string, // код профиля направления
  courseNumber: int, // курс
}
```
## SchedulePlanLesson
```
{
  schedulePlanLessonId: int, //
  type: string, // тип (занятие или экзамен)
  burdenType: string, // тип нагрузки
  number: int, // номер занятия
  journalId: int, // id журнала
  schedules: Schedule[], // расписание
  modules: ScheduleModule[], // модули
  controls: int[], // id контрольных испытаний
  absentStudents: string[], // коды отсутствующих студентов
}
```
## RequestSetScheduleFactDate

```
{
 scheduleId: int, // id
 factDate: date, // фактическая дата проведения занятия
 accessCode: string, // код преподавателя
}
```