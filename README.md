# wallrafapp
## Die Dokumentation der WallrafApp

### Inhalt
1. [Aufsetzen der Umgebung](#umgebung)
2. [Aufsetzen der App](#app)  
2.1 [Aufsetzen des Android Devices](#android)  
&nbsp;&nbsp;&nbsp;&nbsp;a) [Physisches Device](#physisch)  
&nbsp;&nbsp;&nbsp;&nbsp;b) [Virtuelles Device](#virtuell)  
2.2 [Starten der App](#starten)  
2.3 [Gängige Fehler und mögliche Lösungen](#fehler)  
3. [Screens](#screens)  
3.1 [screenStart](#start)  
3.2 [screenDecision](#decision)  
3.3 [Screen qrScan](#qrscan)  
3.4 [screenHome](#home)  
3.5 [screenTourKeyVisual](#tourvisual)  
3.6 [screenTourPicture](#tourpicture)  
3.7 [screenEnd](#end)  
4. [Components](#components)  
4.1 [Component pictureArticle](#picturearticle)  
4.2 [Component textAccordion](#textaccordion)  
4.3 [Component AudioPlayer](#audioplayer)  
4.4 [Component imageGallery](#imagegallery)  
4.5 [Component imageElement](#imageelement)  
4.6 [Component drawer](#drawer)  
4.7 [Component activityLoader](#activityloaders)  
5. [Datenbank](#datenbank)    
5.1 [touren.json](#touren)  
5.2 [tourenStops.json](#tourenStops)  
5.3 [picture.json](#picture)  
6. [To Dos](#todos)


##### Aufsetzen der Entwicklungsumgebung <a name="umgebung"></a>
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

### <a name="app"></a>2.0 Aufsetzen der App
Lasse dich von deiner Projektleitung zum [Gitlab Projekt](https://gitlab.cceh.uni-koeln.de/jschmi42/wallrafapp) hinzufügen und downloade es anschließend. Am besten geht das mit [Github Desktop](https://desktop.github.com/).  

*Stand 20.08.2019 wird die developer Branch verwendet
Über ein Merging mit der Hauptbranch wäre nachzudenken.*

Öffne das Projekt mit einem Editor deiner Wahl. Er sollte aber über ein Terminal verfügen. Gerne verwendet wurde daür [Jetbrains WebStorm](https://www.jetbrains.com/webstorm/), da man es über die Universität umsonst nutzen darf. Ein Account muss hierfür eingerichtet werden.  
Öffne das Projekt. 
Im Terminal installierst du die npm Packages mit

`npm install`

Öffne parallel Android Studio und Öffne den Android Ordner des Projekts (NICHT das Projekt selber, sondern den Ordner im Projekt, das ist wichtig!)

##### <a name="android"></a>2.1	Aufsetzen des Android Devices
###### <a name="physisch"></a>a)	Physisches Device

![buildNumbers](/img/buildNumbers.jpg)


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

###### <a name="virtuell"></a>b)	Virtuelles Device

In Android Studio, öffne den AVD Manager und erstelle ein Neues Gerät unter

`Tools -> AVD Manager -> Create new Virtual Device`

Wähle ein Handy aus. Je Neues das Handy und je besser die Auflösung, desto mehr Rechenleistung wird benötigt, um das Handy zu simulieren.   
Empfehlung: Nexus 5 bei Laptop, Pixel 2 bei neuerem Stand Computer 
Klick auf Next, dann neben Pie auf Download, um die richtige Android Version herunterzuladen und anschließend wieder auf Next und dann auf Finish.  

Starte anschließend das Handy mittels des grünen Pfeils im AVD Manager.
**Hinweis: Beim ersten Starten kann das schon was dauern**

##### <a name="starten"></a>2.2	Starten der App

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

#### <a name="fehler"></a>2.3	Gängige Fehler und ihre möglichen Lösungen 

###### Fehler

`Failed to capture snapshot of output files for task ':app:processDebugResources' property 'sourceOutputDir' during up-to-date check`

###### Lösung

Im Terminal

`cd android && gradlew clean

cd ../`

###### Fehler
Handy bleibt im Start Screen (Bei Google Logo oder Android Schriftzug) stecken
###### Lösung
Länger warten. Das Simulieren eines virtuellen Handys kann für manche Laptops eine Herausforderung sein. Da kann es vorkommen, dass es beim ERSTEN Mal starten bis zu 15 Min braucht, um das Handy zu laden.
Oder
Ein anderes, schwacheres Handy mit kleinerer Auflösung wählen.



### <a name="screens"></a>3.	Screens
##### <a name="start"></a>3.1	screenStart
Willkommen Seite mit Bild & Logos als Hintergrund. 
> Willkommen -> screenDecision

##### <a name="decision"></a>3.2	screenDecision
Auswahl zwischen Tourenübersicht und Qr Code Scanner.

> Wähle eine Tour aus -> screenHome
> Qr Code Scanner -> qrScan

##### <a name="qrscan"></a>3.3	Screen qrScan
Der QR Code Scanner liest TourId und TourIndex aus.
Momentan ist nicht klar, ob das Museum bereit ist QR Codes aufzuhängen, das war noch im Gespräch.
Die Codes, die der Scanner lesen soll, beinhalten eine Nummer für die Tour ID und eine Nummer für den Tour Index. Momentan ist leider nicht bekannt, in welchem Format diese gelesen werden (bsp: 01, 0-1, 0_1, etc.)
Idealerweise soll das scannen eines QR Codes den User dann auf die PictureArticle Seite des gescannten Bildes bringen.
> Scannen eines QR Codes -> pictureArticle[TourId, TourIndex]

##### <a name="home"></a>3.4	screenHome
Rendert alle Elemente des Components HomeArticles.
> Klick auf ein Element von HomeArticles -> screenTourKeyVisual[TourId]

##### <a name="tourvisual"></a>3.5	screenTourKeyVisual
Rendert die Informationen zur aktuellen Tour mit Namen, Text (auch in Audioform)
Informationen kommen aus DatenbankREFERENZ

`src -> assets -> data -> touren.json`

Im developer Branch sind momentan nur 2 Touren eingetragen, da diese vollständig sind und über Audiospuren verfügen. Es stehen weit mehr Touren zur Verfügung. (Aktueller Stand: ??)
> Tour Starten -> screenTourPicture[TourId]

##### <a name="tourpicture"></a>3.6	screenTourPicture

![Karte](/img/map.jpg)

`src -> assets -> img -> maps`

Maps sind beschriftet nach dem Muster STOCKWERK_RAUM (mit unseren Variablen heißt das dann buildingLevel_roomNumber)  
Die Values hierfür sind eingetragen in [picture.json)(#picture)


Auf den Karten ist der richtige Raum dann im museumsrot markiert.   
Wird ein Bild umgehängt, müssen nur die beiden jeweiligen Variablen geändert werden.  
Die Karte kann rechts oben mit dem MapIcon wieder aufgerufen werden.

Die Daten zur aktuellen Tour werden deklariert. Vor allem wichtig: 

> currentTourId, currentTourIndex, currentTourStopId(?) und currentMainPictureId

mit Hilfe der aktuellen TourId und TourIndex werden dann jeweils die nächsten Screens aufgerufen.  
screenTourPicture enthält das component pictureArticle

##### <a name="end"></a>3.7	screenEnd
Der End Screen, der nach dem letzten Bild einer Tour angezeigt wird. Von hier aus kann man zurück zur Startseite oder zurück zur Touren Auswahl
> ToDo: überlegen, ob genau diese 2 Buttons sinnvoll sind, oder man etwa Startseite durch QR Scanner Link ersetzt. (User will wohl      > entweder eine neue Tour starten oder etwas Scannen, da ist durch Startseite ein Klick dazwischen)

### <a name="components"></a>4. Components

##### <a name="pictureArticle"></a>4.1	Component pictureArticle
Das Herzstück der App. Hier handelt es sich um das Component, das dynamisch je nach TourId und TourIndex aufgebaut wird mit zugehörigem Bild, Text, Audiospur und evtl Zusatzbild und oder AccordionText

State prüft, ob wir beim letzten Bild angekommen sind:
lastTourStopId = Länge der Tour – 1  
- Falls true -> Nächstes Bild ist TourEnde (bringMeToTheEnd())
- Falls false -> Nächstes Bild ist regulär (bringMeToTheNextPicture())

Wie schon in screenTourPicture werden wichtige Variablen zu currentTourId etc. deklariert. 
Ein dataArray wird erstellt und in dieses wird der Inhalt gepusht.  
Mittels des react-native Components Image-Zoom wird das passende Bild per pictureID von der currentTour angezeigt.  
AudioPlayer wird aufgerufen mit 3 Parametern: 
-	AudioId = CurrentTourStopId
-	Navigation = navigation (?)
-	audioSource = picture 
Diese werden im Component AudioPlayer näher beschrieben.

Meta Infos zu Bild werden darunter eingeblendet. 
Dann folgen Titel und Text
Dann AccordionText, falls vorhanden. (aufklappbarer Text)

Return liefert dann erst das Data Array und danach die Pfeile zum vor und zurück gelangen.

> Achtung: Gerade sind die Pfeile ebenfalls kopiert, an den Anfang des Arrays, da gewünscht wurde, dies auch ohne Scrollen bewältigen zu > können. Das scheint noch nicht die optimale Lösung zu sein, soll aber erst vom Kurs angeschaut werden, da es eine neue Funktion ist.  > Da nicht sicher ist, wie das ankommt wurde von einer komplexeren / saubereren Lösung abgesehen. 



##### <a name="textaccordion"></a>4.2	Component textAccordion
das textAccordion ist ein selbstgeschriebenes Component.  
Es toggled zwischen zwei states, bei Click auf Aufklapp Button.
- Höhe des Textes 0
- Höhe des Textes normal

Enthält Text, der aus tourenStops.json AccordionText übergeben wird aus pictureArticle.  
Enthält Audioplayer,  
**Achtung: Noch keine Daten eingepflegt, da keine vorhanden. Testweise DummyText verwendet. **

##### <a name="audioplayer"></a>4.3	Component AudioPlayer
Der AudioPlayer besitzt 2 wichtige Parameter:

**aId Soll die CurrentTourStopId, also Index der aufrufenden Seite sein.
audioType unterscheidet zwischen Audio von pictureArticle(picture) und screenkeyTourVIsual (start) Eins von beiden muss verwendet werden, könnte noch weiter ergänzt werden beispielsweise für das Textaccordion.**

Die Sound Files sind benanntnach ts<tourStopId> also beim ersten Bild ts0.  
  
Der Audioplayer kombiniert also die strings ts + aId um die Soundfile abzuspielen, wenn sie von pictureArticle kommen
Der Rest des Components ist der Dokumentation des Audioplayers zu entnehmen.

##### <a name="imagegallery"></a>4.4	Component imageGallery
Derzeit einfache Auflistung von vordefinierten Bildern, die größer werden (aber noch verbuggt) wenn man sie anklickt, ohne Verlinkung auf Stelle in Tour 
Wird noch bearbeitet bis Semesterstart in: 
Alle Bilder des Bilderordners werden angezeigt und verlinken auf die Stelle in der Tour, zu der sie gehören. 

##### <a name="imageelement"></a>4.5	Component imageElement
Returned Bild aus this.props.imgsource? 
Konnte keine Verwendung finden, evtl veraltet 
PRÜFEN

##### <a name="drawer"></a>4.6	Component drawer
???????

#####  <a name="activityloader"></a>4.7	Component activityLoader
Veraltet?




### <a name="datenbank"></a>5. Datenbank

Die Datenbank ist aufgeteilt in drei json Dateien. 
- touren.json enthält Informationen über die Touren an sich
- tourenStops.json enthält Informationen zu den einzelnen Elementen innerhalb einer Tour
- picture.json enthält Informationen zu den Bildern

#### <a name="touren"></a>5.1 touren.json
![touren.json](/img/TourenStruktur.png)


Einträge zu Touren bestehen aus 7 Elementen
1. Tour Id
2. Tour Name
3. Tour Länge
4. Bilderanzahl
5. Teasertext 
6. Array von BilderIds, die in der Tour vorkommen
7. Array von TextIds, die in der Tour vorkommen

#### 5.2 <a name="tourenStops"></a>tourenStops.json

Einträge innerhalb der Touren bestehen aus 10 Elementen
1. Text Id
2. Tour Id
3. TourStop
4. BilderIds auf Screen (i.d.R. 1-3)
5. Überschrift
6. Haupttext
7. Quelle
8. Aufklappbarer Text
9. Audioquelle
10. Kommentar

#### 5.3 <a name="picture"></a>picture.json

Einträge zu Bildern bestehen aus 7 Einträgen
1. Bild Id 
2. Titel
3. Künstler
4. Stockwerk, in dem das Bild hängt
5. Raum, in dem das Bild hängt
6. zugehörige TourId
7. zugehörige TourStopId

#### <a name="todos"></a>6. To Dos

1. Daten für das textAccordion mit Absprache zum Inhaltsteam einpflegen  
2. Besprechen, ob es sich lohnt den Audioplayer zu überarbeiten um einen besseren einzuabauen, der über eine Zeitleiste und Lautstärkeoptionen verfügt  
3. Bildergallerie überarbeiten, da diese momentan keinen Mehrwert bringt. Links zu den Bildenr wären denkbar  
4. Das Icon sieht nicht auf jedem Smartphone gleich aus  
5. Quellenangaben müssen eingefügt werden.   
7. Bildcredits sind noch nicht vollständig in der App.  
8. Für jede Tour sollte eine eigene JSON Datei erstellt werden. BSP: TourID_Tourenstops.json.
