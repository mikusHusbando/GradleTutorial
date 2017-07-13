# Tutorial über die Generierung von einer direkt startbaren Anwendung mit Hilfe von Gradle
## Erstellen einer Gradle-Ordnerstruktur

Zuerst muss mit `cd` in den Ordner gewechselt werden, in dem man sein Projekt speichern möchte.

    cd ~/Projects

Dann erstellt man einen Wurzelordner für das Gradleprojekt.

    mkdir Converter

Im nächsten Schritt wechselt man in den neu erstellten Ordner
    
    cd Converter
    
und initialisert sein Gradle-Projekt. Da wir eine Java-Anwendung erstellen, können wir als Typ java-application angeben.

    gradle init --type=java-application
    
Man kann auch andere Testframeworks verwenden, indem man diese als weiteren Parameter angibt.

    gradle init --type=java-application --test-framework spock
    
Danach erhält man eine Ordnerstruktur-Vorlage für eine durchschnittliche Java-Applikation.
```
nico@pwrdbylnx ~/Projects/Converter % tree
    .
    ├── build.gradle
    ├── gradle
    │   └── wrapper
    │       ├── gradle-wrapper.jar
    │       └── gradle-wrapper.properties
    ├── gradlew
    ├── gradlew.bat
    ├── settings.gradle
    └── src
        ├── main
        │   └── java
        │       └── App.java
        └── test
            └── groovy
                └── AppTest.groovy
```

Alle Einstellungen lassen sich auch im Nachhinein anwenden.

## Anpassen der erstellten Vorlage

Wichtig für das Erstellen einer zip-Datei mit ausführbarem Inhalt ist das Application-Plugin. Wenn Gradle mit den richtigen Parametern ausgeführt wurde, sollten jetzt in `build.gradle` folgende Zeilen eingetragen sein:

    // Apply the application plugin to add support for building an application
    apply plugin: 'application'

Nachdem man die Vorlage erstellt hat, muss man jetzt noch Anpassungen an der `build.gradle`-Datei vornehmen. Die letzte Zeile muss an den eigenen Hauptklassennamen, in unserem Fall `Converter` angepasst werden.

    // Define the main class for the application
    mainClassName = 'Converter'
    
Wenn der Projektname vom Ordnernamen, in dem `gradle init` ausgeführt wurde abweicht, kann der Projektname in der letzen Zeile der Datei `settings.gradle` angepasst werden.

    rootProject.name = 'Converter'

## Erstellen der Anwendung

Jetzt muss der Code für die Converter-Anwendung noch in den richtigen Ordner kopiert werden oder angelegt werden.

    cp ~/Converter.java ~/Projects/Converter/src/main/java
    cp ~/ConverterTest.groovy ~/Projects/Converter/src/test/groovy
    
Ebenfalls sollten die Templates `App.java` und `AppTest.java` gelöscht werden.

    rm ~/Projects/Converter/src/main/java/Apptest.java
    rm ~/Projects/Converter/src/test/groovy/Apptest.java

## Erstellen des zip-Files zum Download

Das Application-Plugin von Gradle erstellt uns einige Tasks für unser Projekt. Alle verfügbaren Tasks lassen sich über den folgenden Befehl anzeigen:

    gradle tasks

Um eine zip-Datei inklusive einer startbaren Anwendung zu erhalten, muss der Task `distZip` ausgeführt werden.

    gradle distZip
    ls ./build/distributions
    
Jetzt sollte als Ausgabe von `ls` eine Datei `Converter.zip` im Ordner `~/Projects/Converter/build/distributions` vorhanden sein.

## Benutzen der erstellten Anwendung

Die Datei `Converter.zip` kann jetzt an  einen Benutzer versendet werden. Um den Converter zu verwenden, braucht er nur die Datei zu entpacken und im Ordner `Converter/bin` die Datei `Converter` unter Linux oder `Converter.bat` unter Windows mit den entsprechenden Parametern zu starten.

    cd ~/Downloads
    unzip Converter.zip
        
Die Applikation läuft jetzt genau so wie als wenn sie mit dem `java`-Befehl aufgerufen wurde.
    
    cd ./Converter/bin/
    ./Converter -I 16 --out 2 --value 19
    11001
    ./Converter --out 2 --in 16 -V 19
    11001
    ./Converter -V 19 --in 16
    25
    ./Converter -O 16 -V 19
    13
    ./Converter --value 19
    19
    ./Converter
    usage: Converter
    -I,--in <arg>     Eingabeformat (2,8,10,16)
