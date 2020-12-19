openmediavault-rsnapshot
========================

This is a plugin for OpenMediaVault.
It allows the user to configure incremental backups of any shared folder to any other shared folder.

It uses rsnapshot for creating the backups, which uses hardlinks to save disk space, and also
automatically rotates the backups.

The created backups can be browsed using SMB/NFS/... by the user.

More information and screenshots at: http://forums.openmediavault.org/viewtopic.php?f=13&t=2726&p=18450#p18450


WARNING: This modification hasn't been tested (as I don't know how to transform this content into a plugin package).
This modification should add a checkbox which ask yo choose for differential backup or not


Small Developing Guide
======

fakeroot debian/rules omv_built_pot builds the main string file to be translated.
fakeroot debian/rules omv_push_pot sends the file to transifex.
fakeroot debian/rules omv_pull_po pulls all the translations from transifex and puts them in the proper location.

fakeroot debian/rules clean binary builds the plugin.

Lesen:

http://wiki.ubuntuusers.de/Grundlagen_der_Paketerstellung

http://en.wikipedia.org/wiki/Debian_build_toolchain

Installieren:

sudo apt-get install build-essential debhelper dh-make quilt fakeroot lintian 
sudo apt-get install python-pip devscripts
pip install transifex-client

Dann dieses repo clonen.

Im Modulverzeichnis aufrufen:

dpkg-buildpackage -us -uc 

Plugin installieren!

Installation fehlgeschlagen/hängt? vermutlich konnte der omv-engined nicht starten:

/usr/sbin/omv-engined -fd
