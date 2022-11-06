
# Описание работы внутри *JVM*
## // 1
Создается примитивная переменная *int i*, cо значением 1, которая записываеться в стэк. 
```java
int i = 1; 
```

## // 2
 Подгружается класс *Object* через *Application ClassLoader*, который отправляет запрос 
*Platform ClassLoader*, который в свою очередь обращается к *Bootstrap ClassLoader*. Bootstrap 
уже загружает *Object* из своей библиотеки. *Object о* инициализируется в *heap*, а ссылка на 
него кладется в стек в переменную *"о"* .

```java
Object o = new Object();
```

## // 3
Подгружается класс *Intenger* через ClassLoader (*Application ClassLoader* -> *Platform ClassLoader* -> *Bootstrap ClassLoader* ).
*Integer ii* создается в heap, cсылка сохраняется в стэке.

```java
Integer ii = 2; 
```

## // 4
В стэке создаеться фрейм для метода *printAll*. Ссылки на аргументы метода уже есть в стэке.
```java
printAll(o, i, ii);
```

## // 5
Создается примитивная переменная *uselessVar*, cо значением 700, которая записываеться в стэк.


```java
Integer uselessVar = 700;
```
## // 6

Конструктор, который выводит объект типа *String* путем сложения аргументов метода *printAll*.
Переменная *"о"* удаляеться сборщиком мусора.
```java
System.out.println(o.toString() + i + ii);
```
##  // 7

Вызываеться фукция, который выводит сообщение со значением *finished*. Для него создается фрейм,
в качестве аргумента передается ссылка на строку *finished*.

```java
System.out.println("finished");
```
