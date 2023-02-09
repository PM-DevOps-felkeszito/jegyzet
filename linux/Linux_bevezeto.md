# Linux bevezető

A linux napjaink egyik meghatározó operációs rendeszere bár tény hogy nem az otthoni felhasználók piacán, hanem főként a szerverek tekintetében. Épp ezért sem fejlesztőként sem üzemeltetőként nem mehetünk el mellette szó nélkül. Épp ezért ebben a rövid anyagban szeretnénk a legalapvetőbb parancsokkal megismertetni Titeket. Mielőtt azonban a konkrét parancsokra rátérnénk pár általános információt osztanék meg veletek.

## Hasznos tudnivalók

1. A Linux case sensitve és ennek megfelelően kezeli a parancsokat ezt érdmes észben tartani mert bizonyos esetekben egy-egy paraméter megadásakor nagy jelentősége van.
2. Az általános elterjedt Linux parancsoknak van manualja amit a `man` parancs segítségével érhetünk el. Ha nem vagy biztos egy-egy parancs, paraméter vagy opció használatában érdemes megnézni.
3. Paraméterek egy részét sok parancsnál egy rövid és hosszú formában is megadhatjuk. A rövid formánál a kötőjel után egy karaktert vár például `ls -a` a hosszú formánál pedig két kötőjelet és utána a hosszú megnevezését a paraméternek például `ls --all`. A rövid és hosszú formák egyenértékűek.
4. Lehetőség van arra hogy egyetlen parancsnál több paramétert is használhatunk a rövid formát használval ezeket össze is vonhatjuk sok esetben például `ls -lah` ezek sorrendjét akár fel is cserélhetjük.
5. A promtunk elárulja az aktuális felhasználó nevét, a gép nevét és hogy hol vagyunk a könytárszerkezetben a következő formában felhasználónév@gépnév:aktuális mappa
6. A `~` tilde karakter mindig az aktuális felhasználó home mappáját jelöli.

## Leggyakoribb parancsok

### Fájlkezelés és navigáció

A linux akár csak a többi operációs rendszer ismeri a realatív és abszolút elérési útvonal fogalmát. Relatív elérési út, az aktuális könyvtárhoz viszonyítva adjuk meg az elérési utat a `.` karakter segítségével jelezzük, hogy az aktuális könyvtártól nézze az elérési utat.
Abszolút elérési út használata esetén a gyökérkönyvtárhoz viszonyítunk ezt úgy jelezzük, hogy `/` jellel kezdjük az elérési utat. 
Az aktuális könytár elérési útja látható a promtunkban, de a `pwd` parancsal le is kérhetjük.

#### `ls` parancs a mappa tartalmának megjelenítése
Ezzel a paranccsal a mappa tartalmát tudjuk megnézni és paraméterek nélkül csak az aktuális mappánkban található fájlok és mappák nevét írja ki. 

Gyakori példák:
 - `ls -a` listázza a rejtett fájlokat is, amit nélküle elrjet előlünk a linux
 - `ls -l` lista formában írja ki a mappa tartalmát részletekkel együtt (jogosultság, tulajdonos, méret, utolsó módosítás dátuma)
 - `ls -h` az ls parancs bájtban adja meg a fájlok méretét, e paraméter hatására átváltja olvashatóbb mértékegységűre a méretet
 - `ls -lah` ez a leggyakoribb használat talán. Így listaként részletekkel együtt jól értelmezhető módon adja vissza a mappánk tartalmát az `ls` parancs

#### `cd` (change directory) mappaváltás

A `cd` paranccsal tudunk mappát váltani és a mappa után meg kell adnunk, hogy hova szeretnénk lépni. Itt megadhatunk abszolút vagy relatív elérési utat is. Illetve van néhány különleges jelölés, amit tudni érdemes.
gyakori példák:
- `cd ..` visszalépés a szülőkönyvtárba
- `cd ~` az aktuális felhasználó home könyvtárába lépés
- `cd /` abszolút útvonal a gyökérkönyvtártól
- `cd ./` relatív útvolnal az aktuális könyvtártól

