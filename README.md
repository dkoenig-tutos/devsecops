<h6 id="section0"></h6>

# DevSecOps - Cas pratique
## Architecture DevSecOps étape par étape

**Table des matières**
======================

****Préparation du poste de travail du développeur - Ubuntu Desktop 20.04****
-----------------------------------------------------------------------------

<a href="#step1">I - Création d'un compte Github [Dev]</a><br/>
<a href="#step2">II - Création d'un repository dans Github [Dev]</a><br/>
<a href="#step3">III - Installation de Git [Dev]</a><br/>
<a href="#step4">IV - Création du repository Git local via HTTPS [Dev]</a><br/>
<a href="#step5">V - Rédaction du fichier README.md dans Git [Dev]</a><br/>
<a href="#step6">VI - Sécurisation de la connection à Github via SSH [DevSec]</a><br/>
<a href="#step7">VII - Signature des commits via GPG [DevSec]</a><br/>
<a href="#step8">VIII - Installation de Visual Studio Code [Dev]</a><br/>
<a href="#step9">IX - Installation d'Oracle VM VirtualBox [Dev]</a><br/>
<a href="#step10">X - Installation de Vagrant [Dev]</a><br/>

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
```

```
$ git --version
git version 2.31.1
```

### Configuration de Git pour Github

```
$ git config --global user.name "dkoenig-tutos"
$ git config --global user.email dkoenig.tutos@gmail.com
```

```
$ git config --list --show-origin
file:/home/dkoenig/.gitconfig   user.name=dkoenig-tutos
file:/home/dkoenig/.gitconfig   user.email=dkoenig.tutos@gmail.com
```

<a href="#section0">Remonter</a>

--------------------

<h2 id="step4">IV - Création du repository Git local via HTTPS [Dev]</h2>

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0004-Creation_du_repository_Git_local-0001.png)

```
$ cd /media/dkoenig/DATA/
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
```

```
$ git add images/
```

```
$ git status
Sur la branche main
Votre branche est à jour avec 'origin/main'.

Modifications qui seront validées :
  (utilisez "git restore --staged <fichier>..." pour désindexer)
	nouveau fichier : images/0005-Redaction_du_fichier_README_dans_Git-0001.png
	nouveau fichier : images/0005-Redaction_du_fichier_README_dans_Git-0002.png
	nouveau fichier : images/WAF.png
```

```
$ git commit -m "Rédaction du fichier README dans Git"
[main cd35688] Rédaction du fichier README dans Git
 3 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 images/0005-Redaction_du_fichier_README_dans_Git-0001.png
 create mode 100644 images/0005-Redaction_du_fichier_README_dans_Git-0002.png
 create mode 100644 images/WAF.png
```

```
$ git status
Sur la branche main
Votre branche est en avance sur 'origin/main' de 1 commit.
  (utilisez "git push" pour publier vos commits locaux)

rien à valider, la copie de travail est propre
```

```
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
```

```
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
SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx dkoenig.tutos@gmail.com
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
```

```
$ ls -al .ssh/
total 16
drwx------  2 dkoenig dkoenig 4096 mai   17 21:06 .
drwxr-xr-x 18 dkoenig dkoenig 4096 mai   17 20:16 ..
-rw-------  1 dkoenig dkoenig  464 mai   17 21:06 id_ed25519
-rw-r--r--  1 dkoenig dkoenig  105 mai   17 21:06 id_ed25519.pub
```

```
$ eval "$(ssh-agent -s)"
Agent pid 229559
```

```
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
```

```
$ cd ..
$ rm -rf devsecops
```

```
$ ssh -T git@github.com
The authenticity of host 'github.com (140.82.121.3)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com,140.82.121.3' (RSA) to the list of known hosts.
Hi dkoenig-tutos! You've successfully authenticated, but GitHub does not provide shell access.
```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0006-Securisation_de_la_connexion_a_Github_via_SSH-0007.png)

```
$ git clone git@github.com:dkoenig-tutos/devsecops.git
Clonage dans 'devsecops'...
remote: Enumerating objects: 83, done.
remote: Counting objects: 100% (83/83), done.
remote: Compressing objects: 100% (79/79), done.
remote: Total 83 (delta 19), reused 34 (delta 3), pack-reused 0
Réception d'objets: 100% (83/83), 3.27 Mio | 1.34 Mio/s, fait.
Résolution des deltas: 100% (19/19), fait.
```

```
$ cd devsecops/
```

```
$ git status
Sur la branche main
Votre branche est à jour avec 'origin/main'.

