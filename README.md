# Bevezetés a programozásba C# nyelven
Tennivalók listájának működési leírása

(Egy elméleti specifikáció)

## Áttekintés

A **tennivalók listája** egy olyan rendszer, ami segít nyilvántartani egy csoport feladatait, és hozzáférhető különböző időben és különböző eszközökről.

Ez a leírás semmilyen értelemben nem teljes. A véglegesítés előtt még jópárszor át kell majd olvasni.
Az aktuális kinézet idővel változni fog a grafikai tervezés és a felhasználói visszajelzések alapján.

A leírás nem tartalmazza a különböző keresési, tárolási és megjelenítési algoritmusokat, egyszerűen csak arról szól, hogy a felhasználók hogyan tudják használni a **tennivalók listáját**.

## Nem célok
- A rendszer nem szeretné megoldani a **több csoport ember feladatai**nak rendszerezését, 

- Ugyanígy **többféle feladatcsoportba tartozó tennivalók** nyilvántartását sem célozzuk meg. 

- Nem lesz nagyon **védett idegenek ellen** sem, a megosztási információt majd egy olyan linkre tesszük amit senki sem ismer (http://titkoshej.csaladunk.hu).

- Az **on-line frissítést** sem szeretnénk megoldani, vagyis amit valaki valahol felír, az nem fog azonnal automatikusan megjelenni máshol.

## Bevezetés: a 21. századi család
A család szeretné a tennivalókat egyszer és mindenkorra egy helyen gyűjteni. Mindenki hozzáfér valamilyen módon az **Internethez**, így a feladat az lenne, hogy egy nagy és közös teendőlistát gyártsunk, amit aztán különböző eszközökről és helyekről minden családtag elér.

## Szereplők

- Jancsi (Apuka)
- Juliska (Anyuka)
- ? (A kamaszgyerek)

## Forgatókönyvek
### Rögzítés
**Jancsi** átnézi a hétvégi grillezéshez a rendelkezésre álló raktárkészletet, és látja, hogy nincs elég *sör*. Ezért __**felírja**__ a teendőlistára: a sör mielőbbi beszerzése, és elindul azonnal vásárolni. 

**Juliska** végiggondolja szintén a tennivalókat, és a salátához az öntet nem áll rendelkezésre. Ezért __**felveszi**__ a tennivalólistára.

**Juliskának** később eszébe jut, hogy este vendégségbe mennek a szomszédhoz, és a tervezett miniruhájához jól illene egy új francia körömlakk festés. *De nincs fehér körömlakk itthon!*

De. Ha **Jancsi** már úgyis vásárolni ment, akkor igazán hozhatna még körömlakkot is, mert úgyis útbaesik. Vagy ha nem, akkor is. 

Ezért a családi tennivalólistára __**felviszi**__ a következő bejegyzést: körömlakkot venni (a szupermarket üzletsorán található illatszerből, fehéret).

### Áttekintés
**Jancsi** a boltba érve __**átnézi**__ mit kell vennie, így előveszi a teendőlistát.

### Módosítás
**Juliskának** közben eszébe jut, hogy a tervezett francia festéshez már nem lesz elég ideje, és ha már így esett, a ruhájához jobban illene egy egyszínű rózsaszín, ami szintén nincs itthon. Ezért gyorsan __**átírja**__ a tennivaló szövegét.

### Megoldás
**Jancsi** végre megveszi megérdemelt sörét, így __**kipipálja**__ a jól végzett munkáját a teendőlistáról. Közben találkozik pár haverral, és egy kicsit dumálnak. Közben azért megnézi mit kéne vennie, de nem siet.

### Törlés
**Juliska** tűkön ül, de aztán be kell látnia, hogy nem lesz már idő a lakkozásra. Ezért szomorú szívvel, de __**leveszi**__ a tennivalót a listáról.

### Áttekintés
Közben **Jancsi** néha ránéz a listájára, és egyre idegesebben figyeli a módosításokat. A végén már annyira begőzöl, hogy elindul haza, hogy szép szavakkal elmagyarázza otthon kedvesének milyen fontos az előre látó és gondos tervezés.

### Keresés
**Juliska** a grillparti reggelén keresi a salátaöntetet, de nem találja. Ezt szóvá teszi, szó szót követ, és a forráshoz fordulva __**ránéznek**__ a teendőlistára, kinek is van igaza?
