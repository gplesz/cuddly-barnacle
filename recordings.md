# A felvételek kezelése a tanfolyami oldalról

## Szereplők

### Remek Elek
Kezdő tanár a NetAcadémiánál, első tanfolyamát tartja nálunk balkezes avókádófarmerek párválasztási szokásairól, mondjuk úgy, hogy nem igazán technikai ember.

### Pofá Zoltán
Rutinos vén róka, sokadik tanfolyamát tolja.

### Kala Pál
A chat masterünk

### Meg Győző
Az adminisztrátor, aki végül mindenről tud és mindent megold.

### Minden Áron
A technikai segítség, aki ha egy tanfolyammal gondok merülnek fel, ugrik, repül, földet ér és segít.

## Forgatókönyvek

### Kezdő tanár tanfolyamot tart
Remek Elek az első alkalommal nagy erőkkel készül a saját szerepére. Így is épp elég nagy a nyomás, a technikai részt szükséges rossznak veszi, ami érthetően kevéssé érdekli.

#### Tanfolyam kezdete előtt
 Az első lépést azért megteszi (megnyitja a tanfolyami élő adás oldalt), onnantól viszont könnyen beszippanthatja az időgép. Ilyenkor a segédeszközök feladata, hogy támogassák az esendő embert.

Ha a közvetítés nincs elindítva, akkor az élő adás oldalon egy feltűnő felirat jelzi, hogy a közvetítés nincs elindítva. A felirat után pedig a link egy tanároknak szóló oldalra visz, ahol a leírás található, hogy lehet elindítani a felvételt.
![Nincs még elindítva a felétel](/img/01-nincs-adas.png)
Még jobb, ha a teljes élő adás oldalt beborítjuk a felirattal, hogy egyértelmű legyen minden kezdő tanárnak, hogy ezt meg kell oldani azonnal.

![Nincs még elindítva a felétel](/img/01b-nincs-adas.png)

Lehetőségek: a tanár elindítja a felvételt, majd frissíti az oldalt. Így eljutunk a következő ponthoz.

*Megjegyzés*: Esetleg az oldalfrissítést is érdemes beleírni a piros szövegbe.

*Technikai megjegyzés*: A közvetítés elindítását -jelenleg- az OBS-ben kell elvégezni, és vagy onnan vagy a Wowza API-ból értesülhetünk a megtörténtéről. Egyik sem fogja értesíteni a pedellust, így annyit tudunk tenni, hogy amíg a felvétel nem indult el, addig a pedellus időnként (5-10 másodpercenként) lekérdezi a Wowza API-t, és ha elindult a felvétel, akkor SignalR-rel push értesítést küldünk a weboldalnak, így nem kell az oldalt frissíteni. Ezt a poll-push mechanizmust ki is szervezhetjük a Pedellus-ból egy külön szervizbe, akár a wowzára.

*Megjegyzés*: Érdemes megfontolni, hogy ha a tanfolyami időpont előtt nem indult el a felvétel, akkor valamilyen értesítési e-mail-t küldeni (mondjuk Minden Áron-nak), Áron aztán segíthet Eleknek elindítani a felvételt.

![Van adás nincs felvétel](/img/02-van-adas-nincs-felvetel.png)
Az oldalon már a következő feladat látszik: a tanfolyam kezdetekor el kell indítani a felvételt. Ezt Elek megteheti a nagy villogó piros gombbal. 

*Megjegyzés*: Célszerű egy visszaszámoló mechanizmust beépíteni az oldalba Elek számára, hogy a a nagy izgalomban a pontos kezdéshez legyen segítsége. Az utolsó másodpercekben esetleg hangjelzéssel, az utolsó kettő-öt másodpercre visszanémulva. Ez a visszaszámoló mechanizmus Elek visszanéző oldalán futhat, a többi szerver funkciótól függetlenül, azokat kiegészítendő. 

*Megjegyzés*: Hogy még egyszerűbb legyen Elek élete, a tanfolyam elején a szerverbe beépített időzített indító másodpercre pontosan elindíthatja automatikusan a felvételt. Ezt az automatikus indítást célszerű a szerverről vezérelni, a megjelenített weboldalaktól függetlenül.

