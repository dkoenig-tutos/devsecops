<h6 id="section0"></h6>

# DevSecOps - Cas pratique
## Architecture DevSecOps étape par étape

**Table des matières**
====================

<a href="#step1">I - Création d'un compte Github [Dev]</a><br/>
<a href="#step2">II - Création d'un repository dans Github [Dev]</a><br/>
<a href="#step3">III - Installation de Git [Dev]</a><br/>
<a href="#step4">IV - Création du repository Git local via HTTPS [Dev]</a><br/>
<a href="#step5">V - Rédaction du fichier README.md dans Git [Dev]</a><br/>
<a href="#step6">VI - Sécurisation de la connection à Github via SSH [DevSec]</a><br/>
<a href="#step7">VII - Signature des commits [DevSec]</a><br/>
<a href="#step8">VIII - Installation de Visual Studio Code [Dev]</a><br/>

--------------------

<h2 id="step1">I - Création d'un compte Github [Dev]</h2>

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

<h2 id="step2">II - Création d'un repository dans Github [Dev]</h2>

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0002-Creation_d_un_repository_dans_Github-0001.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0002-Creation_d_un_repository_dans_Github-0002.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0002-Creation_d_un_repository_dans_Github-0003.png)

<a href="#section0">Remonter</a>

--------------------

<h2 id="step3">III - Installation de Git [Dev]</h2>

[Procédure officielle d'installation](https://git-scm.com/download/linux)
[Repository des releases Git](https://github.com/git/git/releases)

Ouvrir un terminal.

### Installation de Git

```
$ sudo add-apt-repository -y ppa:git-core/ppa
$ sudo apt update
$ sudo apt install -y git
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

<h2 id="step4">IV - Création du repository Git local via HTTPS [Dev]</h2>

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0004-Creation_du_repository_Git_local-0001.png)

```
$ cd /mnt/data
$ mkdir github
$ cd github
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
$ git commit -m "Rédaction du fichier README dans Git"
[main cd35688] Rédaction du fichier README dans Git
 3 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 images/0005-Redaction_du_fichier_README_dans_Git-0001.png
 create mode 100644 images/0005-Redaction_du_fichier_README_dans_Git-0002.png
 create mode 100644 images/WAF.png
$ git status
Sur la branche main
Votre branche est en avance sur 'origin/main' de 1 commit.
  (utilisez "git push" pour publier vos commits locaux)

rien à valider, la copie de travail est propre
$ git push
Username for 'https://github.com': dkoenig-tutos
Password for 'https://dkoenig-tutos@github.com': 
Énumération des objets: 8, fait.
Décompte des objets: 100% (8/8), fait.
Compression par delta en utilisant jusqu'à 8 fils d'exécution
Compression des objets: 100% (6/6), fait.
Écriture des objets: 100% (6/6), 642.88 Kio | 17.86 Mio/s, fait.
Total 6 (delta 2), réutilisés 0 (delta 0), réutilisés du pack 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/dkoenig-tutos/devsecops.git
   0c4fdf2..cd35688  main -> main
```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0004-Creation_du_repository_Git_local-0002.png)

<a href="#section0">Remonter</a>

--------------------

<h2 id="step5">V - Rédaction du fichier README.md dans Git [Dev]</h2>

Cliquer sur <i>Edit this file</i>.

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0005-Redaction_du_fichier_README_dans_Git-0001.png)

[Guide Markdown](https://guides.github.com/features/mastering-markdown/)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0005-Redaction_du_fichier_README_dans_Git-0002.png)

<a href="#section0">Remonter</a>

--------------------

<h2 id="step6">VI - Sécurisation de la connection à Github via SSH [DevSec]</h2>

[Documentation officielle sur Github](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)

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
SHA256:uTEfjicF0fNoBAhXdxsV+6xjmNwK89UIOPem30ptJgM dkoenig.tutos@gmail.com
The key's randomart image is:
+--[ED25519 256]--+
|    ...o+o. o.o. |
|     ..  o+. o . |
|        .. +. .  |
|         oo..  o |
|        S.= E   o|
|         O = B = |
|        + * + & =|
|         o + B B |
|            +.o..|
+----[SHA256]-----+
$ ls -al .ssh/
total 16
drwx------  2 dkoenig dkoenig 4096 mai   17 21:06 .
drwxr-xr-x 18 dkoenig dkoenig 4096 mai   17 20:16 ..
-rw-------  1 dkoenig dkoenig  464 mai   17 21:06 id_ed25519
-rw-r--r--  1 dkoenig dkoenig  105 mai   17 21:06 id_ed25519.pub
$ eval "$(ssh-agent -s)"
Agent pid 229559
$ ssh-add ~/.ssh/id_ed25519
Enter passphrase for /home/dkoenig/.ssh/id_ed25519: 
Identity added: /home/dkoenig/.ssh/id_ed25519 (dkoenig.tutos@gmail.com)
```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0006-Securisation_de_la_connexion_a_Github_via_SSH-0001.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0006-Securisation_de_la_connexion_a_Github_via_SSH-0002.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0006-Securisation_de_la_connexion_a_Github_via_SSH-0003.png)

```
$ sudo apt update
$ sudo apt install -y xclip
$ xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0006-Securisation_de_la_connexion_a_Github_via_SSH-0004.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0006-Securisation_de_la_connexion_a_Github_via_SSH-0005.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0006-Securisation_de_la_connexion_a_Github_via_SSH-0006.png)

```
$ git status
Sur la branche main
Votre branche est à jour avec 'origin/main'.

rien à valider, la copie de travail est propre
$ cd ..
$ rm -rf devsecops
$ ssh -T git@github.com
The authenticity of host 'github.com (140.82.121.3)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com,140.82.121.3' (RSA) to the list of known hosts.
Hi dkoenig-tutos! You've successfully authenticated, but GitHub does not provide shell access.
```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0006-Securisation_de_la_connexion_a_Github_via_SSH-0007.png)

```

```

<a href="#section0">Remonter</a>

--------------------

<h2 id="step7">VII - Signature des commits [DevSec]</h2>

<a href="#section0">Remonter</a>

--------------------

<h2 id="step8">VIII - Installation de Visual Studio Code [Dev]</h2>

<a href="#section0">Remonter</a>

