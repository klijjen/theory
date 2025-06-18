**Порождающие паттерны проектирования:**
- Абстрактная фабрика (Abstract factory) - Класс, который представляет собой интерфейс для создания других классов.
- Строитель (Builder) - Класс, который представляет собой интерфейс для создания сложного объекта.
- Фабричный метод (Factory method) - Делегирует создание объектов наследникам родительского класса. Это позволяет использовать в коде программы не специфические классы, а манипулировать абстрактными объектами на более высоком уровне.
- Прототип (Prototype) - Определяет интерфейс создания объекта через клонирование другого объекта вместо создания через конструктор.
- Одиночка (Singleton) - Класс, который может иметь только один экземпляр.

**Структурные паттерны проектирования:**
- Адаптер (Adapter) - Объект, обеспечивающий взаимодействие двух других объектов, один из которых использует, а другой предоставляет несовместимый с первым интерфейс.
- Мост (Bridge) - Структура, позволяющая изменять интерфейс обращения и интерфейс реализации класса независимо.
- Заместитель (Proxy) - Объект, который является посредником между двумя другими объектами, и который реализует/ограничивает доступ к объекту, к которому обращаются через него.

- Компоновщик (Composite) - Объект, который объединяет в себе объекты, подобные ему самому.
- Декоратор (Decorator) - Класс, расширяющий функциональность другого класса без использования наследования.
- Фасад (Facade) - Объект, который абстрагирует работу с несколькими классами, объединяя их в единое целое.
- Приспособленец (Flyweight) - Это объект, представляющий себя как уникальный экземпляр в разных местах программы, но по факту не являющийся таковым.

**Поведенческие паттерны проектирования:**
- Стратегия (Strategy) - Предназначен для определения семейства алгоритмов, инкапсуляции каждого из них и обеспечения их взаимозаменяемости.
- Цепочка обязанностей (Chain of responsibility) - Предназначен для организации в системе уровней ответственности.
- Команда (Command) - Представляет действие. Объект команды заключает в себе само действие и его параметры.
- Итератор (Iterator) - Представляет собой объект, позволяющий получить последовательный доступ к элементам объекта-агрегата без использования описаний каждого + __из объектов, входящих в состав агрегации.
  
- Интерпретатор (Interpreter) - Решает часто встречающуюся, но подверженную изменениям, задачу.
- Посредник (Mediator) - Обеспечивает взаимодействие множества объектов, формируя при этом слабую связанность и избавляя объекты от необходимости явно ссылаться друг на друга.
- Хранитель (Memento) - Позволяет не нарушая инкапсуляцию зафиксировать и сохранить внутренние состояния объекта так, чтобы позднее восстановить его в этих состояниях.
- Наблюдатель (Observer) - Определяет зависимость типа «один ко многим» между объектами таким образом, что при изменении состояния одного объекта все зависящие от него оповещаются об этом событии.
- Состояние (State) - Используется в тех случаях, когда во время выполнения программы объект должен менять своё поведение в зависимости от своего состояния.
- Шаблонный метод (Template method) - Определяет основу алгоритма и позволяет наследникам переопределять некоторые шаги алгоритма, не изменяя его структуру в целом.
- Посетитель (Visitor) - Описывает операцию, которая выполняется над объектами других классов. При изменении класса Visitor нет необходимости изменять обслуживаемые классы.

* Strategy (стратегия)
* Responsibility chain (цепочка обязанностей)
* Iterator (итератор)

  
# Порождающие паттерны проектирования *

Паттерны проектирования - это проверенные временем решения для типичных задач, которые часто встречаются в разработке программного обеспечения.
Они помогают разработчикам писать код более эффективно и поддерживать его легче.

По своему предназначению они разделяются на три вида:

Порождающие паттерны: определяют механизмы создания объектов, которые повышают гибкость и повторное использование существующего кода

Структурные паттерны: определяют способы составления объектов и классов в более крупные структуры

Поведенческие паттерны: определяют механизмы взаимодействия между объектами и распределения обязанностей между ними

