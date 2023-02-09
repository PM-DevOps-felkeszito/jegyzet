# A leggyakrabban használt linux bash parancsok

- ls: List - Kilistázza egy könyvtár tartalmát. Gyakori flag-ek:
  - -l: long list - hosszú listázási forma.
  - -a: all - mindent, még a rejtett állományokat is mutatja.
  - -h: human readable - a számokat értelmezhetőbb formátumban mutatja.

- pwd: Print working directory - Kiírja, hogy melyik mappában állunk abszolút *(teljes)* elérhetőségi útvonallal.

- cd: Change directory - Könyvtárváltás. Paraméterrel megadhatjuk relatív vagy abszolút útvonallal, hogy melyik könyvtárba szeretnénk belépni. Paraméter nélkül az adott felhasználó home mappájába fog lépni.

- mkdir: Make directory - Könyvtár létrehozása. Gyakran használjuk a -p flag-et, így a 'közbenső' útvonalat is létrehozza.

- mv: Move - File-ok és könyvtárak átnevezése és áthelyezése.

- cp: Copy - File-ok és könyvtárak másolása. Gyakran használjuk a -r kapcsolót, ha rekurzívan szeretnénk könyvtárszerkezetet másolni.

- rm: Remove - File-ok és könyvtárak törlése. Gyakran használt flag-ek:
  - -r: recursive - könyvtárszerkezetek törlésére.
  - -f: force - megerősítés nélkül töröl (pl olyan mappát, ami nem üres).

- touch - Elkészít egy üres file-t vagy meglévő file időbélyegét módosítja.

- ln: Link - Linket (parancsikont) készíthetünk vele.

- cat: Concatenate - Szöveges file tartalmát megjeleníti a kimeneten.

- clear - Lepucolja a terminált *(Ctrl + l)*.

- echo - Tetszőleges szöveget tudunk kiíratni a kimenetre.

- less - Szöveges állományt tudunk vele felolvasni; iránynyilakkal soronként tudunk benne haladni. Kilépés a q megnyomásával.

- more - Szöveges állományt tudunk vele felolvasni; space-el tudunk lapozni, a dokumentum végén automatikusan kilép. A q megnyomásával innen is kiléphetünk. 

- man: Manual - Használati útmutató parancsokhoz.

- uname: Unix name - rendszerinformációt kaphatunk a futó linux-unkról. Gyakran használjuk a -a kapcsolót, amivel bészedesebb a kimenet. A -r flag pedig csak a futó kernel verzióát adja vissza.

- whoami - Megmondja a belépett felhasználó nevét.

- tar: Tape archive - Be- és kicsomagolni tudunk állományokat. A -c flag-el elkészíteni tudunk csomagolt állományt, az -x-el kicsomagolni (create & extract). Tömörítésre is van lehetőségünk, attól függően, hogy milyen tömörítő programok vannak a rendszerre telepítve. Legtöbbször a gz és az xz eljárások alapból támogatottak, az -a opcióval automatikusan fogja választani a megfelelő eljárást a kiterjesztésből. A -v *(verbose)* kapcsolóval pedig beszédes kimentet fogunk kapni. Az -f opcióval fogjuk jelezni, hogy a következő paraméter egy file név lesz.

- grep - Szövegben tudunk keresni minta alapján.

- head - Szöveges file néhány első sorát adja vissza.

- tail - Szöveges file néhány utolsó sorát adja vissza.

- diff - Két szöveges file különbségét adja vissza.

- sort - A bemenet alapján sorrendbe rendezhetünk vele a kimenetre.

- export - Környezeti változót hozhatunk létre.

- zip - Zip eljárással tömöríthetünk.

- unzip - Unzip eljárással kitömöríthetünk.

- ssh: Secure Shell - Biztonságos módon csatlakozhatunk más eszközhöz.

- ps: Processes - Kilistázza a futó programokat.

- kill - Megállíthatunk vele futó programokat.

- df: Disk free - Megtudhatjuk mennyi szabad hely van a diszkjeinken. Gyakori a -h kapcsoló használata.

- mount - File rendszerhez tudunk csatolni tárolókat, pl USB diszket, ISO-t, hálózati meghajtót stb.

- umount - File rendszer lecsatolása.

- chmod: change mode bits - File/mappa elérhetőségi jogosultságát tudjuk állítani.

- chown: change owner - File/mappa tulajdonosát tudjuk módosítani.

- apt: Advanced Package Tool - Debian (és Ubuntu) származékok egyik csomagkezelője.

- dpkg: Debian package - Debian (és Ubuntu) származékok másik csomagkezelője.

- yum: Yellowdog Updater Modified - Red Hat disztribúció és származékok egyik csomagkezelője.

- dnf: Dandified - A yum továbbfejlesztett verziója.

- rpm: Red Hat package manager - Red Hat disztribúció és származékok másik csomagkezelője.

- wget: web get - Az internetről tudunk letölteni vele file-okat.

- alias - Egyedi nevén illethetünk programokat és kapcsolókat.

- find - Kereshetünk a file rendszerben és a találati eredménnyel feladatot is végre tudunk hajtani.

- sudo: superuser do - Emelt szintű jogosultságot szerezhetünk a rendszerben - amennyiben jogosultak vagyunk rá.

- top - Interaktív módon tudjuk megnézni a futó processzeket, rendezhetük, megállíthatjuk és egyes tulajdonságait módosíthatjuk is.

- useradd - A rendszerhez tudunk adni új felhasználót és jó pár dolgot automatizál a feladat során.

- groupadd - Új csoport létrehozása.

- passwd - Jelszóváltoztatás

- systemctl: system control - Szolgáltatások (újra)indítása / leállítása / ellenőrzése / engedélyezése / tiltása