Fichiers non suivis:
  (utilisez "git add <fichier>..." pour inclure dans ce qui sera validé)
	images/0006-Securisation_de_la_connexion_a_Github_via_SSH-0007.png

aucune modification ajoutée à la validation mais des fichiers non suivis sont présents (utilisez "git add" pour les suivre)
```

```
$ git add images/0006-Securisation_de_la_connexion_a_Github_via_SSH-0007.png
```

```
$ git commit -m "Test SSH"
[main ffd1a79] Test SSH
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 images/0006-Securisation_de_la_connexion_a_Github_via_SSH-0007.png
```
 
 ```
$ git push
Énumération des objets: 6, fait.
Décompte des objets: 100% (6/6), fait.
Compression par delta en utilisant jusqu'à 8 fils d'exécution
Compression des objets: 100% (4/4), fait.
Écriture des objets: 100% (4/4), 167.15 Kio | 1.31 Mio/s, fait.
Total 4 (delta 2), réutilisés 0 (delta 0), réutilisés du pack 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To github.com:dkoenig-tutos/devsecops.git
   232f276..ffd1a79  main -> main
```

Le dernier git push, sans identification, valide le fonctionnement.

<a href="#section0">Remonter</a>

--------------------

<h2 id="step7">VII - Signature des commits via GPG [DevSec]</h2>

[Documentation officielle sur Github](https://docs.github.com/en/github/authenticating-to-github/checking-for-existing-gpg-keys)

```
$ cd ~
```

```
$ gpg --version
gpg (GnuPG) 2.2.19
libgcrypt 1.8.5
Copyright (C) 2019 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Home: /home/dkoenig/.gnupg
Algorithmes pris en charge :
Clef publique : RSA, ELG, DSA, ECDH, ECDSA, EDDSA
Chiffrement : IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256,
              TWOFISH, CAMELLIA128, CAMELLIA192, CAMELLIA256
Hachage : SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression : Non compressé, ZIP, ZLIB, BZIP2
```

```
$ gpg --full-generate-key
gpg (GnuPG) 2.2.19; Copyright (C) 2019 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Sélectionnez le type de clef désiré :
   (1) RSA et RSA (par défaut)
   (2) DSA et Elgamal
   (3) DSA (signature seule)
   (4) RSA (signature seule)
  (14) Existing key from card
Quel est votre choix ? 
les clefs RSA peuvent faire une taille comprise entre 1024 et 4096 bits.
Quelle taille de clef désirez-vous ? (3072) 4096
La taille demandée est 4096 bits
Veuillez indiquer le temps pendant lequel cette clef devrait être valable.
         0 = la clef n'expire pas
      <n>  = la clef expire dans n jours
      <n>w = la clef expire dans n semaines
      <n>m = la clef expire dans n mois
      <n>y = la clef expire dans n ans
Pendant combien de temps la clef est-elle valable ? (0) 
La clef n'expire pas du tout
Est-ce correct ? (o/N) o

GnuPG doit construire une identité pour identifier la clef.

Nom réel : dkoenig-tutos
Adresse électronique : dkoenig.tutos@gmail.com
Commentaire : Github
Vous avez sélectionné cette identité :
    « dkoenig-tutos (Github) <dkoenig.tutos@gmail.com> »

Changer le (N)om, le (C)ommentaire, l'(A)dresse électronique
ou (O)ui/(Q)uitter ? O
De nombreux octets aléatoires doivent être générés. Vous devriez faire
autre chose (taper au clavier, déplacer la souris, utiliser les disques)
pendant la génération de nombres premiers ; cela donne au générateur de
nombres aléatoires une meilleure chance d'obtenir suffisamment d'entropie.
De nombreux octets aléatoires doivent être générés. Vous devriez faire
autre chose (taper au clavier, déplacer la souris, utiliser les disques)
pendant la génération de nombres premiers ; cela donne au générateur de
nombres aléatoires une meilleure chance d'obtenir suffisamment d'entropie.
gpg: clef XXXXXXXXXXXXXXXX marquée de confiance ultime.
gpg: revocation certificate stored as '/home/dkoenig/.gnupg/openpgp-revocs.d/5E66455BD2F21F0D3713B3C783D5178EFBB83FDE.rev'
les clefs publique et secrète ont été créées et signées.

