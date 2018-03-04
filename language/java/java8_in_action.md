# Note for Java 8 In Action

## Default Method Resolution

1. Classes always win. A method declaration in the class or a superclass takes prior- ity over any default method declaration.
2. Otherwise, sub-interfaces win: the method with the same signature in the most specific default-providing interface is selected. (If B extends A, B is more specific than A).
3. Finally, if the choice is still ambiguous, the class inheriting from multiple inter- faces has to explicitly select which default method implementation to use by overriding it and calling the desired method explicitly.

> from Java 8 In Action

# Functional Interface

* Any interface with a SAM(Single Abstract Method) is a functional interface, and its implementation may be treated as lambda expressions.

* Note that Java 8’s default methods are not abstract and do not count: a functional interface may still have multiple default methods. 

> from http://www.baeldung.com/java-8-functional-interfaces
> oracle doc: https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html

## Predicate

```java
@FunctionalInterface
public interface Predicate<T>{
    boolean test(T t);
}
```

## Consumer

```java
@FunctionalInterface
public interface Consumer<T>{
    void accept(T t);
}
```

## Function

```java
@FunctionalInterface
public interface Function<T, R>{
    R apply(T t);
}
```

## Suppier

```java
@FunctionalInterface
public interface Consumer<T>{
    T get();
}
```

