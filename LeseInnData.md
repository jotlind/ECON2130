Lese inn data i R
================
Jo Thori Lind
27 1 2021

Hvordan man leser data inn i R avhenger av hva slags datafil man skal
lese fra. Her skal vi ta for oss noen av de vanligste formatene.

# Tekstfiler

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
