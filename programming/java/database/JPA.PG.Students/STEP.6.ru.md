## Имплементирование на уровне JPA используя Hibernate ORM

> ORM Hibernate / JPA очень часто использует принцип построения "прокси", рекомендуется [прочитать это](https://habr.com/ru/post/88722/) или [это](https://javarush.ru/quests/lectures/questcollections.level07.lecture02)  до того как продолжить изучение материала!

### ТРЕТЬЯ ЧАСТЬ

* Обмен данными между приложением и ДБ через JPA + Hibernate происходит по такой схеме
```
[   ]  ---->  |                JPA                 | ----> |        Hibernate         | ----> |   JDBC     | ----> |        DB      |
[App]         | [EntityManager+TransactionManager] |       |        [Session]         |       |[Connection]|       |  [Transation]  |
[   ]  <----  |                                    | <---- | [Persister+Loader+Cache] | <---- |            | <---- | [Native Query] |

                                                                   ^  v 
[   ]  ------------------------------------------------------------^  v
[App]                                                                 v 
[   ]  <--------------------------------------------------------------


```

* Т е когда наше приложение работает через **EntityManager** то наша логика "выходит" на связь с ДБ через стандартизированный JPA интерфейс, проходя через сессионный механизм **Hibernate**, но у нас есть возможность работать "обходя" этот слой - напрямую через объект сессии. Посмотрим на следующие фрагменты кода:

 первый - получает новый объект - менеджера сущности из фабрики

 ```java
  EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("hb-database");
	EntityManager entityManager = entityManagerFactory.createEntityManager();
 ``` 

второй - получает доступ к "подкапотной" сессии из самого менеджера

 ```java
  Session session = entityManager.unwrap(Session.class);
 ``` 
  
* Каждый раз когда устанавливается новая сессия (соединение) через **Hibernate** в памяти выделяется область под **Session Cache** который умным путем будет "запоминать" сущности (передаваемые / извлекаемые в / из баз данных ) в разных состояниях.

ВНИМАНИЕ! большинство серьезных компаний и разработчиков что работают с Hibernate рекомендуют пользоватся в основном - **EntityManager** и только когда требуется какая-то **Hibernate** специфика - обращаться к сессии напрямую!

---

* CRUD на уровние **Session** и **EntityManager**
  1. CREATE - можно создать сущность и записать в базу через:
     1. save()/saveOrUpdate() - работая напрямую с сессией эти функции сохраняют/обновляют объект - гарантируя немедленную синхронизацию сущности из кэша с ДБ и так же сразу возвращают ссылку на обновленную сущность. Это механизм можно назвать - "ручной подход", такой подход дает больше управляемости нашему приложению, но при этом если разработчик приложения не имеет высокого уровня опыт работы с сложными архитектурами ДБ и длинными сессиями, риск потери данных повышается!
     2. persist() - когда работаем через EntityManager - не гарантирует немедленной синхронизации с ДБ, но данный метод гарантирует Атомарность операций, как ? - persist() не работает ВНЕ транзакций!. Этот метод надежнее тем что в нем участвует механизм который можно назвать "автопилотом" - он сам определит момент когда правильнее всего будет синхронизировать данные с ДБ! 
  2. READ - можно прочитать / получит из ДБ сущность через:
     1. сессионный механизм Hibernate  нам предоставил два основных метода: get() - который читает напрямую и возвращает объект сущности немедленно, если он найден, и load() - который возвращает "proxy" - ссылку на будущий объект (содержит только ID) с той целью что если вдруг нам понадобится что-то более детальное позже в коде (например какое-то свойство сущности) - то оно загрузится только ПЕРЕД моментом потребления (обращения) к нему! Такой механизм экономит запросы посылаемые в ДБ и чаще всего называется LAZY (ленивый)
     2. механизм менеджера сущности предоставляет нам методы: find() - который возвращает полностью инициализированную сущность (за исключением явным образом объявленных LAZY  компонентов) тогда как getReference() - возвращает "proxy" - который будет инициализирован только при необходимости
  3. UPDATE - обновить сущность можно:
     1. session - предоставляет нам update() - более простой метод с немедленным результатом, который обновит сущность из текущего транзиентного состояния в ДБ при условии что в кэше сессии нет копии этого же объекта в персистентном состоянии! в ситуациях когда необходимо применить обновления поверх существующих в сессии "снэпшотов" состояния этой же сущности - используется merge()
     2. em - дает нам для достижения цели тот же persist() - метод который "не спеша" но "по умному" определит как именно лучше обновить состояние транзиентного объекта сущности и донести это до ДБ
  4. DELETE - для удаления:
     1. session - предоставляет delete() и remove() почти идентичные методы которые при завершении транзакции полностью удаляют сущность без возможности ее возврата. Эти методы удаляют ассоциирующися с нашей сущностью объекты если это объявлено через (cascade="DELETE")
     2. em - remove() удает сущность, но ее можно востановть в рамках одной и той же сессии! Так же этот метод учитывает  (cascade="DELETE")

---

ТРЕБУЕТСЯ - вспомнить как добавить и добавить JUnit в проект как зависимость через maven а так же добавить ФАСЕТ JUnit самому проекту (пересмотрите примеры что вы делали раньше!) и Построить 3 теста (кейса) по одному на каждую сущность вашей системы. Тесты должны быть названы по принципу "TestCRUDStudent". Для каждого из тестов запустить через EntityManager следующие сценарии:
  1. Открыть соединение, создать сущность и сохранить, получить ее ID (после сохранения база данных выдаст ID) Закрыть соединение
  2. Открыть соединение, Найти сущность по тому ID что у вас запомнилось после предыдущей операции, изменить какое-то поле, обновить; Закрыть соединение
  3. Открыть соединение, Найти сущность по тому ID что у вас запомнилось после предыдущей операции, удалить сущность, Закрыть соединение

ЗАЧЕМ МОЖЕТ ПРИГОДИТСЯ такой тест? ну представим себе что вы разработали софт работающий с ДБ через HB/JPA - у вас на машине работает все нормально, вы публикуете приложение на продакшион сервер - и перед тем как запустить основную логику, запускаете встроенные тесты - после прохождения которых, вы будете увереннее в том что код нормально поведет себя и на другой машине!

