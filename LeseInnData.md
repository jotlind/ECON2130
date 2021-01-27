Lese inn data i R
================
Jo Thori Lind
27 1 2021

Hvordan man leser data inn i R avhenger av hva slags datafil man skal
lese fra. Her skal vi ta for oss noen av de vanligste formatene.

Mange av disse metodene kan du også gjennomføre ved å finne fila du vil
åpne i Files-vinduet (vanligvis nederst til høyre i RStudio), klikke på
fila, og følge import-veiviseren.

## Tekstfiler

Tekstfiler er filer som kan åpnes (og gir mening) i et vanlig
tekstredigeringsprogram som Notepad. Her er det vanlig å ha en linje
øverst med variabelnavn og så en observajon på hver linje nedover. Det
er flere måter å skille kolonnene (variablene) fra hverandre: komma,
tabulatortegn, mellomrom, semikolon osv.

De fleste typer tekstfiler kan leses inn med `read.delim`, men her må
man bruke opsjonen `sep =` for å angi hva som skiller kolonnene. Hvis
man vet det er komma kan man forenkle med å bruke `read.csv`. Hvis du
skal lese inn fila `inntekt.csv` kan du for eksempel bruke

``` r
innt <- read.csv('inntekt.csv')
```

Merk at navnet på fila du skal lese inn må være i enkle eller doble
hermetegn. Vi kan også bruke

``` r
innt <- read.delim('inntekt.csv', sep = ',')
```

I eksemplene over har vi implisitt antatt at datafilene ligger i R sin
arbeidskatalog. Si at filene dine ligger på D-disken i dok-katalogen så
adressen er \`D:/dok/inntekt.csv’. Da kan du enten angi hele stien og
bruke

``` r
innt <- read.csv('D:/dok/inntekt.csv')
```

eller du kan endre R sin arbeidskatalog med

``` r
setwd('D:/dok')
```

Legg merke til at R forventer vanlige skråstreker (/), ikke bakslasker
(\\)

I pakken `readr` finner vi kommandoer som gjør mye av det samme men med
litt andre valgmuligheter og ofte noe mer fleksibilitet. De skl også
være raskere på store filer. Kommandoene som tilsvarer de vi så på over
heter `read_delim` og `read_csv`.

## Excel

For å lese filer i Excel-format trenger vi en ekstrapakke. En enkel
variant er pakka `readxl` som har funksjonen `read_excel`. Den leser
både nye Excel-filer i xlsx-format og gamle filer i xls-format. I
utgangspunktet forventer funksjonen at første linje har variabelnavn og
at hver observasjon er en linje mens hver kolonne er en variabel. Det er
også mulig å droppe noen linjer øverst eller bare lese inn deler av et
Excel-ark.

Har vi en Excel-fil som heter `bnp.xlsx` kan vi lese den inn med

``` r
library(readxl)
bnp <- read_excel('bnp.xlsx')
```

## Filer fra andre statistikkprogram

Pakken `haven` har kommandoer for å lese filer fra Stata, SPSS og SAS.
For eksempel bruker du `read_dta`for å lese Stata sine dta-filer.
