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
$ if [ -r ~/.bash_profile ]; then echo 'export GPG_TTY=$(tty)' >> ~/.bash_profile; \
>   else echo 'export GPG_TTY=$(tty)' >> ~/.profile; fi
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
$ cd /mnt/data/github/devsecops
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

[Site officiel Visual Studio Code](https://code.visualstudio.com/)

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

