Урок 12. Семинар: ООП Дизайн и Solid
Взять реализованный код в рамках семинара 4 и продемонстрировать применение принципов, усвоенных на семинаре. Нужно в проекте прокомментировать участки кода, которые рефакторим, какой принцип применяем и почему
Формат сдачи: ссылка на гитхаб проект

Дополнительное задание (если код в рамках 4 семинара уже прошел рефакторинг)
Проект work6: продемонстрировать применение принципов, усвоенных на семинаре. Нужно в проекте прокомментировать участки кода, которые рефакторим, какой принцип применяем и почему.
Проект: work6 https://drive.google.com/file/d/1TISNEXhZVc9MwIAyeOjiV9E2Kr1Nz8x3/view?usp=sharing (прикрепить файлом)
Формат сдачи: ссылка на гитхаб проект


На вопрос: "Как проверить java класс на соответствие SOLID принципам? Какой алгоритм действий?"
Интернет нам подсказывает вот что:
"Для проверки соответствия Java класса принципам SOLID можно использовать следующий алгоритм действий:

1. Принцип единственной ответственности (Single Responsibility Principle, SRP):
   - Определите, какие задачи и ответственности несет класс.
   - Проверьте, что класс отвечает только за одну задачу или аспект функциональности.
   - Если класс выполняет несколько различных задач, разделите его на отдельные классы, каждый из которых отвечает только за одну задачу.

2. Принцип открытости/закрытости (Open/Closed Principle, OCP):
   - Определите, насколько класс открыт для расширения новыми функциями.
   - Проверьте, что класс можно расширить без изменения его исходного кода.
   - Если класс не соответствует этому принципу, примените паттерны проектирования, такие как стратегия или адаптер, чтобы обеспечить его расширяемость.

3. Принцип подстановки Барбары Лисков (Liskov Substitution Principle, LSP):
   - Убедитесь, что классы, производные от базового класса, могут быть использованы вместо него без нарушения корректности программы.
   - Проверьте, что классы-наследники не изменяют поведение базового класса, а только расширяют или переопределяют его функциональность.

4. Принцип разделения интерфейса (Interface Segregation Principle, ISP):
   - Убедитесь, что интерфейсы, реализуемые классом, являются независимыми и содержат только необходимые методы.
   - Проверьте, что класс не зависит от методов, которые он не использует.
   - Если класс реализует "толстый" интерфейс, разделите его на несколько более узких интерфейсов.

5. Принцип инверсии зависимостей (Dependency Inversion Principle, DIP):
   - Проверьте, что класс зависит от абстракций, а не от конкретных реализаций.
   - Убедитесь, что класс не создает экземпляры зависимых объектов напрямую, а получает их через внедрение зависимости (dependency injection).
   - Используйте интерфейсы или абстрактные классы для определения зависимостей класса.

Применение этих принципов поможет создать гибкие, расширяемые и поддерживаемые классы в вашем Java-приложении."

Для проверки у нас есть два класса с 4 семинара, остальные преподавателем не предоставлены: User и UserComparator.
Проверим по алгоритму класс User.
1. SRP:
Класс User только одну задачу: хранит минимальные атрибуты пользователя - ФИО. 
Т.к. данный класс отвечает только за хранение ФИО, то я считаю, что данный класс соответствует приципу единственной ответственности.
2. OCP:
класс User прекрасно раширяется без изменения его исходного кода, что и было поделано в рамках домашней работы при реализации класса Teacher.
Т.к. данный класс можно расширить без изменения его исходного кода, то я считаю, что данный класс соответствует приципу открытости/закрытости.
3. LSP:
производные от User классы Teacher и Student имеют ФИО и могут быть использованы вместо него без нарушения корректности программы и не изменяют поведение класса User.
Поэтому, я считаю, что данный класс соответствует приципу подстановки Барбары Лисков.
4. ISP:
Класс User содержат только необходимые методы, которые используются для реализации хранения актуальной информации о ФИО пользователя.
Поэтому, я считаю, что данный класс соответствует приципу разделения интерфейса.
5. DIP:
Класс User не зависит ни от одного класса
Поэтому, я считаю, что данный класс соответствует приципу инверсии зависимостей.
Таким образом, класс User полность соответствует принципам SOLID.

Проверим по алгоритму класс UserComparator.
1. Класс UserComparator реализует интерфейс Comparator для класса User и его наследников и решает одну задачу: сравнение двух экземпляров по ФИО.
Я считаю, что данный класс соответствует приципу единственной ответственности.
2. Трудно придумать как можно расширить этот специфический класс, т.к. для сравнения по другим критериям нужно реализовать независимый от этого класса Comparator. А сравнение по фио реализовано полность.
Я считаю, что данный класс соответствует приципу открытости/закрытости.
3. производные классы не планируюся в принципе для компараторов.
Я считаю, что данный класс соответствует приципу подстановки Барбары Лисков.
4. класс содержит единственный метод реализующий интерфейс Comparator полностью выполняющий функцию сравнения двух объектов по ФИО.
Я считаю, что данный класс соответствует приципу разделения интерфейса.
5. класс не имеет зависимостей от других классов. Он зависит только от наличия полей ФИО и возможности получения их значений в сравниваемых объектах.  
Я считаю, что данный класс соответствует приципу инверсии зависимостей.
Таким образом, класс UserComparator полность соответствует принципам SOLID.