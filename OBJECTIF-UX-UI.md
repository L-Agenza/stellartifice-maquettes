> Copie de consultation du 22 octobre 2026. Référence de développement : `prototype-laravel/docs/pilotage-ux-ui.md`. Actualiser cette copie si la référence évolue.

# Objectif produit et pilotage UX/UI

Décision utilisateur du 22 octobre 2026. Document d'application de [reference-ux-ui.md](REGLES-UX-UI.md), pour le développement en cours et les évolutions futures de l'ensemble du logiciel métier.

## Objectif commun

Construire un outil métier cohérent dans lequel chaque utilisateur retrouve rapidement son travail, comprend l'information et l'action attendue, consulte les données liées, agit au bon endroit et revient à son contexte sans perdre sa saisie.

La réussite s'apprécie sur le parcours réalisé : trouver, comprendre, consulter, modifier, enregistrer et reprendre son travail. Les couleurs, composants et maquettes soutiennent cet objectif. Un changement de palette ne démontre pas l'intégration d'un parcours ; la présence d'un bouton ne démontre pas son bon fonctionnement.

Conserver la richesse du métier : champs, fonctions peu fréquentes, règles, droits, calculs et relations croisées. Organiser l'information par priorité, regroupements et consultation progressive. Toute fonction nouvelle bénéficie de ce même cadre, même sans maquette dédiée.

## Résultats attendus à l'échelle de l'application

| Objectif | Comportement attendu | Preuve adaptée |
| --- | --- | --- |
| Retrouver son travail | Accueil utile au profil ; recherche contextualisée ; listes filtrables ; vues métier et reprise selon le lot livré | Scénario avec données connues et droits réels ; résultats, liens et états vides vérifiés |
| Savoir quoi faire | Manque précis, objet concerné et action explicite ; action indisponible expliquée | Action du bloc → bonne rubrique ou formulaire ; retour au contexte |
| Comprendre les données | Termes métier, unité, période, état et origine utiles ; absence/inconnu/zéro distincts | Exemple représentatif relu avec le métier ; libellés et données concordants |
| Consulter sans interrompre la saisie | Boutons Voir/Consulter et panneaux adaptés à la tâche | Ouvrir une branche liée puis retrouver exactement le brouillon parent |
| Modifier le bon objet | Fiche commune, lien et document identifiés ; enregistrement de portée claire | Tester séparément modification de la fiche et de la relation ; vérifier les effets attendus |
| Se repérer dans les imbrications | Chemin complet, ancêtres retrouvables, retour d'un niveau et focus cohérent | Parcours profond et embranchement ; retours avec et sans modifications |
| Travailler efficacement | Tableaux denses mais lisibles, actions hiérarchisées, regroupement des informations secondaires | Tâche métier représentative menée sans navigation ou ressaisie évitable |
| Garder confiance | Succès, chargement, erreur et conflit compréhensibles ; aucun écrasement ou effet métier caché | Cas de validation, conflit et droit insuffisant ; saisie et données protégées |
| Utiliser le clavier et différents écrans | Focus, labels, raccourcis découvrables, zoom et consultation sur écran réduit | Vérification clavier et visuelle ; accessibilité et contrastes mesurés dans le périmètre annoncé |
| Retrouver une interface cohérente | Mêmes conventions, composants, textes et actions dans les deux thèmes et les modules | Comparaison de plusieurs écrans et de leurs états ; clair/sombre fonctionnellement équivalents |

Ces objectifs reprennent les idées utiles discutées autour de monday.com : vues adaptées au travail, informations opérationnelles, données liées, retours sans rupture, cohérence et vérification continue avec les utilisateurs. Ils ne justifient pas de transformer le logiciel en gestionnaire de tâches générique.

## Comment lire et appliquer les documents

1. Lire `reference-ux-ui.md` pour les règles communes et leur priorité sur les imperfections des images.
2. Parcourir `index.html` ou `PARCOURS.md`. L'entrée de galerie `#etape-1` montre l'accueil ; les autres étapes montrent les branches et formulaires. L'adresse HTTP de galerie est temporaire : les fichiers restent la référence consultable.
3. Pour le lot concerné, lire ses étapes et les rubriques Données et fonctions / Existant et proposition / Formulaires, liens et retour. Repérer aussi l'entrée et la sortie dans les étapes voisines.
4. Rapprocher le parcours avec l'ancien système et le code actuel. Vérifier les champs secondaires, fonctions rares, contraintes, effets et droits. Les maquettes ne constituent pas l'inventaire complet du logiciel.
5. Écrire le scénario réel de la tâche et ses branches, puis l'écart entre état courant et cible. Réutiliser les composants et mécanismes communs avant d'ajouter une solution locale.
6. Implémenter le lot autorisé, vérifier ses scénarios et mettre à jour le suivi avec les preuves et les limites. Tout écart volontaire avec la direction commune doit être motivé.

