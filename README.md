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

    git clone https://github.com/mc-b/lernkube
    cd lernkube
    git clone https://github.com/mc-b/iot.kafka# nur für die IoTBeispiele
    cp templates/MISEGR.yaml config.yaml
    #evtl.Memory in config.yaml reduzieren (Standard = 10 GB RAM)
    vagrant plugin install vagrant-disksize
    vag rantup
    # Warten bis Installiert und Ausgabe Token, Cluster erfolgt
    source kubeenv # setzt Umgebungsvariablen
    kubectl.... (wie auf Folien beschrieben)Folie: 16


---

### 704.1 Configuration Management

**Weight:** 8

**Beschreibung** 
Der Kandidat soll in der Lage sein Ansible verwenden und konfigurationen durchführen können. 

**Tagesziele**
* ansible.cfg verstehen
* ansible-playbook verstehen
* ansible-vault verstehen
* ansible-galaxy verstehen
* ansible-doc verstehen
* ansible aufgesetzt


**Vorgehen**  

Ich suche auf der Ansible-Website nach einer Anleitung und installiere Ansible wie dort beschrieben.  

**Beispiele und Arbeitsergebnisse**

**Ansible.cfg**

Das ist das Konfigurationsfile von Ansible. Die standardmässig vorhandenen Konfigurationen sollten in der Regel reichen. Das File findet man unter /etc/ansible.
Im File können auch Umgebungsvariablen erstellt werden, welche die grundsätzlichen Variablen überschreibt.  

**Ansible-playbook**

In Ansible-playbook können Regeln definiert werden oder auch was auf dem Remote System erledigt werden sollte. Das Ansible-playbook-File liegt im besten Fall in einem Directory, wo alle Playbooks gesichert sind. Das Playbook wird im Format .yml gespeichert und kann folgendermassen aussehen: 
```
  - name: Run Powershell Scripts
      hosts: windows
      tasks:
        - name: run a powershell script
          win_command: powershell.exe -ExecutionPolicy ByPass -File C:/Users/Administrator/Documents/simple_ps.ps1
```

In diesem Fall wird eine Remote-Verbindung zum Hosts «windows» gemacht und dort wird das PowerShell-Script ausgeführt, welches sich im Pfad *«C:/Users/Administrator/Documents/simple_ps.ps1»* befindet. 

Zum Ansible mit einem Playbook auszuführen, kann man beispielsweise folgenden Befehl verwenden. 

    ansible-playbook $PlaybookPath -i $HostPath

**Ansible-vault**

Ansible-Vault ist ein Tool, dass es ermöglicht Files zu verschlüsseln. So stehen beispielweise Benutzername und Passwörter nicht im Klartext.
![ Ansible Vault ](/images/ansible_vault_encrypted.png)
  
In diesem Beispiel wären der Benutzername und das Passwort vom Remote-Server klar ersichtlich.

![ Ansible ](/images/ansible_01.png)

Um ein File mit Ansible-Vault zu entschlüsseln kann man beispielsweise folgenden Befehl verwenden: 

    ansible-playbook $PlaybookPath -i $HostPath --ask-vault-pass

**Ansible-galaxy**

bääääääh

**Ansible-doc**

Zeigt Informationen zu Modulen an, die in Ansible-Bibliotheken installiert sind. Es zeigt eine kurze Auflistung von Plugins und deren Kurzbeschreibungen, liefert einen Ausdruck ihrer DOCUMENTATION-Strings und kann einen kurzen "Ausschnitt" erstellen, der in ein Playbook eingefügt werden kann.

**Hosts**

In ansible gibt es im Verzeichnis */etc/ansible* eine File namens hosts. Dort kann man viele IP-Adressen zu einer bestimmten Gruppe auflisten, damit beim Ausführen eines Befehls, die ganze Gruppe den Befehl ausführt. Man könnte dort auch die Benutzername und das Passwort des Remote-Servers angeben, wäre aber nicht so praktisch, weil es dafür eine bessere Lösung gibt. 

![ Ansible Hosts ](/images/ansible_hosts.png)
 
**Group_vars**

Dieser Ordner muss man noch erstellen und normalerweise werde dort auch die Anmeldeinformationen der hosts in .yaml Files gespeichert. Allerdings ist es aber auch möglich einen anderen Namen für diesen Ordner zu definieren, das müsste aber dann wiederrum im ansible.cfg konfiguriert werden. Group_vars ist der Standardname.

**Ansible für nicht-Linux-Systeme**

Ansible kann man auch für Windows benutzen. Dafür wird das Protokoll winrm verwendet. Der ganze Aufbau ist auch sehr ähnlich, wie bei Linux-Systemen. Auf dem Windows-Server müssen nur wenige PowerShell Scripts und PowerShell-Befehle ausgeführt werden, damit die Ports 5985 für http und 5986 für HTTPS. WinRM ist ein SOAP(Simple Object Access Protocol) Netzwerkprotokoll. Die ganze Anleitung für die Konfiguration unter Windows findet man hier: https://docs.ansible.com/ansible/latest/user_guide/windows_winrm.html

**Arbeitsergebnisse**
Die Files der Arbeiten können hier angeschaut werden: 
![ Ansible Dokumente] (ansible)