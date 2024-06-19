базовый класс машина имеет колеса Эти колеса нужно менять. В зависимости от типа машины меняется кол-во колес, радиус и прочие хар-ки.
Исходно мы бы проверяли в классе Car методе repairWheels тип машины и на основании этого как-то выбирали сколько колес надо, радиус и так далее.
Теперь мы разносим это по двум классам и доп проверок не надо. Каждый вид машины сам все знает про свои колеса, просто вызываем метод repairWheels

``` java
class Car {
    Type carType;

    void repairWheels(Load load);
}

class CityCar extends Car {
    
    CityCar() {
        carType = cityCar;
    }

    @Override
    void repairWheels();
}

class Van extends Car {
    
    Van() {
        carType = van;
    }
    
    @Override
    void repairWheels(Load load);
}
```
