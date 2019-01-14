# Buborék rendezés (bubble sort)

Ha azt hitted csak ilyen kis egyszerű programokat tudunk írni a jelenlegi tudásunkal hát hatalmasat tévedtél. Írjunk is gyorsan egy rendező algoritmust, hogy ezt bebizonyítsam. De először is:

## Mi az a rendező algoritmus

Programozásban egy gyakori probléma, hogy van egy kupac adatunk, mondjuk egy tömbben és szeretnénk sorbarendezni őket. Ez a valóságban akár egyerűnek is tűnhet, de programozásban nem nagyon működik a való élet beli logikánk. Szerencsére, nálam sokkal okosabb emberek már rengeteg rendező algoritmust kidolgoztak, nekünk szinte csak választani kell. Ami megint csak nem egyszerű, mert különböző helyzetekben más-más módszerek bizonyultak hatékonyabbnak. Na mi most egy olyat veszünk ami sehogy sem hatékony, de legalább könnyen megérthető és leprogramozható. Ez lesz a buborékrendezés vagy bubble sort.

## Buborék rendezés működése

Működése nagyon egyszerű. Elindulunk a tömbünk elejétől és minden egyes elemet összehasonlítunk az egyel elütte lévővel és ha az kisebb mint a mostani akkor megcseréljük őket. Ezzel ugye azt érjük el, hogy a tömb utolsó eleme legyen a legnagyobb. Lényegében a legnagyobb elem, mint egy buborék, felmegy a tábla tetejére, innen a rendezés neve. Ez volt ugye az első iteráció (igen, mostantól használjuk ezt a kifejezést is. Emlékeztetőül: egy iteráció, egy megtett kör a ciklusban). Hány további iterációra van szükségünk hogy teljesen rendezett legyen a tömb? Tegyük fel, hogy a tömbünk mondjuk 5 elemű.
```
5, 6, 2, 8, 1
```
A első iteráció után így néz ki:
```
5, 2, 6, 1, 8
```
A következő körben teljesen felesleges mind az 5 elemet összehasonlítanunk, ugyanis az ötödik biztosan a legnagyobb. A követhező körben tehát csak az első nágyet hasonlítgatjuk:
```
2, 5, 1, 6, 8
```
Most már az utolsó két elem rendezett, így elég csak első hármat összehasonlítani:
```
2, 1, 5, 6, 8
```
Majd az első kettőt:
```
1, 2, 5, 6, 8
```

Egy példa:

![bubblesort](img\bubblesort.gif)

Java kódban ez így néz ki:
```java
int[] data = {5, 6, 2, 8, 1};

for ( int i = data.length; i > 0; --i) {
    for ( int j = 1; j < i - 1; ++j ) {
        if ( data[j] > data[j+1] ) {
            int tmp = data[j];
            data[j] = data[j+1];
            data[j+1] = tmp;
        }
    }
}
```

A belső ciklus meg végig az elgész tömbön egészen az i-edik elemig és cserélgeti őket ha szükséges. A külső ciklusban az i először megegyezik a tábla méretével, majd ezt folyamatosan csökkentjük, miven nem lesz már rá szükségünk hogy az egész táblát átnézzük.

Ha elsőre nem teljesen világso én azt ajánlom vezessük le papíron egy példával ahogy fent én is tettem, majd kódoljunk is egyet.