pub   rsa4096 2021-05-17 [SC]
      5E66455BD2F21F0D3713B3C783D5178EFBB83FDE
uid                      dkoenig-tutos (Github) <dkoenig.tutos@gmail.com>
sub   rsa4096 2021-05-17 [E]
```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0007-Signature_des_commits_via_GPG-0001.png)

```
$ gpg --list-secret-keys --keyid-format LONG
gpg: vérification de la base de confiance
gpg: marginals needed: 3  completes needed: 1  trust model: pgp
gpg: profondeur : 0  valables :   1  signées :   0
     confiance : 0 i., 0 n.d., 0 j., 0 m., 0 t., 1 u.
/home/dkoenig/.gnupg/pubring.kbx
--------------------------------
sec   rsa4096/XXXXXXXXXXXXXXXX 2021-05-17 [SC]
      5E66455BD2F21F0D3713B3C783D5178EFBB83FDE
uid                [  ultime ] dkoenig-tutos (Github) <dkoenig.tutos@gmail.com>
ssb   rsa4096/CEC8AECEA2297EC3 2021-05-17 [E]

```

```
$ gpg --armor --export XXXXXXXXXXXXXXXX
-----BEGIN PGP PUBLIC KEY BLOCK-----

****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************************************************************
****************
*****
-----END PGP PUBLIC KEY BLOCK-----
```

```
$ git config --global user.signingkey XXXXXXXXXXXXXXXX
```

```
$ if [ -r ~/.bash_profile ]; then echo 'export GPG_TTY=$(tty)' >> ~/.bash_profile; else echo 'export GPG_TTY=$(tty)' >> ~/.profile; fi
```

```
$ sudo nano ~/.profile 
$ source ~/.profile
```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0007-Signature_des_commits_via_GPG-0002.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0007-Signature_des_commits_via_GPG-0003.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0007-Signature_des_commits_via_GPG-0004.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0007-Signature_des_commits_via_GPG-0005.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0007-Signature_des_commits_via_GPG-0006.png)

```
$ cd /media/dkoenig/DATA/github/devsecops/
$ git pull
remote: Enumerating objects: 8, done.
remote: Counting objects: 100% (8/8), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 6 (delta 2), reused 0 (delta 0), pack-reused 0
Dépaquetage des objets: 100% (6/6), 4.04 Kio | 2.02 Mio/s, fait.
Depuis github.com:dkoenig-tutos/devsecops
   a24d7b0..6fc9368  main       -> origin/main
Mise à jour a24d7b0..6fc9368
Fast-forward
 README.md | 82 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 1 file changed, 82 insertions(+)
```

```
$ git status
Sur la branche main
Votre branche est à jour avec 'origin/main'.

Fichiers non suivis:
  (utilisez "git add <fichier>..." pour inclure dans ce qui sera validé)
	images/0007-Signature_des_commits_via_GPG-0002.png
	images/0007-Signature_des_commits_via_GPG-0003.png
	images/0007-Signature_des_commits_via_GPG-0004.png
	images/0007-Signature_des_commits_via_GPG-0005.png
	images/0007-Signature_des_commits_via_GPG-0006.png

aucune modification ajoutée à la validation mais des fichiers non suivis sont présents (utilisez "git add" pour les suivre)
```

```
$ git add *
```

```
$ git commit -S -m "Test de la signature GPG"
```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0007-Signature_des_commits_via_GPG-0007.png)

```
[main 1a88cac] Test de la signature GPG
 5 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 images/0007-Signature_des_commits_via_GPG-0002.png
 create mode 100644 images/0007-Signature_des_commits_via_GPG-0003.png
 create mode 100644 images/0007-Signature_des_commits_via_GPG-0004.png
 create mode 100644 images/0007-Signature_des_commits_via_GPG-0005.png
 create mode 100644 images/0007-Signature_des_commits_via_GPG-0006.png
```

```
$ git push
Énumération des objets: 10, fait.
Décompte des objets: 100% (10/10), fait.
Compression par delta en utilisant jusqu'à 8 fils d'exécution
Compression des objets: 100% (8/8), fait.
Écriture des objets: 100% (8/8), 649.12 Kio | 3.20 Mio/s, fait.
Total 8 (delta 2), réutilisés 0 (delta 0), réutilisés du pack 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To github.com:dkoenig-tutos/devsecops.git
   6fc9368..1a88cac  main -> main