#### `mkdir` (make directory) könyvtár létrehozása
Ezzel a paranccsal tudunk létrehozni könyvtárat, a parancs után meg kell adnunk az új mappa nevét `mkdir mappanév` formában. További paraméterek nélkül az aktuális könyvtárba létrehozza a mappánkat. Ha nem az aktuális könyvtárba szeretnénk, akkor meg kell adnunk az elérési utat is ahova a mappát létre szeretnénk hozni. 

Gyakori példák:
- `mkdir -p ./tesztmappa/tesztalmappa` A `-p` paraméter segítségével nem csak egy mappát, hanem annak almappáit is létrhozhatjuk egyetlen parancsal. Használata nélkül hibára futna a parancs mert a tesztmappa még nem létezik.

#### `rm` fájl vagy mappa törlése

Az `rm` parancs fájlok és mappák törlését teszi lehetővé. Paraméterek nélkül csak csak fájlokat tud törölni. Természetesen mindig meg kell adni a törlendő fájl vagy mappa nevét.

Gyakori példák:
- `rm -d` üres mappát töröl ha a mappában van valami akkor nem engedi törölni
- `rm -r` rekurzívan törli a mappát és a benne lévő fájlokat, mappákat
- `rm -rf` bizonyos esetekben a linux visszakérdezne, hogy tényleg törölni akarom-e az adott mappát az `f` paraméter hatására már nem kérdez vissza. Bánjunk vele nagyon óvatosan. Linux alatt futás közben ki lehet törölni olyan fájlokat mappákat, ami után már nem indul el újra a rendszer vagy nagyon sok funkció hiányozna.

#### `mv` Áthelyezés és átnevezés

Az `mv` parancsot használhatjuk átnevezésre és áthelyezésre attól függően, hogy mit adunk meg utána. Az `mv fájlnév újfájlnév` szintakszisban csak átnevezi a fájlt újfájlnév-re. Ha áthelyezni szeretnénk akkor meg kell adnunk a célmappa elérési útját is az következő módon `mv /forrásmappa/fájlnév /célmappa/fájlnév`. Természetesen az mv parancsnál is egyaránt használhatunk abszolút és relativ elérési útvonalakat.

#### `cp` másolás

A `cp` paranccsal fájlokat és mappákat másolhatunk egyik helyről a másikra. Paraméter nélkül csak fájlokat vagy üres mappákat másolhatunk vele. Ha olyan mappát szeretnénk másolni, amiben van valamilyen fájl akkor azt rekurzívan a `-r` paraméterrel tudjuk megtenni.

Gyakori példák:
- `cp forrásfájl /célmappa` Így egy fájlt másolhatunk át egy megadott mappába.
- `cp -r másolandómappa /célmappa`  A `-r` paraméter segítségével a teljes másoldandómappát minden fájljával és alkönyvtárával másolhatjuk a célmappába.
- `cp -r /forrásmappa/* /célmappa` A * karakter akár csak DOS-ban linuxban is helyettesítő karakter. Ezzel a paranccsal a forrásmappa tartalmát másolhatjuk a célmappába, de magát a forrásmappát nem.

#### `tar` Archiválás és tömörítés

A `tar` parancs segítségével tudunk adatokat archiválni illetve tömöríteni és kitömöríteni is, annak függvényében hogy mire van szükségünk. Azt, hogy ezek közül melyiket szeretnénk csinálni a paraméterekkel tudjuk megadni. 
Gyakori példák:
- `tar -cvf etc.tar /etc` Az etc mappa tartalmát fogja a etc.tar fájlba archiválni. A `-c` paraméter adja meg hogy archiválni szeretnénk és a `-v` verbose opció miatt kiírja az archivált fájlok listáját a képernyőre
- `tar -xf etc.tar -C /home/felhasználónév/etcarchiv` Az imént archivált állományunkat fogja kicsomagolni. A `-C` paraméterrel adjuk meg azt, hogy hozzon létre külön mappát és milyen néven.
- `tar -caf etc.tar.bz2 /etc` Ezzel az utasítással már nem csak archiváljuk az etc mappa tartalmát, hanem bzip2-vel tömörítjük is. Azt hogy melyik tömörítő programot akarjuk használni megadhatjuk konkrét paraméterként is, de a gyakorlatban az `-a` paramétert szoktuk használni, aminek hatására a tar program a fájl kiterjesztése alapján dönti el, hogy melyik tömörítő programot kell használnia jelen példában a bzip2-öt.

