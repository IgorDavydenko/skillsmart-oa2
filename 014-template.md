аследование, композиция и полиморфизм
Решения задания 11
По возможности постройте иерархию, используя готовые General и Any, и замкните её снизу классом None.

Python

В Python нету проверок типов, поэтому можно создать любой класс без предков/потомков, не входящий в нашу систему типов, унаследованную от General.

Java
``` java
class General implements Serializable {
   ...
}

class Any extends General { }

...

final class None extends Any /*A, B, ....*/ { }

//

class Test {
    public static Any getSome() {
        return new None();
    }

    public static void setSome(Any any) {
        if (any instanceof None) {
            System.out.println("wrong value!!!");
        }
    }
}
```
