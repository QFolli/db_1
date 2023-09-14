Вариант 1. База данных «Платный прием в поликлинике»
Платный прием пациентов проводится врачами разных специальностей (хирург, терапевт, кардиолог, офтальмолог и т.д.). При оформлении приема должна быть сформирована квитанция об оплате приема, в которой указывается информация о пациенте, о враче, который консультирует пациента, о стоимости приема, о дате приема.
Пациент оплачивает за прием некоторую сумму, которая устанавливается персонально для каждого врача. За каждый прием врачу отчисляется фиксированный процент от стоимости приема. Процент отчисления от стоимости приема на зарплату врача также устанавливается персонально для каждого врача.
Размер начисляемой врачу заработной платы за каждый прием вычисляется по формуле:
Зарплата = Стоимость приема * Процент отчисления на зарплату.
Из этой суммы вычитается подоходный налог, составляющий 13% от начисленной зарплаты.

![image](https://github.com/QFolli/db_1/assets/88559269/42a3534e-0a2b-4157-aae7-48d7eaef719d)
![image](https://github.com/QFolli/db_1/assets/88559269/5401aa4a-3b9c-413e-968c-ce39a7c67f87)

Функциональные зависимости

Receipt: R1 = (  ServiceName,  DoctorPassportId,   PacientMedicalBookId,   Date)

Pacient: R2 = (  MedicalBookId, FirstName, LastName, Patronumic, Birthday, Address, Phone)
MedicalBookId → (FirstName, LastName, Patronumic, Birthday, Address, Phone)

Service: R3 = (  Name,   DoctorPassportId, Cost)
(Name, DoctorPassportId) → Cost

Doctor: R4 = ( PassportId, FirstName, LastName, Patronumic, Birthday, Address, Phone, Specialization, DeductionPercentage, Salary)
PassportId → (FirstName, LastName, Patronumic, Birthday, Address, Phone, Specialization, DeductionPercentage, Salary)

Зависимости:
Pacient → Receipt: один ко многим
Service → Receipt: один ко многим
Doctor → Service: один ко многим

Нормализация:

1NF
	В каждой ячейке находятся только элементарные значения атрибутов.

2NF
	Отношение в 1NF.
	Нет неполных функциональных зависимостей не первичных атрибутов от атрибутов первичного ключа.

3NF
	Отношение во 2NF.
	Нет транзитивных зависимостей.

BCNF
	Отношение в 3NF
	Каждый детерминант отношения является возможным ключом отношения.

4NF
	Отношение в BCNF
	В случае существования зависимости A->> B все остальные атрибуты R функционально зависят от A.

5NF
	Отношение в 4NF
	Каждая нетривиальная зависимость соединения в нем включает некоторый потенциальный ключ отношения R.

Модель соответствует всем перечисленным нормальным формам.

Второй способ нормализации
Выделяем все атрибуты сущностей инфологических моделей, сводим в одно отношение и нормализуем.
![image](https://github.com/QFolli/db_1/assets/88559269/7023806b-9d1f-4985-bf5c-48c9a4eca244)
Приведём таблицу ко всем нормальным формам. Получим следующее отношение:
![image](https://github.com/QFolli/db_1/assets/88559269/86280fca-7590-4243-a1e0-316394064061)

Receipt: R1 = (  ServiceName,   DoctorPassportId,   PacientMedicalBookId,  Date)
Pacient: R2 = (  MedicalBookId, FirstName, LastName, Patronumic, Birthday, Address, Phone)

MedicalBookId → (FirstName, LastName, Patronumic, Birthday, Address, Phone)
Service: R3 = (  Name,   DoctorPassportId, Cost)
(Name, DoctorPassportId) → Cost
Doctor: R4 = (  PassportId, FirstName, LastName, Patronumic, Birthday, Address, Phone, Specialization, DeductionPercentage, Salary)

PassportId → (FirstName, LastName, Patronumic, Birthday, Address, Phone, Specialization, DeductionPercentage, Salary)

Зависимости: 
Pacient → Receipt: один ко многим
Service → Receipt: один ко многим
Doctor → Service: один ко многим


Вывод
В ходе лабораторной работы №1 были построены инфологическая и даталогическая модели. При нормализации таблиц можно сделать вывод, что отношения выстроены верно и данная схема является верной.


