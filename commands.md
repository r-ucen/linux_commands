- `přihlášení  root (opsys)`
- `přihlášení  student (opsys)`
- `ALT + F2` (switch na druhou konzoli)
- 
- `man loadkeys > napoveda` : vytvoří se soubor napoveda a do souboru napoveda se vepíše manuál příkazu loadkeys
- `touch soubor1` : vytvoří se soubor s názvem soubor1
- `mkdir slozka` : vytvoří se složka s nazvem slozka
- `cp soubor1 slozka` : zkopíruje se soubor1 do složky slozka
- `touch soubor2` : vytvoří soubor s názvem soubor2
- `mv soubor2 slozka` : přemístí soubor2 do složky slozka
- `cd slozka`
- `rm soubor1` : smaže soubor s názem soubor1
- `rm soubor2`
- `rmdir slozka` : smaže složku slozka
-
- `nano soubor`
- 
- `A`
- `B`
- `C`
- `D`
- 
- `cat soubor -n` : očíslovaný vypíše
- `cat soubor | sort NEBO sort soubor` : seřadí
- `sort soubor > souborSort` vpíše seřazený soubor do souborSort
- `cat souborSort -n` vypíše očíslovaný seřazený soubor (očíslovaný souborSort)
- nebo jednokrokově můžem `sort soubor | nl` : vypíše seřazený očíslovaný soubor
- `cpuls 20` : spustí cpuls na popředí na 20 sekund
- `cpuls 20 &` spustí cpuls na pozadí na 20 sekund
- `fg 1` přenese úlohu do popředí tu 1 zjistím pomocí jobs je to v té [] závorce
- `kill <PID>` např `kill 1483`
- `renice +5 1316` (může udělat student) (toto je snížení priority)
- `renice -2 1316` (nemůže udělat student, jen root) (toto je zvýšení proirity)
- `chmod u=rw,g=r,o= soubor` nebo `chmod 640` př. nastavení práv pro soubor s názvem soubor
- `nano script`
- do toho napsat `echo pocet parametru $#`
- `CTRL + O`
- `CTRL + X`
- `sh script` -> pocet parametru 0
- `sh script a b c` -> pocet parametru 3
- v linuxu je `1 false (chyba)` a `0 true (není chyba)`
- je 15:29 a chceme aby se každý den v 15:30 vykonal následující příkaz
- `30 15 * * * last >> vypisusers` : vepíše přihlášené uživatele do souboru vypisusers každý den v 15:30 

***

