## Использование класса - обертки. Чейнинг

* Предположим у вас есть класс который соответствует рецепту приготовления "Pizza". Этот класс содержит список ингредиентов в виде ```List<String>``` в капсуле. У класса есть дефолтный конструктор - который просто резервирует место под список ингредиентов. Второй конструктор вызывает "this()" - обратите внимание! Такой вызов означает выполнение логики из дефолтного конструктора текущего класса! Второй конструктор принимает три аргумента: dough - тесто ("thin", "thick" - тонкое или толстое), salt - соль ("iodized","halit" - с иодом или каменная), oil - масло ("sunflower","olive" - подсолнечное или оливковое). Добавьте "защитную логику" - чтобы в каждом аргументе можно было добавить ТОЛЬКО по одно из этих 3-х пар значений.
* Конструктор у нас задает ОСНОВУ рецепта, после того как он их принял, проверил - конструктор должен добавить все 3 ингредиента в указанном порядке внутрь списка.
* ВНИМАНИЕ! данные 3 ингредиента всегда присутствуют - их нельзя удалять из списка!

```java

public class Pizza {
    private List<String> ingredients;

    public Pizza(){
        this.ingredients = new ArrayList<>();
    }

    public Pizza(String dough, String salt, String oil){
        this();
        // validation logic
    }

    public Boolean isComplete(){
        // testing logic
    }

    // CHAINING METHODS
    public Pizza with(String ingredient){
        // expansion logic
    }

    public Pizza without(String ingredient){
        // reduction logic
    }

    public String toString() {
        // output logic
    }
}
```
* Добавьте логику в метод **isComplete()** (полноценный рецепт) так чтобы он возвращал **true** только если пицца содержит минимум 4 ингредиента, первые 3 из которых в требуемом порядке имеют только допустимые значения (тесто,соль,масло)
* Добавьте логику чейнинга в каждый из методов - **whith()** и **whithout()** так чтобы первый добавлял в список - новый ингредиент а второй удалял из списка ингредиент! ВНИМАНИЕ - первые 3 ингредиента списка нельзя трогать!
* Так же нельзя добавлять по два раза один и тот же ингредиент!
* Вы имеете право создать в данном классе любые вспомогательные методы, но все они должны быть отмечены как **private** так как ими будет пользоваться только каш класс (например можно сделать метод ```boolean checkIfExists(String ingredient)``` - который проверит если данный ингредиент УЖЕ в списке! - можно пользоваться внутренним методом списка: .indexOf(), .contains()  )
* Проверку можно сделать в **main()** например кодом:

```java
Pizza simplePizza = new Pizza("thick","halit","olive")
                                .with("cheese")
                                .with("tomato")
                                .with("mushrooms")
                                .with("meat");

    System.out.println( "IS pizza complete? " + simplePizza.isComplete() );
    System.out.println( simplePizza );
    

``` 