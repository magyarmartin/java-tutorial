# Programozási nyelvek, elmélet

Most hogy már tudunk programozgatni, ideje hogy kicsit megnézzük, mik is azok a programozási nyelvek, hogyan működnek, mi a különbség közöttük.

Eredetileg a számítógépeket a processzoruk utasításaihoz rendelt számokkal "programozták". Ezt nevezzük gépi kódnak, és ez az amit filmekben előszeretettel binárisan, azaz egyesekkel és nullákkal ábrázolják.

```
1011 1000 1101 0100 0000 0111 0000 0000 0000 0000 1001 0000 0100 1000
```

Persze a számok ábrázolásának nem éppen ez a legpraktikusabb módja így gyakran 8-as (oktális) vagy 16-osz (hexadecimális) számrendszert alkalmaztak.

```
B8 D4 07 00 00 90 48
```
Ugye mennyivel olvashatóbb.. Nem? De legalább rövidebb. Természetesen őrült sok munka volt ilyenben egy programot megírni, így született meg az első programozási nyelv, az assembly. Az asszembly egy alacsony szintű programozási nyelv, ahol az asszembler-nek nebezett fordítóprogram értelmezi az álltalunk leírt assemby kódot, majd átalakítja az gépi kóddá. A visszaalakítás is lehetséges, a visszaalakító programot disszemblernek nevezik. Assemblyben mindig processzor specofikusan kell kódot írni, így például egy intel processzorra írt program egy amd-n vagy egy másik intelen már lehet hogy el sem indult. Így néz ki egy Hello World program assemblyben:

```assembly
.LC0:
        .string "Hello, World!"
main:
        push    rbp
        mov     rbp, rsp
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf
        mov     eax, 0
        pop     rbp
        ret
```
Szerintem nyugodtan elmondhatjuk, hogy ez se valami szép. A programozók se annyira szerették, mivel ebben írni még mindig nagyon időígényes volt. Az ezután következő legnagyobb lépés az operációs rendszerek és a `C` nyelv megjelenése volt.

C-ben már nem processzorspecifikus, hanem operációs rendszer specifikus programokat lehetett írni. Az operációs rendszer rendelkezett (és a mai napig rendelkezik is) hívható parancsokkal, amit ő utánna "lekommunikál" a processzor felé. Egy fáljbaíráshoz elég csak meghívni az oprenszer író parancsát és ő elintézi a többit, mindegy milyen processzor van alatta. Ráadásul a C nyelv már sokkal-sokkal egyszerűbb és olvashatóbb mint az assembly. A Hello Wolrd itt már így néz ki:

```C
#include <stdio.h>
int main()
{
   printf("Hello, World!");
   return 0;
}
```

Javahoz szokott szemünknek ez is különös lehet, de azért ez már elég olvasható. Látjuk hogy itt is van `main` függvény és itt is van egy `System.out.println`-hez hasonló kiírató parancs, a `printf`. Nagy eltérés az assembly-hez képest, hogy a C nem közvetlenül gépi kódra fordul, hanem először assembly-re, és csak onnan gépire. Éppen ezért itt már nem létezik visszafordító program.

Még hosszasan lehetne peszélni a C-ről, a különböző trónkövetelőkről, mint a `Pascal` vagy a `C` ugymond utódjáról a `C++`-ról, de ennek mindenki olvasson utánna maga ha érdekli. Ami viszont közös ezekben a nyelvekben, hogy mind képi kódra fordulnak a fordítóprogram (compiler) segítségével, ammi ahhoz a nagy problémához vezet, hogy nem hordozhatóak operációs rendszerek között. Ha szeretnénk, hogy programunk menjen window-on és linuxon is, akkor bizony azt külön meg kell írnunk. Erre a problémára próbáltam megoldást adni az értelmező programok, az úgynevezett interpreterek.

Egy interpreter, egy operációs rendszerre már megírt program, ami fogja az álltalunk írt program kódját, értelmezi, majd végrehajtja. Lényegében egy plusz réteg az operációs renszer fölött. Innentől az előző problémára a megoldás egyszerű, írjuk meg az interpretert minél több oprendszerre, így a kódunk az összesen futni fog. Ilyen nyelv a `Python` a `Perl` vagy a `JavaScript` ahol a interpreter a böngészőprogramban van. A másik nagy előnye ezeknek a nyelveknek, hogy mivel nem kell őket fordítani, sokkal gyorsabban lehet bennük fejleszteni. Nem kell hosszas perceket, vagy akár órákat várni amíg a fordítóproram használható gépi kódot készít az álltanulnk éveh óta hegeszgetett, hatalmas programból. De persze hátránya is van a dolognak, mégpedig a sebesség. Mivel egy plusz réteget húzunk az oprenszer fölé így lassabb lesz a program futási ideje. Manapság ez már nem olyan vészer, de régen nagyon sokat tudott jelenteni. És itt jön be a képbe a harmadik kategóriánk, aminek konkrét neve sincs, de lényegében egy köztes kategória.

Ennek a kategóriának a lényege, hogy az adott nyelv ugyan fordított nyelv, viszont nem gépi kódra, hanem egy köztes kódra fordul, amit az operációs rendszerre feltelepített program értelmez és végrehajt, így mindkét kategória előnyeit élvezi. Fordított, ezért gyors és nem gépi kódra fordul, így hordozható. ÉS mint azt már bizonyára sejtettek, ennek a kategóriának a fő képviselője a `C#` mellett a `Java`. Javaban a .java kiterjesztésű kódokat a fordítóprogram .class kiterjesztésű java bájtkóddá alakítja amit az úgynevezett jvm (Java Virtual Machine) futtat. JVM pedig létezik windowsra, linuxra, macre, sőt még mobilra is.

A következő fejezetekben megnézzük, hogyan alakítja át a fordítóprogram a kódot a gyakorlatban. Viszont előbb szükségünk van egy kevés parancssoros ismeretre.