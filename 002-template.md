Наследование, композиция и полиморфизм
Решения задания 2
Python
``` python
class Bicycle: // велосипед
    def __init__(self, wheel_count: int = 2):
        self.wheels = [Wheel() for _ in range(wheel_count)]

class Engine: // электромотор
    def __init__(self, power: float):
        self.power = power
        print('engine power is', power)

# Специализация: шоссейный велосипед -- подтип велосипеда
# Расширение: электровелосипед, дополнен мотором
class ElectricRoadBicycle(Bicycle):
    def __init__(self, power: float):
        super().__init__()
        self.engine = Engine(power)
```
Java
``` java
public class Human{
    // -- voice()
    // -- walk()
    // -- run()
}

public class Worker extends Human{ 
    // специализация класса-родителя, 
    // т.к. рабочий - более частный случай,
    // т.к. все работники - люди, но не все люди - работники
    // -- work()
}

public class Car{
    // -- drive()
    // -- park()
    // -- startEngine()
}

public class AutonomousCar extends Car{ 
    // расширение класса-родителя, 
    // т.к. все самоуправляемые машины
    // являются машинами, но не все машины - самоуправляемы

    // -- autoDrive()
    // -- autoPark()
}
```
