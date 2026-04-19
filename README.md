# freshmangojuice.github.io
necht nas francl kriz zachrani

## Mint WMVare Setup
  **Setup** - typical<br>
  **OS** - setup later<br>
  **Disk** - 20 GB a single file<br>
  **HW** - muzeme ponechat stejne<br> 
_finish_ <br>

  Virtual Machine Settings --> CD/DVD --> vlozit ISO<br>
  Zapnuti program Install Linux (Podle vasich preferenci, nebo spamujte continue)<br>
  Username: user<br>
  Heslo: user<br> 
_install_ <br>
_restart now_ <br>
## Windows Server Setup
  **Setup** - typical<br>
  **OS** - setup later<br>
  **Disk** - 20 GB a single file<br>
  **HW** - 1 processor, 2-4 cores<br>
  _finish_ <br>
  
  Virtual Machine Settings --> CD/DVD --> vlozit ISO<br>
  Power on, spamovat tlacitko, enter(zase vase preference)<br>
  **Windows Server Desktop Experience!!!**<br>
  Custom Install<br>
  Selectnem jedinej disk<br>
  Heslo: Windows22<br>
 ## Windows Setup
  **Setup** - typical<br>
  **OS** - setup later<br>
  **Disk** - 64 GB a single file<br>
  **HW** - muzeme ponechat stejne<br> 
_finish_ <br>

  Virtual Machine Settings --> CD/DVD --> vlozit ISO<br> 
  Power on, spamovat tlacitko, enter(zase vase preference)<br>
  Windows Education!!!<br>
  Proklikat -> pri doinstalovani ovladacu zakliknout nemam internet<br>
  Settings -> Windows Update -> pozastavit na x tydnu<br>

  ## Samba Linux
  Sudo apt install samba<br>
  Vytvorit adresar k sdileni treba */home/share*
  V souboru */etc/samba/smb.conf*
  Pridat: <br>
  [share]
  path = /home/share <br>
  browseable = yes <br>
  valid users = user <br>
  read only = no <br>
  Pridat user do smb: sudo smbpasswd -a user (dodat heslo) <br>
  Radsi chmod 777 adresari <br>
  Ve Windows v pruzkumniku souboru \\*ipadresalinuxu*

## SSH Klice
Na lokalnim Windows v puttygen vytvorit klic eddsa (zaheslovat treba Heslo123) <br>
V souboru */etc/ssh/sshd_config* odkomentovat radek **#authorizedkeysfile** <br>
Vytvor soubor v */home/user/.ssh/authorized_keys* a vloz public klic (Pokud adresari neni, tak manualne vytvor) <br>
Uloz na plochu lokalniho Windows privatni klic <br>
Doubleclick private klic aby se zaktivoval klic (kontrola v sipce na liste) <br>
Zkusit pripojeni pres putty nebo winscp <br>
  
  
  
