``` java
// ковариантность основаная на типах
class Car {}
class Van extends Car {}

List<Van> vans = new ArrayList<>();
List<? extends Car> cars = vans;


// контравариантность
List<Car> cars = new ArrayList<>();
List<? super Dog> vans = cars;
vans.add(new Van());

```
