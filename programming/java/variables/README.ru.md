## Объявление простых переменных, использование примитивных типов

>  ПЕРЕМЕННЫЕ ( Переменная ) - это основной элемент хранения информации в Java - программе. Переменная характеризуется комбинацией идентификатора, типа и области действия.
> Рекомендуемый способ выбора имен переменных в Java - CamelCase. Это значит что имена состоящие из простых слов / букв пишутся с маленькой начальной буквы, а в составных названиях - каждое следующее слово с заглавной в начале. А так же рекомендуется ограничится набором латинских букв (a..zA..Z)

* К слову, если бы нам дали объявить переменные координат можно было бы написать по простому 
   ```java
   int x = 10;
   int y = 20;
   ``` 

* Если же нас попросили бы "экспрессивным кодом" указать что это координаты например места нахождения авто на карте 
   ```java
   int carX = 10;
   int carY = 20;
   ``` 

* Если бы нам дали объявить например "количество дней каникул студента" и "кол-во часов практики внутри какой-то компании"  
   ```java
   int studentHolidayDays = 30;
   int studentCompanyPracticeHours = 100;
   ``` 

* В некоторых ситуациях вам предложат даже ввести единицу измерения величины в само название для "большей экспрессивности" 

---

* Перед тем как начать выполнение домашнего задания, не забудьте что ВЕСЬ этот код мы пишем внутри функции **main()**
  
* Требуется создать новое приложение с функцией "main()" в виде файла (класса) с именем "DateVariablesApp"
* С таким скелетом (файл DateVariablesApp.java)
    ```java
    public class DateVariablesApp {

        public static void main(String[] args){

            int year  = 2019;
            int month = 5;
            int day   = 25;

     
            System.out.print("Today is: ");
            System.out.print( year );
            System.out.print("-")
            System.out.print( month );
            System.out.print("-");
            System.out.print( day );

            // 1) запустите - проверьте
            // 2) переделайте код так чтобы он выводил сообщение:
                //  > Today is: 25-5-2019

        }

    }
    ```

* Запустите код, появится ошибка, исправьте ее и заново запустите и проверьте!
* В программе мы объявили [3 переменные целого типа](./README.ru.md#L37-L39):
  1. Укажите им значения соответствующие текущей дате
  2. Выберите этим трем переменным более "экспрессивные" имена, так чтобы было понятно что это ТЕКУЩАЯ ДАТА (сегодняшнее число) 
  3. Переделайте код где эти [переменные используются для вывода](./README.ru.md#L43) чтобы программа к ним обратилась при помощи новых имен что вы им присвоили
  4. Переделайте код так чтобы он выводил сообщение в следующем порядке:
    ```Today is: 25-5-2019```

--- 
БОНУС - ответьте на следующие вопросы:
1. Чем отличаются функции **print()** и **println()** ?
2. Помимо простого типа "int", какие еще простые типы есть в Java ?


