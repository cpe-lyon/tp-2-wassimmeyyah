## Wassim MEYYAH - 3ICS



# Exercice 1. Variables d'environnement -

1 - La variable PATH indique à bash où trouver les commandes tapées par l'utilisateur

2 - La variable $HOME permet à la commande cd tapée sans argument de renvoyer vers le répertoire personnel

3 - $LANG affiche la langue du système, $PWD affiche le chemin vers le répertoire courant, $OLDPWD affiche le chemin vers le dernier répertoire et $SHELL affiche le type de shell utilisé, en l'occurence bash

4 - 
```bash
MY_VAR="CONTENU"
echo $MY_VAR
```

5 - La commande bash ouvre un "sous-terminal". Les variables locales créées plus tôt sous donc inaccessible depuis ce dernier.

6 - 
```bash
export MY_VAR="CONTENU"
bash
echo $MY_VAR
```
Cette fois, la variable d'environnement y est accessible

7 - 
```bash

export NOM="wassim meyyah" ; echo $NOM
```

8 - 
```bash
echo "Bonjour à vous $NOM"
```

9 - La commande unset supprime la variable elle même et non son contenu

10 -
```bash
echo '$HOME' "= $HOME"
```

Programmation Bash - 
```bash
nano ~/.bashrc
PATH:$PATH:~/script
```

# Exercice 2. Controle de mot de passe -

```bash
mdp = "password"

read -s -p "Saisissez le mot de passe : " input

if [ _$input == _$mdp ]; then 
    echo "Bon mot de passe !"
else 
    echo "Mauvais mot de passe ..."
fi
```

# Exercice 3. Expressions rationnelles -

```bash
function is_number()
{
    re='^[+-]?[0-9]+([.][0-9]+)?$'
    if ! [[ $1 =~ $re ]] ; then
        return 1
    else
        return 0
    fi
}
```

## 4 - Contrôle d'utilisateur

```bash


if [ $# == 0 ]
then
    echo "Utilisation : $0 username"
else 
    if [ -z $(getent passwd$1) ]
    then
        echo "L'utilisateur $1 n'existe pas"
    else
        echo "L'utilisateur $1 existe"
    fi
fi
```

## 5 - Factorielle

```bash

function fact()
{
    FACT=1
    for (( i=1; i<$1+1; i++ )) ; do
        FACT=$(( FACT * i ))
    done
echo "$FACT"
}

fact
```

## 6 - Le juste prix

```bash

prix=$(((RANDOM % 1000 + 1))
echo 'Entrez un nombre'
read reponse

while [ $reponse -ne $prix ]
do
    if [ $reponse -lt $prix ]; then 
        echo "C'est plus !"
    else
        echo "C'est moins !"
    fi
    read reponse
done

echo 'Gagné !'
```

## 7 - statistiques
```bash


function is_number() {
    re='^[+-]?[0-9]+([.][0-9]+)?$'
    if ! [[ $1 =~ $re ]] && [ $1 -ge -100 ] && [ $1 -le 100] ; then 
        return 1
        fi
    else
        return 0
    fi
}

function stats() {

    tab=()
    for (( i=1; i<$1+1; i++ )) ; do
        read -p "Entrez un nombre compris entre -100 et 100 : " nb
        is_number $nb
        if [[ "$?" -eq 0 ]] ; then
            tab+=("$nb")
        else
            echo "Valeur incorrecte"
        fi
    done

    max=${tab[0]}
    min=${tab[0]}
    moy=0
    somme=0
```
