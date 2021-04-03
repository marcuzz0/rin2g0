# rin2go
## Premessa
rin2go è uno script shell scritto in bash che permette il post processing automatico di files rinex UBX.

## Cosa fa...
- elabora dati grezzi GNSS con osservazioni non più lunghe di un'ora
- scarica in maniera completamente automatica dati grezzi dal sito FTP delle stazioni permanenti della 
Rete FredNET (OGS) http://frednet.crs.inogs.it/ItalianSite/XFReDNetHome.htm

Più nel dettaglio lo script esegue i seguenti passaggi in sequenza:
- creazione delle cartelle di lavoro
- conversione di files rinex (rover) in formato proprietario *.ubx in file rinex *.obs
- download dei files rinex (master) dalla Rete FredNET (OGS) e successiva conversione in file *.21o e *.21n
- post-processing dei dei files rinex raccolti
- media pesata (ponderata) dei risultati ottenuti e conversione in coordinate piane
- rapporti finali in formato *.csv e *.kml


## Come si utilizza...
- copiare i files rinex proprietari in formato *.ubx nella cartella $HOME/bin/rin2go/run
- far partire lo script con il comando:
```
$ rin2go
```
- alla richiesta del sito scegliere la stazione permanente dalla quale volete scaricare i files rinex della master ed
in automatico verranno prese le coordinate della master scelta direttamente dal file stations.pos
- al termine dell'elaborazione verrano visualizzati a video i rapporti con:
	- coordinate piane dei punti 				
	- coordinate piane dei punti (FIX) 			
	- coordinate piane dei punti (STD) 			
- verranno inoltre salvati i seguenti rapporti:
	- coordinate piane dei punti 				- file *csv*
	- coordinate piane dei punti (FIX) 			- file *csv*
	- coordinate piane dei punti (STD) 			- file *csv*
	- coordinate geografiche dei punti (FIX) 	- file *csv*
	- coordinate geografiche dei punti (STD) 	- file *csv*
	- coordinate geografiche dei punti (FIX) 	- file *kml*
	- coordinate geografiche dei punti (STD) 	- file *kml*

Per l'utilizzo dello script devono essere presenti ed installati i seguenti pacchetti software:
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
$ cd $HOME
$ mkdir bin
$ cd $HOME/bin
$ git clone https://github.com/marcuzz0/rin2go.git
$ ./rin2go/install/rin2go_linux_x86_64bit
```

## Installazione per Mac OSX
```
$ brew install proj
$ brew install gdal
$ brew install git
$ brew install coreutils
$ brew install findutils
$ brew install tcsh
$ brew install gawk
$ brew install gfortran
$ brew doctor
$ brew install node
$ sudo npm install -g csv2geojson
$ mkdir bin
$ cd $HOME/bin
$ git clone https://github.com/marcuzz0/rin2go.git
$ git clone https://github.com/mapbox/csv2geojson.git
$ git clone https://github.com/rtklibexplorer/RTKLIB.git
$ cd rin2go/other/
$ wget --no-check-certificate 'https://drive.google.com/uc?export=download&id=1rnXzvScONL01aMBqQG5ro_zsoUAiCH_M' -O CRX2RNX
$ chmod a+x CRX2RNX
$ echo 'export PATH="$PATH:$HOME/bin/rin2go"' >> .bashrc
$ export PATH="$HOME/bin/rin2go:$PATH"
$ export PATH="$HOME/bin/rin2go/other:$PATH"
$ export PATH="$HOME/bin/csv2geojson/other:$PATH"
$ chmod a+x rin2go
````
