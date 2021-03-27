# rin2go
## Premessa
rin2go è uno script shell scritto in bash che permette il post processing automatico di files rinex UBX.
Più nel dettaglio lo script esegue i seguenti passaggi in sequenza:

- creazione delle cartelle di lavoro
- conversione di files rinex (rover) in formato proprietario *.ubx in file rinex *.obs
- download dei files rinex (master) dalla Rete FredNET (OGS) e successiva conversione in file *.21o e *.21n
- post-processing dei dei files rinex raccolti
- media pesata (ponderata) dei risultati ottenuti e conversione in coordinate piane
- rapporti finali in formato *.csv e *.kml

Per lutilizzo dello script devono essere presenti ed installati i seguenti pacchetti software:
- rtklib (https://www.rtklib.com)
- cs2cs (https://proj.org/apps/cs2cs.html)
- pos2enu (https://github.com/marcuzz0/pos2enu)
- csv2geojson (https://github.com/mapbox/csv2geojson)

AVVERTENZE:
- per il sistema operativo Windows 10 è necessario abilitare la bash di Windows, ad esempio (https://www.lffl.org/2016/08/guida-abilitare-la-bash-windows-10.html)
- per il sistema operativo Mac OSX sono necessari gli alias per date(gdate) e find(gfind).
Di seguito vengono riportati i passaggi per l'installazione delle dipendenze necessarie al corretto funzionamento dello script:

## Installazione per Debian, Ubuntu Linux, Windows 10
```
$ sudo apt-get update && sudo apt-get upgrade
$ sudo apt-get install proj-bin
$ sudo apt-get install tcsh
$ mkdir bin
$ cd $HOME/bin
$ git clone https://github.com/marcuzz0/rin2go.git
$ echo "export PATH="$PATH:$HOME/bin/rin2go"" >> .bashrc
```

## Installazione per Mac OSX
```
$ brew install proj
$ brew install coreutils
$ brew install findutils
$ brew install tcsh
$ mkdir bin
$ cd $HOME/bin
$ git clone https://github.com/marcuzz0/rin2go.git
$ echo 'export PATH="$PATH:$HOME/bin/rin2go"' >> .bashrc
````

## Come si utilizza

- copiare i files rinex proprietari in formato *.ubx nella cartella $HOME/bin/run
- far partire lo script con il comando:
```
$ rin2go
```
- alla richiesta del sito scegliere la stazione permanente dalla quale volete scaricare i files rinex della master
- al termine dell'elaborazione verrano visualizzati a video i rapporti con:
	- coordinate piane dei punti (ALL) - file *csv*
	- coordinate piane dei punti (FIX) - file *csv*
	- coordinate geografiche dei punti (FIX) - file *csv*
	- coordinate geografiche dei punti (FIX) - file *kml*
	
	

