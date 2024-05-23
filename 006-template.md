Наследование, композиция и полиморфизм
Решения задания 5
Какие из пяти принципов повторного использования модуля поддерживаются в используемом вами языке программирования?

Python и Java
1) В обоих языках нет возможности параметрировать модуль типом.

2) Поддерживается создание модуля, объединяющего несколько активно обращающихся друг к другу функций.

3) Поддерживается возможность объединения модулей в пакеты/сборки.

4) На уровне модулей в обоих языках нет "автоматического" полиморфизма. Можно вручную импортировать только нужные функции из модуля "родителя" и переопределить оставшиеся.

5) С помощью композиции можно интегрировать несколько модулей с небольшими отличиями в поведении в один. При этом модуль имеет "конструктор" (код, который однократно запускается при его первом импорте).