- `clear` : vyčistí obrazovku
- `ls -l` : výpis adresářů
- `mkdir aaa` : vytvoření adresáře s názem aaa
- `touch aaa` : vytvoří soubor s názvem aaa, pokud tento soubor již existuje, updatuje časovou známku
- `nano` : textový editor
- `cat aaa` : vypíše obsah souboru
- `cat aaa -n` : vypíše obsah souboru s čísly řádků
- `pwd` : print working directory (vypíše cestu do současného umístění v adresářovém stromu)
- `man příkaz` : manuál příkazu
- `cp aaa bbb` : zkopíruje obsah souboru aaa do souboru bbb
- `cd ..` : vrátíme se o adresář zpět
- `mv aaa bbb` : přejmenuje soubor aaa na bbb
- `alias ls='ls -al'` : přejmenování dlouhého příkazu na kratší např.
- `ALT + F1/2/3/4/5...` : přepnutí na jinou virtuální konzoli
- `loadkeys us/cz` : změna jazyka klávesnice
- `jobs` : vypsání úloh
- `ps aux` : vypsání procesů
- `top` : vypsání procesů (lepší než ps aux)
- Pokud napíšeme za příkaz pro spuštění procesu `&`, spustíme ho na pozadí
- `CTRL + C` : ukončení procesu
- `CTRL + Z` : pozastavení procesu
- `fg %1` : tu 1 zjistím pomocí jobs : přenést na popředí
- `bg %1` : přenést úlohu/proces do pozadí, můžeme použít když jsme pozastavili úlohu použitím `CTRL + Z`
- `top` pak zjistit PID a pak `kill <PID>` : zabití procesu
- `top` a pak sloupec NI : priority, -20 je nejvyšší, +19 nejnižší
- `nice` : nastavení priority
- `renice <priorita (-20 až 19)> <PID>` : změna priority
- `ls -l` : použitím tohoto příkazu zjistíme práva r read w write x execute/open, první část je pro vlastníka, druhá pro skupinu, třetí pro ostatní, pokud je na začátku d, je to directory
- `chmod <práva> <jmeno souboru>` : nastavení práv např. `chmod u=wrx,g=wx,o=wx aaa` nebo `chmod u+wrx,g+wx,o+wx aaa`
- Oktalový způsob nastavení práv : `rw-r--r-- == 110 100 100` (binární zápis) --> `644` (octa zápis) takže napíšeme `chmod 644 aaa`, max je `777` všechna práva
- `cat /etc/passwd` : výpis skupin
- `0` skupina root, `1000` skupina student
- `chgrp 1000/student aaa` : změna skupiny
- `chown root aaa` : změní vlastníka souboru aaa na root
- `newgrp` : nastavení uživatele, který není ve skupině např. `newgrp developers` přepne aktuálního uživatele do skupiny developers
- `ln aaa pevny_odkaz` : vytvoření pevného odkazu na soubor aaa
- `<` : soubor přepíše
- `<<` : přidá text do souboru (nepřepíše ho celý)
- `ln -s aaa symbol_odkaz` : vytvoření symbolického odkazu na soubor aaa
- `pico` : editor souborů, buď vytvořit soubor pomocí `touch` a pak dát `pico soubor` nebo prvně `pico` a pak v tom začít psát a pak uložit
- Pokud chceme soubor setřídit a očíslovat až je setřízený, tak buď dvojkrokově: `cat soubor_jmenaM | sort >> setrizeny`, ten setrizeny pak vypsat pomocí `cat setrizeny -n` NEBO jednokrokově: `sort soubor_jmenaM | nl`
- `cat setrizeny | head -2` : vypíše první dva řádky souboru
- `sort aaa | uniq > v1` : do souboru v1 vepíše neduplikátní seřazené řádky souboru aaa
- `cat v1 -n > v2` : očíslovaný soubor v1 dá do nového souboru v2
- `uniq aaa bbb` : do souboru bbb vepíše unikátní řádky ze souboru aaa
- `cat aaa | tail -2` : vypíše poslední dva řádky ze souboru aaa
- `cat aaa -n | tail -2` : vypíše očíslované poslední dva řádky ze souboru aaa
- `diff aaa bbb` : zobrazí rozdíly mezi soubory aaa, bbb
- `grep Josef aaa -n` : najítí řetězce 'Josef' v souboru aaa
- `find -name 'aaa*'` : najde soubory/adresáře začínající na znaky aaa
- `gzip aaa`
- `gunzip aaa`
- `tar` : zipování složek `tar -[c, x, t] [z, j]f archive-name.tar[.gz/bz2] directory-to-zip`
- * -c: create a new archive.
- * -x: extract files from an archive.
- * -t: list the contents of an archive.
- * -v: verbose output (list processed files).
- * -f: specify the filename of the archive.
- * -z: use gzip for compression (.tar.gz or .tgz files).
- * -j: use bzip2 for compression (.tar.bz2 files).
- např: `tar -czvf myarchive.tar.gz mydir` to compress a directory (mydir) into a .tar.gz file
- * -c: create the archive.
- * -z: use gzip for compression.
- * -v: verbose output (shows file names).
- * -f: specify the output file (myarchive.tar.gz).
- extrahování: `tar -xzvf myarchive.tar.gz`
- * -x: extract files.
- * -z: handle gzip compression.
- * -v: verbose output.
- * -f: specify the archive file.
- `bzip2 aaa`
- `bunzip2 aaa`
- `date` : vypíše aktuální datum
- `du /etc -h` : zobrazí velikost adresáře /etc
- `du -h` : ukáže velikost aktuálního adresáře
- `du` : využití disku - velikost složek
- `df` : volné místo na disku
- `-h` znamená, že se vypíší jednotky
- `free` : volná a využívaná paměť
- `uptime` : informace, jak dlouho běží systém
- `whoami` : jak jsem přihlášen
- `who am i` : podrobnější informace
- `w` : kdo je přihlášen a co dělá - podrobný výpis
- `who` : kdo je přihlášený
- `users` : vypíše jména uživatelů, kteří jsou přihlášeni
- `last` : seznam posledních přihlášení do systému
- `id` : info o uživateli
- `which` : vyhledání příkazu, v které je složce např. `which ls` vypíše /usr/bin/ls
- `whatis` : vyhledání nápovědy k příkazu např `whatis ls`
- `a) sh skript` : spuštění způsob 1.
- `b) skript` : nastavit právo spustit - spuštění způsob 2.
- `echo` : výpis na konzoli
- `#` : zapoznámkování řádku
- `!/bin/bash` : barevné zvýraznění kódu
- `$#` : vypíše počet argumentů
- `$0` : vypíše název příkazu
- `$1-9` : vypíše hodnotu parametru
- `$*` : vypíše argumenty jako jedno slovo
- `$@` : vypíše argumenty jako posloupnost
- `$$` : aktuální proces
- `$?` : návratový kód posledního příkazu
- `set` : přiřazení hodnoty do argumentu
- `test nebo []` : výsledek je 0 (pravda) nebo 1 (nepravda)
- `-d složka` existuje a je to adresář
- `-e soubor` existuje
- `soubor1 -nt soubor2` : pravda, když je soubor1 novější než soubor2
- `soubor1 -ot soubor2` : pravda, když je soubor1 starší než soubor2
- `shift`: posunutí pořadí parametrů
- `-eq` porovnání čísel
- `=` porovnání stringů