*Technikai megjegyzés*: Mivel több (sok) tanfolyamot kell "fejben" tartani, érdemes az időzítő mechanizmust precízen tervezni. Egy jó megoldás a szerveren futó időzítésekhez a [Hangfire](https://www.hangfire.io/) ingyenes változata, ami nyílt forráskódú és nuget-tel egyszerűen telepíthető. Ezzel például megoldható az, hogy amikor egy-egy modul kezdési időpontját berögzítjük az Admin felületen, azonnal létrehozza az akár hónapokkal későbbi rögzítési időpontot, amit szerver újraindításkor/frissítéskor/stb. sem felejt el, mivel az SQL szerveren automatikusan tárolja.

*Megjegyzés*: A visszaszámolást és/vagy az automatikus felvétel indítást kikapcsolható módon is el lehet készíteni, vagy később a kikapcsolhatóságot beépíteni.

*Technikai megjegyzés*: Ha visszaszámoló mechanizmusunk van, akkor gondoskodni kell az időszinkronról a szerver és a weboldal között (például SignalR push üzenetekkel percenként).

*Megjegyzés*: ha a tanfolyamról nem készül felvétel, akkor ezt a mechanizmust és a piros gombot letilthatóvá kell tenni a tanfolyami beállítások oldalán.

#### Tanfolyam indítása, modul kezdete

A piros gombot megnyomva (vagy a visszaszámolást követően) elindul az tanóra, elindul a felvétel. Elek leadja az első részt, jó esetben belefeledkezve a mondandójába, a technikai környezetről elfeledkezve. 

#### modul vége
A modul végén Elek leállítja a felvételt a nagy piros gombbal. 
![Van adás, felvétel elindítva](/img/03-van-adas-van-felvetel.png)

*Technikai megjegyzés*: Amennyiben a közvetítésben tudjuk figyelni a hangot valamilyen mechanizmussal (nem triviális feladat, példák: [csendfelismerés](https://stackoverflow.com/questions/19353/detecting-audio-silence-in-wav-files-using-c-sharp), [csendfelismerés2](https://stackoverflow.com/questions/43058522/detect-silence-from-microphone), [csendfelismerés3](https://stackoverflow.com/questions/24037814/identify-silence-packet-in-byte-array-naudio), [csendfelismerés4](https://stackoverflow.com/questions/13043732/using-naudio-for-net-how-do-i-remove-the-silence-wave-at-the-end-of-mp3-file)), akkor be tudunk egy figyelő szervizt állítani, ami nézi a folyamatban lévő stream-eket, és riaszt, ha valahol elhallgat.

A következő feladat két lépésből áll. 

##### A felvétel sorsa

A felvételhez meg kell adni a végleges adatokat, amivel bekerül a többi közé, és az adatok alapján a Wowza szerveren futó automatizmus feltölti a wowza szerverről a Vimeo-ra, és beilleszti a tanfolyami videók közé a megfelelő helyre.

Ehhez a képernyőn a felvétel lezárása után következő lehetőségek közül kell tudnunk választani:

###### A felvétel értékes, megtartjuk
Ebben az esetben a felvétel címét kötelező kitölteni, ha kell, akkor a modult is kiválasztjuk, majd a Modul zárása gombbal Elek megkezdi a szünetet.
![Felvétel elkészült, megtartjuk](/img/04-felvetel-utan-megtartjuk.png)

###### A felvétel csak teszt volt
![Felvétel elkészült, de nem tartjuk meg](/img/05-felvetel-utan-nem-tartjuk-meg.png)
Elek csak bohóckodott a kamera előtt otthon, hogy szokja a kamerát és a lámpalázával küzdjön. Ebben az esetben Elek a második lehetőséget választva jelzi a rendszernek, hogy ez a felvétel nem kerülhet a tanfolyami videók közé. 

Ezzel a rögzített videót nem töröljük, csak szerver oldalon jelezzük, hogy a videót nem kell kitenni a tanfolyami oldalra. 

*Technikai megjegyzés*: A felvett videó tehát megmarad ilyenkor is (jelenleg a Wowza szerveren) egy mappában, és a wowza szerveren futó automatizmus egy beállított idő letelte (mondjuk például 2 hét) után automatikusan törli, ha addig nem volt rá szükség.

*Megjegyzés*: A mezőnevek és gombok feliratai "kitalálás alatt" vannak, ezek helyett lehet jobbat is alkalmazni.

*Megjegyzés*: Érdemes megfontolni, hogy Elek a szünet kezdetekor megadhassa a szünet idejét mondjuk percben, így újraindulhat a visszaszámlálás, és az egész folyamat kezdődhet elölről.

*Megjegyzés*: A felvétel végén az ablak jelenleg nem ad lehetőséget a továbblépésre. Pl. ha Elek oldalt frissít, nem tudja átverni a gépet, ugyanazt a képernyőt kapja vissza. Ez igaz mindegyik képernyőre.

*Megjegyzés*: Amennyiben Elek időzavarba kerül, felmerülhet a kérdés, hogy az adatok megadását későbbre lehessen-e tolni. Ez esetben szükség van egy áttekintő képernyőre a nem lezárt felvételeiből, egyfajta táblázatra, ahol az egyes felvételeket kiválaszva megadhatja az adatokat. Sajnos ilyenkor nem kerülhető meg az sem, hogy bele tudjon nézni a videóba, mert előfordul, hogy ha felgyűlik pár videó, akkor már utólag nehezen vagy egyáltalán nem beazonosíthatóak.

#### következő modul kezdete
Visszaszámlálással vagy anélkül, Elek a következő rész kezdetekor elindítja a felvételt a nagy piros gombbal.

![Van adás nincs felvétel](/img/02-van-adas-nincs-felvetel.png)

#### Modul vége, tanfolyam vége
Mivel az óra véget ért, a felvételt Elek szintén a nagy piros gombbal állítja meg:
![Van adás, felvétel elindítva](/img/03-van-adas-van-felvetel.png)

A felvett anyag sorsáról pedig a felvételt lezőártát követő képernyőn tud Elek dönteni:

![Felvétel elkészült, megtartjuk](/img/04-felvetel-utan-megtartjuk.png)

### Gyakorlott tanár tanfolyamot tart
Pofá Zoltán
### Chat master
Kala Pál
### Admin
Meg Győző

Ezet még ki kell dolgozni.
