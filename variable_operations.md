# Műveletek változókkal

Az előző fejezetben megismert változók önmagukban nem sokat érnek, így most megnézzük milyen műveleteket hajthatunk végre velük.

## Értékadás
Az első és legegyértelműbb a már korábban megismert értékadás, amit az egyenlőségjellel lehet megtenni. Egy vátozónak bármikor lehet értéket adni, akár más változókat is, de a régi értéket mindig felülírja az új.
```java
int a = 10;
inb b = a;
```
Vagy röviden:
```java
int b = a = 10;
```

## Matematikai műveletek
A byte, short, int, long, float és double típusú változókkal működik az összes alapvető logikai művelez.
```java
int a = 10;
int b = 5;

// Összeadás
System.out.println(a + b);
// Kivonás
System.out.println(a - b);
// Szorzás
System.out.println(a * b);
// Osztás
System.out.println(a / b);
```
Egy kissé kevésbé ismert művelet a modulo amivel azt kapjuk meg, hogy egy osztásnak mennyi a maradéka.
```java
int a = 8;
int b = 5;

// Ez 3 lesz mivel a 8/5 = 1 maradék a 3
System.out.println(a % b);
```
Éremes figyelni viszont a változók típusára. Két int típusú változó összege már nem biztos, hogy belefér egy int-be. Ugyan így ha 2 egész típusú változót elosztok egymással akkor a végeredmég egészre lesz kerekítve, nem fogjuk visszakapni a valós tört számot, ahhoz float-ot vagy double-t kell használni.

```java
int i = 6;
int j = 4;

//Ez 1 lesz mivel 6/4 = 1.5 viszont mivel mindekettő egész szám így marad az 1 mint egész rész
System.out.println(i / j);
```

```java
int i = 6;
double j = 4;

//Ez már 1.5 lesz, elég csak az egyiknek double-nek vagy float-nak lenni
System.out.println(i / j);
```

## Logikai műveletek
A matematikai műveletekhez hasonlóan lehet használni logikai műveleteket is. Ezek a következők lehetnek:
* Egyenlőség (==)
* Kisebb reláció (<)
* Nagyobb reláció (>)
* Kisebb egyenlő (<=)
* Nagyobb egyenlő (>=)
* Nem egyenlő (!=)
Ezeknek boolean típúsú lesz a visszatérési értéke.
```java
int i = 5;
int j = 10;
boolean result = i == j;

System.out.println(result);
```
Ez a `false` szót fogja kiírni a képernyőre.

## Műveletek String-el

A string egy elég különleges állatfaj, egyrészt egy objektum, így a primitíveltől eltérő módon lehet hasonló műveleteket végrehajtani, másrészt még az objektumok között is különleges, mivel értelmezett rajt az összeadás.

Mi van? Stringeket lehet összeadni? A válasz igen, ezt konkatenácoónak, vagy összefűzésnek hívjuk. Pl.
```java
String hello = "Hello";
String world = " World!";

System.out.println(hello + world);
```
Ez a `Hello World!` szöveget fogja a képernyőre írni.

A másik érdekesség a már előbb említett objektumos tulajdonságából adódik, ugyanis az egyenlőség stringekkel nem a dupla egyenlőségjellel, hanem az equals szócskával működik. Pl.
```java
boolean result = "almafa".equals("körtefa");
System.out.println(result);
```
Ez megint csak `false` lesz.

## Műveletek char-al
Na ez megint egy érdekes téma. Mit gondoltok, mi lesz a következő kódnak az eredménye?
```java
char a = 'a';
char b = 'b';
System.out.println(a + b);
```
A válasz 195. Hogy miért is? Mert egy karakter, lényegében csak egy szám, és a fordítóprogram a változó típusából találja ki, hogy karakterként és nem számként kéne kezelni.
```java
char a = 97;
System.out.println(a);
```
Ez például az 'a' betűt írja ki.

Ugyanilyen elven működnek a logikai műveletek is. Megnézhetjük például, hogy egy karakter nagyobb-e mint egy másik.

## Műveletek boolean-al
A boolean maradt a legvégére. Könnyen kitalálható, hogy rajta csak a logikai műveletek értelmezettek és pntosan úgy működnek, ahogy azt középiskolában matek órán tanultuk. Ezek az 

* És ( && )
  ```java
  true && true == false;
  true && false == false;
  false && false == false;
  ```
* Vagy ( || )
  ```java
  true || true == true;
  true || false == true;
  false || false == false;
  ```
* Tagadás \ Negáció (!)
  ```java
  !false == true;
  ```

Ez eddig eddig elég száraz volt, de tartsatok ki, ugyanis a következő fejezetben készítünk egy tipp játékprogramot;