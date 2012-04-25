---
layout: main
title: Git documentatie
---                  

Op de github website zijn hele aardige documenten te vinden voor het
installeren van Git tools, en het aanmaken van een github account. Deze zijn
beschikbaar in de volgende smaken:

 * [OS X](http://help.github.com/mac-set-up-git/)
 * [Linux](http://help.github.com/linux-set-up-git)
 * [Windows](http://help.github.com/win-set-up-git) Bij stap-7, kies je 'Checkout-as-is, Commit-as-is', zie ook hier onder.

Lees deze gidsen door voor je verder gaat in dit document (je hoeft niet
alledrie de gidsen door te lezen, enkel de voor jou relevante).

## Achtergrond informatie over Git ##

 * [Git SCM](http://git-scm.com/) Git referentie website van de auteur van "Pro Git"
 * [Git Book](http://book.git-scm.com/) Boek geschreven door de git community
 * [Pro Git](http://progit.org/book/) Website van het Pro Git boek
 * [The Git Parable](http://tom.preston-werner.com/2009/05/19/the-git-parable.html) een artikel met een duidelijke uitleg over hoe git werkt vormgegeven als een leesbaar verhaal
 * [Git Reference](http://gitref.org/) ultieme referentie voor alles git
 * [Git cheat sheets](http://help.github.com/git-cheat-sheets/) lijst van git cheat sheets onderhouden door Topicus medewerkers

## Algemene instellingen ##

Voor het correct gebruik van git zijn een aantal instellingen noodzakelijk:

### Algemeen ###

Het volgende commando zorgt dat een pull standaard een rebase doet, in plaats
van een merge. Dit voorkomt de zogenaamde 'diamonds' in de history van een
project en sluit beter aan bij de manier waarop wij met git werken:

    git config --global branch.autosetuprebase always

Deze instelling kun je in EGit vinden onder Preferences > Team > Git >
Configuration > tab User Settings. Voeg hier met New Entry... hier een
key/value pair toe. Key: branch.autosetuprebase en value: always.

### Windows ###

Voer de volgende commando uit, anders heb je kans dat deze opties verkeerd
staan, waardoor EGit EOLs verkeerd commit.

    git config --system --unset core.autocrlf
    git config --global --unset core.autocrlf

## Tools (Git, Eclipse) ##

De echte diehards (met een vengeance) leven vrij en gaan hard dood, maar
gebruiken ook de commandline tools van git. Natuurlijk zijn die niet te
pruimen als je een windows fanaat bent, even goed kan je het toch proberen.
Github geeft een aantal goede tips voor het installeren van de tools.

 * [OS X](http://help.github.com/mac-set-up-git/)
 * [Linux](http://help.github.com/linux-set-up-git)
 * [Windows](http://help.github.com/win-set-up-git)

### Eclipse gebruikers (Linux, Mac, Windows, HP-UX, whatever) ###

Voor Eclipse gebruiker is er een online [handleiding voor
EGit](http://wiki.eclipse.org/EGit/User_Guide) beschikbaar.

Controleer in het preferences->General->Network Connections->SSH2 menu of je
SSH "home" directory verwijst naar de directory die door de SSH van Git
gebruikt wordt. Onder windows betekent dit meestal dat je de standaard 'ssh'
in moet veranderen in '.ssh'.

Als je een 'Auth fail' foutmelding krijgt, controlleer dan of je private key
bij de SSH2 configuratie staat. Soms kan het nodig zijn om de GIT_SSH env var
te laten wijzen naar je ssh binary.

#### EGit workflow ####

Heb je EGit geinstalleerd ga je naar de github pagina van je project waarop
je de git:// URL ziet van je project. Met de flash-button erachter kan je de
locatie kopieren (klikken in het URL veld en Control-C werkt natuurlijk ook
voor de techneuten hier). In Eclipse open je het "Git Repository Exploring"
perspective en kies je "Clone a Git repository". De URL's worden dan
automatisch in het dialoogvenster ingevuld. De username in dit dialoogvenster
moet "git" zijn, zonder password; gebruik dus niet je github-credentials.
Hoewel je specifieke branches kan overnemen kan je ook gewoon alle branches
klonen.

Bij "Local destination" is het handig de lokale directory _in_ je workspace
te kiezen (bv. /Users/pietje/workspace/projectnaam). De Eclipse mensen hebben
hier iets op tegen maar hun redenering is vrij discutabel. Als het goed is
wordt de Github repository nu gekloond naar je laptop en wordt de "master"
branch als werkkopie beschikbaar.

Na het clonen dien je de 'branch.master.rebase' configuratie optie op true te
zetten. Dit doe via de properties van de repository (rechter muisknop). (zie
https://bugs.eclipse.org/bugs/show_bug.cgi?id=345536 voor de reden)

### Mac OS X gebruikers ###

Wil je buiten Eclipse om ook gebruik maken van git, en een fatsoenlijke UI
gepresenteerd krijgen, kan je kiezen uit de onderstaande 5 clients:

 * [Git Tower](http://git-tower.com) kost €49 maar is wel de meest cleane client
 * [Source Tree](http://www.sourcetreeapp.com/) gratis, en kan mercurial, subversion en git aan
 * [Github](http://mac.github.com/) gratis, goede integratie met github, behoorlijk basic
 * [GitX](http://gitx.frim.nl/) gratis, WYPFIWYG (what you pay for is what you get)
 * [Gitbox](http://gitboxapp.com/) kost geld maar ziet er goed uit

De aanschaf van software wordt niet vergoed.

Je kan ook makkelijk Git op de commandline installeren via
[Homebrew](http://mxcl.github.com/homebrew/).

    $ brew install git

Maar dan moet je wel eerst Homebrew installeren.

### Windows gebruikers ###

Gebruik EGit.
Er is ook [Tortoise Git](http://code.google.com/p/tortoisegit/). Geen idee of het werkt.

### Linux gebruikers ###

Gebruik de commandline of de egit Eclipse plugin. Voor de KDE gebruikers is er
QGit en voor de Gnome gebruiker gitg of giggle. Van deze lijken QGit en giggle de beste.