```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0007-Signature_des_commits_via_GPG-0008.png)

[Documentation pour la signature des tags](https://docs.github.com/en/github/authenticating-to-github/signing-tags)

<a href="#section0">Remonter</a>

--------------------

<h2 id="step8">VIII - Installation de Visual Studio Code [Dev]</h2>

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0008-Installation_de_Visual_Studio_Code-0001.png)

[Site officiel de Visual Studio Code](https://code.visualstudio.com/)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0008-Installation_de_Visual_Studio_Code-0002.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0008-Installation_de_Visual_Studio_Code-0003.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0008-Installation_de_Visual_Studio_Code-0004.png)

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0008-Installation_de_Visual_Studio_Code-0005.png)

```
$ cd /tmp
$ wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
$ sudo install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
$ sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
$ rm -f packages.microsoft.gpg
$ sudo apt install apt-transport-https
$ sudo apt update
$ sudo apt install code
```

```
$ code --version
1.56.2
054a9295330880ed74ceaedda236253b4f39a335
x64
```

```
$ code
```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0008-Installation_de_Visual_Studio_Code-0006.png)

<a href="#section0">Remonter</a>

--------------------

<h2 id="step9">IX - Installation d'Oracle VM VirtualBox [Dev]</h2>

[Site officiel d'Oracle VM VirtualBox](https://www.virtualbox.org/)

[Installation de VirtualBox](https://computingforgeeks.com/install-virtualbox-6-on-ubuntu-debian-linux/)

```
$ sudo apt update
$ sudo apt -y upgrade
$ sudo reboot
```

```
$ wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
$ wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
$ echo "deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian eoan contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
$ sudo apt update
$ sudo apt-get install -y linux-headers-$(uname -r) dkms
$ sudo apt-get install -y virtualbox-6.1
$ sudo /sbin/vboxconfig
$ wget https://download.virtualbox.org/virtualbox/6.1.6/Oracle_VM_VirtualBox_Extension_Pack-6.1.6.vbox-extpack

```

![image](https://raw.githubusercontent.com/dkoenig-tutos/devsecops/main/images/0009-Installation_d_Oracle_VM_Virtual_Box-0001.png)

<a href="#section0">Remonter</a>

--------------------

<h2 id="step10">X - Installation de Vagrant [Dev]</h2>

[Site officiel de Hashicorp Vagrant](https://www.vagrantup.com/)

[Documentation d'installation](https://www.vagrantup.com/downloads)

```
$ cd /tmp
$ sudo apt-get install -y curl
$ curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
$ sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
$ sudo apt-get update && sudo apt-get install -y vagrant
```

```
$ vagrant --version
Vagrant 2.2.16
```

<a href="#section0">Remonter</a>

--------------------

<h2 id="step10">X - Installation de Vagrant [Dev]</h2>

```
2021-05-26 18:56:07+02:00
Bringing machine 'nfsserver.sample.com' up with 'virtualbox' provider...
Bringing machine 'nfsclient.sample.com' up with 'virtualbox' provider...
Bringing machine 'docker.sample.com' up with 'virtualbox' provider...
Bringing machine 'jenkins.sample.com' up with 'virtualbox' provider...
Bringing machine 'gitlab.sample.com' up with 'virtualbox' provider...
Bringing machine 'ansible.sample.com' up with 'virtualbox' provider...
==> nfsserver.sample.com: Box 'ubuntu/focal64' could not be found. Attempting to find and install...
    nfsserver.sample.com: Box Provider: virtualbox
    nfsserver.sample.com: Box Version: 20210518.0.0
==> nfsserver.sample.com: Loading metadata for box 'ubuntu/focal64'
    nfsserver.sample.com: URL: https://vagrantcloud.com/ubuntu/focal64
==> nfsserver.sample.com: Adding box 'ubuntu/focal64' (v20210518.0.0) for provider: virtualbox
    nfsserver.sample.com: Downloading: https://vagrantcloud.com/ubuntu/boxes/focal64/versions/20210518.0.0/providers/virtualbox.box
Download redirected to host: cloud-images.ubuntu.com
==> nfsserver.sample.com: Successfully added box 'ubuntu/focal64' (v20210518.0.0) for 'virtualbox'!
==> nfsserver.sample.com: Importing base box 'ubuntu/focal64'...
==> nfsserver.sample.com: Matching MAC address for NAT networking...
==> nfsserver.sample.com: Checking if box 'ubuntu/focal64' version '20210518.0.0' is up to date...
==> nfsserver.sample.com: Setting the name of the VM: nfsserver.sample.com
==> nfsserver.sample.com: Clearing any previously set network interfaces...
==> nfsserver.sample.com: Preparing network interfaces based on configuration...
    nfsserver.sample.com: Adapter 1: nat
    nfsserver.sample.com: Adapter 2: hostonly
