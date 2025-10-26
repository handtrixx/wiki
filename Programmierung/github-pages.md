---
title: Github Pages für Laien - Deine kostenlose Website, erstellt wie ein Profi
description: 
published: true
date: 2025-10-22T16:48:24.209Z
tags: wcms
editor: markdown
dateCreated: 2025-10-22T16:48:24.209Z
---

![webdesigner.png](/assets/wcms/github-pages/webdesigner.png){.align-center}

Im Artikel [Perfekte Website 2025](https://niklas-stephan.de/blog/perfect-website-2025/) hatte ich beschrieben, dass WordPress mittlerweile nicht mehr die erste Wahl für die Erstellung moderner Websites ist. Dort im Vergleich hatte ich jedoch Profis und Semi-Profis im Auge, die sich gerne mit technischen Details auseinandersetzen, um auch das letzte bisschen an Optimierungspotenzial und Möglichkeiten auszuschöpfen.

Was die Erstellung simpler und doch moderner Websites betrifft, gibt es jedoch auch einfachere Alternativen, die weniger technisches Know-how erfordern. Eine der einfacheren Möglichkeiten, ohne komplett den professionellen Anspruch zu verlieren oder sich auf externe Komplettlösungen verlassen zu müssen, ist die Nutzung von Plattformen wie GitHub Pages.

Dieser Artikel beschreibt, wie GitHub Pages als einfache und effektive Lösung für die Erstellung moderner Websites von dir genutzt werden kann. Dabei gehe ich auf die benötigten Tools und Schritte ein, um eine Website schnell erfolgreich zu erstellen.

## Szenario

Wir gehen davon aus, dass wir Anfänger sind und mit einem Computer mit einem Intel (oder AMD) Prozessor arbeiten, auf dem Windows, macOS oder Linux installiert ist. Unser Ziel ist es, eine von uns erstellte Website unter einer von GitHub generierten URL wie https://handtrixx.github.io/githubpagesdemo/ öffentlich bereitzustellen.
Das Ergebnis soll dann so aussehen:

![Ergebnis](/assets/wcms/github-pages/00_result.webp)

## Was brauchen wir?

Um die Website zu erstellen, benötigst du folgende Werkzeuge:

1. Einen Texteditor
2. Das Tool GIT
3. Ein GitHub-Account
4. Eine HTML-Datei

Als Texteditor werden wir für unser Mini-Projekt "Visual Studio Code" verwenden, da es für fast alle Betriebssysteme verfügbar ist und eine Vielzahl von Erweiterungen, wie z.B. Git, bietet.

Git ist ein Versionskontrollsystem, das es dir ermöglicht, Änderungen am Code nachzuverfolgen, zu kontrollieren und effizient mit anderen zusammenzuarbeiten. So kannst du lokal auf deinem PC an der Website arbeiten, ohne dass die Änderungen sofort live (für alle sichtbar) geschaltet werden.

GitHub ist eine Plattform, die es ermöglicht, deinen Code zu speichern, zu versionieren und mit anderen zu teilen. Anders formuliert handelt es sich um eine grafische Oberfläche von Git mit einer Menge Extras, um deren Betrieb du dich nicht kümmern musst.

Für die Erstellung der HTML-Datei werden wir zunächst einfaches HTML verwenden, für das es bei Interesse überall im Internet Tutorials gibt, z.B. auch hier: https://www.w3schools.com/html/default.asp.

## Voraussetzungen und erste Schritte

Die folgende Anleitung weicht je nach Betriebssystem und persönlicher Konfiguration leicht ab.

### Installation von Visual Studio Code und Git

Das Programm Visual Studio Code kannst du kostenlos von der offiziellen Website unter https://code.visualstudio.com/ herunterladen und installieren.

![VSCode Download](/assets/wcms/github-pages/01_download_vscode.webp)

Beim ersten Start des Programms begrüßt dich ein Assistent, den du einfach schließen kannst.

Stattdessen navigierst du im linken Bereich auf die dritte Option, die für die Git-Integration steht. Dort wirst du darauf hingewiesen, dass du Git zunächst installieren musst.

![Git Download](/assets/wcms/github-pages/02_download_git.webp)

Den darauf folgenden Dialog bestätigst du, was die Öffnung der Git-Downloadseite in deinem Browser zur Folge hat. Dort lädst du die Installationsdatei herunter.

![Git Downloadpage](/assets/wcms/github-pages/03_git_hp.webp)

Nach dem Download der Installationsdatei startest du die Installation, indem du die Datei ausführst. Bei der Auswahl der zu installierenden Komponenten belässt du es bei den Standardeinstellungen und klickst auf "Weiter".

![Git Editor](/assets/wcms/github-pages/04_git_editor.webp)

Bei den restlichen Schritten der Installation folgst du ebenfalls den vorgeschlagenen Werten und wartest, bis die Installation abgeschlossen ist.

Damit dein Editor (VSCode) optimal mit Git zusammenarbeitet, beendest du ihn und startest ihn nach der Installation von Git neu.

Weiter geht es mit dem Einrichten deines Projekts.

### Einrichtung des Projektverzeichnisses

Du öffnest Visual Studio Code und erstellst ein neues Projektverzeichnis auf deiner lokalen Festplatte deines PCs.

![Neues Projektverzeichnis erstellen](/assets/wcms/github-pages/05_new_project.webp)

Hierbei ist es egal wo auf der Festplatte du den Ordner anlegst, du musst dir den Ort nur merken können und solltest dort unter keinen Umständen andere Dateien speichern, da du diesen Ordner gleich mit Github synchronisieren wirst.

In unserem Beispiel erstellst du also einen Ordner "webdev" in deinen eigenen Dateien und darin den Unterordner "githubpagesdemo".
So ähnlich sollte das dann aussehen:

![Projektverzeichnis](/assets/wcms/github-pages/06_emptyfolder.webp)

In Windows in etwa:

```bash
C:\Users\niklas\OneDrive\webdev\githubpagesdemo
``` 

Unter Linux:

```bash
/home/niklas/webdev/githubpagesdemo
``` 
Und genau diesen Ordner öffnest du nun in Visual Studio Code.

![Ordner öffnen](/assets/wcms/github-pages/07_openfolder.webp)

In der Regel erscheint nun ein Dialog der dich fragt ob du dem Author dieses Ordners vertraust. Da du selber der Author bist, kannst du das natürlich bedenklos bestätigen.

![Ordner vertrauen](/assets/wcms/github-pages/07_a_trustfolder.webp)

Da dein Ordner nun geöffnet ist, kannst du mit der Einrichtung des Projekts beginnen.

Für den Start legst du erstmal nur eine Datei mit dem Namen `README.md` an. Das ist bei GitHub üblich, um grundlegende Informationen über das "Projekt" auf dessen Startseite in Github bereitzustellen.

Um eine neue Datei in VSCode zu erstellen, klicke auf das Symbol für "Neue Datei" oder nutze die Tastenkombination `Strg+N`, oder du machst einen Rechtsklick im VSCode Explorer und wählst "Neue Datei".

![Neue Datei](/assets/wcms/github-pages/09_newfile.webp)

Als Dateiname gibst du `README.md` ein und bestätigst die Eingabe, um dann einen ersten Text in der Datei zu speichern.

![Neue Datei](/assets/wcms/github-pages/10_readmemd.webp)

Hier der Text zum kopieren, falls du keine Lust hast zu tippen:

```markdown
# GithubPages Demo

This is our first edit of the README.MD file for our new GitHubPages project.
``` 

Weiter geht es nun mit der Einrichtung deines Github Projekts.

### Github und Git

Für die Nutzung von Git und GitHub Pages benötigst du ein GitHub-Konto und ein Repository, in dem du deine Website hosten kannst.

Auf https://github.com erstellst du zunächst einen neuen Account oder meldest dich mit einem bestehenden an.

![Github Account](/assets/wcms/github-pages/08_github.webp)

Nun machst du deinen Github User dem lokal installierten Git bekannt, indem du die Befehle `git config --global user.name "DeinName"` und `git config --global user.email "DeineEmail@example.com"` ausführst.

Dazu brauchst du eine Kommandozeile, wie die Eingabeaufforderung (Windows), das Terminal (Mac) oder eine Shell (Linux). Glücklicherweise ist die Kommandozeile, auch Terminal genannt, in VSCode integriert.

![Terminal in VSCode](/assets/wcms/github-pages/11_terminal.webp)

Das Terminalfenster erscheint unterhalb des Editors und ermöglicht dir, direkt Befehle einzugeben. Passe die beiden oben genannten Konfigurationsbefehle an, indem du deinen Namen und deine E-Mail-Adresse einfügst und jeweils mit der Eingabetaste bestätigst.

Sobald dass erledigt ist, kannst du den Prozess zum Veröffentlichen deines Repositories starten.

![Erste Veröffentlichung](/assets/wcms/github-pages/12_firstpublish.webp)

Die folgende Abfrage kannst du bestätigen, um den Zugriff auf dein GitHub-Konto zu erlauben.

![Berechtigungen erlauben](/assets/wcms/github-pages/13_allowaccount.webp)

Nun sollte sich dein Browser öffnen und die GitHub-Seite anzeigen, auf der du den Zugriff autorisieren kannst. Melde dich hier mit deinem zuvor angelegten GitHub-Konto an.

![Github Login für VSCode](/assets/wcms/github-pages/14_githubvscodelogin.webp)

Wenn das erfolgt ist, solltest du in VSCode im oberen Bildschirmbereich eine Abfrage nach dem gewünschten Namen deines Repositories sehen.
Du kannst den vorgeschlagenen Namen übernehmen oder einen eigenen Namen für dein Repository eingeben. Außerdem musst du hier die Sichtbarkeit des Repositories auf öffentlich (Publish to GitHub public repository) einstellen, damit deine Website für alle zugänglich ist. Bestätige anschließend deine Auswahl, um fortzufahren.

![Repository Einstellungen](/assets/wcms/github-pages/15_namerepository.webp)

Im Normalfall sollte dein Repository nun erfolgreich erstellt und veröffentlicht sein. Entsprechende Meldungen in VSCode bestätigen dies. Du kannst nun die generierte URL verwenden, um deine Repository im Browser bei Github aufzurufen. Außerdem fragt dich VSCode ob es regelmäßig nach Änderungen im Repository schauen soll, was nicht schaden kann.

![Einrichtung abgeschlossen](/assets/wcms/github-pages/16_linkdone.webp)

Wenn du dem Link aus Neugier gefolgt bist, sollte dein Repository bei GitHub nun so aussehen:

![Repository auf Github](/assets/wcms/github-pages/17_cleanrepository.webp)

Ok, zugegeben, das klingt alles ein wenig technisch, aber keine Sorge – mit ein wenig Übung wird dir das alles schnell vertraut vorkommen.
Und vora allem: Die vorherigen Schritte waren alle einmalig, d.h. deine Website zu bearbeiten ist nun fast ein "Kinderspiel."

## Zum Inhalt

Bis jetzt haben wir in unserem Repository nur eine README-Datei, die als Platzhalter dient. Nun fehlt noch der Inhalt deiner künftigen Website, den wir mit einer `index.html`-Datei erstellen werden.

### index.html - Die Grundlage deiner Website

Im nächsten Schritt fügen wir eine `index.html`-Datei hinzu, um den Inhalt unserer Website zu erstellen.
Erstelle also diese Datei mit deinem gewünschten HTML Inhalt oder benutze meinen Beispielcode hier:

```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Meine erste Website</title>
</head>
<body>
    <h1>Willkommen auf meiner Website!</h1>
    <p>Dies ist ein Beispielinhalt für deine erste GitHub Pages-Website.</p>    
    <p>Erstelle deine eigene Website mit nur wenigen Schritten und teile sie mit der Welt!</p>
</body>
</html>
``` 
Stelle sicher, dass du die Änderungen speicherst, was z.B. auch dadurch erkennbar wird das auf der linken Seite in VSCode im 3 Symbol (Git) die Zahl 1 aufleuchtet.

![index.html](/assets/wcms/github-pages/18_indexhtml.webp)

Und and dieser Stelle wird nun auch der Vorteil von Git erst so richtig klar. Während du die von dir erstellte index.html Datei lokal in deinem Browser ansehen kannst (öffne sie einfach über den Dateimanager deines Betriebssystems), ist diese noch nicht in deinem Repository. Das heisst du kannst alle deine Änderungen in Ruhe auch über Tage hinweg vornehmen und entscheidest selbst, wann du veröffentlichen willst.

Und um dann zu veröffentlichen, wechseln wir mit einen Klick in die linke Symbolleiste für Git (3. Symbol). Dann geben wir eine sogenannte Commit-Nachricht ein, die unsere Änderungen dokumentiert. Also z.B. "Mein erster Commit.". Dann klicken wir auf die "Commit" Schaltfläche.

![Erster Commit](/assets/wcms/github-pages/19_firstcommit.webp)

Im folgenden einmalig auftauchenden Dialogfenster wählst du "always" bzw. "immer", um zukünftige Bestätigungen zu automatisieren und den Workflow zu vereinfachen. Dadurch sparst du Zeit und kannst dich auf das Wesentliche konzentrieren.

![Always Commit](/assets/wcms/github-pages/20_alwayscommit.webp)

Jetzt ist unsere Änderung als freigegeben verzeichnet, aber immer noch nicht veröffentlicht (synchronisiert). Dies holen wir nach, indem wir auf die "Sync Changes" oder "Synchronisieren"-Schaltfläche klicken, um die Änderungen in das Remote-Repository hochzuladen.

![Synchronisieren](/assets/wcms/github-pages/21_syncchanges.webp)

Im folgenden Dialogfenster wählst du "OK, Don't Show Again" bzw. "Immer", um zukünftige Bestätigungen zu automatisieren und den Workflow weiter zu vereinfachen.

![Immer Synchronisieren](/assets/wcms/github-pages/22_alwayssync.webp)

Damit ist der lokale Stand mit dem Remote-Repository synchronisiert.


**Deine letzten Aktionen wirst du künftig immer wieder wiederholen. Also bei jeder Dateiänderung speichern, diese Änderung "commiten" und dann Synchronisieren.**


## GitHub Pages aktivieren

Ok, nun hast du eine rudimentäre Website erstellt und mit Github synchronisiert. Der letzte Schritt, daraus eine echte Website zu machen, ist das Aktivieren von GitHub Pages für dein Repository.

Um GitHub Pages zu aktivieren, gehe zu den Einstellungen deines Repositories, scrolle nach unten zu "Pages" und wähle den Branch aus, der als Quelle für die Website dienen soll ("main"). Speichere die Einstellungen, und deine Website wird veröffentlicht.

![Github Pages](/assets/wcms/github-pages/23_githubpages.webp)

Tada! Deine Website ist jetzt live!
Den Link findest du im rechten Bereich der Startseite deines Repositories oder du gibst in händisch in deinem Browser ein.
Das Schema ist dabei immer das Gleiche:

https://DEINBENUTZERNAME.github.io/DEINREPOSITORYNAME 

in meinem Beispiel also:

https://handtrixx.github.io/githubpagesdemo/


## Warum ist das alles kostenlos? Wo ist der Haken?

Git ist ein von Linus Torvalds (dem "Erfinder des Betriebssystems Linux") mehr oder minder aus Frust über mangelnde Alternativen geschriebenes Open-Source-Versionierungssystem. Open Source bedeutet, dass jeder den Code einsehen, nutzen und verändern kann. Das Geschäftsmodell dahinter besteht aus Beratungsdienstleistungen und Support.

Die Plattform GitHub und die zugehörigen Services gehören mittlerweile der Microsoft Corporation und sind nur teilweise Open Source. Microsoft bietet die Basisservices kostenlos an, um mit erweiterten Dienstleistungen für den professionellen Einsatz Geld zu machen.

Visual Studio Code ist ebenfalls von Microsoft als Open-Source-Software entwickelt. Es gilt als leichtgewichtige Alternative zum kostenpflichtigen Visual Studio (ohne Code am Ende).

Das Bootstrap Framework stammt von Twitter (heute X), als Nebenprodukt der Entwicklung von Twitter selbst entstanden, und wurde später vom Team als Open Source veröffentlicht. Ähnlich wie das Material Design von Google, werden über solche populären Frameworks die Designrichtlinien für moderne Webanwendungen definiert.

Alle genannten haben sich über einen Zeitraum von wenigen bis vielen Jahren zu "Quasistandards" in der Webentwicklung entwickelt und werden von Millionen von Menschen genutzt.

Der Haken dabei ist, dass Open Source zwar kostenlos ist, aber oft technisches Wissen und Eigeninitiative erfordert, um es effektiv zu nutzen.

## Fazit

Mit ein wenig Geduld und Arbeit kannst du auch als Anfänger beeindruckende Ergebnisse erzielen und deine eigene Website professionell erstellen!

Wenn du Unterstützung beim Erstellen des HTML-Inhalts benötigst, empfiehlt sich ein Blick in die gut strukturierten Tutorials bei W3Schools https://www.w3schools.com/html/default.asp oder der Einsatz eines Frameworks wie Bootstrap https://getbootstrap.com/docs/5.3/getting-started/introduction/.

Sobald deine Website mehr als die Startseite und auch dynamische Inhalte enthält, solltest du in Betracht ziehen, einen Static Site Generator Framework oder ein Content Management System (CMS) zu verwenden, um die Entwicklung zu erleichtern. Guck mal hier: https://niklas-stephan.de/blog/perfect-website-2025/.

Für Fragen direkt zum Artikel, nutze bitte die Kommentarfunktion.