## Trame de parcours à utiliser pour chaque travail

Une fiche courte suffit dans le rapport du lot ou dans le suivi existant ; éviter de dupliquer la même information dans plusieurs registres.

```text
Identifiant du parcours :
Utilisateur / droits / but :
Point d'entrée et contexte initial :
Objets : fiche commune / relation / document ou événement :
Chemin principal et résultat attendu :
Branches Voir / Choisir / Créer / Modifier / Archiver et profondeur :
Saisies parent/enfant à conserver et portée des enregistrements :
Retours, focus, recherche, filtres, page et défilement :
Cas vide / chargement / erreur / conflit / droit insuffisant :
Règles métier et champs secondaires conservés :
Étapes des maquettes ou motif d'absence de maquette :
Écarts actuels et changements prévus dans le lot :
Contrôles réalisés, captures, résultats, limites et statut de déploiement :
```

Un parcours peut partir d'une recherche, d'un dossier, d'un registre, d'un traitement, d'un document ou d'un planning. Le dossier est un exemple structurant ; la méthode s'applique également aux contrats, frais, exports, référentiels et paramètres.

## Ordre de travail proposé

| Lot | Résultat recherché | Dépendances / vigilance |
| --- | --- | --- |
| Socle commun | Thèmes, composants, actions, textes, messages, focus, panneaux et conservation des contextes | Respecter Filament/Livewire, droits et mécanismes existants ; éviter les variantes propres à chaque module |
| Entrées du produit | Accueil, recherche cohérente et accès vers les tâches | Agrégations vérifiées, résultats selon les droits, navigation aboutissant à une action utile |
| Parcours témoin profond | Dossier/client/contact et ligne/produit/groupe, avec édition et retours | Corriger les blocages dans un lot autorisé ; vérifier les brouillons et objets réellement enregistrés |
| Généralisation métier | Organisation, préparation, documents et suivi | Réutiliser le socle vérifié ; conserver les branches rares, effets de stock et particularités documentaires |
| Modules transversaux et nouveaux travaux | Contrats, frais, règlements, imports, exports, référentiels et administration | Appliquer les mêmes conventions et créer la déclinaison nécessaire ; ne pas les déclarer couverts par une maquette de dossier |

Ce séquencement ne remplace pas le planning métier ni le lot en cours. Sécuriser les modifications déjà engagées ; appliquer les conventions compatibles dans chaque nouvelle fonction et programmer les évolutions transversales explicitement.

## Couverture et suivi initial

Ce tableau indique les cibles de conception, pas l'avancement fonctionnel global. **À établir** signifie absence de recette courante dans ce suivi. Les anciens tests, registres de fonctionnalités et audits de remplacement restent distincts.

| Surface / parcours | Repères de galerie | Application de la cible UX au 22/10/2026 | Prochaine preuve nécessaire |
| --- | --- | --- | --- |
| Accueil opérationnel | 01 | Partiel visuel : capture utilisateur montrant recherche, À traiter, récents et prestations | Cliquer chaque action sur données représentatives, vérifier pertinence et retours ; examiner les libellés |
| Recherche et commandes | 02 | À recontrôler dans la version courante ; ancienne revue avec référence introuvable en global | Référence/nom/client/produit, résultats vides, droits, clavier et brouillon préservé |
| Liste, aperçu et vues | 03 | Cible partiellement illustrée ; recette de la nouvelle présentation à établir | Recherche/filtres/tri/pagination/défilement, vues nommées si livrées, retour du panneau |
| Création et synthèse dossier | 04–05 | À établir | Champs exacts, modèle facultatif, manques réels, besoins sans affectation implicite |
| Client, contact et liens | 06 | À recontrôler : blocage de droit observé dans l'ancienne revue du jour | Parcours complet avec création/modification et retour au brouillon dossier |
| Conception, catalogue, groupe/dépôt | 07–08 | Mécanisme existant parcouru ; conformité à la cible visuelle à établir | Rejouer les branches après évolution, modèles/copie, modes, cumuls et gardes de lancement |
| Préparation préfectorale | 09 | À établir | Responsable choisi, pièces liées, manques, droits et retour des profils/documents |
| Affectations et planning | 10–11 | À établir | Profil et lien séparés, partage, déplacement/interversion, semaine et état conservés |
| Nuitées, personnes et hôtels | 12 | À établir | Plusieurs branches, coût total, doublons, droits et retours sans réservation implicite |
| Ramassage et mouvements | 13 | À établir | Total et delta, réintégration, mouvements consultables, erreurs/conflits |
| Fabrication et étapes physiques | 14 | À établir | Lignes, lancement/retrait, cartons, dépôt/sortie/retour ; état administratif indépendant |
| Accessoires | 15 | À établir | Recalcul explicite, portée d'écrasement, validation et réouverture |
| Transports et matériel | 16 | Formulaire de lien existant ouvert ; cible UX à établir | Plusieurs dossiers/camions, quantité vs fiche, loueur/chauffeur, verrous et retours |
| Batteries | 17 | À établir | Calcul/préparation/stock distincts ; revue requise selon le cas ; validation/réouverture |
| Feuille de route | 18 | À établir | Consignes, contact opérationnel distinct, jour, branches et génération documentaire |
| Pièces et PDF | 19 | À établir | Dépôt, version, archive, traitement en cours/erreur/prêt, téléchargement autorisé |
| Rapport, commentaires et historique | 20–21 | À établir | Champs conditionnels, portée d'événement, avant/après, journal propre des fiches communes |
| Contrats et documents personnel | Déclinaison à préparer | À établir | Contrat → personne/affectation/documents → génération/classement → retour ; droits privés |
| Frais, règlements et exports | Déclinaison à préparer | À établir | Déclaration → contrat/dossier/personne/justificatif → registre/export → retour |
| Produits, annuaires et référentiels | 06–08, puis déclinaison des registres | À établir | Identités, archives, fiches partagées, liens, sélection et comptages distincts |
| Imports et traitements | Déclinaison à préparer | À établir | Choisir → prévisualiser → confirmer → suivre → comprendre erreurs/résultat ; aucune perte de contexte |
| Stocks et inventaires à date | 13–17, puis déclinaison des inventaires | À établir | Période, dépôt, produit et mouvements liés, données figées et documents ; règles inchangées |
| Administration et paramètres | Déclinaison à préparer | À établir | Conventions communes, droits sensibles explicites, erreurs et confirmations ciblées |

