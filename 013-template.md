Наследование, композиция и полиморфизм
Решения задания 10
Запрещаем переопределение методов в потомках.

Python

"""
Возможность запрета и для методов, и для классов, 
появилась в Python 3.8 -- 
с помощью декоратора @final
"""

class Base:
    @final
    def do_not_override_this(self) -> None: ...

class A(Base):
    # error: Cannot override final attribute "do_not_override_this"
    # (previously declared in base class "Base")
    def do_not_override_this(self) -> None: ...


@final
class FinalBase: ...

class B(FinalBase): ...
# error: Cannot inherit from final class "FinalBase"
Java

Для этого используется ключевое слово final.

public final Class getType() 
{ return this.getClass(); } 
