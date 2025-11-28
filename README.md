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


















