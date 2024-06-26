Наследование, композиция и полиморфизм
Решения задания 16
Если используемый вами язык программирования это допускает, напишите примеры полиморфного и ковариантного вызовов метода.

Python
``` python
# Полиморфный вызов.

class Person():
    def walk(self):
        print('Yes, i can walk...')

# Наследник расширяет класса-предок
# новым методом:
class Baker(Person):
    def bake(self):
        print('and bake!')

somebody = Baker()

# Тип Baker ведет себя как тип Person
# при вызове этого метода:
somebody.walk()
# Ковариантный вызов.

from typing import Generic, TypeVar, Callable

animal = TypeVar('animal', covariant=True)

class Animal():
    def make_sound(self):
        raise NotImplementedError

class Cat(Animal):
    def make_sound(self):
        print('Meow!')

class Dog(Animal):
    def make_sound(self):
        print('Woof!')

# ящик на вход принимает любой объект типа Animal
class Box(Generic[animal]):
    def __init__(self, content: animal) -> None:
        self._content = content

    def make_sound(self):
        self._content.make_sound()

# Ковариантный вызов:
def shake_box(box: Box[Animal]):
    box.make_sound()

some_animal = Cat()
box = Box(some_animal)
shake_box(box)
```

Java

``` java 
class Expression {
    @Override
    public String toString() {
        return "some expression";
    }

    public void method() {
        System.out.println("some method from expression");
    }
}

class SimpleExpression extends Expression {
    @Override
    public String toString() {
        return "some simple expression";
    }

    @Override
    public void method() {
        System.out.println("some method from simple expression");
    }
}

class ComplexExpression extends SimpleExpression {
    @Override
    public String toString() {
        return "some complex expression";
    }

    @Override
    public void method() {
        System.out.println("some complex expression");
    }
}


class Calculator {
    Expression getExpression() {
        System.out.println("Некоторая логика простого калькулятора");
        return new Expression();
    }

    // В Java только массивы ковариантны,
    // остальные обобщенные коллекции использовать нельзя.
    public <T extends Expression> void covariantMethod(T[] values) {
        for (T value : values) {
            System.out.println(value.toString());
        }
    }

    // Можно передавать как объект типа Expression, 
    // так и любого его потомка
    public void polymorphicMethod(Expression value) {
        value.method();
    }
}

class EngineeringCalculator extends Calculator {
    @Override
    SimpleExpression getExpression() {
        System.out.println("Некоторая логика инженерного калькулятора");
        return new SimpleExpression();
    }

    @Override
    public <T extends Expression> void covariantMethod(T[] values) {
        super.covariantMethod(values);
        System.out.println(values.length);
    }
}

...

Calculator calculator = new EngineeringCalculator();
Expression[] expressions = new Expression[2];
expressions[0] = new SimpleExpression();
expressions[1] = new ComplexExpression();

// пример вызовы ковариантного метода (только для массивов)
calculator.covariantMethod(expressions);

// пример вызова полиморфного метода 
// передаем наследника класса Expression, 
// а не объект класса Expression
calculator.polymorphicMethod(new SimpleExpression());
```
