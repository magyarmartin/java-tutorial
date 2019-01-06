# Programozási tételek.

Mielőtt új dolgokat tanulnánk, ismételjünk kicsit és nézzünk néhány gyakran használt algoritmust. Ezeket az egyetemen programozási tételeknek is szokás nevezni, mivel olyan alapvető funkciók ezek melyeket szinte kívülről, tétel szerűen kell ismerni. Aggodalomra azonban semmi gond, mivel könnyű kikövetkeztetni őket, és elég hamar megjegyezhetőek. Ezek olyan, ciklust használó programok, amik egy tömbön, szigorúan egy feladatot végeznek el. Persze a tömb később behejettesíthető listával, felhasználó álltal beírt vagy esetleg adatbázisból jövő adattal. Na de akkor nézzük azokat a tételeket.

## Összegzés
Ez talán a legkönyebben kikövetkeztethető.

**Feladat**: Adott egy tömb benne számokkal. Egy változóba számítsuk ki a számok összegét.

**Megoldás**: Itt a megoldás eléggé adja megát. Létrehozunk egy `int` tíőusú változót aminek a kezdeti értéke 0, majd egy ciklussal végigmegyünk a tömb összes elemén (ezt úgy is mondjuk, hogy végigiterálunk) és hozzáadjuk az értékeket a változónkhoz.

```java
int numbers = {5, 78, 5, 34, 8, 56, 43, 9};
int sum = 0;

for ( int i = 0; i < numbers.length; ++i ) {
    sum += numbers[i];
}
```

## Keresés

**Feladat**: Adott egy tömb, benne számokkal, karakterekkel, esetleg `String`-ekkel. A feladat, hogy keressük meg a tömb hányadik eleme tartalmazza a keresett értéket.

**Megoldás**: Erre már láttunk egy példát a `brake`-es fejezetben, ezért most a változatosság kedvéért `while` ciklust használunk. Kell egy int típusú változó amiben tároljuk, hogy hányadik elem a keresett. A változó kezdeti értéke legyen -1 így könnyen kitalálható, ha a keresett elem nem található. A ciklusban addig megyünk amíg meg nem találtuk a keresett értéket, azaz a változónk értéke nem -1, vagy amíg el nem fogy a tömb. Ugyanis nem szeretnénk a végtelenségig keresni.

```java
int numbers = {5, 78, 5, 34, 8, 56, 43, 9};
int index = -1;
int i = 0;

while ( index == -1 || i < numbers.length ) {
    //A keresett elem legyen mondjuk megint 3
    if ( numbers[i] == 3 ) {
        index = i;
    }
    ++i;
}
```

## Számlálás

**Feladat**: Van egy kezdeti tömbünk benne azonos típusú értékekkel (pl. számok). Számoljuk meg, hogy hány olyan érték van ami megfelel a feltételünknek.

**Megoldás**: Legyen egy változónk 0-ás kezdeti értékkel, hívjuk mondjuk `x`-nek. Egy ciklussal végigmegyünk az egész tömbön és ha a tömb adott eleme megfelel a felételünknek, növeljük meg `x`-et.

**Példa**: A tömbünkben legyenek `int` értékek és a példa feltétel legyen: kisebb mint 10.
```java
int numbers = {5, 78, 5, 34, 8, 56, 43, 9};
int x = 0;

for ( int i = 0; i < numbers.length; ++i ) {
    if ( numbers[i] < 10 ) {
        ++x;
    }
}
```

## Maximum keresés

**Feladat**: Van egy kezdeti, számokat tartalmazó tömbünk. Keressük meg a legnagyobb értékét.

**Megoldás**: Mint mindig, itt is szükségünk van egy változóra, amiben a legnagyobb értéket fogjuk tárolni. Híjuk `max`-nak és legyen a kezdeti értéke a tömb első elemének értéke. Egy ciklussal menjünk végig a tömb elemein, az elsőtől kezdve és ha az adott érték nagyobb mint a `max`-ban tárolt érték, akkor kicseréljük a `max`-ot.

```java
int numbers = {5, 78, 5, 34, 8, 56, 43, 9};
int max = numbers[0];

for ( int i = 1; i < numbers.length; ++i ) {
    if ( numbers[i] > max ) {
        max = numbers[i];
    }
}
```

## Feltételes maximumkeresés

**Feladat**: Van egy kezdeti, számokat tartalmazó tömbünk. Keressük meg a legnagyobb értékét ami még az általunk támaszott feltételnek is megfelel.

**Megoldás**: A megoldás nagyon hasonlít a sima maximum kereséshez, viszont most a max kezdeti értéke nem lehet a tömb első elemének értéke, mivel az nem biztos, hogy megfelel a feltételnek. De akkor mi legyen a kezdeti érték? Akár mit is adunk, nem fogjuk tudni, hogy az-e a legnagyobb elem, vagy csak nincs a feltételnek megfelelő érték. Vezessünk be egy második, `boolean` típusú változót amivel azt jelöljük, hogy találtunk a feltételnek megfelelő értéket.
A cikluson belül most már három eset lehetséges. 

1. Eddig még nem találtunk a feltételnek megfelelő értéket és most találtunk egyet. Ebben az esetben autómatikusan az lesz a maximum érték.
2. Már találtunk korábban is, de a mostani érték is megfelel a feltételnek, ráadásul nagyobb is mint az előző. Ebben az esetben az lesz az új legnagyobb.
3. A szám vagy nem felel meg a feltételnek, vagy kisebb mint a már megtalált. Ebben az esetben semmit sem teszünk.

**Példa**: A példában a feltétel legyen: páratlan szám.

```java
int numbers = {5, 78, 5, 34, 8, 56, 43, 9};
int max = 0;
boolean found = false;

for ( int i = 1; i < numbers.length; ++i ) {
    if ( found = false && numbers[i] % 2 != 0 ) {
        max = numbers[i];
        found = true;
    } else if ( found == true && numbers[i] % 2 != 0 && numbers[i] > max ) {
        max = numbers[i];
    }
}
```