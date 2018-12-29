# Ciklusok
Programozás során nagyon gyakran előfordul, hogy ugyan azt a műveletet vagy műveleteket többször is végre akarjuk hajtani. Például írjuk ki tízszer, hogy _Hello world_.
```java
System.out.println("Hello world");
System.out.println("Hello world");
System.out.println("Hello world");
System.out.println("Hello world");
System.out.println("Hello world");
System.out.println("Hello world");
System.out.println("Hello world");
System.out.println("Hello world");
System.out.println("Hello world");
System.out.println("Hello world");
```
Már ez is sok fölösleges munkának tűnik, de mi van akkor ha mondjuk 100-szor kell kiírni? Vagy ezerszer. Ilyen esetekben jönnek jól a ciklusok. Általánosságban a ciklusok arra jók, hogy egy vagy több műveletet többször, egymás után végrehajtsunk. Java-ban három féle ciklus van:

* while
* do-while
* for

## While
A `while` egy elől tesztelős ciklus, ami azt jelenti, hogy először megvizsgál egy feltételt, majd ha a feltétel igaz, akkor végrehajtja az adott műveletet, hasonlóan mint egy `if` esetén. A különbség, hogy a művelet végrehajtása után, megint megvizsgáljuk a feltételt, és ha kell, megint végrehajtjuk a műveleteket. Pl.
```java
while ( 1 == 1 ) {
    System.out.println("Hello world");
}
```
Ez az idők végezetéig fogja írni, a _Hello worold_-öt. Ennél egy kicsit hasznosabb lehet a következő megvalósítás:
```java
int i = 0;

while ( i < 10 ) {
    System.out.println("Hello world");
    i += 1; //Ez ugyan az mint az i = i + 1, csak rövidebb
}
```
Ez pont 10szer fogja kiírni a már jól ismert _Hello world_-öt. Ez a számlálós megoldás annyira gyakori, hogy egy saját ciklust is szenteltek neki, ez a `for` ciklus.

## For
A `for` ciklus szintén egy elől tesztelő ciklus, lényegében a `while` egy leegyszerűsített formája. A következőképp néz ki:
```java
for( számláló változó létrehozása; ciklus feltétel; számláló megnövelése a ciklus végén) {
    Ciklusmag;
}
```
Az előző _Hello world_-es példe for-ral így nézne ki:
```java
for ( int i = 0; i < 10; ++i ) {
    System.out.println("Hello world");
}
```
A `++i` ne ilyesszen meg senkit, lényegében csak az `i += 1`-nek egy még rövidebb alakja. (Ugyan így `--i` is létezik ami az `i -= 1` vagy az `i = i - 1` rövidített alakja.)
Ha kételkednénk, hogy ez lényegében csak egy `while` akkor nézzünk rá így:
```java
int i = 0;

for ( ; i < 10; ) {
    System.out.println("Hello world");
    ++i;
}
```
Így már egészen úgy néz ki mint egy `while` ciklus.

## Do-while
A végére maradt a legkevésbé használt ciklus, a `do-while`. Ez egy hátul tesztelős ciklus, ami azt jelenti, hogy csak azután nézi meg a feltételt miután már egyszer megcsinálta a ciklus magjában lévő utasításokat. Így néz ki a már sokat mutogatott _Hello world_ program.
```java
int i = 0;
do {
    System.out.println("Hello world");
    ++i;
} while ( i < 10 );
```
És hogy mitől is más ez mint a `while` ciklus? Nézzük meg, hogy a következő két kód mit csinál.
```java
while ( 1 == 2 ) {
    System.out.println("Hello world");
}
```
```java
do {
    System.out.println("Hello world");
} while ( 1 == 2 );
```
A első, először megnézi, hogy 1 egyenlő-e 2-vel és mivel nem, így nem csinál semmit. Ezzel szemben a második először kiírja, hogy _Hello world_ és csak ezután ellenőrzi a feltételt, ami mivel nem teljeszül így ő is befejezi működését.

Általános igazság, hogy amit meg lehet csinálni `do-while`-al az megvalósítható `while`-al is, ezért a `do-while`-t nem is szokás használni. Persze ha valakinek az a szimpatikus, használja nyugodtan.

