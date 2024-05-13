классический пример наследования можно показать на шахматах. Абстрактный класс фигуры декларирует 
``` java
abstract class ChessFigure

    private final Role role
    private int position_X
    private int position_Y

    public ChessFigure(Role role, int x, int y)

    abstract void move()

class Pawn extends ChessFigure

    public ChessFigure(Role role, int x, int y)

    void move()
        position_Y += 2;
```
Композицию удобно показать на машинах и двигателях. Независимо от реализации (дизель-бензин) у машины должен быть двигатель который можно завести. 
Полиморфизм - любая машина должна уметь ехать, независимо от реализации
``` java
abstract class Car

    private Engine engine

    Car(Engine engine)

    abstract move()

abstract class Engine

    private Type engineType
    private int horse_power

    Engine(Type engine, int horse_power)

    abstract void run()

class Diesel extends Engine

    Diesel(int horse_power)
        super(Type.Diesel, horse_power)
    
    void run()

class Gas extends Engine
    Gas(int horse_power)
        super(Type.Gas, horse_power)
    
    void run()

class CityCar extends Car
    Car(Engine engine)
        super(engine)
    
    void move()

 
Engine engine = new Gas(150)
Car car = new CityCar(engine);
car.engine.run()
car.move()
```
