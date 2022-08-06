# ERP - Enterprise resourse planing

#### СПРАВОЧНО:Опциональные подсистемы

name | description | translate
--|--|--
MES | Manufacturing Execution System | производственные управляющие системы;
WMS | Warehouse Management System | системы управления складами;
CRM | Customer Relationship Management | системы управления взаимоотношениями с клиентами;
SCM |Supply Chain Management | системы управления цепочками поставок;
TMS |Transportation Management System|  системы управ ления транспортировками;
PDM | Product Data Management | системы управления данными о продуктах (изделиях);
KPI |Key Performance Indicators| – ключевые показатели эффективности. Входят во многие системы показателей, например, BSC (Balanced Scorecard) – сбалансированная система показателей. Объединяются в отдельный блок (подси стему) визуализации показателей (монитор/витрина целевых показателей);
EAM |Enterprise Asset Management | управление основными фондами предприятия (процессами эксплуатации и ремонта).  ТОиР – техническое обслуживание и ремонт;
HRM |Human Resources Management | управление персоналом;
CPM |Corporate Performance Management| – система управления эффективностью предприятия. Синонимы для такого класса систем: BPM (Business Performance Management), EPM (Enterprise Performance Management), SEM (Strategic Enterprise Management);
MDM | Master Data Management | системы управления мастер-данными (сведение и управление общей НСИ – нормативно-справочной информацией);
BPMS | Business Process Management System | системы управления бизнес-процессами.


### СПРАВОЧНО:Облачные инфраструктуры

#### IaaS (инфраструктура как сервис)
_клиент использует физические или виртуальные серверы, дисковые хранилища и прочее оборудование оператора облака для конфигурирования своей ИТ-инфраструктуры._
__Клиент__ не может определять, как указанные блоки физически соединены между собой, но может строить из них логические конфигурации в рамках ограничений, определенных оператором.
__Оператор__ несет ответственность за функционирование аппаратных блоков и их связь между собой.
__Обслуживанием__ ОС и программного обеспечения (включая ERP) занимается клиент.
__Резервное копирование СУБД__ и приложений настраивает и обеспечивает клиент.
#### PaaS (платформа как сервис) 
_позволяет пользователю установить в облачной инфраструктуре необходимое приложение, использующее операционные системы, языки программирования, библиотеки, СУБД и другие сервисы, предоставленные оператором._
__Оператор__ обеспечивает функционирование платформы и ее масштабирование при необходимости.
__Клиент__ занимается только поддержкой и работой приложения.
__Резервное копирование__ настраивает и обеспечивает оператор.
#### SaaS (программное обеспечение как сервис) 
_клиент использует приложение, запущенное внутри cloud-среды оператора._
__Пользователи__ подключаются к нему с помощью различных протоколов (HTTP, RDP или VPN) и разных устройств, состав которых определен оператором, возможностями приложения (например, вся работа через веб-браузер).
__Поддержка__ приложения и аппаратуры полностью осуществляется оператором.
__Клиент__ может влиять только на ограниченное число настроек (заведение пользователей, назначение прав, включение/выключение дополнительных опций).
__Резервное__ копирование настраивает и обеспечивает оператор.


### СПРАВОЧНО:Методологии управления проектом при внедрении ERP
#### Гибкие (Agile) - Scrum, Kanban, Exstreme programming
_МАНИФЕСТ AGILE_ 
- люди и взаимодействие важнее процессов и инструментов. 
- работающий продукт важнее полной документации
- сотрудничество с заказчиком важнее согласования условий контракта
- готовность к изменениям важнее следования первоначальному плану
#### ISO 21500, ГОСТ 34, PMBOK
Каскадные или водопадные модели из последовательных этапов, подробное планирование, документирование стадий, есть четкий план
PMBOK (англ. Project Management Body of Knowledge) – свод знаний по управлению проектами, разрабатываемый и поддерживаемый инсти- тутом по управлению проектами PMI (англ. Project Management Institute)


### Как проводить внедрение 


### Что требуется от нас
- Внятный список функциональных требований. 
- Холистический подход
- Формирование рабочей группы
- Формирование центра компетенции
- Тиражирование знаний


### На что обратить внимание
- Клиент банкинг (функционал должен быть интегрирован и КИС) 
- HR - есть ли сейчас? - если есть можно ли интегрировать? 
- Производственный учет (у нас есть несколько направлений, следует учитывать)
- Работа с договорами
- Отслеживание финансовых обязательств кредиторской и дебиторской задолженности
- Оперативная отчетность
- Планирование запасов: КАКИМ образом 
- Просчет себестоимости
- Генерация необходимых документов (инвойсы, счета, договора)
- Формирование финансовой отчетности (отчет о прибылях и убытках, баланс)
- Финансовое планирование


### РЕИНЖИНИРИНГ бизнес - процессов
Инициатиа должна исходить из команды заказчика. 


### Вопросы, требующие проснения
1.Обновление на актуальную версию при серьезных доработках системы как будет происходить?
2.Нагрузка на аппаратную часть 
3.Архитектура приложения (трехзвеная? -сервер приложений -клиент -субд) 
4.IT-ландшафт (как есть, как будет)
5.Возможность облачной инфраструктуры. 
