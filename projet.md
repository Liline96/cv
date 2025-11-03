# Projet de développement

## Choix de projet 

Mon projet de développement consistera à une animation Javascript d'une forme qui suivra le curseur de la souris 
(https://animejs.com/documentation/animatable/)

## Étapes principales
### Objectifs
En dehors de l'objectif d'avoir une animation fonctionnelle qui suit le curseur, la forme devra :
- Changer de couleurs périodiquement 
- changer de forme après un click de souris 

### Conception 
La page commencera par un Html de base pour générer la page 
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>projet curseur ainime</title>
</head>
<body>
</body>
</html>
```
puis une div classe pour afficher le code 

Pour l'animation 
- importer le module animejs
- importer animate
- Modifier le paramètre de la couleur avec CSS et définir un temps en ms pour le changement
- Modifier le paramètre de la forme et définir une fonction pour changer la forme à chaque click

