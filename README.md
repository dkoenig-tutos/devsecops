<h6 id="section0"></h6>

# DevSecOps - Cas pratique
## Architecture DevSecOps étape par étape

**Table des matières**
====================

<a href="#step1">I - Création d'un compte Github [Dev]</a><br/>
<a href="#step2">II - Création d'un repository dans Github [Dev]</a><br/>
<a href="#step3">III - Installation de Git [Dev]</a><br/>
<a href="#step4">IV - Création du repository Git local via HTTPS [Dev]</a><br/>
<a href="#step5">V - Rédaction du fichier README dans Git [Dev]</a><br/>
<a href="#step6">VI - Sécurisation de la connection à Github [DevSec]</a><br/>
<a href="#step7">VII - Signature des commits [DevSec]</a><br/>
<a href="#step8">VIII - Installation de Visual Studio Code [Dev]</a><br/>

--------------------

<h3 id="step1">I - Création d'un compte Github [Dev]</h3>

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0001-Creation_d_un_compte_Github-0001.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0001-Creation_d_un_compte_Github-0002.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0001-Creation_d_un_compte_Github-0003.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0001-Creation_d_un_compte_Github-0004.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0001-Creation_d_un_compte_Github-0005.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0001-Creation_d_un_compte_Github-0006.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0001-Creation_d_un_compte_Github-0007.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0001-Creation_d_un_compte_Github-0008.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0001-Creation_d_un_compte_Github-0009.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0001-Creation_d_un_compte_Github-0010.png)

<a href="#section0">Remonter</a>

--------------------

<h3 id="step2">II - Création d'un repository dans Github [Dev]</h3>

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0002-Creation_d_un_repository_dans_Github-0001.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0002-Creation_d_un_repository_dans_Github-0002.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0002-Creation_d_un_repository_dans_Github-0003.png)

<a href="#section0">Remonter</a>

--------------------

<h3 id="step3">III - Installation de Git [Dev]</h3>

[Procédure officielle d'installation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
[Repository des releases Git](https://github.com/git/git/releases)

Ouvrir un terminal.

### Installation de Git

```
$ sudo apt-get install -y dh-autoreconf libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev
$ sudo apt-get install -y asciidoc xmlto docbook2x
$ sudo apt-get install -y install-info
$ cd /tmp
$ wget https://github.com/git/git/archive/refs/tags/v2.31.1.tar.gz
$ tar -zxf v2.31.1.tar.gz
$ cd git-2.31.1/
$ make configure
$ ./configure --prefix=/usr
$ make all doc info
$ sudo make install install-doc install-html install-info
$ git --version
git version 2.31.1
```

### Configuration de Git pour Github

```
$ git config --global user.name "dkoenig-tutos"
$ git config --global user.email dkoenig.tutos@gmail.com
$ git config --list --show-origin
file:/home/dkoenig/.gitconfig   user.name=dkoenig-tutos
file:/home/dkoenig/.gitconfig   user.email=dkoenig.tutos@gmail.com
```

<a href="#section0">Remonter</a>

--------------------

<h3 id="step4">IV - Création du repository Git local via HTTPS [Dev]</h3>

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0004-Creation_du_repository_Git_local-0001.png)

```
$ cd /mnt/data
$ mkdir github
$ cd github
$ git config --global user.name "dkoenig-tutos"
$ git config --global user.email "dkoenig.tutos@gmail.com"
$ git config --list
user.name=dkoenig-tutos
user.email=dkoenig.tutos@gmail.com
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
remote.origin.url=https://github.com/dkoenig-tutos/devsecops.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.main.remote=origin
branch.main.merge=refs/heads/main
$ git clone https://github.com/dkoenig-tutos/devsecops.git
```

Ajout des screenshots effectués et sauvegardés dans le répertoire images

```
$ git status
Sur la branche main
Votre branche est à jour avec 'origin/main'.

Fichiers non suivis:
  (utilisez "git add <fichier>..." pour inclure dans ce qui sera validé)
	images/

aucune modification ajoutée à la validation mais des fichiers non suivis sont présents (utilisez "git add" pour les suivre)
$ git add images/
$ git status
Sur la branche main
Votre branche est à jour avec 'origin/main'.

Modifications qui seront validées :
  (utilisez "git restore --staged <fichier>..." pour désindexer)
	nouveau fichier : images/0001-Creation_d_un_compte_Github-0001.png
	nouveau fichier : images/0001-Creation_d_un_compte_Github-0002.png
	nouveau fichier : images/0001-Creation_d_un_compte_Github-0003.png
	nouveau fichier : images/0001-Creation_d_un_compte_Github-0004.png
	nouveau fichier : images/0001-Creation_d_un_compte_Github-0005.png
	nouveau fichier : images/0001-Creation_d_un_compte_Github-0006.png
	nouveau fichier : images/0001-Creation_d_un_compte_Github-0007.png
	nouveau fichier : images/0001-Creation_d_un_compte_Github-0008.png
	nouveau fichier : images/0001-Creation_d_un_compte_Github-0009.png
	nouveau fichier : images/0001-Creation_d_un_compte_Github-0010.png
$ git push
```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0004-Creation_du_repository_Git_local-0002.png)