==> nfsserver.sample.com: Forwarding ports...
    nfsserver.sample.com: 22 (guest) => 2222 (host) (adapter 1)
==> nfsserver.sample.com: Running 'pre-boot' VM customizations...
==> nfsserver.sample.com: Booting VM...
==> nfsserver.sample.com: Waiting for machine to boot. This may take a few minutes...
    nfsserver.sample.com: SSH address: 127.0.0.1:2222
    nfsserver.sample.com: SSH username: vagrant
    nfsserver.sample.com: SSH auth method: private key
    nfsserver.sample.com: Warning: Connection reset. Retrying...
    nfsserver.sample.com: Warning: Remote connection disconnect. Retrying...
    nfsserver.sample.com: 
    nfsserver.sample.com: Vagrant insecure key detected. Vagrant will automatically replace
    nfsserver.sample.com: this with a newly generated keypair for better security.
    nfsserver.sample.com: 
    nfsserver.sample.com: Inserting generated public key within guest...
    nfsserver.sample.com: Removing insecure key from the guest if it's present...
    nfsserver.sample.com: Key inserted! Disconnecting and reconnecting using new SSH key...
==> nfsserver.sample.com: Machine booted and ready!
==> nfsserver.sample.com: Checking for guest additions in VM...
==> nfsserver.sample.com: Setting hostname...
==> nfsserver.sample.com: Configuring and enabling network interfaces...
==> nfsserver.sample.com: Mounting shared folders...
    nfsserver.sample.com: /vagrant => /opt/infra-ansible
==> nfsserver.sample.com: Detected mount owner ID within mount options. (uid: 1000 guestpath: /vagrant)
==> nfsserver.sample.com: Detected mount group ID within mount options. (gid: 1000 guestpath: /vagrant)
==> nfsclient.sample.com: Box 'ubuntu/focal64' could not be found. Attempting to find and install...
    nfsclient.sample.com: Box Provider: virtualbox
    nfsclient.sample.com: Box Version: 20210518.0.0
==> nfsclient.sample.com: Loading metadata for box 'ubuntu/focal64'
    nfsclient.sample.com: URL: https://vagrantcloud.com/ubuntu/focal64
==> nfsclient.sample.com: Adding box 'ubuntu/focal64' (v20210518.0.0) for provider: virtualbox
==> nfsclient.sample.com: Importing base box 'ubuntu/focal64'...
==> nfsclient.sample.com: Matching MAC address for NAT networking...
==> nfsclient.sample.com: Checking if box 'ubuntu/focal64' version '20210518.0.0' is up to date...
==> nfsclient.sample.com: Setting the name of the VM: nfsclient.sample.com
==> nfsclient.sample.com: Fixed port collision for 22 => 2222. Now on port 2200.
==> nfsclient.sample.com: Clearing any previously set network interfaces...
==> nfsclient.sample.com: Preparing network interfaces based on configuration...
    nfsclient.sample.com: Adapter 1: nat
    nfsclient.sample.com: Adapter 2: hostonly
==> nfsclient.sample.com: Forwarding ports...
    nfsclient.sample.com: 22 (guest) => 2200 (host) (adapter 1)
==> nfsclient.sample.com: Running 'pre-boot' VM customizations...
==> nfsclient.sample.com: Booting VM...
==> nfsclient.sample.com: Waiting for machine to boot. This may take a few minutes...
    nfsclient.sample.com: SSH address: 127.0.0.1:2200
    nfsclient.sample.com: SSH username: vagrant
    nfsclient.sample.com: SSH auth method: private key
    nfsclient.sample.com: Warning: Connection reset. Retrying...
    nfsclient.sample.com: Warning: Remote connection disconnect. Retrying...
    nfsclient.sample.com: 
    nfsclient.sample.com: Vagrant insecure key detected. Vagrant will automatically replace
    nfsclient.sample.com: this with a newly generated keypair for better security.
    nfsclient.sample.com: 
    nfsclient.sample.com: Inserting generated public key within guest...
    nfsclient.sample.com: Removing insecure key from the guest if it's present...
    nfsclient.sample.com: Key inserted! Disconnecting and reconnecting using new SSH key...
