Наследование, композиция и полиморфизм
Решения задания 1
Предлагаемые варианты решений, эти и все последующие -- это немного подправленные ответы лучших учеников (mikhail-z, YaphetS7, gala, Gex и др.). Не относитесь к ним как к абсолютным эталонам, а творчески перерабатывайте :) В частности, изучайте комментарии к ним других занимающихся.

В ответах возможны ошибки, если найдёте новые, будет очень здорово. Возможно, и ваши ответы станут образцами для других.

``` Python
# колесо
class Wheel:
    def __init__(self):
        print('wheel...')

# Композиция: велосипед содержит/"has-a" колёса
class Bicycle:
    def __init__(self, wheel_count: int = 2):
        self.wheels = [Wheel() for _ in range(wheel_count)]

    def ride(self):
        print("bicycle riding...")

# Наследование: байк есть/"is-a" велосипед с двумя колёсами
class Bike(Bicycle):
    def __init__(self):
        super().__init__(wheel_count=2)

    def ride(self):
        print("bike riding...")

# Полиморфизм
bikes = [Bicycle(), Bike()]
for b in bikes:
    b.ride()
```

``` Java
public class Animal { // животное

    public void voice(){ // голос
        System.out.println("I am animal!");
    }
}

public class Head { // голова

}

public class Cat extends Animal { // наследование

    private Head head; // композиция: у кота всегда имеется голова

    //полиморфизм 
    @Override
    public void voice(){ // голос
        System.out.println("I am the cat!");
    }

    // При вызове voice() у подтипов типа Animal 
    // не обязательно знать конкретный тип объекта,
    // главное, что его подтип -- потомок класса Animal.

}
```
