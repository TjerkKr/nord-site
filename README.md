Doku: https://gluon.readthedocs.org/en/latest/releases/v2016.2.4.html

Gluon Version auf der die Freifunk Nord Firmware basiert:

* 2016.2.5 - Gluon 2016.2.5

Download der Firmware:

* https://nord.freifunk.net/firmware.html

Firmware selber bauen:

1. Vorbereitung:
1.1 Abhängigkeiten installieren

  	sudo apt-get install git subversion build-essential gawk unzip libncurses5-dev zlib1g-dev libssl-dev

1.2 Gluon repo clonen

	cd /opt/
	git clone https://github.com/freifunk-gluon/gluon


1.3 Freifunk Nord Site clonen

	cd gluon
	git clone https://github.com/ffnord/nord-site.git site

2. Firmware bauen 
2.1 Build vorbereiten

	git checkout v2016.2.5 && make update

2.2 Build durchführen

	make -j8 GLUON_TARGET=ar71xx-generic ##-j $ZAHL$ = Anzahl der CPU Kerne


Mögliche Targets:

GLUON_TARGET=ar71xx-generic
GLUON_TARGET=ar71xx-mikrotik
GLUON_TARGET=ar71xx-nand
GLUON_TARGET=mpc85xx-generic
GLUON_TARGET=x86-64
GLUON_TARGET=x86-generic
GLUON_TARGET=x86-kvm_guest
GLUON_TARGET=x86-xen_domu
GLUON_TARGET=brcm2708-bcm2708
GLUON_TARGET=brcm2708-bcm2709
GLUON_TARGET=ramips-mt7621
GLUON_TARGET=ramips-rt305x
GLUON_TARGET=sunxi
GLUON_TARGET=mvebu

3. Rebuild
3.1 Updaten

	cd /opt/gluon/site
	git pull
	cd ..
	git pull
	make update

3.2 Build Verzeichnis säubern

	make clean GLUON_TARGET=