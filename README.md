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

A szabályok határértékeinek túllépésénél e-mail értesítést kerül beállításra még, amely az általunk beállított "severity" vagyis súlyossági fok alapján küld értesítőt az e-mail fiókunkba. 
