В этой лекции поговорим о порождающих паттернах проектирования.
Их много, но рассмотрим пока что только:

* Singleton (одиночка)
* Factory method (Фабричный метод)
* Abstract factory (Абстрактная фабрика)
* Builder (Строитель)

## Singleton (одиночка) *
Паттерн, который гарантирует, что у класса есть только один экземпляр, и предоставляет глобальную точку доступа к этому экземпляру.

Этот паттерн полезен в ситуациях, когда необходимо контролировать доступ к ресурсам, таким как файлы, базы данных или конфигурационные параметры,
и обеспечить, что эти ресурсы используются только одним экземпляром класса.

Пример реализации на Java:

```Java
public class Singleton {
    // Приватное статическое поле для хранения единственного экземпляра
    private static Singleton instance;

    // Приватный конструктор, чтобы предотвратить создание экземпляров извне
    private Singleton() {
        // Инициализация, если необходимо
    }

    // Статический метод для получения единственного экземпляра
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }

    // Другие методы класса
    public void someMethod() {
        // Реализация метода
    }
}
```

Можно реализовывать его по-разному:
инициализировать объект сразу или по запросу, делать класс потокобезопасным или нет

## Factory method (Фабричный метод) *
Паттерн, который определяет интерфейс для создания объекта, но позволяет подклассам изменять тип создаваемого объекта.

Этот паттерн позволяет делегировать создание объектов подклассам, что делает код более гибким и расширяемым.

Пример использования:

Предположим, что у нас есть приложение для создания различных типов логгеров (например, для файлового логирования и консольного логирования).
Мы хотим, чтобы наше приложение могло легко добавлять новые типы логгеров без изменения существующего кода.

```java
// Интерфейс для продукта (логгера)
interface Logger {
    void log(String message);
}

// Конкретный продукт: Файловый логгер
class FileLogger implements Logger {
    @Override
    public void log(String message) {
        System.out.println("Logging to file: " + message);
    }
}

// Конкретный продукт: Консольный логгер
class ConsoleLogger implements Logger {
    @Override
    public void log(String message) {
        System.out.println("Logging to console: " + message);
    }
}

// Создатель (фабрика)
abstract class LoggerFactory {
    // Фабричный метод
    public abstract Logger createLogger();

    // Метод, использующий фабричный метод
    public void logMessage(String message) {
        Logger logger = createLogger();
        logger.log(message);
    }
}

// Конкретный создатель: Фабрика для файлового логгера
class FileLoggerFactory extends LoggerFactory {
    @Override
    public Logger createLogger() {
        return new FileLogger();
    }
}

// Конкретный создатель: Фабрика для консольного логгера
class ConsoleLoggerFactory extends LoggerFactory {
    @Override
    public Logger createLogger() {
        return new ConsoleLogger();
    }
}
```

## Abstract factory (Абстрактная фабрика) *

Паттерн, который предоставляет интерфейс для создания множества взаимосвязанных или взаимозависимых объектов, независимо от их конкретных реализаций.

Этот паттерн позволяет создавать объекты, которые могут работать вместе, обеспечивая при этом гибкость и расширяемость.

Пример реализации на Java:

