# API Профиль сотрудника

- [Общая информация о сотруднике](PROFILE.md#общая-информация-о-сотруднике)
- [Образование](PROFILE.md#Образование)
- [Контакты](PROFILE.md#Контакты)
- [Достижения](PROFILE.md#Достижения)
- [Награды](PROFILE.md#Награды)
- [Повышение квалификации](PROFILE.md#Повышение-квалификации)
- [Дисциплины и направления](PROFILE.md#Дисциплины-и-направления)

## Общая информация о сотруднике
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить информацию о сотруднике | [GET] /api/v1/employee/getInfo | - | [EmployeeInfo](PROFILE.md#employeeinfo) |
| Обновить фотографию* | [POST] /api/v1/employee/updatePhoto | photo | [EmployeeInfo](PROFILE.md#employeeinfo) |
| Получить статистику по научной деятельности | [GET] /api/v1/employee/getSdiStats | - | [Indicator](PROFILE.md#indicator) |

## Контакты
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить контактную информацию | [GET] /api/v1/employee/contacts | - | Список [EmployeeContact](PROFILE.md#employeecontact) |
| Получить контактную информацию | [GET] /api/v1/employee/contacts/{id} | - | [EmployeeContact](PROFILE.md#employeecontact) |
| Добавить контактную информацию | [POST] /api/v1/employee/contacts | [EmployeeContact](PROFILE.md#employeecontact) | [EmployeeContact](PROFILE.md#employeecontact) |
| Обновить контактную информацию | [PUT] /api/v1/employee/contacts/{id} | [EmployeeContact](PROFILE.md#employeecontact) | [EmployeeContact](PROFILE.md#employeecontact) |
| Удалить контактную информацию | [DELETE] /api/v1/employee/contacts/{id} | - | ResponseStatus 204 |

## Образование
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить достижения | [GET] /api/v1/employee/educations | - | Список [EmployeeEducation](PROFILE.md#employeeeducation) |
| Получить достижение | [GET] /api/v1/employee/educations/{id} | - | [EmployeeEducation](PROFILE.md#employeeeducation) |
| Добавить достижение | [POST] /api/v1/employee/educations | [EmployeeEducation](PROFILE.md#employeeeducation) | [EmployeeEducation](PROFILE.md#employeeeducation) |
| Обновить достижение | [PUT] /api/v1/employee/educations/{id} | [EmployeeEducation](PROFILE.md#employeeeducation) | [EmployeeEducation](PROFILE.md#employeeeducation) |
| Удалить достижение | [DELETE] /api/v1/employee/educations/{id} | - | ResponseStatus 204 |
| Отправить на утверждение | [POST] /api/v1/employee/educations/changeStatus | id | ResponseStatus 200 |

## Достижения
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить достижения | [GET] /api/v1/employee/achievements | - | Список [EmployeeAchievement](PROFILE.md#employeeachievement) |
| Получить достижение | [GET] /api/v1/employee/achievements/{id} | - | [EmployeeAchievement](PROFILE.md#employeeachievement) |
| Добавить достижение | [POST] /api/v1/employee/achievements | [EmployeeAchievement](PROFILE.md#employeeachievement) | [EmployeeAchievement](PROFILE.md#employeeachievement) |
| Обновить достижение | [PUT] /api/v1/employee/achievements/{id} | [EmployeeAchievement](PROFILE.md#employeeachievement) | [EmployeeAchievement](PROFILE.md#employeeachievement) |
| Удалить достижение | [DELETE] /api/v1/employee/achievements/{id} | - | ResponseStatus 204 |
| Отправить на утверждение | [POST] /api/v1/employee/achievements/changeStatus | id | ResponseStatus 200 |

## Награды
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить награды | [GET] /api/v1/employee/awards | - | Список [EmployeeAward](PROFILE.md#employeeaward) |
| Получить награду | [GET] /api/v1/employee/awards/{id} | - | [EmployeeAward](PROFILE.md#employeeaward) |
| Добавить награду | [POST] /api/v1/employee/awards | [EmployeeAward](PROFILE.md#employeeaward) | [EmployeeAward](PROFILE.md#employeeaward) |
| Обновить награду | [PUT] /api/v1/employee/awards/{id} | [EmployeeAward](PROFILE.md#employeeaward) | [EmployeeAward](PROFILE.md#employeeaward) |
| Отправить на утверждение | [POST] /api/v1/employee/awards/changeStatus | id | ResponseStatus 200 |
| Удалить награду | [DELETE] /api/v1/employee/awards/{id} | - | ResponseStatus 204 |

## Повышение квалификации
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить информацию о повышении квалификации | [GET] /api/v1/employee/addEducations | - | Список [EmployeeAddEducation](PROFILE.md#employeeaddeducation) |
| Получить информацию о повышении квалификации | [GET] /api/v1/employee/addEducations/{id} | - | [EmployeeAddEducation](PROFILE.md#employeeaddeducation) |
| Добавить информацию о повышении квалификации | [POST] /api/v1/employee/addEducations | [EmployeeAddEducation](PROFILE.md#employeeaddeducation) | [EmployeeAddEducation](PROFILE.md#employeeaddeducation) |
| Обновить информацию о повышении квалификации | [PUT] /api/v1/employee/addEducations/{id} | [EmployeeAddEducation](PROFILE.md#employeeaddeducation) | [EmployeeAddEducation](PROFILE.md#employeeaddeducation) |
| Отправить на утверждение | [POST] /api/v1/employee/addEducations/changeStatus | id | ResponseStatus 200 |
| Удалить информацию о повышении квалификации | [DELETE] /api/v1/employee/addEducations/{id} | - | ResponseStatus 204 |

## Дисциплины и направления
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить список дисциплин | [GET] /api/v1/employee/getDisciplines | - | Список дисциплин |
| Получить список направлений преподавателя | [GET] /api/v1/employee/getDirections | - | Список направлений преподавателя |
| Добавить направление преподавателю | [POST] /api/v1/employee/createDirection | directionCode | Направление |
| Удалить направления преподавателя | [POST] /api/v1/employee/removeDirection | - | ResponseStatus 204 |
| Получить список направлений | [GET] /api/v1/employee/references/getDirections | - | Список всех направлений |

## Справочники
| ACTION | URL | PARAMS | RESULT |
|--------|-----|--------|--------|
| Получить категории достижений | [GET] /api/v1/employee/references/achievement/categories | - | [RefAchievementCategory](PROFILE.md#refachievementcategory) | 
| Получить категорию достижений | [GET] /api/v1/employee/references/achievement/categories/{id} | - | [RefAchievementCategory](PROFILE.md#refachievementcategory) | 
| Получить масштабы достижений | [GET] /api/v1/employee/references/achievement/scales | - | [RefAchievementScale](PROFILE.md#refachievementscale) | 
| Получить масштаб достижений | [GET] /api/v1/employee/references/achievement/scales/{id} | - | [RefAchievementScale](PROFILE.md#refachievementscale) | 
| Получить типы повышений квалификаций | [GET] /api/v1/employee/references/addEducationTypes | - | [RefAddEducationType](PROFILE.md#refaddeducationtype) | 
| Получить тип повышений квалификаций | [GET] /api/v1/employee/references/addEducationTypes/{id} | - | [RefAddEducationType](PROFILE.md#refaddeducationtype) | 
| Получить масштабы наград | [GET] /api/v1/employee/references/award/scales | - | [RefAwardScale](PROFILE.md#refawardscale) | 
| Получить масштаб наград | [GET] /api/v1/employee/references/award/scales/{id} | - | [RefAwardScale](PROFILE.md#refawardscale) | 
| Получить типы наград | [GET] /api/v1/employee/references/award/types | - | [RefAwardType](PROFILE.md#refawardtype) | 
| Получить тип наград | [GET] /api/v1/employee/references/award/types/{id} | - | [RefAwardType](PROFILE.md#refawardtype) | 
| Получить организации | [GET] /api/v1/employee/references/organizations | - | [RefOrganization](PROFILE.md#reforganization) |
| Получить организацию | [GET] /api/v1/employee/references/organizations/{id} | - | [RefOrganization](PROFILE.md#reforganization) |
| Добавить организацию | [POST] /api/v1/employee/references/organizations | organization | [RefOrganization](PROFILE.md#reforganization) |
| Обновить организацию | [PUT] /api/v1/employee/references/organizations/{id} | organization | [RefOrganization](PROFILE.md#reforganization) |
| Получить типы образования | [GET] /api/v1/employee/references/educationTypes | - | [RefEducationType](PROFILE.md#refeducationtype) | 
| Получить тип образования | [GET] /api/v1/employee/references/educationTypes/{id} | - | [RefEducationType](PROFILE.md#refeducationtype) | 
| Получить университеты | [GET] /api/v1/employee/references/institutions | - | [RefInstitution](PROFILE.md#refinstitution) |
| Получить университет | [GET] /api/v1/employee/references/institutions/{id} | - | [RefInstitution](PROFILE.md#refinstitution) |
| Добавить университет | [POST] /api/v1/employee/references/institutions | institution | [RefInstitution](PROFILE.md#refinstitution) |
| Обновить университет | [PUT] /api/v1/employee/references/institutions/{id} | institution | [RefInstitution](PROFILE.md#refinstitution) |
| Получить квалификации | [GET] /api/v1/employee/references/qualifications | - | [RefQualification](PROFILE.md#refqualification) |
| Получить квалификацию | [GET] /api/v1/employee/references/qualifications/{id} | - | [RefQualification](PROFILE.md#refqualification) |
| Добавить квалификацию | [POST] /api/v1/employee/references/qualifications | qualification | [RefQualification](PROFILE.md#refqualification) |
| Обновить квалификацию | [PUT] /api/v1/employee/references/qualifications/{id} | qualification | [RefQualification](PROFILE.md#refqualification) |
| Получить специальности | [GET] /api/v1/employee/references/specialities | - | [RefSpeciality](PROFILE.md#refspeciality) |
| Получить специальность | [GET] /api/v1/employee/references/specialities/{id} | - | [RefSpeciality](PROFILE.md#refspeciality) |
| Добавить специальность | [POST] /api/v1/employee/references/specialities | speciality | [RefSpeciality](PROFILE.md#refspeciality) |
| Обновить специальность | [PUT] /api/v1/employee/references/specialities/{id} | speciality | [RefSpeciality](PROFILE.md#refspeciality) |

## EmployeeInfo
```
{
  employeeId: int, // id сотрудника
  lastName: string, // фамилия
  firstName: string, // имя
  patronymic: string, // отчество
  sex: string, // пол (M/F)
  birthDate: date, // дата рождения
  photoFileCode: string, // код файла фотографии
  employments: Employment[], // сведения о работе
  experience: EmployeeExperience[], // сведения о стаже
  educations: EmployeeEducation[], // сведения об образовании
  degrees: EmployeeDegree[], // сведения об ученых степенях
  ranks: EmployeeRank[], // сведения об ученых званиях
  interests: EmployeeScientificInterest[], // сведения о научных интересах
}
```
## Employment
```
{
  employeeId: int, //
  employeeCode: string, // код
  department: Department, // подразделение
  post: Post, // должность
  postType: string, // тип (осн, внутр. внеш совм)
  wageRate: float, // ставка
  workHours: float, // часы
  acceptDate: date, // дата устройства
  dismissDate: date, // дата увольнения
  contractStartDate: date, // дата начала ТД
  contractEndDate: date, // дата окончания ТД
  contractFactEndDate: date, // дата факт. оконччания ТД
  contractInfo: string, //
  status: string, // статус
}
```
## EmployeeExperience
```
{
  employeeId: int, //
  experienceType: string, // тип стажа
  years: int, // лет
  months: int, // месяцев
  days: int, // дней
}
```
## EmployeeEducation
```
{
  id: int, //
  employeeId: int, //
  educationType: EducationType, // уровень образования
  institution: Institution, // университет
  qualification: Qualification, // квалификация
  speciality: Speciality, // специальность
  note: string, //
  series: string, // серия
  number: string, // номер
  receiptDate: date, // дата получения
  specialityCode: string, // код специальности
  fileCode: string, // код файла
  status: string, // статус
}
```
## EmployeeDegree
```
{
  id: int, //
  employeeId: int, //
  degree: AcademicDegree, // ученая степень
  scientificSpeciality: ScientificSpeciality, // научная специальность
  specialityCode: string, // код научной специальности
  specialityName: string, // наименование научной специальности
  organizationName: string, // наименование организации
  organizationPlace: string, // место
  series: string, // серия
  number: string, // номер
  approveDate: date, // дата получения
  defenceDate: date, // дата защиты
  fileCode: string, // код файла
  status: string // статус
}
```
## EmployeeRank
```
{
  id: int, //
  employeeId: int, //
  approveDate: date, //
  rank: AcademicRank, //
  chair: string, //
  speciality: string, //
  series: string, //
  number: string, //
  fileCode: string, // код файла
  status: string, // статус
}
```
## EmployeeScientificInterest
```
{
  id: int, //
  employeeId: int, //
  scientificInterestArea: ScientificInterestArea, //
  status: string // статус
}
```
## Indicator
```
{
  indicatorCode: int, // Код показателя
  indicatorName: string, // Название показателя
  projectCount: int, // Количество проектов
  onVerificationCount: int, // Количество находящихся на проверке
  confirmedCount: int, // Количество подтверждённых
  rejectedCount: int, // Количество отклонённых
}
```

## EmployeeAchievement
```
  id: int, //
  employeeId: int, //
  category: refAhievementCategory, // категория
  scale: refAchievementScale, // масштаб
  organization: refOrganization, // организация
  achievementName: string, // наименование
  achievementDate: date, // дата
  fileCode: string, // код файла
  status: string, // статус
  creationTime: timestamp, // дата и время создания
  modificationTime: timestamp, // дата и время редактирования
```
## EmployeeAward
```
  id: int, //
  employeeId: int, //
  scale: refAwardScale, // масштаб
  type: refAwardType, // тип
  organization: refOrganization, // организация
  awardName: string, // наименование
  awardDate: date, // дата
  series: string, // серия
  number: string, // номер
  fileCode: string, // код файла
  status: string, // статус
  creationTime: timestamp, // дата и время создания
  modificationTime: timestamp, // дата и время редактирования
```

## EmployeeAddEducation
```
  id: int, //
  type: refAddEducationType, // тип
  employeeId: int, //
  name: string, // наименование
  length: int, // продолжительность
  place: string, // место учебы
  startDate: date, // дата начала
  endDate: date, // дата окончания
  series: string, // серия
  number: string, // номер
  receiptDate: date, // дата получения
  internal: boolean, // в ВСГУТУ
  fileCode: string, // код файла
  status: string, // статус  
  creationTime: timestamp, // дата и время создания
  modificationTime: timestamp, // дата и время редактирования
```

## RefAchievementCategory
```
{
  id: int, //
  name: string, //
  code: string, //
  ranking: int, //
}
```
## RefAchievementScale
```
{
  id: int, //
  name: string, //
  code: string, //
  ranking: int, //
}
```
## RefAddEducationType
```
{
  id: int, //
  name: string, //
}
```
## RefAwardScale
```
{
  id: int, //
  name: string, //
  code: string, //
  ranking: int, //
}
```
## RefAwardType
```
{
  id: int, //
  name: string, //
  code: string, //
  ranking: int, //
}
```
## RefOrganization
```
{
  id: int, //
  name: string, //
  shortName: string, //
  ranking: int, //
}
```
## RefEducationType
```
{
  id: int, //
  name: string, //
  code: string, //
}
```
## RefInstitution
```
{
  id: int, //
  name: string, //
  shortName: string, //
}
```
## RefQualification
```
{
  id: int, //
  name: string, //
}
```
## RefSpeciality
```
{
  id: int, //
  name: string, //
}
```