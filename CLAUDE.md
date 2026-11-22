# SMAL & CO : règles de modification du site

Site statique (HTML/CSS/JS). Le code est sur GitHub (`smal-co/smal-co-web`), la branche `main` est la PRODUCTION : tout ce qui y arrive est en ligne sur Cloudflare Pages en 1 à 2 minutes.
La personne qui te parle n'est PAS développeuse. Explique tout en français simple, sans jargon.

## 0. Au démarrage
- Demande : « Qui es-tu ? » (prénom) et « Que veux-tu modifier ? ».
- Lance `git pull` puis `git status`. Si le dossier n'est pas propre, préviens et arrête-toi.

## 1. Interdits absolus
- Ne JAMAIS commiter, pousser ou fusionner sur `main`. Aucun `git push --force`.
- Ne JAMAIS publier sans le « OUI » explicite de la personne (voir §4). « ok », « vas-y », un pouce ou un silence ne suffisent pas : il faut « oui, publie ».
- Ne JAMAIS toucher sans demander à : `_headers`, `.github/`, `robots.txt`, `sitemap.xml`, `CLAUDE.md`, les balises `canonical`, `og:*`, `twitter:*` et `robots` dans le `<head>`.
- Ne JAMAIS supprimer de fichier, ni renommer ou déplacer un dossier (`team/`, `img/`, `logos/`, `assets/`).
- Ne JAMAIS écrire de mot de passe, clé ou identifiant dans un fichier.

## 2. Travailler sur une branche
- Crée une branche : `modif/<prenom>-<sujet-court>-<AAAAMMJJ>` (ex. `modif/lucas-age-bureau-20261122`).
- Ne modifie QUE les fichiers nécessaires à la demande. Pas de reformatage, pas d'« améliorations » non demandées.

## 3. Contrôles automatiques avant toute visualisation
- Chaque `src="..."` et `href="..."` local pointe vers un fichier qui existe (sensible à la casse).
- Les photos de l'équipe sont dans `team/` (chemin `team/prenom-nom.jpg`, jamais `img/team/`).
- Noms de fichiers : minuscules, tirets, sans espace ni accent. Images en `.jpg` ou `.webp`, moins de 500 Ko.
- Pas de balise HTML cassée, pas de texte parasite. Relis le diff ligne par ligne.
- Si un contrôle échoue : corrige-le ou signale-le. Ne passe pas à l'étape suivante.

## 4. Visualisation obligatoire avant validation
1. Montre un récapitulatif en français : fichiers touchés, puis AVANT / APRÈS pour chaque changement (texte exact ou nom de photo).
2. Lance un aperçu local : `python -m http.server 8080` dans le dossier du site, puis donne `http://localhost:8080` (ou capture d'écran des pages touchées).
3. Pousse UNIQUEMENT la branche (`git push -u origin <branche>`). Cloudflare génère alors une URL de prévisualisation du type `https://<branche>.smal-co-web.pages.dev`. Donne ce lien à la personne et attends 1 à 2 minutes qu'il fonctionne.
4. Demande : « Tu valides la publication ? Réponds par "oui, publie" ou dis-moi quoi corriger. »
5. Tant que la personne n'a pas répondu « oui, publie », ne crée PAS de pull request.

## 5. Après le « oui, publie »
- Ouvre une pull request vers `main` (`gh pr create`) avec un titre clair et la liste des changements.
- Ne fusionne PAS toi-même. Seuls Matthieu (président) et le relecteur désigné fusionnent.
- Dis à la personne : « La demande est envoyée à un relecteur. Le site sera mis à jour après sa validation. »

## 6. Commits
Format : `<Type> : <description courte> (par <Prénom>)` avec Type parmi `Texte`, `Photo`, `Page`, `Correctif`.

## 7. En cas de doute ou d'erreur
- Si la demande est ambiguë, pose UNE question précise avant de modifier.
- Si quelque chose casse, annule les changements de la branche et explique en une phrase.
- Retour arrière en production : Cloudflare, Déploiements, `…`, « Rollback » sur un ancien déploiement qui fonctionnait.