```java
// Интерфейс для продукта A
interface Button {
    void paint();
}

// Конкретный продукт A1
class WindowsButton implements Button {
    @Override
    public void paint() {
        System.out.println("You have created a Windows button.");
    }
}

// Конкретный продукт A2
class MacButton implements Button {
    @Override
    public void paint() {
        System.out.println("You have created a Mac button.");
    }
}

// Интерфейс для продукта B
interface Checkbox {
    void paint();
}

// Конкретный продукт B1
class WindowsCheckbox implements Checkbox {
    @Override
    public void paint() {
        System.out.println("You have created a Windows checkbox.");
    }
}

// Конкретный продукт B2
class MacCheckbox implements Checkbox {
    @Override
    public void paint() {
        System.out.println("You have created a Mac checkbox.");
    }
}

// Интерфейс абстрактной фабрики
interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}

// Конкретная фабрика 1
class WindowsFactory implements GUIFactory {
    @Override
    public Button createButton() {
        return new WindowsButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new WindowsCheckbox();
    }
}

// Конкретная фабрика 2
class MacFactory implements GUIFactory {
    @Override
    public Button createButton() {
        return new MacButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new MacCheckbox();
    }
}

// Клиентский код
public class Application {
    private Button button;
    private Checkbox checkbox;

    public Application(GUIFactory factory) {
        button = factory.createButton();
        checkbox = factory.createCheckbox();
    }

    public void paint() {
        button.paint();
        checkbox.paint();
    }
}

// Пример использования
public class Main {
    public static void main(String[] args) {
        Application app1 = new Application(new WindowsFactory());
        app1.paint();

        Application app2 = new Application(new MacFactory());
        app2.paint();
    }
}
```

В этом примере мы обстрагировались от конкретных реализаций Checkbox и Button, работаем с интерфейсами, и если захотим поддерживать, например, линукс,
не придётся переписывать логику всего приложения, а просто создать новую фабрику - и всё

## Builder (Строитель) *

Паттерн, который предоставляет способ создания сложных объектов поэтапно.

Он позволяет разделить процесс создания объекта на несколько шагов, что делает его более гибким и управляемым.

Это особенно полезно, когда объект имеет много параметров или его создание требует выполнения нескольких действий.

Пример на языке Java:

```java
// Продукт
class Pizza {
    private String dough;
    private String sauce;
    private String topping;

    public void setDough(String dough) {
        this.dough = dough;
    }

    public void setSauce(String sauce) {
        this.sauce = sauce;
    }

    public void setTopping(String topping) {
        this.topping = topping;
    }

    @Override
    public String toString() {
        return "Pizza{" +
                "dough='" + dough + '\'' +
                ", sauce='" + sauce + '\'' +
                ", topping='" + topping + '\'' +
                '}';
    }
}

// Интерфейс строителя
interface PizzaBuilder {
    void buildDough();
    void buildSauce();
    void buildTopping();
    Pizza getResult();
}

// Конкретный строитель
class HawaiianPizzaBuilder implements PizzaBuilder {
    private Pizza pizza;

    public HawaiianPizzaBuilder() {
        this.pizza = new Pizza();
    }

    @Override
    public void buildDough() {
        pizza.setDough("cross");
    }

    @Override
    public void buildSauce() {
        pizza.setSauce("mild");
    }

    @Override
    public void buildTopping() {
        pizza.setTopping("ham+pineapple");
    }

    @Override
    public Pizza getResult() {
        return pizza;
    }
}

// Директор
class PizzaDirector {
    private PizzaBuilder builder;

    public PizzaDirector(PizzaBuilder builder) {
        this.builder = builder;
    }

    public void constructPizza() {
        builder.buildDough();
        builder.buildSauce();
        builder.buildTopping();
    }
}

// Пример использования
public class Main {
    public static void main(String[] args) {
        PizzaBuilder builder = new HawaiianPizzaBuilder();
        PizzaDirector director = new PizzaDirector(builder);

        director.constructPizza();
        Pizza pizza = builder.getResult();

        System.out.println(pizza);
    }
}
```

Здесь получаем, что пиццу мы готовим поэтапно: сначала занимаемся тестом, потом соусом, а потом - начинкой.
Тем самым мы разбили создание сложного объекта на несколько более простых этапов

# Поведенческие паттерны проектирования *

**Напоминание**: звёздочками выделено то, что будет на защите и экзамене.

Все примеры кода написаны на Java, но эти паттерны можно реализовывать на любом языке.

------

Как мы обсудили в третьей лекции, поведенческие паттерны определяют механизмы взаимодействия между объектами и распределения обязанностей между ними.

Их тоже существует много, но в этой лекции рассмотрим только:

