# wallrafapp
## Die Dokumentation der WallrafApp

<ol>Inhalt
  <li>Aufsetzen der Umgebung</li>
  <li>Aufsetzen der App</li>
  <li>Screens und Components</li>
  <li>Datenbank</li>
</ol>

##### Aufsetzen der Entwicklungsumgebung
Die App wurde in react-native geschrieben. 
Installiere <a href = https://nodejs.org/en/> Node.JS (V. 8+)</a>, <a href = https://www.python.org/downloads/>Python 2</a> (Nicht 3!) und das <a href = https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html> Java SE Development Kit</a>. 
Am bequemsten geht das mit Chocolatey, einem package manager für Windows. 

```choco install -y nodejs.install python2 jdk8```

Nachdem die 3 Komponenten installiert wurden, installiere die react-native CLI in einem command prompt mit Administratorrechten.

```npm install -g react-native-cli```

Installiere anschließend Android Studio und wähle beim Installationstyp Custom aus. Folgende Dinge solltest du auswählen:
-	Android SDK
-	Android SDK Plattform
-	Performance (Intel HAXM)
-	Android Virtual Device

Installiere zuletzt noch die Android SDK in Android Studio unter

```	Settings -> Appearance & Behaviour -> System Settings -> Android SDK```

Installiere (Falls nicht bereits geschehen) Android 9 (Pie). Klick dann unten rechts auf Show Package Details und installiere unter Android 9 
-	Android SDK Platform 28
-	Intel x86 Atom_64 System Image oder Google APIs Intel x86 Atom System Image

Klick jetzt auf den Reiter SDK Tools, wieder auf Show Package Details und aktiviere nur den Wert 28.0.3 unter Android SDK Build Tools
Klick auf Apply

Zuletzt werden Umgebungsvariablen verändert.
In Windows 10, geh auf 

```Systemsteuerung -> System & Sicherheit -> System -> Computerschutz -> Erweitert```

Klick auf Umgebungsvariablen
Im Punkt Umgebungsvariablen für <Nutzer>. Ändere <NUTZER> auf deinen Benutzernamen!
  
Erstelle Umgebungsvariable ANDROID_HOME

```c:\Users\<NUTZER>\AppData\Local\Android\Sdk```
Suche die Variable Path, klick auf Bearbeiten und dann auf Neu und füge ein

```c:\Users\<NUTZER>\AppData\Local\Android\Sdk\platform-tools```

##### Deine Entwicklungsumgebung ist eingerichtet!
* test
+ test