#### `find` Fájlok és mappák keresése

A `find` parancs segítségével megkeresni fájlokat vagy mappákat rengeteg szempont szerint. Szűrhetünk névre, méretre, jogosultságokra, utolsó módosításra stb. Érdmes átböngészné a man oldalát mert rengeteg lehetőség van benne. Most csak egy példát nézünk. Használatakor meg kell adni, hogy hol keressen ellenkező esetben csak az aktuális mappában fog keresni.

Példa:
- `find /etc -name passwd` Ez a parancs az etc mappában keresi meg a passwd nevű fájlokat. 

### Szöveg műveletek

#### `cat` szöveges fájl kiíratása az elsődleges kimenetre

Elsődleges kimeneten általában a monitort értjük. A `cat` paranccsal ki tudjuk iratni egy szöveges fájl tartalmát. Így a fájl végét fogjuk látni a képernyőn és egyből vissza is kapjuk a promtunk. 

Példa:
`cat /etc/passwd` Kiírja a passwd fájl tartalmát a monitorra majd visszaadja a promtunk.

#### `less` szöveges állomány kiíratása és soronkénti navigáció

A `less` parancs is szöveges állományok megnézésére használható. Ez viszont az első oldalt nyitja meg és utána kurzorbillentyűkkel tudunk benne előre hátra mozogni. Kilépni az állományból a q betű megnyomásával tudunk.

Példa:
`less /etc/passwd` Kiírja a passwd fájl tartalmának első oldalát a monitorra.

#### `more` szöveges állomány kiíratása és olalanként lapozhatjuk

A `more` parancs is szöveges állományok megnézésére használható. Ez viszont az első oldalt nyitja meg és utána a space billentyűvel tudunk benne lapozni. A terminálablakunk beállításait figyelembe veszi és úgy határozza meg mit tekint egy oldalnak. Ha az állomány végére érünk automatikusan kilép vagy a q betű megnyomásával bármikor szabadon kiléphetünk.

Példa:
`more /etc/passwd` Kiírja a passwd fájl tartalmának első oldalát a monitorra.

#### `echo` tetszőleges szöveg kiíratása a kimenetre

Az echo parancsal bármilyen tetszőleges szöveget kiírathatunk. Jellemzően más parancsokkal kombinálva használjuk.

Példa:
`echo Hello world` Kiírja a monitorra hogy Hello world.

#### `grep` Keresés szöveges állományban

A `grep` parancs segítségével tudunk keresni szöveges állományokban. A szöveges állománynak csak azokat a sorait adja vissza, amiben szerepel az általunk keresett karakterlánc. Joker karaktereket is tudjuk használni. Használatakor meg kell adni, hogy mit és milyen állományban keresünk `grep mit hol` sorrendben.

Példa:
`grep sys /etc/passwd` Kiírja a passwd fájl azon sorait amik tartalmazzák a sys karakterláncot.

#### `tail` Egy szöveges állomány végének a kiíratása

Vannak esetek, amikor egy-egy állomány végét szeretnénk csak látni például, amikor egy-egy logfájlt akarunk megnézni hibakereséskor. Ilyenkor jön jól a `tail` parancs.
Ennek a parancsnak meg kell mondanunk, hogy az utolsó hány sort szeretnénk látni és az állomány nevét a következő formában `tail -hánysor állomány`

Példa:
`tail -5 /etc/passwd` A passwd fájl utolsó 5 sorát adja vissza.

#### `head` Egy szöveges állomány első néhány sorának a kiíratása