* Strategy (стратегия)
* Responsibility chain (цепочка обязанностей)
* Iterator (итератор)

## Strategy (стратегия) *

Паттерн "Стратегия" — это поведенческий паттерн проектирования, который позволяет определить семейство алгоритмов, инкапсулировать каждый из них и сделать их взаимозаменяемыми.

Это позволяет изменять алгоритмы независимо от клиентов, которые ими пользуются.

### Основные части паттерна "Стратегия" *

* Strategy (Стратегия): Интерфейс или абстрактный класс, который определяет метод для выполнения алгоритма.
* ConcreteStrategy (Конкретная стратегия): Конкретные реализации интерфейса или абстрактного класса стратегии. Каждая реализация представляет собой конкретный алгоритм.
* Context (Контекст): Класс, который использует стратегию. Он содержит ссылку на объект стратегии и вызывает метод стратегии для выполнения алгоритма.

В качестве использования паттерна "стратегия" рассмотрим реализации различных алгоритмов сортировки.

Интерфейс стратегии:
```java
public interface SortingStrategy {
    void sort(int[] array);
}
```

Реализация конкретных стратегий:
```java
public class BubbleSortStrategy implements SortingStrategy {
    @Override
    public void sort(int[] array) {
        // Реализация сортировки пузырьком
        System.out.println("Sorting using Bubble Sort");
    }
}

public class QuickSortStrategy implements SortingStrategy {
    @Override
    public void sort(int[] array) {
        // Реализация быстрой сортировки
        System.out.println("Sorting using Quick Sort");
    }
}
```

Создание контекта:
```java
public class Sorter {
    private SortingStrategy strategy;

    public void setStrategy(SortingStrategy strategy) {
        this.strategy = strategy;
    }

    public void sortArray(int[] array) {
        strategy.sort(array);
    }
}
```

Пример использования:
```java
public class Main {
    public static void main(String[] args) {
        Sorter sorter = new Sorter();

        // Использование стратегии сортировки пузырьком
        sorter.setStrategy(new BubbleSortStrategy());
        int[] array1 = {5, 3, 8, 4, 2};
        sorter.sortArray(array1);

        // Использование стратегии быстрой сортировки
        sorter.setStrategy(new QuickSortStrategy());
        int[] array2 = {5, 3, 8, 4, 2};
        sorter.sortArray(array2);
    }
}
```

## Responsibility chain (цепочка обязанностей) *

Поведенческий паттерн проектирования, который позволяет передавать запросы по цепочке обработчиков.

Каждый обработчик решает, может ли он обработать запрос сам или нужно передать его следующему обработчику в цепочке, запросы передаются по цепочке обработчиков до тех пор, пока один из них не обработает запрос

```Java
interface Handler {
    void handleRequest(Request request);
    void setNextHandler(Handler nextHandler);
}

// Конкретный обработчик A
class ConcreteHandlerA implements Handler {
    private Handler nextHandler;

    @Override
    public void handleRequest(Request request) {
        if (request.getType() == RequestType.TYPE_A) {
            System.out.println("ConcreteHandlerA handled the request.");
        } else if (nextHandler != null) {
            nextHandler.handleRequest(request);
        }
    }

    @Override
    public void setNextHandler(Handler nextHandler) {
        this.nextHandler = nextHandler;
    }
}

// Конкретный обработчик B
class ConcreteHandlerB implements Handler {
    private Handler nextHandler;

    @Override
    public void handleRequest(Request request) {
        if (request.getType() == RequestType.TYPE_B) {
            System.out.println("ConcreteHandlerB handled the request.");
        } else if (nextHandler != null) {
            nextHandler.handleRequest(request);
        }
    }

    @Override
    public void setNextHandler(Handler nextHandler) {
        this.nextHandler = nextHandler;
    }
}

// Запрос
class Request {
    private RequestType type;

    public Request(RequestType type) {
        this.type = type;
    }

    public RequestType getType() {
        return type;
    }
}

// Типы запросов. В реальной жизни может быть чем-то типа POST или GET
enum RequestType {
    TYPE_A, TYPE_B
}

// Пример использования
public class Main {
    public static void main(String[] args) {
        Handler handlerA = new ConcreteHandlerA();
        Handler handlerB = new ConcreteHandlerB();

        handlerA.setNextHandler(handlerB);

        Request requestA = new Request(RequestType.TYPE_A);
        Request requestB = new Request(RequestType.TYPE_B);

        handlerA.handleRequest(requestA); // Вывод: ConcreteHandlerA handled the request.
        handlerA.handleRequest(requestB); // Вывод: ConcreteHandlerB handled the request.
    }
}
```

