возвращаясь к моим любимым машинам
``` java

class Car
  move() - у базового класса автомобиля есть только метод двигаться

class Van extends Car
    void carry() - грузовик может не только ехать, но и перевозить грузы

main()
  Van van = new Van()
  van.move // в наследнике не переопределен метод, однако его можно вызвать
```