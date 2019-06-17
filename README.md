## Fahrplan
***


| Datum    | behandelte Unterrichtsinhalte:                                                                                                                                 | Gewichtung |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| 15.05.19 | Installation SW, Einrichten Linux VM(s)<br>[701.1 Modern Software Development, 1. Teil](https://github.com/w901-fr19-mi/E701#7011-modern-software-development) | 6          |
| 22.05.19 | [701.3 Source Code Management](https://github.com/w901-fr19-mi/E701#7013-source-code-management)                                                               | 5          |
| 29.05.19 | Planung nächste Mal                                                                                                                                            |            |
| 05.06.19 | 702.1 Container Usage, 1. Teil                                                                                                                                 | 7          |
| 12.06.19 | 702.1 Container Usage, 2. Teil                                                                                                                                 | (7)        |
| 19.06.19 | 702.2 Container Deployment and Orchestration                                                                                                                   | 5          |
| 26.06.19 | LB1 Theoretische Prüfung und Abschluss LB2                                                                                                                     | -          |
| 03.07.19 | Sommersporttage                                                                                                                                                | -          |
|          | Total Punkte                                                                                                                                                   | 27 (34) !  |

Kapitel aus E701 wurden in der Gruppe mit .... erarbeitet. Davon sind mindestens 14 Punkte selbständig erarbeitet worden. 

## Dokumention des Lern- und Entwicklungsprozesses
***

### Kapitel: 701.1 Container Usage (Status: In Arbeit)

**Weight**: 7 (7)

**Beschreibung** Gegenüberstellung welche Linux Technologien für Container verwendet werden.

**Tagesziele**, z.B. Erstellung einer Tabelle Linux - Container. 

**Vorgehen**, z.B. Studieren Background Linux Namespaces vs. Container, UnionFS vs. Container Layer, Unix Prozesse (Jobs) vs. Docker run/start/stop

**Beispiele und Arbeitsergebnisse**

| Linux         | Container           | Beschreibung                                                               |
| ------------- | ------------------- | -------------------------------------------------------------------------- |
| Namespaces    | laufender Container | beim Starten des Containers wird in eine andere Linux Namespace gewechselt |
| UnionFS       | Image Layer         | Container Verwenden UnionFileSysteme um ....                               |
| Unix Prozesse | run/start/stop      | docker run/start/stop Befehle ähneln dem .... Subsystem                    |

**Fazit und Aussicht**, z.B. Die Durcharbeitung von ... gab mir ein besseres Verständnis über die Funktionsweise von Containern.

## Links

* [Exam 701: DevOps Tools Engineer](https://www.lpi.org/our-certifications/exam-701-objectives) 
* [E701 Dokumentation](https://github.com/w901-fr19-mi/E701)
* [myE701 Original Repository](https://github.com/w901-fr19-mi/myE701) 
***

### 701.3 Source Code Management

**Weight:** 5

**Beschreibung** 
Kandidaten sollten in der Lage sein, Git zur Verwaltung und Freigabe von Quellcode zu verwenden. Dazu gehören das Erstellen und Beitragen zu einem Repository sowie die Verwendung von Tags, Zweigen und Remote-Repositories. Darüber hinaus sollte der Kandidat in der Lage sein, Dateien zusammenzuführen und Konflikte zu lösen.

**Tagesziele**
* Das Konzept von Git und Repository verstehen
* Dateien in einem Git-Repository verwalten können
* Branches, Tags und Forks verwalten können und verstehen
 


**Vorgehen** Mit Hilfe von den verlinkten Seiten, welche von Herrn Bernet bereitgestellt worden sind und indem ich selber mit Git arbeite. Ich erstelle einen eigenen Repo und lerne so auch gleich das Verwalten von einem Repo. Damit ich Branches, Tags und Forks verstehen und verwalten kann, schaue ich mir die unterschiedlichen Links an und informiere mich im Internet.  

**Beispiele und Arbeitsergebnisse**
Ich schreibe meine Dokumentation in Github. Als Editor verwende ich Visual Studio Code.

![Github in Visual Studio Code ](/images/visual_studio_code_github.png)

*Branch*
Ein Branch ist ein isolierter Bereich, bei dem beispielsweise Porgramme oder Scripts entwickelt werden. Durch die Isolation beinträchtigt ein selber erstellen Branch den "master" nicht. 

| Commands     | Beschreibung                                                                                                                                                                                |
| ------------ | -------------- |
| git branch   | Mit diesem Befehl können neue Branches erstellt werden (z.B. git branch Test123) oder alle Branches aufgelistet werden                                                                      |
| git commit   | Wird das Gespeicherte bestätigt                                                                                                                                                             |
| git checkout | Mit diesem Befehl wechselt man unter den verschiedenen Branches (z.B git checkout Test123). Auch können mittels Paramater z.B. -b einen neuen Branch erstellt und gleich gewechselt werden. |
| git clone    | Mit diese Befehl klont man ein Repository aus einem Git.                                                                                                                                    |
*Tags*
Tags sind Referenzen für eine Version einer Git-Datei. So kann man beliebig auf eine Version wechseln oder diese ansehen. 

*Forks*
Mit Forks kann man ein Git Repository forken, somit "kopiert" man ein Repository zu seinem eigenen Git.


**Fazit und Aussicht**
Ich konnte meine Ziele erreichen und habe nun eine bessere Vorstellung von Git. 
***

### 702.1 Container Usage

**Weight:** 
7 (Für Schüler die das Modul 300 nicht besucht haben, +7 Bonuspunkte)

**Beschreibung**
Kandidat kann eine Docker Umgebung aufbauen, betreiben und teilen. Dazu gehört das Erstellen von Dockerfiles und weiteres. 
 

**Tagesziele**
* Dockerfunktionen dokumentieren
* eigenes Dockerfile erstellen
* Dockercontainer erstellen
* Bedienung und Zugriff auf Docker-Container 

**Vorgehen**  
Ich erstelle ein eigenes Dockerfile. Mit diesem Dockerfile wird automatisch ein MySQL Container erstellt und gestartet. 

**Beispiele und Arbeitsergebnisse**
*Was ist Docker?*
Mit Docker kann man vereinfacht Container bereitstellen und installieren. 

*Docker Befehle*

| Command | Bedeutung |
| ---- | ---- |
| docker build "Source" | Erstellt ein Docker image | 
| docker images | Zeigt alle verfügbare Docker images |
| docker rmi "image" | Löscht ein Docker image |
| docker run "image" | startet ein Docker image |
| docker exec -it "Container" \bin\bash | Exploriert einen Container |

*Dockerfile*
Folgend ist der Inhalt des Dockerfiles.

    FROM ubuntu:14.04

    # root Password setzen
    RUN echo 'mysql-server mysql-server/root_password password Server.22' | debconf-set-selections 
    RUN echo 'mysql-server mysql-server/root_password_again password Server.22' | debconf-set-selections 

    # Installation
    RUN apt-get update && apt-get install -y mysql-server

    # mysql config
    RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/my.cnf

    EXPOSE 3306

    VOLUME /var/lib/mysql

    CMD ["mysqld"]
***

### 702.2 Container Deployment and Orchestration

**Weight:**
5

**Beschreibung**
Der Kandidat ist in der Lage, Kubernetes einzurichten und Docker Compose einzusetzen.  
 

**Tagesziele**
* Kubernetes umgebung einrichten
* Weave einrichten
* Docker Compose verstehen

**Vorgehen**  
Ich werde die Lernumgebung starten un Kuberentes genau anschaun. Ausserdem installiere ich noch Weave. 

**Beispiele und Arbeitsergebnisse**
gitclonehttps://github.com/mc-b/lernkube
cd lernkube
gitclonehttps://github.com/mc-b/iot.kafka# nur für die IoTBeispiele
cptemplates/MISEGR.yamlconfig.yaml
#evtl.Memory in config.yamlreduzieren (Standard = 10 GB RAM)
vagrantplugininstallvagrant-disksize
vagrantup
# Warten bis Installiert und Ausgabe Token, Cluster erfolgt
source kubeenv# setzt Umgebungsvariablen
kubectl.... (wie auf Folien beschrieben)Folie: 16
