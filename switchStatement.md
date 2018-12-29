# Switch szerkezet

Az if-else if-ese szerkezetet már kellően jól ismerjünk, így akár egy olyan feladatot is meg tudunk oldani, hogy bekérjük egy ember születési hónapját és ez alapján kiírunk valamit, mondjuk a horoszkópját.

```java
Scanner scan = new Scanner(System.in);
//A scan.next() hasonló mint a scan.nextInt() csak ez nem int-et hanem Stringet ad vissza
String month = scan.next();

//Ne felejtsük hogy Stringeknél nem == hanem .equals() kell
if ( month.equals("Januar") ) {
    //Csinálj valamit
} else if ( month.equals("Februar") ) {
    //Csinálj valami mást
} else if ( month.equals("Marcius") ) {
    //Csinálj valami megint mást
} else if...
```
Valahogy így nézne ki. Nem tűnik bonyolultnak, de valami piszok sokszor le kell írni, hogy `else if`. Erre egy lehetséges megoldás lehet a `switch` használata. Ez így néz ki:

```java
Scanner scan = new Scanner(System.in);
String month = scan.next();

switch ( month ) {
    case "Januar":
        //Csinálj valamit
        break;
    case "Februar":
        //Csinálj valami mást  
        break;
    case "Marcius":
        //Csinálj valami megint mást
        break;
    case...
    ...
    default:
        //Ha egyik se jött be, akkor ezt csináld
}
```
Látható hogy itt csak 1szer kell megadni azt a változót amit össze szeretnénk hasonlítani a hónapokkal, a `switch` szó után, zárójelben. Ezután csak annyi a dongunk, hogy `case` után megadjuk azt amivel össze szeretnénk hasonlítani, és kettőspont után azt, hogy mi történjek. Ahogy `else if`-ből, `case`-ből is bárhány lehet. A végére írhatunk még egy `default:` ágat is ami a sima `else`-nek felel meg `if`-nél, ez akkor fog bekövetkezni, ha egyik feltétel se teljesül. 

Ami még feltőnhetett az a `brake;` szó használata. Erre azért van szükség, mert a `switch` kicsit máshogy működik mint az `if-else`. Itt ha az egyik feltétel teljesül, akkor onnantól az összes feltételt tejlesítettnek vesszük. Ha például a _Januar_ szót írjuk, akkor az összes feltétel teljesülni fog és az összes parancsot végrehajtjuk. A `brake` szóval viszont jelezzük, hogy itt vége a `switch`-nek, abbahagyhatjuk a működést.

Most kicsit furának és feleslegesnek tűnhet a `switch` és megnyugtatok mindenkit, főleg az `if`-et fogjuk használni a jövőben. Ennek ellenére, jó ha a switch-el is tisztában vagyunk, néha ezt is fogjuk használni gyakorlás gyanánt.