## Знакомство с PostgreSQL

* Для того чтобы лучше понять с каким движком мы имеем дело прочитайте вот [эту](https://habr.com/ru/post/282764/) статейку 
* Официальный сайт движка ДБ [тут](https://www.postgresql.org/) 
* Зайдите в "Downloads" выберите последнюю версию и установите его для своего ОС при помощи инсталера
* В процессе установки укажите пароль для акка администратора базы и порт на котором сервем будет ждать запросы:
  * Модерн движки баз данных (в отличие от SQLite) содержат ACL (Access Control List) тоесть в них есть встроенные схемы защиты данных благодаря ролям, правам и уровням доступа
  * Порт - это номер (условное обозначение) входа или/и выхода како-то приложения, в данном случае Сервер PostgreSQL будет ожидать на выбранном порту запросов / подключений, оставьте дефолтный предложенный порт - только номер его запомните
  * Локализацию рекомендую оставить тоже дефолтную  

* После установки убедитесь в том что он у вас работает, можно через "Task Manager" Операционной системы просто посмотреть если в списке "Services" есть "postgre"
* Поиском в системе проверьте наличне "PSQL SHELL" - командная строка которая должна была установиться вместе с сервером
* При запуске командной строки жмакаем "ENTER" до того момента как он про пароль спросит - вводит тот что выбрали при установки если все верно - вы залогинетесь на сервере

---

* Проверим список баз данных командой "\list"
* Далее пользуясь документацией выполните следующее:
  * создать базу данных "university_app"
  * создать таблицу "students" с примерно такими же полями как в SQLite
  * вставить новую запись студента в таблицу
  * запросить всех студентов из таблицы
  * обновить данные студента
  * удалить студента

ВСЕ ЭТИ КОМАНДЫ ВЫПОЛНИТЬ ЧЕРЕЗ "SHELL" на чистом SQL