==> nfsclient.sample.com: Machine booted and ready!
==> nfsclient.sample.com: Checking for guest additions in VM...
==> nfsclient.sample.com: Setting hostname...
==> nfsclient.sample.com: Configuring and enabling network interfaces...
==> nfsclient.sample.com: Mounting shared folders...
    nfsclient.sample.com: /vagrant => /opt/infra-ansible
==> nfsclient.sample.com: Detected mount owner ID within mount options. (uid: 1000 guestpath: /vagrant)
==> nfsclient.sample.com: Detected mount group ID within mount options. (gid: 1000 guestpath: /vagrant)
==> nfsclient.sample.com: Detected mount owner ID within mount options. (uid: 1000 guestpath: /vagrant)
==> nfsclient.sample.com: Detected mount group ID within mount options. (gid: 1000 guestpath: /vagrant)
==> docker.sample.com: Box 'ubuntu/focal64' could not be found. Attempting to find and install...
    docker.sample.com: Box Provider: virtualbox
    docker.sample.com: Box Version: 20210518.0.0
==> docker.sample.com: Loading metadata for box 'ubuntu/focal64'
    docker.sample.com: URL: https://vagrantcloud.com/ubuntu/focal64
==> docker.sample.com: Adding box 'ubuntu/focal64' (v20210518.0.0) for provider: virtualbox
==> docker.sample.com: Importing base box 'ubuntu/focal64'...
==> docker.sample.com: Matching MAC address for NAT networking...
==> docker.sample.com: Checking if box 'ubuntu/focal64' version '20210518.0.0' is up to date...
==> docker.sample.com: Setting the name of the VM: docker.sample.com
==> docker.sample.com: Fixed port collision for 22 => 2222. Now on port 2201.
==> docker.sample.com: Clearing any previously set network interfaces...
==> docker.sample.com: Preparing network interfaces based on configuration...
    docker.sample.com: Adapter 1: nat
    docker.sample.com: Adapter 2: hostonly
==> docker.sample.com: Forwarding ports...
    docker.sample.com: 22 (guest) => 2201 (host) (adapter 1)
==> docker.sample.com: Running 'pre-boot' VM customizations...
==> docker.sample.com: Booting VM...
==> docker.sample.com: Waiting for machine to boot. This may take a few minutes...
    docker.sample.com: SSH address: 127.0.0.1:2201
    docker.sample.com: SSH username: vagrant
    docker.sample.com: SSH auth method: private key
    docker.sample.com: Warning: Connection reset. Retrying...
    docker.sample.com: Warning: Remote connection disconnect. Retrying...
    docker.sample.com: 
    docker.sample.com: Vagrant insecure key detected. Vagrant will automatically replace
    docker.sample.com: this with a newly generated keypair for better security.
    docker.sample.com: 
    docker.sample.com: Inserting generated public key within guest...
    docker.sample.com: Removing insecure key from the guest if it's present...
    docker.sample.com: Key inserted! Disconnecting and reconnecting using new SSH key...
==> docker.sample.com: Machine booted and ready!
==> docker.sample.com: Checking for guest additions in VM...
==> docker.sample.com: Setting hostname...
==> docker.sample.com: Configuring and enabling network interfaces...
==> docker.sample.com: Mounting shared folders...
    docker.sample.com: /vagrant => /opt/infra-ansible
==> docker.sample.com: Detected mount owner ID within mount options. (uid: 1000 guestpath: /vagrant)
==> docker.sample.com: Detected mount group ID within mount options. (gid: 1000 guestpath: /vagrant)
==> docker.sample.com: Detected mount owner ID within mount options. (uid: 1000 guestpath: /vagrant)
==> docker.sample.com: Detected mount group ID within mount options. (gid: 1000 guestpath: /vagrant)
==> jenkins.sample.com: Box 'ubuntu/focal64' could not be found. Attempting to find and install...
    jenkins.sample.com: Box Provider: virtualbox
    jenkins.sample.com: Box Version: 20210518.0.0
==> jenkins.sample.com: Loading metadata for box 'ubuntu/focal64'
    jenkins.sample.com: URL: https://vagrantcloud.com/ubuntu/focal64
