# Version finale testprojet6
## Objectifs
- Implémenter des boutons pour enregistrer et lire les sons produits par Tone.js 
- ajouter un bouton pour un mode sombre et clair
- animer un texte avec anime.js 

## Outil
Visual Studio
JSbin
Gemini 3.0 mode raisonnement 

## Source 
- [Using On-Screen Buttons & Sliders to control Tone and P5](https://www.youtube.com/watch?v=kyJoJy2CpJc)
- [Sound triggering, FX and Recording with Tone.js: HTML/CSS/Javascript](https://www.youtube.com/watch?v=QklWIeZLZYY)
- [Anime.JS splittext](https://animejs.com/documentation/text/splittext/textsplitter-settings/lines)

## Réalisation 
- Modification manuelle pour l'animation du texte avec l'ajout dans import de "stagger, splitText" et des codes CSS et JS d'exemple avec des modifications pour que le code s'applique au texte ".instruction" 
- Modification de la taille du bouton à 120px de long

Prompt 
- "Vérifie que les modules stagger et splitText soient bien intégrés au code"
- "Ajoute un bouton qui permet de modifier l'arrière-plan avec un thème sombre ou clair sur le haut de l'écran"
- "Ajoute sur la gauche du bouton thème deux boutons pour enregistrer et lire les sons de Tone.js. Respecte le rythme de clic de la souris pour que les silences entre deux clics soient enregistrés aussi" 

## Flowchart
```mermaid
flowchart TD
    %% --- DÉBUT ---
    Start([Début du Programme]) --> Import["Imports :<br/>Anime.js & Tone.js"]
    Import --> InitDOM["Initialisation DOM :<br/>Sélection $zone, boutons, canvas"]
    
    InitDOM --> InitAudio["Setup Audio :<br/>Création Synthé & Oscillateur Silencieux<br/>Préparation MediaRecorder"]
    
    InitAudio --> InitAnim["Animation Auto :<br/>Découpage Texte 'SplitText'<br/>Lancement boucle 'Stagger'"]
    
    InitAnim --> CalcBounds["Calcul Initial :<br/>Limites de la zone 'bounds'"]
    
    CalcBounds --> Listeners["Action :<br/>Activation Écouteurs<br/>(Mouse, Click, Resize)"]
    
    Listeners --> Wait{EN ATTENTE<br/>D'ACTION}

    %% --- BRANCHE 1 : MOUVEMENT (Souris) ---
    Wait -- "Souris bouge" --> CalcPos["Calcul Math :<br/>Clamp X/Y & Rotation"]
    CalcPos --> MovePoly[/"Sortie Visuelle :<br/>Translation + Rotation du Groupe"/]
    MovePoly --> Wait

    %% --- BRANCHE 2 : INTERACTION (Clic Zone) ---
    Wait -- "Clic Zone SVG" --> StartTone["Action :<br/>Démarrer Tone.js Context"]
    
    %% Sous-branche Audio
    StartTone --> GenNote["Logique Audio :<br/>Calcul Note + Octave aléatoire"]
    GenNote --> PlaySynth[/"Sortie Sonore :<br/>Synth.triggerAttackRelease"/]
    
    %% Sous-branche Visuelle
    StartTone --> GenColor["Logique Visuelle :<br/>Couleur HSL & Points aléatoires"]
    GenColor --> Morph[/"Sortie Visuelle :<br/>Morphing Forme & Couleur"/]
    
    PlaySynth --> Wait
    Morph --> Wait

    %% --- BRANCHE 3 : THÈME (Dark/Light) ---
    Wait -- "Clic Bouton Thème" --> ToggleVar["Logique :<br/>Inversion booléen isDarkMode"]
    ToggleVar --> CheckMode{"Mode Sombre ?"}
    CheckMode -- OUI --> ApplyDark[/"Sortie :<br/>CSS Background Noir / Texte Blanc"/]
    CheckMode -- NON --> ApplyLight[/"Sortie :<br/>CSS Background Blanc / Texte Noir"/]
    ApplyDark --> Wait
    ApplyLight --> Wait

    %% --- BRANCHE 4 : ENREGISTREMENT ---
    Wait -- "Clic REC" --> CheckRec{"Enregistrement<br/>en cours ?"}
    CheckRec -- NON --> StartRec["Action :<br/>Recorder.start()"]
    StartRec --> UIrec[/"Sortie :<br/>Bouton devient 'Stop'"/]
    CheckRec -- OUI --> StopRec["Action :<br/>Recorder.stop()"]
    StopRec --> BlobRec["Traitement :<br/>Création Blob & URL Audio"]
    BlobRec --> EnablePlay[/"Sortie :<br/>Activer bouton PLAY"/]
    UIrec --> Wait
    EnablePlay --> Wait

    Wait -- "Clic PLAY" --> PlayAudio[/"Sortie :<br/>Lecture AudioURL"/]
    PlayAudio --> Wait

    %% --- BRANCHE 5 : MAINTENANCE ---
    Wait -- "Redimensionnement" --> Refresh["Calcul :<br/>Mise à jour variable 'bounds'"]
    Refresh --> Wait

    %% --- STYLES ---
    style Start fill:#212121,stroke:#fff,stroke-width:2px,color:#fff
    style Wait fill:#fff,stroke:#333,stroke-width:4px
    
    classDef init fill:#e3f2fd,stroke:#1565c0,stroke-width:2px;
    classDef audio fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px;
    classDef visuel fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px;
    classDef ui fill:#fff3e0,stroke:#e65100,stroke-width:2px;

    class Import,InitDOM,InitAnim,CalcBounds,Listeners init;
    class InitAudio,StartTone,GenNote,PlaySynth,StartRec,StopRec,BlobRec,PlayAudio audio;
    class CalcPos,MovePoly,GenColor,Morph visuel;
    class ToggleVar,ApplyDark,ApplyLight,UIrec,EnablePlay ui;
```

## Conclusion 
Mon objectif était de créer une animation avec les modules anime.js Animatable et MorpheTo, avec une animation qui change de couleur au hasard et une animation déclenchée au clic.
L'une des plus grandes difficultés a été de faire en sorte que l'animation de morpheTo ne rentre pas en conflit avec le calcul du mouvement du polygone avec la souris. La taille du SVG a aussi été un problème puisque le ratio d'écran impacte la taille du polygone et son déplacement. 
Ma version finale respecte bien plus le mouvement que je voulais et est bien plus fidèle à l'animation Animatable. 
