# rin2go
## Premessa
rin2go è uno script shell scritto in bash che permette il post processing automatico di files rinex UBX.
Più nel dettaglio lo script esegue i seguenti passaggi in sequenza:

- creazione delle cartelle di lavoro
- conversione di files rinex (rover) in formato proprietario *.ubx in file rinex *.obs
- download dei files rinex (master) dalla Rete FredNET e successiva conversione in file *.21o e *.21n
- post-processing dei dei files rinex raccolti
- media pesata (ponderata) dei risultati ottenuti e conversione in coordinate piane
- rapporti finali in formato *.csv e *.kml

Per lutilizzo dello script devono essere presenti ed installati i seguenti pacchetti software:
- rtklib (www.rtklib.com)
- cs2cs
- pos2enu
- csv2geojson

Di seguito vengono riportati i passaggi per l'installazione delle dipendenze necessarie al corretto funzionamento dello script.
NB: per il sistema operativo Windows 10 è necessario abilitare la bash di Windows, ad esempio (https://www.lffl.org/2016/08/guida-abilitare-la-bash-windows-10.html)

## Installazione per Debian, Ubuntu Linux, Windows 10
```
$ sudo apt-get update && sudo apt-get upgrade
$ sudo apt-get install proj-bin
$ mkdir bin
$ cd $HOME/bin
$ git clone https://github.com/marcuzz0/rin2go.git
$ echo "export PATH="$PATH:$HOME/bin/rin2go"" >> .bashrc
```

## Installazione per Mac OSX
```
$ brew install proj
$ mkdir bin
$ cd $HOME/bin
$ git clone https://github.com/marcuzz0/rin2go.git
$ echo 'export PATH="$PATH:$HOME/bin/rin2go"' >> .bashrc
````

## Come si utilizza
```
$ rin2go
```
