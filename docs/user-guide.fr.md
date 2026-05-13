# Tidy — Guide d'utilisation

> Tidy apprend votre façon de ranger vos fichiers et vous aide à les mettre à leur place.

---

## Qu'est-ce que Tidy ?

Tidy est un petit programme qui vit dans la barre de notification de votre
système. Il surveille votre dossier **Téléchargements**, et chaque fois que
vous déplacez manuellement un fichier en dehors de ce dossier, il retient où
vous l'avez rangé. Après quelques déplacements, il construit un modèle
personnalisé de *votre* façon d'organiser — et commence à suggérer une
destination pour les nouveaux fichiers.

Tidy ne lit jamais le contenu de vos fichiers. Il regarde uniquement les noms,
les extensions, la taille, et fait une détection de type basique. Tout
s'exécute localement, sur votre machine.

## Installation

### Windows

1. Téléchargez `Tidy-windows-x64.exe` depuis la
   [dernière version](https://github.com/fdevelopment-department-ai/tidy-releases/releases/latest).
2. Double-cliquez pour lancer. Windows SmartScreen peut afficher un
   avertissement (application non signée) — cliquez sur
   **Informations complémentaires → Exécuter quand même**.
3. Une petite icône **T** apparaît dans la zone de notification, près de
   l'horloge.

Pour lancer Tidy automatiquement avec Windows, placez un raccourci dans :

```
%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup
```

### macOS

1. Téléchargez `Tidy-macos.zip` depuis la dernière version.
2. Dézippez et déplacez `Tidy.app` dans `/Applications`.
3. Au premier lancement, macOS va bloquer l'application
   (« développeur non identifié »).
   Clic droit → **Ouvrir** → **Ouvrir quand même**.
4. Le **T** apparaît dans la barre de menus (en haut à droite de l'écran).

Pour lancer au démarrage : **Réglages système → Général →
Ouverture → +** et ajoutez `Tidy.app`.

### Linux

1. Téléchargez `Tidy-linux-x64`.
2. Rendez-le exécutable et placez-le dans votre `$PATH` :
   ```bash
   chmod +x Tidy-linux-x64
   mv Tidy-linux-x64 ~/.local/bin/tidy
   ```
3. Vérifiez que votre environnement de bureau supporte les icônes système.
   Sur GNOME, vous aurez probablement besoin de l'extension **AppIndicator
   and KStatusNotifierItem Support**.
4. Lancez `tidy` depuis un terminal ou votre lanceur d'applications.

## Premier lancement

La première fois que vous lancez Tidy :

- Il commence à surveiller `~/Téléchargements` (ou `~/Downloads`).
- Il ne fait **rien de visible** — aucune suggestion pour l'instant.
- Il enregistre silencieusement chaque fichier que vous déplacez en dehors
  du dossier surveillé.

Après environ **6 déplacements** manuels répartis sur **au moins
2 dossiers de destination différents**, Tidy entraîne son premier modèle en
arrière-plan. À partir de là, quand un nouveau fichier apparaît dans
Téléchargements, Tidy vérifie s'il reconnaît un motif familier ; s'il est
suffisamment confiant (> 65 %), il affiche une notification de bureau qui
vous suggère où ranger le fichier.

> **Vous gardez le contrôle.** Tidy en v0.1 ne fait que **suggérer**.
> Il ne déplace jamais de fichier à votre place.

## Le menu de la barre

Clic droit (ou clic) sur l'icône pour ouvrir le menu :

- **N exemples appris · actif/en pause** — état courant.
- **Mettre en pause / Reprendre** — bascule le surveillant.
- **Suggestions récentes** — les 5 dernières suggestions affichées, avec
  leur score de confiance.
- **Ouvrir le dossier de données** — où vivent le modèle et la base
  (voir ci-dessous).
- **À propos de Tidy** — ouvre le site.
- **Quitter** — arrête le démon.

## Où sont mes données ?

Tidy stocke tout localement :

- **Windows :** `%APPDATA%\Fdevelopment\Tidy\`
- **macOS :** `~/Library/Application Support/Tidy/`
- **Linux :** `~/.local/share/Tidy/`

Contenu :

- `tidy.db` — base SQLite avec les exemples d'apprentissage et les
  suggestions récentes.
- `model.joblib` — le modèle scikit-learn entraîné.
- `tidy.log` — fichier de log quotidien.

Pour réinitialiser complètement Tidy : quittez-le et supprimez ce dossier.

## Vie privée

Tidy fonctionne **entièrement hors-ligne**. Pas de télémétrie, pas
d'analytics, pas de backend cloud. Les seules connexions réseau que Tidy
peut faire sont quand vous cliquez explicitement sur « À propos » (qui
ouvre ce site dans votre navigateur).

## Dépannage

**Pas d'icône dans la barre sous Linux.** Votre environnement de bureau
n'expose pas de barre système par défaut. Installez l'extension
AppIndicator pour GNOME, ou utilisez un bureau qui le supporte
nativement (KDE, Cinnamon, MATE, XFCE).

**« Application non signée » sous macOS.** Clic droit → Ouvrir au premier
lancement ; macOS retiendra votre choix.

**Les suggestions sont fausses.** Tidy a besoin d'exemples pour apprendre.
Plus vous rangez de manière cohérente, mieux il devient. Si vous changez
d'avis sur une destination, déplacez quelques fichiers vers la nouvelle
destination — le modèle se rattrapera au prochain entraînement.

**Je veux repartir de zéro.** Quittez Tidy, supprimez le dossier de
données, relancez.

## Licence & contact

Tidy est un freeware — gratuit d'utilisation, redistribution restreinte.
Voir `LICENSE.txt` livré avec le binaire.
Pour les demandes commerciales : `contact@fdevelopment.fr`.
