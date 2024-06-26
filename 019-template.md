Наследование, композиция и полиморфизм
Решения задания 15
Приведите пример иерархии, где вместо некоторого поля родительского класса с набором предопределённых значений применяется наследование.

Python
``` python
class _ClassificationDataInput(Any):
    def get_prepared(self, *args, **kwargs) -> t_Any:
        """Request method, must return acceptable
        object as input for classification model."""
        raise NotImplementedError()

class YesNoQuestionnaire(_ClassificationDataInput):
    """
    >>> q = YesNoQuestionnaire()
    >>> q.get_prepared(True, False, True)
    (1, 0, 1)
    """
    def get_prepared(self, *user_answers: bool, **kwargs) -> Tuple[int, ...]:
        prepared = tuple(map(int, user_answers))
        return prepared

class MovementTest(_ClassificationDataInput):
    """
    >>> BAD, AVERAGE, GOOD = range(3)
    >>> m = MovementTest()
    >>> m.get_prepared(BAD, GOOD, AVERAGE)
    (0, 2, 1)
    """
    def get_prepared(self, *test_result_enums: int, **kwargs) -> Tuple[int, ...]:
        prepared = test_result_enums
        return prepared
```
        
Java
``` java
public abstract class Developer {
}

// Так делать плохо:
public class Worker extends Developer {
    public int skill; // -1 junior, 0 middle, 1 senior

    public Worker(int skill){
        this.skill = skill;
    }
}


// Лучше делать так:
public class Senior extends Developer {
}

public class Middle extends Developer {
}

public class Junior extends Developer {
}

// Теперь наш код открыт для расширений, но закрыт для изменений, 
// и с точки зрения семантики так куда лучше :)
```