==> jenkins.sample.com: Adding box 'ubuntu/focal64' (v20210518.0.0) for provider: virtualbox
==> jenkins.sample.com: Importing base box 'ubuntu/focal64'...
==> jenkins.sample.com: Matching MAC address for NAT networking...
==> jenkins.sample.com: Checking if box 'ubuntu/focal64' version '20210518.0.0' is up to date...
==> jenkins.sample.com: Setting the name of the VM: jenkins.sample.com
==> jenkins.sample.com: Fixed port collision for 22 => 2222. Now on port 2202.
==> jenkins.sample.com: Clearing any previously set network interfaces...
==> jenkins.sample.com: Preparing network interfaces based on configuration...
    jenkins.sample.com: Adapter 1: nat
    jenkins.sample.com: Adapter 2: hostonly
==> jenkins.sample.com: Forwarding ports...
    jenkins.sample.com: 22 (guest) => 2202 (host) (adapter 1)
==> jenkins.sample.com: Running 'pre-boot' VM customizations...
==> jenkins.sample.com: Booting VM...
==> jenkins.sample.com: Waiting for machine to boot. This may take a few minutes...
    jenkins.sample.com: SSH address: 127.0.0.1:2202
    jenkins.sample.com: SSH username: vagrant
    jenkins.sample.com: SSH auth method: private key
    jenkins.sample.com: Warning: Connection reset. Retrying...
    jenkins.sample.com: Warning: Remote connection disconnect. Retrying...
    jenkins.sample.com: 
    jenkins.sample.com: Vagrant insecure key detected. Vagrant will automatically replace
    jenkins.sample.com: this with a newly generated keypair for better security.
    jenkins.sample.com: 
    jenkins.sample.com: Inserting generated public key within guest...
    jenkins.sample.com: Removing insecure key from the guest if it's present...
    jenkins.sample.com: Key inserted! Disconnecting and reconnecting using new SSH key...
==> jenkins.sample.com: Machine booted and ready!
==> jenkins.sample.com: Checking for guest additions in VM...
==> jenkins.sample.com: Setting hostname...
==> jenkins.sample.com: Configuring and enabling network interfaces...
==> jenkins.sample.com: Mounting shared folders...
    jenkins.sample.com: /vagrant => /opt/infra-ansible
==> jenkins.sample.com: Detected mount owner ID within mount options. (uid: 1000 guestpath: /vagrant)
==> jenkins.sample.com: Detected mount group ID within mount options. (gid: 1000 guestpath: /vagrant)
==> jenkins.sample.com: Detected mount owner ID within mount options. (uid: 1000 guestpath: /vagrant)
==> jenkins.sample.com: Detected mount group ID within mount options. (gid: 1000 guestpath: /vagrant)
==> gitlab.sample.com: Box 'ubuntu/focal64' could not be found. Attempting to find and install...
    gitlab.sample.com: Box Provider: virtualbox
    gitlab.sample.com: Box Version: 20210518.0.0
==> gitlab.sample.com: Loading metadata for box 'ubuntu/focal64'
    gitlab.sample.com: URL: https://vagrantcloud.com/ubuntu/focal64
==> gitlab.sample.com: Adding box 'ubuntu/focal64' (v20210518.0.0) for provider: virtualbox
==> gitlab.sample.com: Importing base box 'ubuntu/focal64'...
==> gitlab.sample.com: Matching MAC address for NAT networking...
==> gitlab.sample.com: Checking if box 'ubuntu/focal64' version '20210518.0.0' is up to date...
==> gitlab.sample.com: Setting the name of the VM: gitlab.sample.com
==> gitlab.sample.com: Fixed port collision for 22 => 2222. Now on port 2203.
==> gitlab.sample.com: Clearing any previously set network interfaces...
==> gitlab.sample.com: Preparing network interfaces based on configuration...
    gitlab.sample.com: Adapter 1: nat
    gitlab.sample.com: Adapter 2: hostonly
==> gitlab.sample.com: Forwarding ports...
    gitlab.sample.com: 22 (guest) => 2203 (host) (adapter 1)
==> gitlab.sample.com: Running 'pre-boot' VM customizations...
==> gitlab.sample.com: Booting VM...
==> gitlab.sample.com: Waiting for machine to boot. This may take a few minutes...
    gitlab.sample.com: SSH address: 127.0.0.1:2203
    gitlab.sample.com: SSH username: vagrant
    gitlab.sample.com: SSH auth method: private key
    gitlab.sample.com: Warning: Connection reset. Retrying...
    gitlab.sample.com: Warning: Remote connection disconnect. Retrying...
    gitlab.sample.com: 
    gitlab.sample.com: Vagrant insecure key detected. Vagrant will automatically replace
    gitlab.sample.com: this with a newly generated keypair for better security.
    gitlab.sample.com: 
    gitlab.sample.com: Inserting generated public key within guest...
    gitlab.sample.com: Removing insecure key from the guest if it's present...
    gitlab.sample.com: Key inserted! Disconnecting and reconnecting using new SSH key...