Test existence souboru:  

if test -e $1 (NEBO POUŽÍT if [ -e $1 ])  
then  
echo existuje  
else  
echo neexistuje  
fi  
  
  
Test dostatek parametrů  
if [ $# -eq 3 ]  
then  
echo pocet parametru je 3  
case $3 in  
    -c) echo Parametr je -c; cp $1 $2 ;;  
    -r) echo Parametr je -r; rm $1 ;;  
    -k) echo Parametr je -k; gzip $1 ;;  
    *) Byl zadan neznamy parametr ;;  
esac  
else  
echo Pocet parametru neni 3  
fi  
  
  
### WHILE   
  
echo $  
while [ $ = stop ]  
do  
    echo$  
    shift  
done  
  
### UNTIL  
until [ $ = stop ]    
do  
    echo $1  
    shift  
if [ $# -eq 0]  
then  
break  
fi  
done  

### FOR  
for i in 1 3 5 7  
do  
    touch soubor$i  
echo Byl vytvořen soubor$i  
done  
  
###  

trap 'echo zmackli jste CTRL + C; exit 1' 2  
while true  
do  
    echo Program bezi...  
    sleep 1  
done  
  
###  
  
echo -n Zadejte nějake čislo  
read cislo  
echo zadali jste $cislo  
  
### Plánování úloh

`crontab -e` : editace naplánovaných úloh  
`MIN HOUR DAY MONTH DAYOFWEEK  COMMAND`  
PŘ:  
`37 12 * * * date`  
`0 23-7/2,8 * * * date`  
`0 11 4 * mon-wed date`  
DAYOFWEEK: 0-Neděle, 6-Sobota  
`crontab -l` : výpis naplánovaných úloh

### Práce s uživatelskými účty  
`adduser "username"` : přidá uživatele a doptá se na další informace  
`useradd test_user` : přidá uživatele
`useradd -d /home/test_user test_user` - nastaví domovský adresář  
`useradd -u 1234 test_user` : přidá nový účet test_user s user ID 1234  
`useradd -g 1000 test_user` : přidá nový účet test_user a nastaví mu skupinu 1000  
`useradd -M test_user` : přidá uživatele test_user který nemá domovský adresář  
`useradd -e 2024-05-30 test_user` : přidá učet s datem platnosti

