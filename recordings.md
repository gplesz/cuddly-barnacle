# A felvételek kezelése a tanfolyami oldalról

## Forgatókönyvek

### Kezdő tanár tanfolyamot tart

#### Tanfolyam kezdete előtt
Remek Elek az első alkalommal nagy erőkkel készül a saját szerepére. Így is épp elég nagy a nyomás, a technikai részt szükséges rossznak veszi, ami érthetően kevéssé érdekli. Az első lépést azért megteszi (megnyitja a tanfolyami élő adás oldalt), onnantól viszont könnyen beszippanthatja az időgép. Ilyenkor a segédeszközök feladata, hogy támogassák az esendő embert.

Ha a közvetítés nincs elindítva, akkor az élő adás oldalon egy feltűnő felirat jelzi, hogy a közvetítés nincs elindítva. A felirat után pedig a link egy tanároknak szóló oldalra visz, ahol a leírás található, hogy lehet elindítani a felvételt.

![Nincs még elindítva a felétel](/img/01-nincs-adas.png)

Lehetőségek: a tanár elindítja a felvételt, majd frissíti az oldalt. Így eljutunk a következő ponthoz.

*Megjegyzés*: Esetleg az oldalfrissítést is érdemes beleírni a piros szövegbe.

![Van adás nincs felvétel](/img/02-van-adas-nincs-felvetel.png)
Az oldalon már a következő feladat látszik: a tanfolyam kezdetekor el kell indítani a felvételt. Ezt Elek megteheti a nagy villogó piros gombbal. 

*Megjegyzés*: Hogy még egyszerűbb legyen Elek élete, a tanfolyam elején a beépített időzített indító másodpercre pontosan elindíthatja automatikusan a felvételt.

*Megjegyzés*: Ehhez célszerű egy visszaszámoló mechanizmust beépíteni az oldalba a tanárnak. Az utolsó másodpercekben esetleg hangjelzéssel, az utolsó kettő-öt másodpercre visszanémulva.

*Megjegyzés*: Ha visszaszámoló mechanizmusunk van, akkor gondoskodni kell az időszinkronról a szerver és a weboldal között.

*Megjegyzés*: ha a tanfolyamról nem készül felvétel, akkor ezt a mechanizmust és a piros gombot letilthatóvá kell tenni a tanfolyami beállítások oldalán.

#### Tanfolyam indítása, modul kezdete

A piros gombot megnyomva (vagy a visszaszámolást követően) elindul az tanóra, elindul a felvétel. Elek leadja az első részt, jó esetben belefeledkezve a mondandójába, a technikai környezetről elfeledkezve. 

#### modul vége
A modul végén Elek leállítja a felvételt a nagy piros gpmbbal. 
![Van adás, felvétel elindítva](/img/03-van-adas-van-felvetel.png)

A következő feladat két lépésből áll. 

##### A felvétel sorsa

A felvételhez meg kell adni a végleges adatokat, amivel bekerül a többi közé, és az adatok alapján automatizmus feltölti a wowza szerverről a Vimeo-ra, és beilleszti a tanfolyami videók közé a megfelelő helyre.

Ehhez a képernyőn a felvétel lezárása után következő lehetőségek közül kell tudnunk választani:

###### A felvétel értékes, megtartjuk
Ebben az esetben a felvétel címét kötelező kitölteni, ha kell, akkor a modult is kiválasztjuk, majd a Modul zárása gombbal Elek megkezdi a szünetet.
![Felvétel elkészült, megtartjuk](/img/04-felvetel-utan-megtartjuk.png)

###### A felvétel csak teszt volt
![Felvétel elkészült, de nem tartjuk meg](/img/05-felvetel-utan-nem-tartjuk-meg.png)
Elek csak bohóckodott a kamera előtt otthon, hogy szokja a kamerát és a lámpalázával küzdjön. Ebben az esetben Elek a második lehetőséget választva jelzi a rendszernek, hogy ez a felvétel nem kerülhet a tanfolyami videók közé.

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
Kala Pál, Pofá Zoltán, Meg Győző, Minden Áron
Ezt még ki kell dolgozni.







