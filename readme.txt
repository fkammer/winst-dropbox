== Dropbox-Installer ==
Leider lässt sich mit dem normalen Installer von Dropbox keine unattended
Installation durchführen. Es gibt zwar einen /S Schalter für eine Silent-
Installation, doch ist die Installation nicht vollständig stumm, da sich am
Ende ein Einrichtungsassistent öffnet, welcher eigentlich von jedem Nutzer
selbst ausgeführt werden muss.

== Installer entpacken ==
Auch wenn nach einer Installation auf dem Client als Domain Admin mehrere
Dateien im Ordner %ProgramFilesDir%\Dropbox\ liegen, reicht eine Datei namens
Dropbox.exe aus dem Installer aus!
Diese ist an folgender Stelle zu finden:
1. Aktuellen Windows-Installer von https://www.dropbox.de/ runterladen
2. Die exe-Datei mit 7-Zip (oder ähnlich) in einen Ordner entpacken
3. In diesem folgenden Pfad öffnen: Microsoft.VC90.CRT\$INSTDIR\
4. In diesem ist die Datei Dropbox.exe zu finden, welche in den data-Ordner des
Software-Pakets kopiert werden muss.

== Was ist bei einem Update wichtig? ==
Bei einem Update sollte die Dropbox.exe im data-Ordner durch die aus dem
aktuellen Dropbox-Installer ersetzt werden.

_WICHTIG_ ist, dass der Name der Datei nicht verändert wird (z.B. nicht die
Versionsnummer anhängen). In den User-Profilen werden bei der Einrichtung von
Dropbox automatisch Links zur Dropbox.exe-Datei angelegt, welche ins leere
zeigen würden, wenn die Datei in einer neueren Version einen anderen Namen
trägt.

== Wie genau läuft die Installation ab? ==
Das install.ins-Skript kopiert lediglich die Dropbox.exe in den Ordner
%ProgramFilesDir%\Dropbox\ und legt einen Link im Start-Menü an, welcher für
alle User sichtbar ist.

Öffnet ein User Dropbox in seinem Profil das erste mal, so erscheint das Fenster
zum Einrichten von Dropbox. Hier kann entweder ein bestehender Account angegeben
oder ein neu angelegt werden. Die Einrichtung ist nur möglich, wenn das Internet
freigeschaltet ist.
Bei der Einrichtung wird der Dropbox.exe-Prozess gestartet und ein Link auf die
Datei in den Autostart-Ordner des Users gelegt. Der Dropbox-Prozess startet
somit in Zukunft bei jedem Login automatisch. Meldet sich der Nutzer an einem
Rechner an, auf dem Dropbox nicht installiert ist, passiert nichts weiter. Im
Autostart-Ordner befindet sich dann ledigleich ein toter Linke, der aber auch
nicht gelöscht wird.

Meldet sich der Nutzer an einem Rechner an, für den der Internet-Zugang gesperrt
ist, wird der Dropbox-Dienst gestartet und versucht eine Verbindung
herzustellen. Ist dies jedoch nicht möglich, läuft der Dienst stumm im
hintergrund weiter und versucht regelmäßig eine Verbindung aufzubauen. Mit
Fehlermeldungen ist dabei nicht zu rechnen. Ein Eintrag von dropbox.com in die
Goldlist hat keinen Erfolg, da Dropbox grundsätzlich auch eine verschlüsselte
Verbindung wechselt, welche von IServ blockiert wird.

Möchte ein Nutzer Dropbox nicht mehr benutzen, reicht es folgenden Ordner zu
löschen:
I:\Remote\Anwendungsdaten\Dropbox\

== Für zukünftige Paketversion ==
Exe- oder Bat-Datei, welche im Startmenü mit verlinkt ist und die Dropbox-
Konfiguration des angemeldeten Nutzers löscht.