

Python

Пример 1

#ковариантность

from typing import Generic, TypeVar, Callable

animal = TypeVar('animal', covariant=True)

class Animal(): pass
class Cat(Animal): pass

# Контейнер на вход принимает любой объект типа Anuimal
class Box(Generic[animal]):
    def __init__(self, content: animal) -> None:
        self._content = content

# Можно проверить контейнер с животным, 
# а значит, и с котом, как частным случаем животного
def check_box(box: Box[Animal]):
    pass

box = Box(Cat())
check_box(box)
#контравариантность

class Person(): pass
class Sportsman(Person): pass
class Policeman(Person): pass

def person_run(person: Person) -> None:
    print('Person running')

# Спортсмен и полисмен могут бегать: 
def sportsman_run(sportsman: Sportsman) -> None:
    print('Sportsman running. So fast!')
def policeman_run(policeman: Policeman) -> None:
    print('The policemen don\'t run. He shoots.')

# ковариантным типом по документации считается Callable
def make_sportsman_run(sportsman: Sportsman, run_func: Callable[[Sportsman], None]):
    print('Shoot in the air with gun!')
    run_func(sportsman)

# подойдёт даже обычный Person
make_sportsman_run(Sportsman(), person_run)

# а вот на типе Policeman будет ошибка
make_sportsman_run(Sportsman(), policeman_run)
Пример 2

# ковариантность

class Sword: pass
class FuryBlade(Sword): pass

class Knight:
    def get_melee_weapon(self):
        return Sword()
class Paladin(Knight):
    def get_melee_weapon(self):
        return FuryBlade()

knigt, paladin = Knight(), Paladin()
s, fb = knigt.get_melee_weapon(), paladin.get_melee_weapon()

isinstance(s, Sword), isinstance(s, FuryBlade)
# (True, False)

isinstance(fb, Sword), isinstance(fb, FuryBlade)
# (True, True)
# контравариантность

from typing import TypeVar, Generic

T_contra = TypeVar('T_contra', contravariant=True)

class _T(Generic[T_contra]):
    def __init__(self, item: T_contra) -> None: ...

class BladedWeapon: pass
class Sword(BladedWeapon): pass
class Broadsword(Sword): pass
class Cutlass(Broadsword): pass
class Shuriken(BladedWeapon): pass

def sharpen_melee_weapon(weapon: _T[Broadsword]) -> None: pass

sword1, sword2 = _T(Broadsword()), _T(Sword())
sharpen_melee_weapon(sword1)  # OK
sharpen_melee_weapon(sword2)  # OK

shuriken = _T(Shuriken()) 
# error: "sharpen_melee_weapon" has incompatible type _T[Shuriken]
sharpen_melee_weapon(shuriken) # error

cutlass = _T(Cutlass()) # error ...
sharpen_melee_weapon(cutlass) # error

Java
``` java
// Ковариантность:
List<Integer> l1 = new ArrayList<>();
l1.add(42);
List<? extends Number> l2 = l1; // read-only список. 
// Безопасное приведение потомка(Integer) к родителю (Number)


// Контравариантность:
List<Number> l3 = new ArrayList<>();

List<? super Double> l4 = l3; // write-only список. 
// Безопасное приведение родителя (Number) к потомку (Double)

// Такой механизм позволяет обходить небезопасное приведение типов,
// когда в List<Double> могут оказаться значения типа Integer, 
// если сначала List<Double> привести к List<Number>
```
