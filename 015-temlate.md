Наследование, композиция и полиморфизм
Решения задания 12
Добавьте в классы General и Any попытку присваивания и её реализацию.

Python

class Any(General):

    @classmethod
    def assignment_attempt(cls, target, source):
        if isinstance(target, cls) and isinstance(source, cls):
            target.value = source.value
            return target
        return Void
Java

class General implements Serializable {

    public static <TFrom extends Any, TTo extends Any>
            TTo assignmentAttempt(TFrom from, TTo to) {

        var classFrom = from.getType();
        var classTo = to.getType();
        if (classTo.isAssignableFrom(classFrom)) {
            return (TTo) from;
        }
        return None;
    }
