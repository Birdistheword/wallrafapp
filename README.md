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
Installiere  [Node.JS (V. 8+)](https://nodejs.org/en/), [Python 2](https://www.python.org/downloads/)  und das  [Java SE Development Kit.](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
Am bequemsten geht das mit Chocolatey, einem package manager für Windows. 

`choco install -y nodejs.install python2 jdk8`

Nachdem die 3 Komponenten installiert wurden, installiere die react-native CLI in einem command prompt mit Administratorrechten.

`npm install -g react-native-cli`

Installiere anschließend Android Studio und wähle beim Installationstyp Custom aus. Folgende Dinge solltest du auswählen:
-	Android SDK
-	Android SDK Plattform
-	Performance (Intel HAXM)
-	Android Virtual Device

Installiere zuletzt noch die Android SDK in Android Studio unter

`	Settings -> Appearance & Behaviour -> System Settings -> Android SDK`

Installiere (Falls nicht bereits geschehen) Android 9 (Pie). Klick dann unten rechts auf Show Package Details und installiere unter Android 9 
-	Android SDK Platform 28
-	Intel x86 Atom_64 System Image oder Google APIs Intel x86 Atom System Image

Klick jetzt auf den Reiter SDK Tools, wieder auf Show Package Details und aktiviere nur den Wert 28.0.3 unter Android SDK Build Tools
Klick auf Apply

Zuletzt werden Umgebungsvariablen verändert.
In Windows 10, geh auf 

`Systemsteuerung -> System & Sicherheit -> System -> Computerschutz -> Erweitert`

Klick auf Umgebungsvariablen
Im Punkt Umgebungsvariablen für <Nutzer>. Ändere <NUTZER> auf deinen Benutzernamen!
  
Erstelle Umgebungsvariable ANDROID_HOME

`c:\Users\<NUTZER>\AppData\Local\Android\Sdk`
Suche die Variable Path, klick auf Bearbeiten und dann auf Neu und füge ein

`c:\Users\<NUTZER>\AppData\Local\Android\Sdk\platform-tools`

##### Deine Entwicklungsumgebung ist eingerichtet!

### 2.0 Aufsetzen der App
Lasse dich von deiner Projektleitung zum [Gitlab Projekt](https://gitlab.cceh.uni-koeln.de/jschmi42/wallrafapp) hinzufügen und downloade es anschließend. Am besten geht das mit [Github Desktop](https://desktop.github.com/).
*Stand 20.08.2019 wird die developer Branch verwendet
Über ein Merging mit der Hauptbranch wäre nachzudenken.*
Öffne das Projekt mit einem Editor deiner Wahl. Er sollte aber über ein Terminal verfügen. Gerne verwendet wurde daür [Jetbrains WebStorm](https://www.jetbrains.com/webstorm/), da man es über die Universität umsonst nutzen darf. Ein Account muss hierfür eingerichtet werden.
Öffne das Projekt. 
Im Terminal installierst du die npm Packages mit
`npm install`
Öffne parallel Android Studio und Öffne den Android Ordner des Projekts (NICHT das Projekt selber, sondern den Ordner im Projekt, das ist wichtig!)
##### 2.1	Aufsetzen des Android Devices
###### a)	Physisches Device

- [ ] Bild noch einfügen


Je nachdem welches Handy du besitzt findest du deine Build Number auf verschiedenen Pfaden
 

Clicke 7 Mal auf die Build Number. Nach dem letzten Click Sollte die Nachricht 

> Du bist jetzt ein Entwickler! 

(Herzlichen Glückwunsch) erscheinen.
Geh jetzt auf 

`Einstellungen -> Entwickler Optionen -> USB Debugging erlauben`

und stelle die Einstellung auf an.
Schließe dein Android Handy (5+) an deinen Computer an. Im Terminal deines Projekts, schreibe 

`Adb devices`

Um den Namen deines Handies rauszufinden.
Schreib dann

`adb -s <device name> reverse tcp:8081 tcp:8081`

wobei <device name> für den Namen deines Handies steht.

###### b)	Virtuelles Device

In Android Studio, öffne den AVD Manager und erstelle ein Neues Gerät unter

`Tools -> AVD Manager -> Create new Virtual Device`

Wähle ein Handy aus. Je Neues das Handy und je besser die Auflösung, desto mehr Rechenleistung wird benötigt, um das Handy zu simulieren. 
Empfehlung: Nexus 5 bei Laptop, Pixel 2 bei neuerem Stand Computer 
Klick auf Next, dann neben Pie auf Download, um die richtige Android Version herunterzuladen und anschließend wieder auf Next und dann auf Finish.
Starte anschließend das Handy mittels des grünen Pfeils im AVD Manager.
**Hinweis: Beim ersten Starten kann das schon was dauern**

##### 2.2	Starten der App

In Android Studio geh auf 

`File -> Sync Project with Gradle Files`

Anschließend, mit “app” als Modul, und deinem eingerichteten Handy, ausgewählt klick auf Run „app“ (alles in der oberen Leiste) 
Im Terminal:

`npm start`

In neuem Terminal:

`react-native run-android`

Die App sollte nun auf dein Handy geladen werden. 
Schüttle dein physisches Device oder drücke STRG + M beim virtuellen, um weitere Optionen anzuzeigen und klicke auf „Enable live Reload“, falls du diese Funktion aktiviert haben möchtest. 
Das Setup ist beendet!
Falls etwas noch nicht klappt, nicht verzagen! Bei den meisten von uns gab es erstmal Startschwierigkeiten. Im Folgenden liste ich die häufigsten Fehler auf.

##### 2.3	Gängige Fehler und ihre möglichen Lösungen 

###### Fehler

`Failed to capture snapshot of output files for task ':app:processDebugResources' property 'sourceOutputDir' during up-to-date check`

###### Lösung

Im Terminal

`cd android && gradlew clean
cd ../`

###### Fehler
Handy bleibt im Start Screen (Bei Google Logo oder Android Schriftzug) stecken
###### Lösung
Länger warten (dauert tatsächlich bis zu 15 Minuten bei manchen) 
Oder
Ein anderes, schwacheres Handy mit kleinerer Auflösung wählen.
NOCH WEITERE BEISPIELE?

