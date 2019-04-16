# API Портфолио cтудента
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить информацию о студенте | [GET] /api/v1/student/getInfo | - | [StudentInfo](STUDENTPROFILE.md#studentinfo) |
| Получить элементы портфолио | [GET] /api/v1/student/portfolio/getElements | type: award, achievement, traineeship, conference, contest, exhibition | Список [PortfolioElement](STUDENTPROFILE.md#portfolioelement) |
| Создать элемент портфолио* | [POST] /api/v1/student/portfolio/createElement | [PortfolioElement](STUDENTPROFILE.md#portfolioelement) | [PortfolioElement](STUDENTPROFILE.md#portfolioelement) |
| Обновить элемент портфолио* | [POST] /api/v1/student/portfolio/updateElement | [PortfolioElement](STUDENTPROFILE.md#portfolioelement) | [PortfolioElement](STUDENTPROFILE.md#portfolioelement) |
| Удалить элемент портфолио* | [DELETE] /api/v1/student/portfolio/removeElement | id | ResponseStatus 204 |
| Получить информацию об оценках | [GET] /api/v1/student/portfolio/getAttestation | - | Список [StudentAttestation](STUDENTPROFILE.md#studentattestation) |
## StudentInfo
```
{
  studentCode: string, // код студента
  photoFileCode: string, // код файла фотографии
  lastName: string, // фамилия
  firstName: string, // имя
  patronymic: string, // отчество
  groupName: string, // группа
  courseNumber: string, // курс
  chairName: string, // кафедра
  facultyName: string, // факультет
  standardName: string, // стандарт обучения
  directionCode: string, // код направления
  directionName: string, // наименование направления
  profileName: string, // профиль
  studyFormCode: string, // код формы обучения
  studyFormName: string, // форма обучения
  educationLevelName: string, // уровень образования (бакалавриат, магистратура и др)
  educationLevelCode: string, // код уровня образования
  status: string, //
}
```
## PortfolioElement
```
{
  id: int, //    
  type: string, // ACHIEVEMENT, CONFERENCE, AWARD, CONTEST, EXHIBITION, SCIENCEREPORT, WORK, TRAINEESHIP, REVIEWS, THEME, SCIENCEWORK,
  studentCode: string, // код студента
  eventName: string, //
  eventStatus: string, //
  eventPlace: string, //
  eventStartDate: long, //
  eventEndDate: long, //
  eventUrl: string, //
  workName: string, //
  workType: string, //
  result: string, //
  coauthorsText: string, //
  fileCode: string, // код файла
  status: string, // статус
}
```
## StudentAttestation
```
{
  code: string, //
  subject: Subject, // дисциплина
  eduYear: int, // год обучения
  eduBlock: int, // блок
  controlType: ControlType, // форма аттестации
  journalId: int, // id электронного журнала
  rating: StudentRating, // рейтинг студента
  note: string, // примечание
  files: AttestationFile[], // файлы
  courseActivity: string, // КП/КР/null
}
```
## ControlType
```
{
  code: string, // код
  name: string, // наименование
  shortName: string, // краткое наименование
}
```
## StudentRating
```
{
  subgroupRating: int, // рейтинг в подгруппе
  studentsSubgroupCount: int, // количество студентов в подгруппе
  groupRating: int, // рейтинг в группе
  studentsGroupCount: int, // количество студентов в группе
  journalRating: int, // рейтинг в потоке
  studentsJournalCount: int, // количество студентов в потоке
  attendance: int, // процент посещения
  maxScore: float, // максибалл
  currentScore: float, // текущая успеваемость (указаны в процентах от максибалла)
  additionalControlWeight: float, // вес оценок за опросы
  additionalScore: float, // оценка за опросы (указаны в процентах от максибалла)
  intermediateWeight: float, // вес итогового КИ (ИКИ)
  intermediateScore: float, // оценка за ИКИ (указаны в процентах от максибалла)
  pollingScore: float, // оценка за опросы
  pollingCount: int, // количество опросов
  intermediateGrade: string, // Итоговая оценка
}
```
## AttestationFile
```
{
  id: int,
  fileCode: string, // код файла
  fileName: string, // наименование
  teacherCode: string, // код преподавателя
  approvalTime: timestamp, // время утверждения
}
```
