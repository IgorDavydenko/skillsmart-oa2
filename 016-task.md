### 16. Политика скрытия методов при наследовании
 
Насколько наследование методов и видимость методов -- схожие по смыслу понятия? Эти понятия ортогональные, по сути, непересекающиеся.

Наследование -- это про отношение между классами внутри иерархии классов,
а видимость методов -- про отношение между классом и его внешним пользователем-программистом (пользователем публичного интерфейса, множества операций соответствующего АТД).

На курсе по проектированию классов на основе АТД мы договаривались, что все поля класса всегда скрыты от внешнего пользователя класса -- ему доступен только публичный интерфейс операций (методов), набор команд и запросов. Поэтому при обсуждении технических деталей наследования мы говорим только о возможном изменении видимости методов, а поля считаем всегда приватными.
К сожалению, в ряде языков это может вызвать проблемы с их наследованием (если приватные поля наследовать не разрешается). В таких случаях надо придерживаться как минимум рекомендательной системы: оформлять компоненты классов, которые нельзя скрыть физически, но желательно скрыть от внешнего мира, исходя из принципов проектирования, как рекомендательно скрытые. В Python например это делается указанием в названии поля или метода префикса из одного символа "_".

Всего существует четыре варианта скрытия метода:
1. метод публичен в родительском классе А и публичен в его потомке B;
2. метод публичен в родительском классе А и скрыт в его потомке B;
3. метод скрыт в родительском классе А и публичен в его потомке B;
4. метод скрыт в родительском классе А и скрыт в его потомке B.

Варианты 1 и 4 поддерживают практически все языки (наследование видимости по умолчанию), вариант 2 также часто возможен, а вот вариант 3 встречается уже весьма редко.

Однако принцип наследования должен иметь под собой прежде всего не техническую специфику, а правильную теорию, методологическую, формальную основу. Так как мы проектируем классы на основе АТД, то и принцип скрытия простой: в каждом классе публичны только те методы, которые входят в спецификацию соответствующего АТД.

Задание 13.

Разберитесь, какие из четырёх вариантов скрытия методов доступны в используемом вами языке программирования. Приведите примеры кода для каждого из доступных вариантов.
