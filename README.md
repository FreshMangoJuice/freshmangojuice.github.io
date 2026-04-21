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
  V souboru */etc/samba/smb.conf* <br>
  Pridat: <br> <br>
  *[share] <br>
  path = /home/share <br>
  browseable = yes <br>
  valid users = user <br>
  read only = no <br>* <br>
  Pridat user do smb: sudo smbpasswd -a user (dodat heslo) <br>
  Radsi chmod 777 adresari <br>
  sudo systemctl restart smbd (radsi zkus jeste samba) <br>
  Ve Windows v pruzkumniku souboru \\*ipadresalinuxu*

## SSH Klice
Na lokalnim Windows v puttygen vytvorit klic eddsa (zaheslovat treba Heslo123) <br>
V souboru */etc/ssh/sshd_config* odkomentovat radek **#authorizedkeysfile** <br>
Vytvor soubor v */home/user/.ssh/authorized_keys* a vloz public klic (Pokud adresari neni, tak manualne vytvor) <br>
Uloz na plochu lokalniho Windows privatni klic <br>
Doubleclick private klic aby se zaktivoval klic (kontrola v sipce na liste) <br>
Linux: sudo systemctl restart ssh <br>
Zkusit pripojeni pres putty nebo winscp <br>

## Web Server Linux (Apache)
sudo apt install apache2 <br>
sudo systemctl start apache2 <br>
sudo systemctl enable apache2 <br>
Pridat adresare do */var/www/stranka1* a do nej soubor index.html (s paragrafem treba) <br>
V */etc/apache2/sites-available* zkopirovat soubor 000-default.conf a prejmenovat (stranka1.conf): <br> <br>
**Servername** = mojetestovacistranka1.com <br>
**ServerAdmin** = webmaster@localhost <br>
**DocumentRoot** /var/www/stranka1 <br> <br>
sudo a2ensite stranka1.conf (mel by se vytvorit symlink do sites-enabled) <br>
V souboru /etc/hosts pridej: <br>
127.0.0.1 mojetestovacistranka1.com <br>
sudo systemctl restart apache2 jenom protoze muzu <br>

## RDP (Remmina)
Linux: sudo apt install remmina <br>
Na Windows: searchbar - remote desktop settings -> settings -> Enable remote desktop on<br>
Linux: otevrit program remmina rdp - ip adresa windows serveru<br>
Zadat username a heslo Windows -> connect<br>

## ADDS 
Add roles and features -> zaskrtnout *Active Directory Domain Services*<br>
Po instalaci vlajecka -> Post deployment configuration -> Promote this server to a domain controller:<br>
Add a new forest, jmeno domeny treba BLABLA.local<br>
DSRM password: Heslo123<br>
Nezaskrtavat create DNS<br>
NetBiosName by melo byt BLABLA<br>
Paths nechame<br>
Install<br>

  
