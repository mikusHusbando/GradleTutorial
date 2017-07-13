# Tutorial über die Generierung von einer direkt startbaren Anwendung mit Hilfe von Gradle
## Erstellen des Application-Templates
Zuerst muss mit cd in den Ordner gewechselt werden, in dem man sein Projekt speichern möchte.

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
nico@pwrdbylnx ~/Converter % tree
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

Wichtig für das Erstellen einer zip-Datei mit ausführbarem Inhalt ist das Application-Plugin. Wenn Gradle mit dem richtigen Parameter ausgeführt wurde, sollten jetzt in build.gradle folgende Zeilen eingetragen sein:

    // Apply the application plugin to add support for building an application
    apply plugin: 'application'

Nachdem man die Vorlage erstellt hat, muss man jetzt noch Anpassungen an der build.gradle-Datei vornehmen. Die letzte Zeile muss an den eigenen Hauptklassennamen, in unserem Fall Converter angepasst werden.

    // Define the main class for the application
    mainClassName = 'Converter'
    
Wenn der Projektname vom Ordnernamen, in dem gradle init ausgeführt wurde abweicht, kann der Projektname in der letzen Zeile der Datei settings.gradle angepasst werden.

    rootProject.name = 'Converter'

## Erstellen der Anwendung

Jetzt muss der Code für die Converter-Anwendung noch in den richtigen Ordner kopiert werden oder angelegt werden.

    cp ~/Converter.java ~/Projects/Converter/src/main/java
    cp ~/ConverterTest.groovy ~/Projects/Converter/src/test/groovy
    
Ebenfalls sollten die Templates App.java und AppTest.java gelöscht werden.

    rm ~/Projects/Converter/src/main/java/Apptest.java
    rm ~/Projects/Converter/src/test/groovy/Apptest.java
aaaa
aaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaaaaaa
aaaa
aaaa
aaaa
