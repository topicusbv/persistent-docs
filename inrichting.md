---
layout: main
title: Initiele project inrichting
---

Als je je [git installatie][git.html] afgerond hebt, kan één van je teamleden 
de volgende acties ondernemen om de start code te maken waaraan jullie 
gezamelijk zullen werken. Slechts één persoon hoeft dit te doen, de anderen 
kunnen de stappen aan het eind van dit document uitvoeren.


## Initiële inrichting ##

De volgende stappen worden ondernomen:

 1. Nieuw android project maken in Eclipse
 2. Git initialiseren in het project
 3. Github remote toevoegen
 4. Github code binnenhalen
 5. Android code aan git toevoegen
 6. Android code pushen naar github

### Nieuw android project ###

Gebruik de android wizard om een project te maken in je workspace. Dit levert 
de volgende folders/bestanden op:


    projectnaam/
	    src/
		gen/
		assets/
		bin/
		res/
		AndroidManifest.xml
		proguard-project.txt
		project.properties

### Git initialiseren ###

Open een git prompt (of probeer de juiste incantaties te vinden in EGit) en ga 
naar je project folder in je workspace (bijvoorbeeld:)


    c:\> cd \workspace\hellodroid
	c:\workspace\hellodroid>_

Voer dan het commando:

    git init

uit. Dit initialiseert de git repository en zorgt ervoor dat je je code kan 
committen.


### Github remote toevoegen ###

Met het onderstaande commando vertellen we Git waar de centrale server staat en 
waar het wijzigingen van je teamgenoten kan vandaan halen en waar je je eigen 
wijzigingen kwijt kan:


    git remote add origin <GIT-URL>

Vervang `<GIT-URL>` met je eigen project's URL:

 - ein1b1: `git@github.com:topicusbv/kom-ik-te-laat-ein1b1.git`
 - ein1b2: `git@github.com:topicusbv/wat-moet-ik-halen-ein1b2.git`
 - ein1b3: `git@github.com:topicusbv/kom-ik-te-laat-ein1b3.git`
 - ein1b4: `git@github.com:topicusbv/wat-moet-ik-halen-ein1b4.git`

Je kan controleren of het allemaal goed staat door

    git remote -v

uit te voeren. Je zou dan twee regels moeten zien in de vorm van:

    origin	git@github.com:topicusbv/wat-moet-ik-halen-ein1b4.git (fetch)
	origin	git@github.com:topicusbv/wat-moet-ik-halen-ein1b4.git (push)

### Github inhoud ophalen ###

Nu moeten we eerst de code die op github staat (bijv. de .gitignore) 
binnenhalen voor we onze code kunnen delen:

    git pull origin master

Dit commando haalt twee bestanden op: .gitignore en README.md

### Android code aan git toevoegen ###

Als je nu de status van je workspace opvraagt:

    > git status
    # On branch master
    #
    # Initial commit
    #
    # Untracked files:
    #   (use "git add <file>..." to include in what will be committed)
    #
    #	AndroidManifest.xml
    #	README.md
    #	proguard-project.txt
    #	project.properties
    #	res/
    #	src/
    nothing added to commit but untracked files present (use "git add" to track)

Dan zie je dat alleen de `res` en `src` folders getoond worden en niet de `bin` 
en `gen` folders. Deze laatste twee zijn specifiek voor jouw workspace: daar 
worden de binaries en gegenereerde code neergezet op basis van wat jij lokaal 
hebt staan, inclusief *jouw* wijzigingen. Het is niet handig om dit op de 
centrale code server neer te zetten omdat het te groot is (gecompileerde 
bestanden kunnen erg groot worden), en zijn eigenlijk altijd out-of-date: ze
worden toch elke keer bij een wijziging opnieuw overschreven door de compiler.

Met het volgende commando voeg je alles uit de huidige directory (en 
subdirectories) toe aan de git staging area:

    git add .

Met git status kijken levert nu dit op:

	> git status
	# On branch master
	#
	# Initial commit
	#
	# Changes to be committed:
	#   (use "git rm --cached <file>..." to unstage)
	#
	#	new file:   .classpath
	#	new file:   .project
	#	new file:   AndroidManifest.xml
	#	new file:   README.md
	#	new file:   proguard-project.txt
	#	new file:   project.properties
	#	new file:   res/drawable-hdpi/ic_launcher.png
	#	new file:   res/drawable-ldpi/ic_launcher.png
	#	new file:   res/drawable-mdpi/ic_launcher.png
	#	new file:   res/drawable-xhdpi/ic_launcher.png
	#	new file:   res/layout/main.xml
	#	new file:   res/values/strings.xml
	#	new file:   src/nl/topicus/KomIkTeLaat/KomIkTeLaatActivity.java
	#	new file:   src/nl/topicus/KomIkTeLaat/LocatieActivty.java
	#	new file:   src/nl/topicus/KomIkTeLaat/PlanningActivity.java
	#	new file:   src/nl/topicus/KomIkTeLaat/VoertuigenActivity.java
	#

(Let erop dat de `.project` en `.classpath` bestanden ook toegevoegd zijn)

Het volgende commando vertelt Git om de bestanden toe te voegen aan de lokale repository:

    git commit -m "Initiele commit"

De tekst tussen de "" is het begeleidende bericht. Hiermee kan je bijvoorbeeld 
github issues sluiten ("Fixes #1"). Laat je de `-m "..."` achterwege, dan zal 
Git je vragen om een bericht in te voeren met de ingestelde editor. Dit kan 
Notepad zijn, maar ook vi.

### Android code pushen naar github ###

De code is nu lokaal toegevoegd, maar github is nog leeg. Daar gaan we nu 
verandering in aanbrengen:

    git push

Dit stuurt de gegevens naar github en kunnen je overige teamleden de code 
ophalen.

## Inrichting voor de overige leden ##

Als je team de invulling op github heeft staan kan je het volgende doen om het 
project binnen te harken:

1. git clone
2. importeer project in eclipse
3. ...
4. profit!

### Git clone ###

Open een git prompt in je workspace, bijvoorbeeld:

    C:\> cd \workspace

En voer dan het volgende git commando uit met jouw project's git URL:

    git clone <GIT-URL>

Bijvoorbeeld:

	> git clone git@github.com:topicusbv/kom-ik-te-laat-ein1b3.git
	Cloning into kom-ik-te-laat-ein1b3...
	remote: Counting objects: 32, done.
	remote: Compressing objects: 100% (23/23), done.
	remote: Total 32 (delta 0), reused 28 (delta 0)
	Receiving objects: 100% (32/32), 35.13 KiB, done.

### Importeer project in Eclipse ###

Eclipse is een beetje dom (wij noemen Eclipse ook wel Lex-Alexander), dus moet 
je Eclipse vertellen dat er een project aangemaakt is. Ga in het "File" (voor 
de Nederlandse gebruikers "Bestand") naar de optie "Import...". In het venster 
dat tevoorschijn komt kies je voor "Existing project"/"Bestaand project", en 
klik op volgende. Daarna browse je naar je workspace en klik je OK. Je kan dan 
in het scherm je nieuwe project kiezen.

Eclipse gaat dan lekker pruttelen, genereren en compileren. Je kan dan beginnen 
met ontwikkelen.

