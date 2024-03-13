
[File encryption using OpenSSL](https://gist.github.com/dreikanter/c7e85598664901afae03fedff308736b/raw/00c61d96fa58a4d4f32c601682090966d399fd54/encrypt_openssl.md)

## Symmetic encryption

For symmetic encryption, you can use the following:

To encrypt:

```
openssl aes-256-cbc -salt -a -e -in plaintext.txt -out encrypted.txt
```

To decrypt:

```
openssl aes-256-cbc -salt -a -d -in encrypted.txt -out plaintext.txt
```

More information :
https://community.jaguar-network.com/chiffrer-vos-fichiers-avec-openssl-sous-linux/#:~:text=Pour%20chiffrer%20un%20fichier%2C%20nous,qu'on%20effectue%20un%20chiffrement.
## Installer OpenSSL

Il est possible que **OpenSSL** ne soit pas présent sur votre système, on l’installe via la commande :

apt-get install openssh-client
apt-get install openssh-server

Le nombre d’algorithme étant important, la liste est consultable pour faire votre choix :

openssl enc help

Nous poursuivrons avec l’algorithme **-aes-256-cbc** par la suite qui est l’algorithme actuel le plus performant en terme de sécurité et rapidité.

---

## Chiffrage avec OpenSSL

Pour chiffrer un fichier, nous devons simplement adapter la commande suivante :

openssl enc -e -aes-256-cbc -in fichier -out fichier_secret
enter aes-256-cbc encryption password:
Verifying - enter aes-256-cbc encryption password:

-e -aes-256-cbc Paramètre pour spécifier à OpenSSL qu’on effectue un chiffrement.

-e Paramètre indiquant le chiffrage de fichier.

-aes-256-cbc Algorithme de chiffrement choisi.

-in fichier Fichier d’entré pour le chiffrage.

-out fichier Fichier de sortie chiffré.

On consulte le résultat :

cat fichier.txt
Contenu non chiffré

cat fichier_secret.txt
Salted__A��r�bNj~B�\��vJF�"���=w����oUk19�

Le mot de passe peut également être saisi directement par la commande suivante mais il sera accessible à qui accèdera à vos commandes, nous vous conseillons donc de l’éviter :

openssl enc -e -aes-256-cbc -in fichier -out fichier_secret -pass pass: V0trEm0tdepass3

---

## Déchiffrage OpenSSL

Pour déchiffrer un fichier, nous inversons les 2 fichiers et le paramètre d’action **-e** à **-d** :

openssl enc -e -aes-256-cbc -in fichier_secret -out nouveau_fichier

-d -aes-256-cbc Paramètre pour spécifier à OpenSSL qu’on effectue un chiffrement.

-d Paramètre indiquant le déchiffrage de fichier.

-aes-256-cbc Algorithme de chiffrement choisi.

-in fichier Fichier d’entré pour le chiffrage.

-out fichier Fichier de sortie chiffré.

On consulte le résultat :

cat fichier_secret.txt
Salted__A��r�bNj~B�\��vJF�"���=w����oUk19�

cat nouveau_fichier.txt
Contenu non chiffré
