Порождающие паттерны: определяют механизмы создания объектов, которые повышают гибкость и повторное использование существующего кода

Структурные паттерны: определяют способы составления объектов и классов в более крупные структуры

Поведенческие паттерны: определяют механизмы взаимодействия между объектами и распределения обязанностей между ними

# Порождающие паттерны проектирования *

## Singleton (одиночка) *
Паттерн, который гарантирует, что у класса есть только один экземпляр, и предоставляет глобальную точку доступа к этому экземпляру.

Этот паттерн полезен в ситуациях, когда необходимо контролировать доступ к ресурсам, таким как файлы, базы данных или конфигурационные параметры,
и обеспечить, что эти ресурсы используются только одним экземпляром класса.

## Factory method (Фабричный метод) *
Паттерн, который определяет интерфейс для создания объекта, но позволяет подклассам изменять тип создаваемого объекта.

Этот паттерн позволяет делегировать создание объектов подклассам, что делает код более гибким и расширяемым.

## Abstract factory (Абстрактная фабрика) *

Паттерн, который предоставляет интерфейс для создания множества взаимосвязанных или взаимозависимых объектов, независимо от их конкретных реализаций.

Этот паттерн позволяет создавать объекты, которые могут работать вместе, обеспечивая при этом гибкость и расширяемость.

## Builder (Строитель) *

Паттерн, который предоставляет способ создания сложных объектов поэтапно.

Он позволяет разделить процесс создания объекта на несколько шагов, что делает его более гибким и управляемым.

Это особенно полезно, когда объект имеет много параметров или его создание требует выполнения нескольких действий.

# Поведенческие паттерны проектирования *

## Strategy (стратегия) *

Паттерн "Стратегия" — это поведенческий паттерн проектирования, который позволяет определить семейство алгоритмов, инкапсулировать каждый из них и сделать их взаимозаменяемыми.

Это позволяет изменять алгоритмы независимо от клиентов, которые ими пользуются.

### Основные части паттерна "Стратегия" *

* Strategy (Стратегия): Интерфейс или абстрактный класс, который определяет метод для выполнения алгоритма.
* ConcreteStrategy (Конкретная стратегия): Конкретные реализации интерфейса или абстрактного класса стратегии. Каждая реализация представляет собой конкретный алгоритм.
* Context (Контекст): Класс, который использует стратегию. Он содержит ссылку на объект стратегии и вызывает метод стратегии для выполнения алгоритма.

## Responsibility chain (цепочка обязанностей) *

Поведенческий паттерн проектирования, который позволяет передавать запросы по цепочке обработчиков.

Каждый обработчик решает, может ли он обработать запрос сам или нужно передать его следующему обработчику в цепочке, запросы передаются по цепочке обработчиков до тех пор, пока один из них не обработает запрос

## Iterator (итератор) *

Поведенческий паттерн проектирования, который предоставляет способ последовательного доступа к элементам составного объекта (например, коллекции или массиву) независимо от его реализации.

# Структурные паттерны проектирования *

## Proxy (прокси) *

Proxy — это структурный паттерн проектирования, который предоставляет суррогатный объект вместо реального.

Прокси-класс управляет доступом к реальному объекту, добавляя свою логику (например, кеширование, контроль доступа или отложенную инициализацию).

### Основные части паттерна "Прокси" *
Subject (Субъект): Интерфейс или абстрактный класс для реального объекта и прокси.

RealSubject (Реальный субъект): Класс, представляющий настоящий объект, доступ к которому мы контролируем.

Proxy (Прокси): Класс, который выступает в качестве заместителя реального объекта.

## Adapter (адаптер) *

Adapter — это структурный паттерн проектирования, который позволяет объектам с несовместимыми интерфейсами работать вместе.

### Основные части паттерна "Адаптер" *

Target (Цель): Интерфейс, ожидаемый клиентом.

Adaptee (Адаптируемый): Класс с несовместимым интерфейсом, который нужно адаптировать.

Adapter (Адаптер): Класс, который реализует интерфейс Target и преобразует запросы клиента в формат, понятный Adaptee.

## Bridge (мост) *

Bridge — это структурный паттерн проектирования, который разделяет абстракцию (интерфейс) и реализацию (конкретные детали) на разные иерархии, чтобы их можно было изменять независимо.

### Основные части паттерна "Мост" *

Abstraction (Абстракция): Базовый интерфейс для управления объектами.

Implementor (Реализатор): Интерфейс для конкретной реализации.

ConcreteImplementor (Конкретный реализатор): Конкретная реализация интерфейса Implementor.

RefinedAbstraction (Расширенная абстракция): Конкретная реализация интерфейса Abstraction.