<a href="#section0">Remonter</a>

--------------------

<h3 id="step5">V - Rédaction du fichier README dans Git [Dev]</h3>

Cliquer sur <i>Edit this file</i>.

[Guide Markdown](https://guides.github.com/features/mastering-markdown/)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0005-Redaction_du_fichier_README_dans_Git-0001.png)

<a href="#section0">Remonter</a>

--------------------

<h3 id="step6">VI - Sécurisation de la connection à Github [DevSec]</h3>

[Connecting to Github with SSH](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)

```
$ cd ~
$ ls -al .ssh/
total 8
drwx------  2 dkoenig dkoenig 4096 mai   14 20:54 .
drwxr-xr-x 18 dkoenig dkoenig 4096 mai   15 17:41 ..
```

```
$ ssh-keygen -t ed25519 -C "dkoenig.tutos@gmail.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/dkoenig/.ssh/id_ed25519): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/dkoenig/.ssh/id_ed25519
Your public key has been saved in /home/dkoenig/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:C+q9+TZqU08P+tMp8sSfOIkkkdfwEnV7QXVO+AvYK0U dkoenig.tutos@gmail.com
The key's randomart image is:
+--[ED25519 256]--+
|         .. ..oo+|
|        o  . E.+.|
|       . =  = ...|
|      o o o. =  .|
|      .oS.  . o .|
|     ...ooo. . . |
|    .  +.=o=..   |
|   . .o.*.*o+.   |
|    ..=*.=++o    |
+----[SHA256]-----+
$ ls -al .ssh/
total 16
drwx------  2 dkoenig dkoenig 4096 mai   16 09:37 .
drwxr-xr-x 18 dkoenig dkoenig 4096 mai   15 17:41 ..
-rw-------  1 dkoenig dkoenig  464 mai   16 09:37 id_ed25519
-rw-r--r--  1 dkoenig dkoenig  105 mai   16 09:37 id_ed25519.pub
$ eval "$(ssh-agent -s)"
Agent pid 114994
$ ssh-add ~/.ssh/id_ed25519
Enter passphrase for /home/dkoenig/.ssh/id_ed25519: 
Identity added: /home/dkoenig/.ssh/id_ed25519 (dkoenig.tutos@gmail.com)
```

```
$ sudo apt update
$ sudo apt install -y xclip
$ xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```

<a href="#section0">Remonter</a>

--------------------

<h3 id="step7">VII - Signature des commits [DevSec]</h3>

<a href="#section0">Remonter</a>

--------------------

<h3 id="step8">VIII - Installation de Visual Studio Code [Dev]</h3>

<a href="#section0">Remonter</a>