Ahogy előfordul, hogy egy szöveges állomány végére vagyunk kíváncsiak ugyanúgy van olyan is amikor csak az első néhány sorra van szükségünk. Erre szolgál a `head` parancs. Működési mechanizmusa megegyezik a `tail` parancséval. Tehát `head -hánysor állomány`

Példa:
`head -5 /etc/passwd` A passwd fájl első 5 sorát írja ki az elsődleges kimenetre.

#### Parancsok kimenetének átirányítása

### Parancsok összefűzése

Több parancs esetén említettük már, hogy a parancs eredményét az elsődleges kimenetre írja ki. Ezt az elsőre furcsa meghatározást azért használtuk mert az elsődleges kimenet alapértelmezésben ugyan többnyire a monitorunk a szöveges műveletekenél, de ezt át tudjuk irányítani másik parancsnak. Ezt a `|` pipe jellel tudjuk megtenni és segítségével össze tudunk kombinálni több parancsot is oly módon, hogy az első parancs kimenete lesz a második bemenete (tehát amivel dolgozni fog). 

Példa:
`grep sys /etc/passwd | tail -2` A grep paranccsal kigyűjtjük azokat a sorokat, amik tartalmazzák a sys karaterláncot majd ezek közül a tail paranccsal csak az utolsó kettőt jelenítjük meg. Mivel a pipe jellel már megadjuk a tail parancsnak, hogy milyen adatokkal kell dolgozni így a tail parancsnál nem kell megadni a fájl nevét.

### Parancsok eredményének fájlba írása

Az elsődleges kimenet eredményét nem csak másik parancsnak adhatjuk át, hanem a kimenetet fájlba is irányíthatjuk és ezzel elmenthetjük. Ezt kétféleképpen is megtehetjük. Az egy darab `>` kacsacsőrrel a parancsunk eredményét kiírjuk egy fájlba, ha a fájl már létezett akkor az eredeti tartalma elvész, felülírásra kerül.
Ha azonban két kacsacsőrt `>>` használunk akkor, amennyiben a fájl már létezett a parancsunk eredményét hozzáfűzi a meglévő tartalomhoz. A fájl eredeti tartalma megmarad és csak kiegészül az új adatokkal.

Példák:
`grep sys /etc/passwd > syspasswd` A grep paranccsal kigyűjtjük azokat a sorokat, amelyek tartalmazzák a sys karakterláncot és azt elmentjük a syspasswd nevű fájlba.

`grep root /etc/passwd >> syspasswd` A syspasswd fájlunkhoz hozzáfűzzük azokat a sorokat a passwd fájlból, amelyek tartalmazzák a root karakterláncot.

## Jogosultságkezelés Linuxban

A Linux jogosultság kezelése alapvetően egész egyszerű. Minden fájlnak és mappának van egy tulajdonos felhasználója és egy tulajdonos csoportja és jogosultsági szempontból van mindenki más. Ennek a három csoportnak tudjuk beállítani a jogosultságait. Amikor az `ls -l` parancsot kiadjuk akkor látjuk is az adott fájlhoz vagy mappához tartozó jogosultságokat. Az első oszlopban a 2-4. karakter a tulajdonos felhasználó, a 5-7. karakter a tulajdonos csoport és a 8-10. karakter mindenki más jogosultságait mutatja. Az r betű az olvasási jogot a w betű az írási jogot az x betű pedig a futtatási jogot jelenti. Mappák esetén az x jelenti, hogy egyáltalán beléphetünk-e a mappába.
Amikor jogosultságot akarunk állítani akkor ezeket tudjuk variálni vagy a tulajdonos felhasználót vagy csoportot módosítani. Ennek részleteiről majd a képzésen fogunk beszélni.

## Useraccount adatok tárolása

Linuxban a legalapvetőbb user adatokat a /etc/passwd fájlban tároljuk, ami egy szöveges állomány és alapértelmezésben bárki meg tudja nyitni a szerkesztéséhez viszont már külön jogosultság kell. Ebben a fájlba kettősponttal elválasztva találjuk a legfontosabb adatokat, amelyek a következők:
    - 1 user neve
    - 2 jelszó tárolására vonatkozó infó itt többnyire x-et találunk, ami azt jelenti, hogy a /etc/shadow fájlban található tikosított formában a jelszó.
    - 3 userid
    - 4 user alapértelmezett csoportjának az id-ja
    - 5 leírás az accountról ez nem kötelező
    - 6 user home mappájának elérési útvonala
    - 7 alapértelmezett parancsértelmező
