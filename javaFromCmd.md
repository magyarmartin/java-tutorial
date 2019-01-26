# Java a gyakorlatban

Végre elérkezett a várva várt pillanat, hogy megnézzük hogyan is működi ez a java. Először menjünk a jdk mappájába. Ez nálam a `C:\Program Files\Java\jdk1.8.0_181` de neked is hasonló kell, hogy legyen, hacsak telepítéskor át nem állítottad. De persze a jdk után található szám nálad már lehet más, az ugyanis a verziót mutatja.

![jdk könyvtár](img\jdk_folder.jpg)

Itt elég sok mindent látunk és később lehet meg is nézzük őket, de egyelőre koncentráljunk a bin mappára.

![jdk könyvtár](img\jdk_bin_folder.jpg)

Ebben rengeteg exe fájlt találunk amik ugye kis futtatható programok. Ezek közül is különösen fontos nekünk a java.exe és a javac.exe. A javac-al tudjuk lefordítani a kódunkat jvm bytekóddá, míg a java-val tudjuk futtatni a már lefordíttott programokat. De hogyan? Ha rákattintunk látszólag nem történik semmi. Ez azért van mert ezeket parancssorból tudjuk futtatni, olyan módon hogy mögé írjuk a fordítani, vagy futtatni kívánt fájl nevét, momdjuk `javac hello.java`.

Ez eddig tök jó, ilyet már csináltunk, tudjuk hogy működik a parancssor, de mi van akkor ha nem ebben a mappában vagyunk? Mert a program ugye itt van, szóval itt kell lennünk hogy elindítsuk, nem? Hát nem, túl macerás lenne. Ugyan is vannak olyanok window-ban hogy környezeti változók, amik hasonlóak mint a már megismert java változók. Adhatunk nekik értéket és később elkérhetjük azokat, csak ezúttal parancssorból. Ezek között is különösen fontos nekünk a `PATH` elnevezésű. Neki fájl útvonalakat adhatunk meg, pontosvesszővel elválasztva. Ha szeretnénk futtatni egy programot parancssorból, akkor a windows először megnézi, az adott helyet ahol vagyunk, majd végigmegy a `PATH`-nél megadott útvonalakon is és ha azokon se találja akkor ír csak ki hibát.

Manapság a java telepítője be szokta állítani magátol az `PATH` változót, így mielőtt elkezdenénk ezt kézzel megtenni, ellenőrizzük le hogy szükséges-e ez egyáltalán. Ehhez parancssorba adjuk ki a `java -version` utasítást.

Siker esetén a következőhöz hasonló szöveget fogja kiírni:
```
java version "1.8.0_181"
Java(TM) SE Runtime Environment (build 1.8.0_181-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.181-b13, mixed mode)
```
Persze a verziószám eltérhet. Ha nincs beállítva akkor pedig ez lesz az eredmény:
```
'java' is not recognized as an internal or external command,
operable program or batch file.
```
Bár ez lehet, hogy nálatok magyarul lesz, nálam valamiért angolul írta most ki.

## Path beállítása
A `PATH` változó beállítása a következő éppen történik:
1. Jobb klikk a start menűre.
![első lépés](img\path_1.jpg)
1. Kattintsunk a `Rendszer` gombra
1. Itt görgessünk le a `Kapcsolódó beállítások` részhez és kattintsunk a `Rendszerinfó` gombra.
![második lépés](img\path_2.jpg)
1. Kattintsunk a `Speciális rendszerbeállítások`ra
![harmadik lépés](img\path_3.jpg)
1. Itt válasszuk a `Környezeti változók` menüpontot.
![negyedik lépés](img\path_4.jpg)
1. Válasszuk a `Path`-et a `... felhasználói változói`, vagy a `Rendszerváltozók` rész alól és kattintsunk a szerkesztés gombra.
![ötödik lépés](img\path_5.jpg)
1. Itt kattintsunk az `Új`-re és írjuk be a jdk mappájának elérését, és egy `\bin`-t a végére. Tehát nálam ez: `C:\Program Files\Java\jdk1.8.0_181\bin`.
![hatodik lépés](img\path_6.jpg)

Ezzel meg is volnánk. Próbáljuk ki megint a `java -version` parancsot. Ha működik akkor ideje írni egy programot és lefordítani ezekkel az ősi módszerekkel.

## Hello world parancssorból

Ez a program egy már jól ismert hello world program lesz. A lényeg hogy most nem használunk Eclipse-t, mindent magunk rakunk össze. Készítsünk egy mappát, legyen a neve mondjuk `hello`, de igazából ez teljesen mindegy. Nyissunk egy szövegszerkesztőt. Én a `notepad++`-t ajánlom, de persze más, tetszőleges programot is ér használni. A `hello` mappában hozzunk létre egy `Hello.java` nevű fájlt, aminek a tartalma legyen:
```java
class Hello {

	public static void main(String[] args) {

		System.out.println("Hello world!");

	}

}
```
Fontos, hogy a fájl neve pontosan ugyan az legyen mint a class neve, azaz jelen esetben `Hello` és nagybetűvel kezdődjön.

A programkódunk már megvan, hogy lesz ebből bítekód? Nyissunk egy parancssort, és navigáljunk a `hello` mappába. Adjuk ki a következő parancsot: `javac Hello.java`. Ha minden jól sikerült akkor a `Hello.java` mellett megjelent egy `Hello.class` is. Ha nagyon szeretnénk, ezt is megnyithatjuk valamilyen szövegszerkesztővel, de ebből már semmit sem fogunk érteni, mivel ez maga a jvm bytekód. A programot futtatni a `java Hello` parancsal tudjuk, itt már nem kell kiírni, hogy `Hello.class`, tudni fogja hogy a class-ra és nem a java fájlra gondolsz. Ha mindent jól csináltunk akkor már meg is jelent a a parancssorban a kedvenc `Hello world!` feliratunk.