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

