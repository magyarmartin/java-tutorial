# brake és continue
Két fontos, bár ritkán használt kulcsszó kimaradt eddig. Ezek a `brake` és a `continue`, amik közül a `brake`-el már találkoztunk a `switch`-es példáknál.

## brake
A `brake` azon kívül, hogy a `switch` elengedhetetlen eleme, használhatü még ciklusokban is. Ilyenkor hasonlóan működik mint a `switch` esetében, azaz a kulcsszó hatására megszakad a ciklus futása és a program közvetlenül a ciklus után folytatja a működését. Van például egy tömbünk számokkat, és meg szeretnénk mondani, hogy hányadik eleme a 3. Ez valahogy így nézne ki:

```java
int[] numbers = {1, 5, 8, 3, 7, 5, 85, 8675};
int result = 0;

for ( int i = 0; i < numbers.length; ++i ) {
    if ( numbers[i] == 3 ) {
        result = i + 1;
        brake;
    }
}

System.out.println("A tomb " + result + ". eleme a 3.");
```
A brake miatt a ciklus addig futna amíg meg nem találja a 3-ast, majd továbblépne a kiíratáshoz, ezzel jelen esetben 4 kört sőóroltunk a ciklusban. Ez mind szép és jó, viszont a gyakorlatban kicsit fölösleges, mivel ezt úgy is meg lehetne oldani, hogy a `for` ciklus eleve csak addig menjen amíg meg nem találja a 3-ast.
```java
int[] numbers = {1, 5, 8, 3, 7, 5, 85, 8675};
int result = -1;

//Addig meg amíg az i kisebb mint a tömb hossza, vagy a result egyenlő -1
for ( int i = 0; i < numbers.length || result == -1 ; ++i ) {
    if ( numbers[i] == 3 ) {
        result = i + 1;
    }
}

System.out.println("A tomb " + result + ". eleme a 3.");
```
Ahogy a fenti példa is mutatja, a `brake`-t általában könnyen ki lehet váltani, így nem is szokás használni, de azért jó tiszában lenni vele.

## continue
A `continue` már egy kicsit más történet. A `brake`-hez hasonlóan ezt is ciklusokban használjuk és ez is megállítja a ciklus addigi futását, viszont ez csak az adott kört állítja meg és nem az egész ciklust. Ez elsőre zavaros lehet, nézzünk erről is egy példát.
```java
for ( int i = 1; i <= 100; ++i) {
    if ( i % 2 != 0 ) {
        continue;
    }
    System.out.println(i);
}
```
Itt minden páratlan szám esetén kihagyjuk az adott kört, és a következőre ugrunk, így végeredményképp csak a páros számokat írjuk ki 1-től 100-ig.