## Iterator (итератор) *

Поведенческий паттерн проектирования, который предоставляет способ последовательного доступа к элементам составного объекта (например, коллекции или массиву) независимо от его реализации.

```Java
// Интерфейс итератора
interface Iterator<T> {
    boolean hasNext();
    T next();
}

// Конкретный итератор
class ArrayIterator<T> implements Iterator<T> {
    private T[] items;
    private int position;

    public ConcreteIterator(T[] items) {
        this.items = items;
        this.position = 0;
    }

    @Override
    public boolean hasNext() {
        return position < items.length;
    }

    @Override
    public T next() {
        if (this.hasNext()) {
            return items[position++];
        }
        throw new ArrayIndexOutOfBoundsException(); // либо как-то по-другому обрабатывать этот случай, но лучше бросать ошибку
    }
}
```

# Структурные паттерны проектирования *

**Напоминание**: звёздочками выделено то, что будет на защите и экзамене.

Все примеры кода написаны на Java, но эти паттерны можно реализовывать на любом языке.

------

Структурные паттерны проектирования описывают, как классы и объекты могут быть составлены в более крупные структуры, обеспечивая гибкость и масштабируемость.

Сегодня мы рассмотрим три ключевых паттерна:

* Proxy (прокси)
* Adapter (адаптер)
* Bridge (мост)


## Proxy (прокси) *

Proxy — это структурный паттерн проектирования, который предоставляет суррогатный объект вместо реального.

Прокси-класс управляет доступом к реальному объекту, добавляя свою логику (например, кеширование, контроль доступа или отложенную инициализацию).

### Основные части паттерна "Прокси" *
Subject (Субъект): Интерфейс или абстрактный класс для реального объекта и прокси.

RealSubject (Реальный субъект): Класс, представляющий настоящий объект, доступ к которому мы контролируем.

Proxy (Прокси): Класс, который выступает в качестве заместителя реального объекта.

### Пример

Ситуация: Вы создаёте систему, где некоторым пользователям нужен доступ к ограниченным ресурсам.

Например, вы работаете с базой данных, но хотите ограничить доступ к её некоторым функциям.

Реализация:

Интерфейс работы с базой данных:

```java
public interface Database {
    void query(String sql);
}
```

Реальный класс базы данных:

```java
public class RealDatabase implements Database {
    @Override
    public void query(String sql) {
        System.out.println("Executing query: " + sql);
    }
}
```

Прокси с проверкой доступа:

```java
public class DatabaseProxy implements Database {
    private RealDatabase realDatabase;
    private boolean hasAccess;

    public DatabaseProxy(boolean hasAccess) {
        this.realDatabase = new RealDatabase();
        this.hasAccess = hasAccess;
    }

    @Override
    public void query(String sql) {
        if (hasAccess) {
            realDatabase.query(sql);
        } else {
            System.out.println("Access denied. Query cannot be executed.");
        }
    }
}
```

Использование:

```java
public class Main {
    public static void main(String[] args) {
        Database userDb = new DatabaseProxy(false);
        Database adminDb = new DatabaseProxy(true);

        userDb.query("SELECT * FROM users"); // Вывод: Access denied. Query cannot be executed.
        adminDb.query("SELECT * FROM users"); // Вывод: Executing query: SELECT * FROM users
    }
}
```

## Adapter (адаптер) *

