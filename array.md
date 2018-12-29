# Tömbök
Egy fontos alapvető elem még eddig kimaradt. Gyakran megesik, hogy kifejezetten sok adattal szeretnénk dolgozni, annyival, hogy nem szeretnénk hozzájuk külön változót létrehozni. Vegyünk például egy általános iskolai osztályt, ahol osztály átagot szeretnénk számolni. Ha csak mondjuk 20-an járnak oda, akkor is létre kell hozni külön 20 változót a gyerekek átlagainak.
```java
double pisti = 3.4d;
double eszter = 2.8d;
double imre = 4.5d;
...
```
Ha meg minden gyerek átlagát is ki kell számolni akkor meg aztán tényleg megszámlálhatatlan változónk lenne. Erre a problémára lettek kitalálva a tömbök. 

A tömbök hasonlóak mint a változók, nekik is van nevük, van típusuk, csak éppen nem egy, hanem több érték is rendelhető hozzájuk. Létrehozásuk így néz ki:
```java
double[] averages = new double[20];
```
A típus után teszünk egy nyitó és egy záró négyzetes zárójelet, hogy jelezzük, egy tömböt szeretnénk. Majd az egyenlőségjel után nem egy értéket írunk hanem a `new` szócskát, a tömb típusát, majd négyzetes zárójelek között a tömb méretét. A példában szereplő tömb mérete 20, így maximum 20 `double` típusu értéket tehetünk bele. Az értékeket ezután így rendeljük hozzá:
```java
averages[0] = 3.4d;
averages[1] = 2.8d;
averages[2] = 4.5d;
```
Most a tömb neve után tesszük a négyzetes zárójelet, és a benne lévő számmal jelezzük hogy hányadik helyre szeretnénk az értéket pakolni. A tömböket 0-tól indexeljük, ami azt jelenti, hogy egy 20 elemü tömb első eleme igazából a nulladik (`averages[0]`) míg a huszadik a tizenkilencedik (`averages[19]`). Ez a nullától indexelés egy általános dolog programozásban, így akár mekkora hülyeségnek tűnik, jobb ha megszokjátok.

Érték kiolvasása hasonló képpen történik.
```java
double imre = averages[2];
//vagy
System.out.println(averages[2]);
```
Egy másik módszer tömb létreozására és egyben értékadásra:
```java
String[] months = {"Januar", "Februar", "Marcius", "Aprilis", "Majus", "Julius", "Junius", "Augusztus", "Szeptember", "Oktober", "November", "December"};
```
Így sokkal kevesebb kóddal létrehoztam egy 12 elemű `String` típusú tömböt ami a hónapokat tartalmazza.

Még egy érdekes tulajdonsága a tömböknek, hogy `tömbNeve.length` parancsal elkérhetjük a tömb hosszát, így tudunk olyan programot írni ami tetszőleges méretű tömbel tud működni.
```java
int[] array = {1, 2, 3, 4, 5, 6};

System.out.println("A tomb hossza: " + array.length);
System.out.println("A tömb utolso eleme: " + array[array.length - 1];
```
Fontos!!! Mivel a tömböket nullától indexeljük így az utolsó eleme a `length - 1`-dik eleme lesz. A `length`-edik eleme nem létezik így a program hibát fog dobni.

## Több dimenziós tömbök
Egy érdekes koncepció a több dimenziós tömbök, vagy más néven a tömbök tömbje. Ilyenkor azt mondjuk hogy a tömb elemei maguk is tömbök. Ezt a végtelenségig lehet csinálni, csinálhatunk tömbök, tömbjének tömbjét is, csak átláthatatlan lesz. A leggyakoribb a két dimenziós tömb, vagy más néven mátrix.

Egy mátrix létrehozása:
```java
int[][] matrix = new int[5][];
matrix[0][0] = 5;
matrix[0][1] = 8;
matrix[1][0] = 4;
matrix[1][1] = 6;
//Vagy
int[][] matrix = {{5,8}, {4,6}};
```
Ezek a következő mátrixot eredményezik:

| | |
| - | :-: |
| 5 | 8 |
| 4 | 6 |

Általános szabály, hogy tömbök első méretét kötelezően meg kell adni, de a többit nem muszáj. Ezért van a `new int[5][]` mivel itt nem adjuk meg a második méretet. Persze megadhatnánk ha akarnánk. Egyébként a mátrixok (vagy bárhány dimenziós tömbök) pontosan úgy működnek mint egy sima tömb.

## Házi feladat
Ezúttal két házi feladatot is adnék, egy tömböset és egy mátrixosat.

1. Adott a követkető tömb: `int[] array = {3, 1, 4, 9, 5};
Írjunk egy ciklust ami megcseréli a tömb elemeit. Úgy írjuk meg hogy bármekkora tömbbel tudjon működni.

    Lehetséges megoldás:
    ```java
    int[] array = {3, 1, 4, 9, 5};

    for ( int i = 0; i < array.length / 2; ++i ) {
        int temp = array[i];
        array[i] = array[array.length - (1 + i)];
        array[array.length - (1 + i)] = temp;
    }

    //Eredmény:
    for ( int i = 0; i < array.length; ++i ) {
        System.out.print(array[i] + " ");
    }
    ```

1. Adott a következő mátrix 
    ```java
    int[][] matrix = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}}
    ```
    Írjunk egy olyan programot ami a mátrix elemeit megtükrözi az 1, 5, 9 átlón.
    Tehát ebből:

    | | | |
    | - | :-: | :-: |
    | 1 | 2 | 3 |
    | 4 | 5 | 6 |
    | 7 | 8 | 9 |
    Ez lesz:
    | | | |
    | - | :-: | :-: |
    | 1 | 4 | 7 |
    | 2 | 5 | 8 |
    | 3 | 6 | 9 |
    Ez is tetszőleges, ugyanolyan hosszúságú és szélességű tömbön működjön.

    Lehetséges megoldás:
    ```java
    int[][] matrix = { { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };

    for ( int i = 0; i < matrix.length; ++i ) {
        for ( int j = 0; j < i; ++j ) {
            int temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
        }
    }

    // Eredmény:
    for ( int i = 0; i < matrix.length; ++i ) {
        for ( int j = 0; j < matrix[i].length; ++j ) {
            System.out.print(matrix[i][j] + " ");
        }
        System.out.println();
    }
    ```