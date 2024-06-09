``` java
class General implements Serializable {
    
    public void assignmentAttempt(target, source) {
        if (source instanceof target.class) {
            source = (target.class) source;
        } else {
            source = (None) source;
        }
    }

}

class Any extends General { }

...

final class None extends Any /*A, B, ....*/ { }
```
