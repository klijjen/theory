# Java Core

## Модификаторы доступа

**private (приватный)**: члены класса доступны только внутри класса. Для обозначения используется служебное слово private.

**default, package-private, package level (доступ на уровне пакета):** видимость класса/членов класса только внутри пакета. Является модификатором доступа по умолчанию - специальное обозначение не требуется.

**protected (защищённый):** члены класса доступны внутри пакета и в наследниках. Для обозначения используется служебное слово protected.

**public (публичный):** класс/члены класса доступны всем. Для обозначения используется служебное слово public.

Последовательность модификаторов по возрастанию уровня закрытости: public, protected, default, private.

Во время наследования возможно изменения модификаторов доступа в сторону большей видимости (для поддержания соответствия принципу подстановки Барбары Лисков).

## Ключевое слово **final**

Модификатор final может применяться к переменным, параметрам методов, полям и методам класcа или самим классам.
  - Класс не может иметь наследников;
  - Метод не может быть переопределен в классах наследниках;
  - Поле не может изменить свое значение после инициализации;
  - Параметры методов не могут изменять своё значение внутри метода;
  - Локальные переменные не могут быть изменены после присвоения им значения.

## Типы классов 

  - Top level class (Обычный класс):
    Abstract class (Абстрактный класс);
    Final class (Финализированный класс).
  - Interfaces (Интерфейс).
  - Enum (Перечисление).
  - Nested class (Вложенный класс):
    Static nested class (Статический вложенный класс);
    Member inner class (Простой внутренний класс);
    Local inner class (Локальный класс);
    Anonymous inner class (Анонимный класс).

## Статические методы и поля *

Существуют статические поля и методы, которые не привязаны к конкретному объекту, а к самому классу, и доступ к ним нужно осуществлять уже из класса, а не объекта. Из этого следует, что поля будут в одном экземпляре на всю программу, так как класс всего один.

```java
public class Computer {
  public static String name = "Computer"; // статическое поле

  public static String getName() { // статический метод
    return name;
  }

  public int cores;

  public int getCores() {
    return cores;
  }
}

public class Main {
  public static void main(String[] args) { // тоже статический метод
    Computer computer1 = new Computer();
    Computer computer2 = new Computer();

    // попробуем вывести значение
    System.out.println(computer1.name); // работать не будет, у объектов нет этого поля, только у класса
    System.out.println(Computer.name); // сработает!
  }
}
```

## Exception

Исключения делятся на несколько классов, но все они имеют общего предка — класс Throwable, потомками которого являются классы Exception и Error.

**Ошибки (Errors)** представляют собой более серьёзные проблемы, которые, согласно спецификации Java, не следует обрабатывать в собственной программе, поскольку они связаны с проблемами уровня JVM. Например, исключения такого рода возникают, если закончилась память доступная виртуальной машине.

**Исключения (Exceptions)** являются результатом проблем в программе, которые в принципе решаемы, предсказуемы и последствия которых возможно устранить внутри программы. Например,произошло деление целого числа на ноль.

![image](https://github.com/user-attachments/assets/ceb3b1c7-0da0-4162-b1c5-7fb005950fd7)


## Generics

**Generics** - это технический термин, обозначающий набор свойств языка позволяющих определять и использовать обобщенные типы и методы. Обобщенные типы или методы отличаются от обычных тем, что имеют типизированные параметры.

Примером использования обобщенных типов может служить Java Collection Framework. Так, класс LinkedList<E> - типичный обобщенный тип. Он содержит параметр E, который представляет тип элементов, которые будут храниться в коллекции. Создание объектов обобщенных типов происходит посредством замены параметризированных типов реальными типами данных. Вместо того, чтобы просто использовать LinkedList, ничего не говоря о типе элемента в списке, предлагается использовать точное указание типа LinkedList<String>, LinkedList<Integer> и т.п.
