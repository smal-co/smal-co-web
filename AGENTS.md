# SMAL & CO : règles de modification du site

Site statique (HTML/CSS/JS). Le code est sur GitHub (`smal-co/smal-co-web`). La branche `main` est la PRODUCTION : tout ce qui y arrive est en ligne sur Cloudflare Pages en 1 à 2 minutes.
Ces règles s'adressent à tout assistant IA qui travaille dans ce dossier. La personne qui te parle n'est PAS développeuse : explique tout en français simple, sans jargon.

## 0. Au démarrage
- Demande : « Qui es-tu ? » (prénom) et « Que veux-tu modifier ? ».
- Lance `git pull` puis `git status`. Si le dossier n'est pas propre, préviens la personne et arrête-toi.

## 1. Interdits absolus
- Ne JAMAIS commiter ni pousser directement sur `main`. Aucun `git push --force`. Passe toujours par une branche et une pull request.
- Ne JAMAIS publier sans le « OUI » explicite de la personne (voir §4). « ok », « vas-y », un pouce ou un silence ne suffisent pas : il faut « oui, publie ».
- Ne JAMAIS toucher sans demander à : `_headers`, `.github/`, `robots.txt`, `sitemap.xml`, `AGENTS.md`, `CLAUDE.md`, les balises `canonical`, `og:*`, `twitter:*` et `robots` dans le `<head>`.
- Ne JAMAIS supprimer de fichier, ni renommer ou déplacer un dossier (`team/`, `img/`, `logos/`, `assets/`).
- Ne JAMAIS écrire de mot de passe, jeton, clé ou identifiant dans un fichier, un commit ou une réponse.
- Ne JAMAIS modifier les réglages du compte GitHub ou de Cloudflare.

## 2. Travailler sur une branche
- Crée une branche : `modif/<prenom>-<sujet-court>-<AAAAMMJJ>` (ex. `modif/lucas-age-bureau-20261122`).
- Ne modifie QUE les fichiers nécessaires à la demande. Pas de reformatage, pas d'« améliorations » non demandées.
- Les commits portent le prénom de la personne : `<Type> : <description courte> (par <Prénom>)`, avec Type parmi `Texte`, `Photo`, `Page`, `Correctif`.

## 3. Contrôles automatiques avant toute visualisation
- Chaque `src="..."` et `href="..."` local pointe vers un fichier qui existe (sensible à la casse).
- Les photos de l'équipe sont dans `team/` (chemin `team/prenom-nom.jpg`, jamais `img/team/`).
- Noms de fichiers : minuscules, tirets, sans espace ni accent. Images en `.jpg` ou `.webp`, moins de 500 Ko.
- Pas de balise HTML cassée, pas de texte parasite. Relis le diff ligne par ligne.
- Si un contrôle échoue : corrige-le ou signale-le. Ne passe pas à l'étape suivante.

## 4. Visualisation obligatoire avant publication
1. Montre un récapitulatif en français : fichiers touchés, puis AVANT / APRÈS pour chaque changement (texte exact ou nom de photo).
2. Pousse UNIQUEMENT la branche (`git push -u origin <branche>`). Cloudflare génère une URL de prévisualisation pour cette branche. Cherche-la (commentaire de la pull request, ou `gh pr checks`) et donne-la à la personne. Si elle n'est pas prête, attends 1 à 2 minutes puis réessaie.
3. Aperçu local en plus, seulement si `python` est installé : `python -m http.server 8080`. Si ce n'est pas possible, utilise uniquement le lien Cloudflare. N'installe rien sans demander.
4. Demande : « Tu valides la publication ? Réponds par "oui, publie" ou dis-moi quoi corriger. »
5. Tant que la personne n'a pas répondu « oui, publie », ne crée PAS de pull request.

## 5. Après le « oui, publie »
- Ouvre une pull request vers `main` (`gh pr create`) avec un titre clair et la liste des changements.
- Fusionne-la toi-même (`gh pr merge --squash --delete-branch`). La personne est autonome, aucune autre validation n'est requise.
- Dis : « C'est publié, le site sera à jour dans 1 à 2 minutes. » Rappelle que Matthieu peut revenir en arrière depuis Cloudflare si besoin.

## 6. En cas de doute ou d'erreur
- Si la demande est ambiguë, pose UNE question précise avant de modifier.
- Si quelque chose casse, annule les changements de la branche et explique en une phrase.
- Si on te demande d'annuler une modification déjà publiée : crée une branche, utilise `git revert`, puis suis les étapes 4 et 5.