==> gitlab.sample.com: Machine booted and ready!
==> gitlab.sample.com: Checking for guest additions in VM...
==> gitlab.sample.com: Setting hostname...
==> gitlab.sample.com: Configuring and enabling network interfaces...
==> gitlab.sample.com: Mounting shared folders...
    gitlab.sample.com: /vagrant => /opt/infra-ansible
==> gitlab.sample.com: Detected mount owner ID within mount options. (uid: 1000 guestpath: /vagrant)
==> gitlab.sample.com: Detected mount group ID within mount options. (gid: 1000 guestpath: /vagrant)
==> gitlab.sample.com: Detected mount owner ID within mount options. (uid: 1000 guestpath: /vagrant)
==> gitlab.sample.com: Detected mount group ID within mount options. (gid: 1000 guestpath: /vagrant)
==> ansible.sample.com: Box 'ubuntu/focal64' could not be found. Attempting to find and install...
    ansible.sample.com: Box Provider: virtualbox
    ansible.sample.com: Box Version: 20210518.0.0
==> ansible.sample.com: Loading metadata for box 'ubuntu/focal64'
    ansible.sample.com: URL: https://vagrantcloud.com/ubuntu/focal64
==> ansible.sample.com: Adding box 'ubuntu/focal64' (v20210518.0.0) for provider: virtualbox
==> ansible.sample.com: Importing base box 'ubuntu/focal64'...
==> ansible.sample.com: Matching MAC address for NAT networking...
==> ansible.sample.com: Checking if box 'ubuntu/focal64' version '20210518.0.0' is up to date...
==> ansible.sample.com: Setting the name of the VM: ansible.sample.com
==> ansible.sample.com: Fixed port collision for 22 => 2222. Now on port 2204.
==> ansible.sample.com: Clearing any previously set network interfaces...
==> ansible.sample.com: Preparing network interfaces based on configuration...
    ansible.sample.com: Adapter 1: nat
    ansible.sample.com: Adapter 2: hostonly
==> ansible.sample.com: Forwarding ports...
    ansible.sample.com: 22 (guest) => 2204 (host) (adapter 1)
==> ansible.sample.com: Running 'pre-boot' VM customizations...
==> ansible.sample.com: Booting VM...
==> ansible.sample.com: Waiting for machine to boot. This may take a few minutes...
    ansible.sample.com: SSH address: 127.0.0.1:2204
    ansible.sample.com: SSH username: vagrant
    ansible.sample.com: SSH auth method: private key
    ansible.sample.com: Warning: Connection reset. Retrying...
    ansible.sample.com: Warning: Remote connection disconnect. Retrying...
    ansible.sample.com: 
    ansible.sample.com: Vagrant insecure key detected. Vagrant will automatically replace
    ansible.sample.com: this with a newly generated keypair for better security.
    ansible.sample.com: 
    ansible.sample.com: Inserting generated public key within guest...
    ansible.sample.com: Removing insecure key from the guest if it's present...
    ansible.sample.com: Key inserted! Disconnecting and reconnecting using new SSH key...
==> ansible.sample.com: Machine booted and ready!
==> ansible.sample.com: Checking for guest additions in VM...
==> ansible.sample.com: Setting hostname...
==> ansible.sample.com: Configuring and enabling network interfaces...
==> ansible.sample.com: Mounting shared folders...
    ansible.sample.com: /vagrant => /opt/infra-ansible
==> ansible.sample.com: Detected mount owner ID within mount options. (uid: 1000 guestpath: /vagrant)
==> ansible.sample.com: Detected mount group ID within mount options. (gid: 1000 guestpath: /vagrant)
==> ansible.sample.com: Detected mount owner ID within mount options. (uid: 1000 guestpath: /vagrant)
==> ansible.sample.com: Detected mount group ID within mount options. (gid: 1000 guestpath: /vagrant)
2021-05-26 19:06:57+02:00
```

<a href="#section0">Remonter</a>