## Előző házi folkosítása
Emlékezzünk vissza az előző házi feladatra, ahol három számot kellett bekérni a felhasználótól, és megmondani, hogy sikeresen tippelt-e. Ezt akkor még úgy oldottuk meg, hogy háromszór leírtuk lényegében ugyan azt. Most próbáljuk meg ezt felokosítani, hogy ciklust használjonk.

Eredeti kód:
```java
Random rand = new Random();
Scanner scan = new Scanner(System.in);

int firstRandomNumber = rand.nextInt(5) + 1;
System.out.print("Adj meg egy szamot 1 es 5 kozott: ");
int firstBet = scan.nextInt();

int secondRandomNumber = rand.nextInt(5) + 1;
System.out.print("Adj meg egy szamot 1 es 5 kozott: ");
int secondBet = scan.nextInt();

int thirdRandomNumber = rand.nextInt(5) + 1;
System.out.print("Adj meg egy szamot 1 es 5 kozott: ");
int thirdBet = scan.nextInt();

if ( firstRandomNumber == firstBet || secondRandomNumber == secondBet || thirdRandomNumber == thirdBet ) {
    System.out.println("Nyertel");
} else {
    System.out.println("Sajnos nem nyertel.");
}
```
Ami ismétlődik, hogy létrehozunk egy véletlen számot, és bekérjük a felhasználótól a tippjét. Ezt ki tudjuk emelni modjuk egy for ciklusba, ami háromszor ismétli meg a műveletet. De akkor hogy fogjuk a végén összehasonlítani a random számokat a felhasználó álltal megadottakkal? Mi lenne ha mondjuk ezt is a cikluson belül tennénk meg és lenne egy `int` változó aminek minden esetben megnöveljük az értékét, ha a megoldás jó. Így a végén csak azt kéne megvizsgálni, hogy ez a szám nagyobb-e mint 0.
```java
Random rand = new Random();
Scanner scan = new Scanner(System.in);

int counter = 0;

for ( int i = 0; i < 3; ++i ) {
    int randomNumber = rand.nextInt(5) + 1;
    System.out.print("Adj meg egy szamot 1 es 5 kozott: ");
    int bet = scan.nextInt();
    if ( bet == randomNumber ) {
        counter = counter + 1;
    }
}

if ( counter > 0 ) {
    System.out.println("Nyertel");
} else {
    System.out.println("Sajnos nem nyertel.");
}
```
Lehet, hogy elsőre nehezebben értelmezhető, de ez a kód már rövidebb és jobban karbantartható mint az előző. Képzeljük el azt a szituációt hogy kiderül, mostantól 5 esélyt kell hogy kapjon  a játékos. Csak annyi a dolgunk, hogy a `for` ciklusban átírjuk a 3-at 5-re és már kész is vagyunk.

## Házi feladat
És akkor most jöjjön egy tényleges gyakorló feladat. Készítsünk egy olyan tippjátékot, ahol csak 1 véletlen szám van 1 és 10 között, és a felhasználó addig próbálkozhat eltalálni, míg nem sikerül és a végén kiírjuk, hogy hány próbálkozásába került. Ráadásul, ha nem találja el akkor egy segítségül írjuk ki, hogy a keresett szám nagyobb vagy kisebb-e mint az ő tippje.

## Egy lehetséges megoldás

```java
package demo;

import java.util.Random;
import java.util.Scanner;

public class Main {

    public static void main( final String[] args ) {
        Random rand = new Random();
        Scanner scan = new Scanner(System.in);

        int randomNumber = rand.nextInt(10) + 1;
        boolean success = false;
        int numberOfAttempts = 0;

        System.out.println("Gondoltam egy szamot, tippeld meg.");
        while ( !success ) {
            System.out.print("A tipped: ");
            int bet = scan.nextInt();
            if ( bet == randomNumber ) {
                success = true;
            } else if ( randomNumber > bet ) {
                System.out.println("A keresett szam nagyobb!");
            } else {
                System.out.println("A keresett szam kisebb");
            }
            ++numberOfAttempts;
        }

        System.out.println("Nyertel. Probalkozasaid szama: " + numberOfAttempts);
    }

}
```