# Microsoft Azure projects

## Komplex monitoring környezet Windows és Linux virtuális gépekhez

### Virtuális gépek létrehozása

*Windows virtuális gép létrehozása*

Az erőforráscsoport létrehozását követően a "Create" gombra kattintva a Marketplace keresősávjába beírjuk, hogy Virtual Machine és elindítjuk a folyamatot.

<img src="./images/marketplace - vm.jpg" width="350">

A több fülből álló folyamatlépcső "Basics" fülén kiválasztjuk a Windows image fájlt, amelyet a virtuális gépünkre szeretnénk installálni az Azure segítségével és a használathoz szükséges felhasználónév és jelszó párost is megadjuk. A következő "Disks" fülön hozzáadjuk a Standard SSD disk-et és meghagyjuk a rendszer által felkínált alapértelmezett tárolóhelyet.
<table>
  <tr>
    <td><img src="./images/choose windows server.jpg" width="300"></td>
    <td><img src="./images/windows password.jpg" width="300"></td>
  </tr>
</table>

A további beállítások elvégzését a Monitoring fülön kell elvégeznünk, ahol először az "Enable Reccomended Alert Rules" jelölőnégyzetét kell kipipálni, amelynek segítségével hozzáférhetünk a riasztási szabályokhoz és magunk definiálhatjuk azokat. A következő képeken a processzor és a memória használat rendszer általi felhasználására állítunk be szabályokat. 
<table>
  <tr>
    <td><img src="./images/Windows - CPU alert.jpg" width="300"></td>
    <td><img src="./images/Windows - Memory alert.jpg" width="300"></td>
  </tr>
</table>

A szabályok határértékeinek túllépésénél e-mail értesítést kerül beállításra még, amely az általunk beállított "severity" vagyis súlyossági fok alapján küld értesítőt az e-mail fiókunkba. Az utolsó lépést a Review+Create fülön végezzük el

<img src="./images/Windows - Email notify.jpg" width="400">

*Linux virtuális gép létrehozása*

A Linux rendszerű virtuális gép létrehozásának folyamata hasonló lépésekből épül fel, mint a korábban létrehozott gép. Az első érdemi változás a "Basics" fülön az image fájl kiválasztásánál lesz tapasztalható, ahol már egy "Ubuntu 24.04 LTS x64" képfájlt kell használni. Mindemellett a Windows részére szánt gépméretet érdemes lehet kisebbre cserélni (Standard_B1s), amelyen a Linux rendszer könnyedén el fog futni a kisebb erőforrásigénye miatt. 

<img src="./images/Linux - Image and size.jpg" width="350">

Újdonság lesz az SSH kulcs használata, amivel használni lehet majd a virtuális gépet és egyúttal biztonságos hozzáférhetőséget nyújt a felhasználó számára. A kulcs létrehozásánál generálhatunk újat vagy akár meglévővel is dolgozhatunk. 

<img src="./images/Linux - SSH key.jpg" width="350">

A Standard SSD használatának kiválasztásán túl a lényegi módosításokat ez esetben is a "Monitoring" fülön kell elvégezni. A riasztási szabályok definiálásánál a CPU használati beállítást változatlanul hagyjuk, viszont a csökkentett erőforrásigényű gépünk memória használatára vonatkozóan állítunk be új szabályt, ami akkor küld riasztást a megadott e-mail fiókunkba, hogyha a rendelkezésre álló memória 250Mb alá süllyed. Egyéb változtatásra nincs szükség, a "Create" gombbal létrehozzuk.

<img src="./images/Linux - Monitoring.jpg" width="350">


### Komplex irányítópult létrehozása

Az elkészített virtuális gépek értékeinek felügyeletéhez, optimális működésének ellenőrzéséhez érdemes nyomon követni a gépek egészségügyi állapotát, terheltségét, hogy további szabályokkal, módosításokkal rövidebb és hosszabb távon is megfelelően tudjunk optimalizálni. 
A Microsoft Azure minderre széleskörű lehetőséget nyújt és a keresősávban a "Monitor" szolgáltatást megkeresve számos lehetőség adódik a fentiek vizsgálatára. 
Az irányítópult létrehozásához a bal oldali menüsávban rá kell kattintani a "Metrics" menüpontra. 

<img src="./images/Monitor - Overview.jpg" width="350">

Testreszabjuk, hogy a két korábban létrehozott virtuális gépeinket szeretnénk majd monitorozni és adatokat gyűjteni a viselkedésükről. A többi lehetőséget figyelmen kívül hagyva ki kell jelölni a két virtuális gépet. A keresősáv használata opcionális, de hasznos lehetőség, hogy a virtuális gépeket megkeressük, ha már számos más erőforrás is található abban az erőforráscsoportban. 

