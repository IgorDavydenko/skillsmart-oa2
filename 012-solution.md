``` java

abstract class Any implements Serializable, Clone, Copy, Comparative {}

class General extends Any {
  String serialize()

  static General deserialize(String data)

  General clone()

  void copy(General target)

  boolean compare(General compare)

  boolean checkClassType(Any tested)
  
}

```