Az utolsó oszlopban sok esetben találkozhatunk a nologin bejegyzéssel, ami azt jelenti, hogy ugyan az account létezik és a nevében tudunk folyamatokat futtatni, de belépni nem lehet vele. Ettől még jelszava ugyanúgy lehet. Ha például egy kolléga távozik a cégtől, akkor elég az accountjánál beírni a nologin kulcsszót és utána ő már nem tud belépni a rendszerbe viszont minden adata megmarad és elérhető.

A /etc/shadow fájlban találjuk a useraccountok jelszavait titkosított formában. Ahol megtaláljuk a felhasználó nevét, a titkosítás módjára utaló kódot, hogy mivel sózta a titkosítás a jelszavunk, a titkosított jelszavunk és a megújításra és lejáratra vonatkozó adatokat.

A következő igazán fontos fájl számunka a /etc/group ez szintén egy szöveges fájl. Itt találjuk a csoportjaink nevét és groupid-ját valamint, hogy kik a tagjai. A csoportok kezelésénél fontos, hogy alapértelmezett csoportja minden felhasználónak csak egy lehet, de másodlagos csoportja több is. Ha megnézitek ezt a fájlt akkor azt fogjátok látni, hogy a telepítéskor létrehozott useretek tagja lesz a adm, a cdrom, sudo és még több más csoportnak is. 

Természetesen a useradatok lekérésére számos parancs is létezik ezekkel majd a képzésen fogunk foglalkozni.

## Userek létrehozása

User accountot több paranccsal is létrehozhatunk mi most az `adduser` parancsot fogjuk megnézni. User accountot alapértelmezésben megfelelő jogosultsággal lehet létrehozni. Ehhez többnyire elég a sudo parancsot használnunk (alapértelmezésben ez elég a képzésen majd beszélünk a sudo parancsról), ami után beírjuk az adduser parancsot és a usernevet `sudo adduser devtest`. Ezután a linux kérni fogja a jelszavunkat, hogy megbizonyosodjon róla, hogy mi ülünk a gépnél és jogosan használjuk a sudo utasítást nem csak egy tréfás kollégánk ült be a gépünk elé. Ezek után az `adduser` parancs létrehozza a useraccountot, azonos néven a user alapértelmezett csoportját ezeknek id-t is ad létrehozza a user home directory-ját és pár alapértelmezett fájlt és beállítást eszközöl a /etc/skel fájlban definiáltak szerint. Erről a fájlról szintén majd a képzésen beszélünk. Ezek után kéri tőlünk az új user jelszavát. Majd ha akarunk megadhatunk további adatokat. Ezeket az adatokat fogjuk viszontlátni a /etc/passwd fájl leírás mezőjében. Majd rákérdez, hogy minden adat helyes-e és ha igennel válaszolunk akkor létrehozza az accountot.

## Csoporttagság módosítása

Erre is több lehetőség van mi most a `usermod` parancsot nézzük meg és annak két paraméterét, amivel a jogosultságokat módosíthatjuk. A g (kis g) paraméterrel, az alapértelmezett csoportját tudjuk módosítani, míg a G (nagy) paraméterrel a másodlagos csoportot. E parancs használatához szintén használnunk kell a sudo-t majd a szintaktikája `usermod felhasználónév paraméter érték`

Példa:
`sudo usermod  devtest -G games` Ezzel a parancsal hozzáadjuk a felhasználót a games csoporthoz is. Hatását a /etc/group fájlban tudjuk ellenőrözni.
`sudo usermod  devtest -g cdrom` Ezzel a parancsal pedig az elsődleges csoportot módosítjuk. Hatását a /etc/passwd fájlban tudjuk megnézni.


