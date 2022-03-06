# 1753c - Warmup

### Crypto
- [Szymfr](#szymfr)
- [Scrypto](#scrypto)

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

```
!function(){const e=require("fs"),n=e.readFileSync("secret.txt",{encoding:"ascii"}).split("").map(e=>e.charCodeAt());for(let e=0;e<n.length;e++){const i=e%256;n[e]=(n[e]+i)%256}const i=String.fromCharCode(...n);e.writeFileSync("enc.bin",i,{encoding:"ascii"})}();
```

Kod wrzucamy do jakiegoś prettiera i możemy otrzymać go w nieco przyjaźniej wyglądającej postaci:

```
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

```
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
