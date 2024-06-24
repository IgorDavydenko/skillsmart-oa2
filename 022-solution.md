``` java
class Car {
    void move();
}

class Van extends Car {
    void move();
}

public static void main() {
    Car car = new Van();
    car.move(); // полиморфный вызов метода. Вызовется метод из move из Van

    List<Van> vans = new ArrayList<>();
    List<? extends Car> cars = vans; // ковариантность при вызове методов
}
```
