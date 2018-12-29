# Változók
A változók minden programozási nyel valaegységei. Úgy lehet elképzelni őket mint kicsi tárolók, amikben különböző fontos dolgokat tárolunk. Az egyikben egy számot, a másikban egy szöveget, a harmadikban egy elefántot, attól függ éppen mire van szükség. Később ezeket tetszés szerint kivehetjük a tárolókból hogy aztán új értéket helyezzünk beléjük. 

Úgy is elképzelhetjük őket mint a matematikai változókat. Ahogy ott is minden feladatban más volt az X értéke, úgy itt is folyamatosan változhat.

A változók java-ban típusosak, azaz meg kell mondani, hogy milyen típusú elemeket tárolhat és csak olyan értéket helyezhetünk bele. Gondolj csak bele, egy kutya tárolóba nem fér bele egy elefánt.

Java-ban a változók 2 csoportba osztahók: primitívek és objektumok.

A primitívek a következők:
1. byte - 1 byte-nyi értéket tud tárolni, azaz egy -128 és 127 közötti számot
1. short - 2 byte-nyi érték, min. -32,768 max. 32,767
1. int - 4 byte-nyi érték min. -2^31 max. 2^31-1. Ezt használjuk leggyakrabban számok tárolására
1. long - 8 byte-nyi érték min. -2^63 max. 2^63-1
1. float - lebegőpontos, azaz tört számok tárolására használjuk
1. double - hasonló mint az előző, pontosabb, viszont több memóriát használ
1. char - egy hosszúságú karakter, pl. a vagy c
1. boolean - igaz-hamis érték, true - igaz, false - hamis

Az objektumokról később még sokat fogunk beszélni, egyelőre elég ismerni a `String`-et ami szövegek tárolására alkalmas. De elég a szóból, nézzünk egy kis gyakorlatot.

Készítsünk egy új programot ugyan úgy ahogy az előbb. Hozzunk létre miden változó típusból egyet, majd irassuk ki az értéküket.

Változót létrehozni a következőképp lehet:
változó_típusa változó_neve = változó értéke;. Azaz pl. int x = 5;

A teljes kód így néz ki:
```java
package com.company;

public class Main {

    public static void main(String[] args) {
	    byte b = 1;
        short s = 10;
        int i = 100;
        long l = 1000;
        float f = 1.5f;
        double d = 14.9d;
        char c = 'a';
        boolean bol = true;
        String str = "Hello John";

        System.out.println(b);
        System.out.println(s);
        System.out.println(i);
        System.out.println(l);
        System.out.println(f);
        System.out.println(d);
        System.out.println(c);
        System.out.println(bol);
        System.out.println(str);
    }
}
```

Figyeld meg, hogy float esetén f-et, double esetén d-t írunk az érték végére, char esetén aposztófokat teszünk a karakter elejére és végére, String esetén pedig idézőjeleket. Ezzel segítünk a fordítóprogramnak kitalálni a típust. Nem mindegy például, hogy 1, '1' vagy "1". A másik érdekesség, hogy a `System.out.println();`-ba ezúttal nem írtunk idézőjelet. Ennek az az oka, hogy normál esetben nem is kell, ő csuipán egy változót vár. Az hogy `System.out.println("Hello world");` lényegében csak egy rövidítése a következőnek.
```java
String helloWorld = "Hello World";
System.out.println(helloWorld);
```

Egyelőre nem tűnnek túl érdekesnek vagy hasznosnak a változók, de a következő fejezetben megnézzük milyen műveleteket végezhetünk velük.