<img src="./images/Metrics - Apply VMs.jpg" width="350">

A létrehozást követően a diagramhoz metrikákat adhatunk hozzá, amikkel vizsgálódhatunk és elemezhetjük a megfigyelt erőforrásainkat. Az adatgyűjtés rendszeres iőközönként történik és szűrhetjük az eredményeket az időközök megválasztásával, ami órában, napban, de akár hónapban is elérhetőek számunkra. Jelen esetben a memória és a processzor terheltségét mutatják a diagramok. Fontos megjegyezni, hogy egy diagramon kombinált eredményeket is létrehozhatunk, nem csak és kizárólag egy eredmény kimutatására alkalmasak. 
<table>
  <tr>
    <td><img src="./images/Metrics - CPU chart.jpg" width="300"></td>
    <td><img src="./images/Metrics - Charts.jpg" width="300"></td>
  </tr>
</table>

Az eredményeinket külön irányítópultban kezelhetjük, ahol újbóli lekérdezések nélkül az általunk létrehozott erőforráscsoportban megtekinthetőek a legfrisebb eredmények az erőforrások állapotáról. Az irányítópultot használhatjuk saját célra, de akár megosztott állapotban a szervezet különböző felhasználói reszére is közzé tehetjük. Az irányítópultok létrehozása néhány kattintással elérhetővé válik, ahol a fentiek szerint eldönthetjük a felhasználás célját.

<img src="./images/Metrics - Pin dashboard.jpg" width="300">  
<img src="./images/Metrics - Create dashboard.jpg" width="150">

A létrehozott irányítópultokat tovább színesíthetjük csempék hozzáadásával, amikkel számunkra releváns és hasznos funkciókkal tudjuk bővíteni az irányítópult megjelenését. Közvetlen hozzáférést biztosíthatunk erőforrásainkhoz vagy akár API segítségével egy kattintás segítségével végezhetünk [műveleteket](https://learn.microsoft.com/hu-hu/rest/api/compute/virtual-machines?view=rest-compute-2025-04-01) a megfigyelt virtuális gépeinken.

<img src="./images/Dashboard - Edit button.jpg" width="300">
<img src="./images/Dashboard - Tile gallery.jpg" width="300">


### Naplók engedélyezése

A létrehozott virtuális gépeinknél az adatgyűjtés megkezdése előtt engedélyezni kell a Monitoringot. Az engedélyezési folyamatot a Monitoring eszközt megkeresve az Insights menüpontnál tudjuk elindítani. Ezen az oldalon keresztül felügyelni és követni tudjuk majd a virtuális gépünk egészségügyi és a teljesítményhez kötött állapotát. Az "Enable" gombra kattintva felugrik egy kisebb ablak, amely a Monitoring konfigurációjának beállításán vezet végig. 
Be kell állítani egy adatgyűjtési szabályt, amit át is lehet nevezni, ezzel párhuzamosan az adatgyűjtési folyamatnak a rendszer létrehoz alapértelmezetten egy "Log Analytics Workspace-t", amely az Azure Monitor tárolójaként is értelmezhető és ide kerülnek be az erőforrásokból kinyert metrikák, információk. 


A Monitoring felületen a virtuális gépek gombra kattintva láthatjuk, hogy a gépeink jelenleg monitorozva vannak vagy sem. Ha utóbbit tapasztaljuk, akkor a "Not Monitored" fülre kattintva az felügyelni kívánt virtuális gépünk monitorozását az "Enable" gombbal tudjuk aktívvá tenni.


Az alapokat elvégezve testre kell szabni, hogy az adatgyűjtés milyen forrásokból származzon a virtuális gépekre levetítve, ezért egy Linux, Windows vagy akár mindkét rendszerre vonatkozó virtuális gépekre szabott adagyűjtési szabályt (Data Collection Rule) kell létrehozni, aminek segítségével teljesítmény adatokat vagy logokat gyűjthetünk. Mindezek tárolására a Workspace nyújt segítséget, amit majd ki is kell választani az adatforrás típusának megerősítését követően. 
Az adatok vizualizációja 10-15 perc múltán megjelenik a megfigyelt virtuális gépünk Monitoring fülére kattintva az Insights fülön, ahol többek között olyan információkkal találkozhatunk, mint a CPU terhelése, hálózati adatforgalom vagy a diszk használat.






  






















