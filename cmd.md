# Parancssor

A parancssor az a filmekben látott fekete hátterű mező amibe a hackerek 200km/h-val a programkódokat. Filmekben lehet menőn néz ki, de ez valójában nem más mint egy ezköz, hogy irányítsuk a window-unkat szövegesen. Hasonlóan mint amikor kattintgatással jutnánk el egyik mappából a másikba, új fájlokat hoznánk létre vagy programokat futtatnánk. Viszont itt mindent írott szöveggel teszünk, ami elsőre ilyesztőnek tűnhet, de nagyon hamar megszokható, és egy gyakorlott felhasználó számára gyorsabban is kezelhető mint mindjuk egy windows explorer.
![parancssor](img\cmd.png)

## Parancssor megnyitása
A parancssor használatának első lépése, a megnyitása. Szerencsére ez többféleképpen is lehetséges. Az egyik legegyszerűbb talán ha megnyitjuk a start menünt és beírjuk, hogy parancssor, majd rákattintunk az ikonjára.
![parancssor megnyirása 1](img\cmd_open.jpg)

Az én kedvenc módszerem az, hogy a `Windows + r` gombal előcsalogatom a futtaás menüt, ahova beírom hogy cmd, majd nyomok egy `entert`.

![parancssor megnyirása 2](img\cmd_open2.jpg)

## Jelenlegi mappa adatainak megjelenítése
Ha már sikerült megnyitnunk a parancssort akkor feltűnhetett hogy a villogó kis vonal valamilyen szöveg után jelent meg. Ez a fenti pédában `C:\Users\martin4955>`. Ez nem más mint az az útvonal ahol jelenleg tartózkodunk. Mondhatnánk úgy is, hogy jelenleg ez a mappa van megnyitva. Ha nyitunk egy sajátgépet, és a felső sorba ezt begépeljük akkor egy enter után már láthatjuk grafikusan is hogy pontosan hol vagyunk.

![windows explorer](img\win_explorer.jpg)

Most gépeljük be a parancssorba a `dir` szót ami a `directory` azaz könyvtár rövidítése. Valami ilyesmit láthatunk

```
2019. 01. 14.  20:28    <DIR>          .
2019. 01. 14.  20:28    <DIR>          ..
2018. 12. 13.  22:15    <DIR>          important
2018. 12. 09.  14:45    <DIR>          something
2019. 01. 14.  21:59            12 505 gamest
2018. 07. 08.  14:07    <DIR>          videos
2018. 07. 07.  14:33    <DIR>          other
2018. 08. 12.  13:33    <DIR>          eclipse
              10 File(s)         43 169 bytes
              45 Dir(s)  736 043 155 456 bytes free
```

Itt mindent sor egy könyvtárat vagy egy fájlt jelent. Az egyső 4 oszlop mutatja az utolsó modosítás dátumát, úgymint év, hó, nap és óra perc. A következp oszlop `<DIR>` ha egy mappáról van szó és üres, ha egy fájlról. Ezután fordítva lesz, üre, hogyha mappa és a fájl mérete, ha fájl. Legvégül jön a fájl vagy mappa neve. Az utolsó elötti sor kiírja, hogy hány fájlod van az adott mappában, és mennyit foglalnak összesen, míg az utolsó oszlop ugyan ez csak mappákkal.

Feltűnhetett, hogy az első két sorban a fájl neve `.` illetve `..` . Itt a pont a jelenlegi mappát jelenti, míg a két pont a szülő mappát, azaz azt a mappát amiben a most megnyitott mappánk található. Látjuk is, hogy mindkettő könyvtár típusú és hogy mindekettőt január 14-én módosították utoljára.

## Mappák megnyitása

Most, hogy már látjuk a máppákat, ideje hogy beléjük is másszunk. Mappa megnyitás a `cd` azaz change directory parancsal történik. Ha most kiadom a `cd important` parancsot, akkor rögtön az important mappában találom magam. Amúgy Tab billentyűt nyomogatva a parancssor megpróbálja kitalálni melyik mappára/fájlra gondolsz, pl. beírom hogy `cd im` majd nyomok egy Tab-ot és autómatikusan felugrik a `cd important`. A már megtárgyalt `.` és `..` is működik, azaz a `cd .` nem csinál semmit (hiszen már amúgy is itt vagyunk), míg a `cd ..` visszavisz az előző mappába. Perszer ezeket egymás után is lehet fűzni, nem muszáj egysével ugrálgatnunk. Kiadhatom mondjuk a `cd important/videos/cool` parancsot, hogy kapásból a cool mappát nyissam meg. A `cd /` parancs a gyökérkönyvtárba navigál ami a nevével ellentétben nem egy undok könyvtár, hanem maga a meghajtó, a legkülső mappa. Ebben a példában a C: meghajtó az. És hamár meghajtók, ha valakinek több meghajtója is van akkor felmerül az igény, hogy ezek között is tudjunk váltogatni. Ez úgy törénik, hogy beírjuk a meghajtó nevét és egy kettőspontot. Pl. `D:`.

## Programok futtatása
Fájlok megnyitása a világ legegyszerűbb dolga, csak írd be a nevét és nyomj egy entert és meg megy is.

## Mappa létrehozás
Ez az `mkdir` parancsal történik. Pl. `mkdir cica` létrehoz egy cica nevű könyvtárat.

Mint láthatod, rengeteg mindent meg lehet csinálni parancssorban, amit amúgy windows-ba tennél és ennek a fejezetnek most nem célja mindenen végigmenni mert akkor örökre ittragadnánk, menjünk is tövább.