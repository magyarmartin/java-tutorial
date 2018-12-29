# Kommentek
Programozás során előfordulhat, hogy szeretnénk gondolatokat, magyarázatokat, emlékeztetőket, vagy bármi mást írni a kódba, amit nem szeretnénk ha a fordítóprogram figyelembe venne. Ezeket hívják kommenteknek. Java-ban 3 féle komment van:

* Egysoros
* Többsoros
* Dokumentációs / javadoc

Most ez elő kettőről fogunk beszélni.

## Egysoros komment
Ahogy a neve is mondja, ezek a kommentek egy soron keresztül értelmezetek. A `//` jel után bermit írhatunk, az adott sor végéig, a fordítóprogram azt nem fogja figyelembe venni.
```java
System.out.println("Ez nem komment");
//Ide bármit írhatok
System.out.println("Ez sem"); //Ide is azt írok amit akarok
```
## Többsoros komment
A többsoros komment `/*`-al kezdődik és `*/`-el végződik. Bármit amit ezek közé írunk, figyelmen kívül lesz hagyva a program fordításakor.
```java
System.out.println("Ez nem komment"); /*De ez
már
az
System.out.println("Ez is komment");
De ez már*/ System.out.println("Nem az");
```