Pour chaque ligne traitée, ajouter la date, le périmètre, le lien vers le rapport du lot et la preuve. Distinguer **prévu**, **implémenté**, **vérifié dans le navigateur** et **à corriger**. Ne pas remplacer les constats datés ni attribuer une validation globale au logiciel depuis quelques lignes.

## Exemple : accueil montré par l'utilisateur

La capture du 22 octobre montre une structure qui progresse vers la maquette : recherche principale, À traiter, Reprendre un dossier, Prochaines prestations et Accès directs. Elle ne prouve pas le bon fonctionnement des actions, des résultats ou des retours.

Points à examiner dans ce lot :

- Des boutons répétés « Compléter le dossier » ne disent pas quel manque résoudre. Quand un besoin précis est connu, utiliser l'action précise et ouvrir la bonne rubrique. Si seule la qualité Brouillon est connue, l'annoncer clairement et ne pas inventer un manque d'équipe ou de pièce.
- Les explications « six premières par date », « trois premiers par date », « jusqu'à six résultats » sont des détails de sélection qui encombrent le premier niveau. Préférer un titre/périmètre métier utile et une aide secondaire accessible pour la règle détaillée ; préserver toute information nécessaire à la décision.
- Deux champs de recherche visibles demandent une règle claire. Harmoniser leur rôle ou réutiliser le même point d'entrée/composant ; éviter des résultats et commandes incohérents entre les deux.
- Adapter la densité à l'écran et limiter les grands vides sans remplir l'accueil de compteurs. « Nouveau dossier » doit avoir une priorité visuelle cohérente avec son importance.
- Les données portant Démo dans cette capture peuvent être des noms fictifs du jeu de travail : ne pas les confondre avec un libellé d'interface à supprimer, et ne pas renommer les données métier automatiquement.

Ces observations viennent de la capture fournie ; elles ne constituent pas une nouvelle inspection fonctionnelle du site courant.

## Condition de fin d'un lot UX/UI

Un lot est présenté comme intégré lorsqu'il apporte le comportement prévu, préserve les fonctions et données, suit les conventions communes et possède des preuves courantes adaptées. La vérification porte sur les branches réellement touchées et les risques, sans relancer des tests sans raison.

Le compte rendu indique : objectif et étapes couverts, changements de comportement et de présentation, règles préservées, tests pertinents, contrôles navigateur et captures des deux thèmes, erreurs/conflits/droits vérifiés, écarts restants et statut local/déployé. Un contrôle non effectué reste explicite.

Pour apprécier le confort réel, observer des utilisateurs représentatifs sur des tâches : retrouver une prestation, compléter un lien, consulter une donnée commune puis reprendre une saisie. Relever réussite, hésitations, erreurs, navigation et ressaisie évitables ; comparer avant/après lorsque possible. Aucune promesse de temps gagné n'est déduite des seules maquettes.
