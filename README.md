# freshmangojuice.github.io
necht nas francl kriz zachrani
# OPA 
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

## U kazdeho stroje jako prvni zmenit hostname (U Windows jeste posusnout Windows Update)
## U Windows Serveru nastavit statickou ip adresu subnet (192.168.x - podle VMWare Network Editor -> Subnet Ip)
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
  Ve Windows v pruzkumniku souboru \\*ipadresalinuxu*<br>
  
## SSH Server BEZ KLICU (no puttygen)
sudo apt install ssh<br>
sudo systemctl enable ssh<br>
sudo systemctl start ssh<br>
sudo systemctl status ssh(pro kontrolu)<br>
Potom pripojeni z jineho stroje<br>

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

## Windows web ISS a FTP Server
Add server roles Web Server (IIS)<br>
V role services zaskrtnout FTP server<br>
Otevrit ISS manager<br>
Pravym tlacitkem v sites - add FTP site<br>
Pridat physical path (vytvor nejakej adresar na sdileni)<br>
Ip adresa - All unassigned<br>
No SSL<br>
Zaskrtnout basic users<br>
Allow access to all users (Read, Write)<br>
Finish<br>
otevrit wf.msc<br>
Windows defender firewall properties -> Firewall **OFF** ve vsech kartach, apply<br>
pripoj se z winscp nebo putty<br>


## ADDS 
Add roles and features -> zaskrtnout *Active Directory Domain Services*<br>
Po instalaci vlajecka -> Post deployment configuration -> Promote this server to a domain controller:<br>
Add a new forest, jmeno domeny treba blabla.local<br>
DSRM password: Heslo123<br>
Nezaskrtavat create DNS<br>
NetBiosName by melo byt BLABLA<br>
Paths nechame<br>
Install<br>
V DHCP autorizovat predtim udelane dhcp a refresh<br>
V network adapteru DNS zase pridat alternative DNS (8.8.8.8 nebo skolni 10.20.0.10) ADDS to prepise....<br>
V jinych Windows -> Nastaveni -> System -> O systemu -> Domena nebo pracovni skupina -> Zmenit -> Je clenem domeny: blabla.local<br>
AD Users and Computers =: vytvorit novy organizational unit (podle zadanai, ted treba zaci) -> New User -> zadat jmeno (treba jan) atd... heslo:User123, nezaskrtnout aby musel zmenit heslo pri loginu, zasktrnout *password never expires*<br>
Pote na jinym windows prihlasit se jako jiny uzivatel -> Domena\jmeno tedy BLABLA\jan<br>
Windows Server: Group policy management -> blabla.local v Group Policy Objects -> New -> jmeno prava<br>
Right click nove vytvorene pravo - edit -> pote enable zadano user/computer policies (pravdepodobne Administrative templates)<br>
Dragnout to pravo do slozky zaci - zaskrtnout enforced <br>
Na Windows 11 pokud nefunguje cmd - gpupdate /force a odhlasit uzivatele <br> 

# OPB
## Zadani 1 (Vybaveni kancelare)
<img width="1241" height="1755" alt="OP_Novak17 (1)_page-0001" src="https://github.com/user-attachments/assets/e9302fff-069c-4e55-b2de-b441be18d16e" />
<img width="1241" height="1755" alt="OP_Novak17 (1)_page-0002" src="https://github.com/user-attachments/assets/25627382-2915-4276-810f-19880ab37c7c" />
<img width="1241" height="1755" alt="OP_Novak17 (1)_page-0003" src="https://github.com/user-attachments/assets/5f104518-0b09-4ad5-8961-bc22aa728059" />
<img width="1241" height="1755" alt="OP_Novak17 (1)_page-0004" src="https://github.com/user-attachments/assets/0b35df94-4900-4742-804a-ce439117e747" />
<img width="1241" height="1755" alt="OP_Novak17 (1)_page-0005" src="https://github.com/user-attachments/assets/4a313abb-041d-420e-8c98-e5e414040e01" />
<img width="1241" height="1755" alt="OP_Novak17 (1)_page-0006" src="https://github.com/user-attachments/assets/94101295-e9ab-4aad-a638-94d4e39203e3" />
<img width="1241" height="1755" alt="OP_Novak17 (1)_page-0007" src="https://github.com/user-attachments/assets/61d73bd2-28ef-4400-a349-b3a6804ed1db" />
<img width="1241" height="1755" alt="OP_Novak17 (1)_page-0008" src="https://github.com/user-attachments/assets/9537117b-f779-481f-bdc1-a4809861a190" />
<br>
## Zadani 2 (Vybaveni Skoly)
## Zadani 3 (Vybaveni rodinneho domu)

#CADY
## AutoCad datove rozvody v kanclu
<img width="120%" height="2482" alt="Navrh_Novak16_pages-to-jpg-0006" src="https://github.com/user-attachments/assets/747d20e6-14d0-4afe-b149-88d511e0e98a" />
Nezapomenout na vyber Rackove skrine, metaliku CAT6a, Datovou zasuvku, pristupovy bod a podlahovou krabici<br>



  
