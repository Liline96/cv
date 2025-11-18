# Projet de développement

## Choix de projet 

Mon projet de développement consistera à une animation Javascript d'une forme qui suivra le curseur de la souris 
(https://animejs.com/documentation/animatable/)

## Étapes principales
### Objectifs
En dehors de l'objectif d'avoir une animation fonctionnelle qui suit le curseur, la forme devra :
- Changer de couleurs périodiquement 
- changer de forme après un click de souris 

## Conception 18/11  
### Outils 
- Visual Studio Code
- JsBin 
- Gemini 2.5 Pro 

### Méthode de travail
- Expérimentation sur JsBin pour visualiser des codes
- Débogage sur Visual Studio Code 
- S'il y a un blocage utilisation demander à Gemini pour mieux comprendre le code, expliquer puis corriger si nécessaire.
https://gemini.google.com/share/c3b671215c15


### Réalisation 
- Lecture de la bibliographie de animejs
- Explication du fonctionnement de chaque code
- Essaie sur Jsbin du deuxième code (https://animejs.com/documentation/animatable) en prenant la base du 1er code (à partir de import).
- Tentative de création des 2 codes en 1
- Demande à Gemini d'expliquer chaque étape du code avec le prompt "explique comment fonctionne chaque étape de ce code"
- rédaction des const zone et poly manuellement 
- Modification du SVG manuellement
- utilisation d'un math random pour générer 6 chiffre pour code HEX
- random.color crée par Visual Studio Code

### Axe d'amélioration 
- Ajouter des commentaires plus clairs qui explique bien le code
- Modifier le SVG pour qu'il prenne soit toute la page, soit qu'il soit dans un rectangle avec une animation du polygone moins grand (résolution du conflit entre les pixels du polygone et les pixels du SVG soit création d'un id pour le SVG et formatage CSS dans <style> avec taille fixe en px ou vh/vw ).
- Créer un <background> qui change de couleur en fonction de la taille de la fenêtre dans <style> avec valeur px min et max



