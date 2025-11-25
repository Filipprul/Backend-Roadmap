# Was sind Lambda Expressions?
Eine Lambda Expression ist eine kurze Funktion ohne Namen, die man wie ein Objekt behandelt und überall hin übergeben kann.
Wichtig:
- In Java kann man Lambda nur für Functional Interfaces verwenden.
- Ein Functional Interface hat genau eine abstrakte Methode (z.B. `Runnable`, `Comperator`, `Consumer`, `Function`, `Predicate`).

Beispiel eines Functional Interfaces:
```java
@FunctionalInterface
interface Operation {
	int run(int a, int b);
}
```
Lambda sind einfach eine kompakte Schreibweise für diese eine Methode.

# Warum gibt es Lambdas?
1. Weniger Boilerplate-Code (keine anonymen Klassen mehr).
2. Funktionen wie Daten behandeln (an Methoden übergeben, speichern, kombinieren).
3. Streams API wäre ohne Lambdas praktisch unbenutzbar.

# Syntax
```java
(Parameter) -> { Codeblock }
```

Weitere Varianten:
#### Ein Parameter, ein Ausdruck
```java
x -> x * x
```

#### Mehrere Parameter
```java
(a, b) -> a + b
```

#### Mit Block
```java
(x) -> {
	System.out.println(x);
	return x * 2;
}
```

# Vergleich: anonyme Klasse vs. Lambda
Ohne Lambda
```java
Runnable r1 = new Runnable() {
    @Override
    public void run() {
        System.out.println("Hello");
    }
};
```

Mit Lambda
```java
Runnable r2 = () -> System.out.println("Hello");
```
Begründung: Runnable hat nur run(), daher reicht `() -> ...`

# Wann funktioniert Lambda
Nur wenn man ein Interface mit 1 abstrakten Methode hat.

Beispiele:
- `Consumer<T>` → `void accept(T t)`
- `Function<T,R>` → `R apply(T t)`
- `Predicate<T>` → `boolean test(T t)`
- `Supplier<T>` → `T get()`
- `Comparator<T>` → `int compare(T a, T b)`

# Was Lambda nicht ist!
- „Ein Lambda ersetzt ein Objekt“ → Falsch. Es ist ein Objekt, nur eben kompakt geschrieben.
- „Ein Lambda kann auf alles angewendet werden“ → Nein. Nur bei Functional Interfaces.
- „Ein Lambda ist schneller“ → Geschwindigkeit ist identisch zu anonymen Klassen.