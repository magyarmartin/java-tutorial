# Hello World
Első programunk egy _hello world_ program lesz. A hello world program egy olyan egyszerű program ami kiírja a képernyőre hogy hello world. Sok értelme önmagában nincs, de hagyományosan midnen programnyelv tanulása ezzel kezdődik. Lássunk is neki:

Indítjuk el az Intellij-t. File -> New -> Project. Bal oldalsó sávban válasszuk ki a java-t. Next. Pipáljuk be a _Create project from template_-t és válasszuk a _Command Line App_-ot. Next. Adjuk neki valami projekt nevet. pl hello_world és állítsuk be a Project location alatt hogy hova mentsük. A _Base package_ egyelőre maradhat. Finish.

A következőt látjuk:
```java
package com.company;

public class Main {

    public static void main(String[] args) {
	// write your code here
    }
}
```
Ebből egyelőre nem sokat értünk, de ez nem is probnléma. Előbbutóbb minden világos lesz. Most koncentráljunk a `public static void main(String[] args)` részre. Ezt hívják main függvénynek vagy main metódusnak és ez a mi kis programunk kiinduló pontja. Amit a kapcsos zárójelek közé írunk, az fog lefutni és pontosan abban a sorrendben ahogy írjuk. A main metódus mindig ugyan így néz ki, így hamarosan már te is fejből fogod tudni, hogy: `public static void main(String[] args)`.

A programot a jobb felső sarokban található zöld nyíllal futtathatjuk. Kattintsunk is rá. Alúlról felugrott egy ablak, de mint várható volt ezen kívül semmi se történt, a programunk nem csinál semmit. Ahhoz hogy kiírassuk a _Hello World_ mondatot, a következő sort kell a kapcsos zárójelek közé írni.
```java
System.out.println("Hello World");
```
Ha most megint kipróbáljuk, láthatjuk hogy kiírja a kívánt szöveget.

A `System.out.println` ugyanis kiírja a képernyőre az idézőjelek közé írt szöveget. Sőt, nem csak hogy kírja, de még egy plus sortörést is ír a végére. Így most ha a hello world alá írunk egy `System.out.println("Hello Dave");`-et is, akkor a _Hello Dave_ a _Hello World_ alatt jelenik meg. Ha nem ez lenne a célunk akkor sincs baj, ugyanis van egy `System.out.print()` parancs is ami ugyan ezt csinálja, csak sortörés nélkül.

Fontos még a pontosvessző a sor végén. Ezzel jelezzük ugyanis hogy vége az adott parancsnak. Pontosvessző nélkül a program megpróbál tovább "olvasni" hátha hosszabb az utasítás, és hibára fut.