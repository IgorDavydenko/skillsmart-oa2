Пример специализации - геометрические фигуры

``` java
abstract class FourAngle 
    private int a, b, c, d - задает рамеры сторон четырехугольника
    private int alpha, beta, gama, delta - задает величины углов четырехугольника

    FourAngle(int a, int b, int c, int d, int alpha, int beta, int gama, int delta) - консткрутор в котором необходимо задать все 4 стороны и углы

    // getters
    // setters


class Rectangle extends FourAngle
    Rectangle(int a, int b) - уже на уровне конструктора можно задать только две стороны, по свойствам прямоугольника

    // необходимо ограничить сеттеры и убрать сеттеры для углов - иначе можно сделать из прямоугольника четрыехугольник, и фигура будент не соответствовать к примеру для вычислений площади, центра вписаной/описанной окружности и пр.
```

Пример расширения - вернемся к машинам из прошлого примера
``` java
abstract class Car
    Car()

    abstract move() - у базового класса автомобиля есть только метод двигаться

class Van extends Car
    Van()
    
    void move()

    void carry() - грузовик может не только ехать, но и перевозить грузы определенного объема/веса. Т.о. функционал базового класса расширен
```