Adapter — это структурный паттерн проектирования, который позволяет объектам с несовместимыми интерфейсами работать вместе.

### Основные части паттерна "Адаптер" *

Target (Цель): Интерфейс, ожидаемый клиентом.

Adaptee (Адаптируемый): Класс с несовместимым интерфейсом, который нужно адаптировать.

Adapter (Адаптер): Класс, который реализует интерфейс Target и преобразует запросы клиента в формат, понятный Adaptee.

### Пример

Интеграция сторонней библиотеки

Ситуация: Вы используете библиотеку для обработки данных, но её интерфейс не совпадает с вашими требованиями.

Реализация:

Сторонний класс библиотеки:

```java
public class ExternalLogger {
    public void logMessage(String msg) {
        System.out.println("External log: " + msg);
    }
}
```

Ваш целевой интерфейс:

```java
public interface Logger {
    void log(String message);
}
```

Адаптер для интеграции:

```java
public class LoggerAdapter implements Logger {
    private ExternalLogger externalLogger;

    public LoggerAdapter(ExternalLogger externalLogger) {
        this.externalLogger = externalLogger;
    }

    @Override
    public void log(String message) {
        externalLogger.logMessage(message); // Адаптируем метод
    }
}
```

Использование:

```java
public class Main {
    public static void main(String[] args) {
        ExternalLogger externalLogger = new ExternalLogger();
        Logger logger = new LoggerAdapter(externalLogger);

        logger.log("This is a test message."); // Вывод: External log: This is a test message.
    }
}
```

## Bridge (мост) *

Bridge — это структурный паттерн проектирования, который разделяет абстракцию (интерфейс) и реализацию (конкретные детали) на разные иерархии, чтобы их можно было изменять независимо.

### Основные части паттерна "Мост" *

Abstraction (Абстракция): Базовый интерфейс для управления объектами.

Implementor (Реализатор): Интерфейс для конкретной реализации.

ConcreteImplementor (Конкретный реализатор): Конкретная реализация интерфейса Implementor.

RefinedAbstraction (Расширенная абстракция): Конкретная реализация интерфейса Abstraction.

### Пример
Устройства вывода данных
Ситуация: Вы разрабатываете систему вывода данных, и ваша архитектура должна поддерживать как разные типы устройств (например, монитор и принтер), так и форматы данных (текст, изображения).

Реализация:

Интерфейс устройства:

```java
public interface Device {
    void print(String data);
}
```

Конкретные устройства:

```java
public class Monitor implements Device {
    @Override
    public void print(String data) {
        System.out.println("Displaying on monitor: " + data);
    }
}

public class Printer implements Device {
    @Override
    public void print(String data) {
        System.out.println("Printing to paper: " + data);
    }
}
```

Абстракция вывода:

```java
public abstract class Output {
    protected Device device;

    public Output(Device device) {
        this.device = device;
    }

    public abstract void render(String data);
}
```

Расширенная абстракция:

```java
public class TextOutput extends Output {
    public TextOutput(Device device) {
        super(device);
    }

    @Override
    public void render(String data) {
        device.print("Text: " + data);
    }
}

public class ImageOutput extends Output {
    public ImageOutput(Device device) {
        super(device);
    }

    @Override
    public void render(String data) {
        device.print("Image: [Binary data: " + data + "]");
    }
}
```

Использование:

```java
public class Main {
    public static void main(String[] args) {
        Device monitor = new Monitor();
        Device printer = new Printer();

        Output textOnMonitor = new TextOutput(monitor);
        Output textOnPrinter = new TextOutput(printer);

        textOnMonitor.render("Hello, world!"); // Вывод: Displaying on monitor: Text: Hello, world!
        textOnPrinter.render("Hello, world!"); // Вывод: Printing to paper: Text: Hello, world!

        Output imageOnMonitor = new ImageOutput(monitor);
        imageOnMonitor.render("101010101"); // Вывод: Displaying on monitor: Image: [Binary data: 101010101]
    }
}
```

