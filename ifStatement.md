# if-else szerkezet
Már képesek vagyunk létrehozni változókat, értéket adni nekik, műveleteket végrehajtani rajtuk és kiíratni eredményüket. Most bevezetjük a döntési helyzetet ahol bizonyos feltételek meghatérozzák, hogy a program hogyan fusson tovább. Ez az if-else szerkezettel velósul meg, ami a következőképp néz ki:
```java
if ( feltétel ) { // Ha a fejtétel teljesül
    történjen valami
} else { // Különben
    történjen valami más
}
```
A feltételnek egy boolean értéknek kell lennie, tehát például az
```java
if ( true ) {
    System.out.println("Hello");
}
```
mindig ki fogja írni a képernyőre, hogy `Hello`. Ahogy látható az `else` opcionális. Persze általában nem ilyen egyszerű egy feltétel. Vegyünk például egy x változót. Ha az x értéke nagyobb mint 10 akkor írjuk ki hogy nagyobb, különben pedig, hogy kisebb.
```java
int x = 15;

if ( x > 10 ) {
    System.out.println("Nagyobb");
} else {
    System.out.println("Kisebb");
}
```
Ez persze nem túl izgalma, mivel mindig azt fogja kiírni, hogy `Nagyobb` de hamarosan keresünk rá egy megoldást. Viszont most még térjünk vissza az if-else szerkezethez mert van még egy dolog amiről eddig nem beszéltem. Tegyük fel hogy az `x` 3 féle lehet:
* Kisebb mint 10
* 10 és 100 közötti
* Nagyobb mint 100

Többféleképp is meg lehet oldani a problémát viszont most, viszont én most az `else if` használatát szeretném bemutatni ami kb azt tudja mit a neve is sejtet. Az `if` után írható olyan else ág ami szintén vár egy feltételt. Megoldás az elöbbi példára:
```java
int x = 15;

if ( x < 10 ) {
    System.out.println("Kisebb mint 10");
} else if ( x > 100 ) {
    System.out.println("Nagyobb mint 100");
} else {
    System.out.println("10 és 100 közötti");
}
```
`else if`-ből bárhányat lehet egymás után használni.
Na de aakor lássuk azt a tippjátékot.

## Tippjáték
A játék úgy fog működni, hogy generálunk egy véletlen számot 1 és 10 között. Ezután bekérünk a jatékostól egy számot és ha eltatálja, kiíjuk, hogy nyert, különben pedig, hogy veszített. Amit eddig még nem tanultunk az a véletlen szám generálás, illetve a szám bekérése a felhasználótól.

### Véletlen szám generálás
Ez egy úgynevezett Random objektummal fog történni. Ezt a következőképp hozhatjuk létre:
```java
Random rand = new Random();
```
Ez nem csak véletlen számokat,de véletlen karaktereket vagy véletlen boolean-eket is létre tud hozni. De egyelére maradjunk a számoknál.
```java
rand.nextInt(x);
```
Ez egy 0 és x közötti véletlen számot fog visszaadni. Mi a játékban 1 és 10 közötti számokat szeretnénk így a végső változat így fog kinézni:
```java
int number = rand.nextInt(10) + 1;
```
A `rand.nextInt(10)` 0-9 számokat adná vissza, ehhez hozzáadunk még 1-et és így megkapjuk a kívánt 1-10 közötti számot.

### Szám bekérése felhasználótól
Ez is hasonlóan működik mint a véletlen szám, csak itt egy scanner-t kell létrehoznunk először, amit a következőképpen tehetünk meg:
```java
Scanner scan = new Scanner(System.in);
```
Ezután a `scan.nextInt()` utasításra a program várni fog a felhasználóra amíg az be nem ír egy számot, és azt adja vissza. Figyeljünk rá, hogy ha nem számot írunk be akkor nem fog működni. Késöbb perszer erre is lesznek jó megoldásaink.

### A teljes megoldás
A teljes megodás valahogy így fog kinéni:
```java
package demo;

//Ez a 2 sor elengedhetetlen a Scanner és a Random használatához.
import java.util.Random;
import java.util.Scanner;

public class Main {

    public static void main( final String[] args ) {
        Random rand = new Random();
        int randomNumber = rand.nextInt(10) + 1;

        Scanner scan = new Scanner(System.in);
        //print-et használunk println helyett mivel szeretnénk ha ugyan abban a sorban 
        //kéne megadni a számot mint amelyikben bekérjük
        System.out.print("Adj meg egy szamot 1 es 10 kozott: ");
        int bet = scan.nextInt();
        if ( randomNumber == bet ) {
            System.out.println("Nyertel");
        } else {
            System.out.println("Sajnos nem nyertel. A helyes valasz: " + randomNumber);
        }
    }

}
```
## Házi feladat
Egy kis házi feladat, hogy tényleg megértsük itt a dolgokat.

Készítsünk egy olyan tippjátékot ami 3szor enged tippelni 3 különböző  1 és 5 közötti számra és ha legalább az egyiket eltaláljuk, nyertünk.

Egy lehetséges megoldás:
```java
package demo2;

import java.util.Random;
import java.util.Scanner;

public class Main {

    public static void main( final String[] args ) {
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
    }

}
```