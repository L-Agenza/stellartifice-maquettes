> Copie de consultation du 22 octobre 2026. Référence de développement : `prototype-laravel/docs/reference-ux-ui.md`. Actualiser cette copie si la référence évolue.

# Référence UX/UI du projet

Décision utilisateur du 22 octobre 2026 : baser le développement en cours et les futures évolutions sur la direction UX/UI et les parcours préparés dans `maquettes-parcours-dossier/`.

Cette référence s'applique à chaque nouvelle interface et à chaque modification d'un écran existant. Elle fixe une direction commune ; elle ne constitue ni une recette des maquettes, ni une autorisation de modifier toutes les interfaces immédiatement. La portée de chaque lot reste celle demandée par l'utilisateur.

## Documents et ordre de référence

Le [cadre produit et suivi par parcours](OBJECTIF-UX-UI.md) explique l'objectif à l'échelle de toute l'application, la lecture des documents, la trame de travail par lot et la couverture des modules. L'utiliser avec la présente référence pour piloter les travaux actuels et futurs. Les 21 écrans sont des exemples structurants ; leurs principes s'appliquent aussi aux modules sans maquette dédiée.

1. La demande utilisateur et les règles métier qualifiées déterminent le comportement, les champs, les droits, les calculs et les effets de chaque action.
2. Le présent document détermine les principes communs de conception et de recette UX.
3. Le [parcours détaillé](PARCOURS.md) explique les 21 écrans, les relations et les limites. Les étapes sont indexées dans [parcours.json](parcours.json).
4. La [galerie locale](index.html) et ses images donnent la direction visuelle. Les données fictives, compteurs, badges, pictogrammes, variations de navigation et imperfections d'image ne sont pas des spécifications fonctionnelles.

Les fichiers visuels sont actuellement dans le dossier de conception adjacent au dépôt. Leur absence dans un autre checkout ne permet pas de déclarer une conformité visuelle ; retrouver la référence avant de modifier le design. Le présent document reste la règle commune versionnable. Ne pas dépendre du serveur temporaire de galerie pour lire les exigences.

Les rapports plus anciens, notamment `conception-backoffice.md`, conservent leur valeur de contexte et de preuve datée. Pour la direction visuelle et les textes, appliquer cette décision plus récente. Ne pas masquer les contrôles ou limites antérieurs.

## Identité et thèmes

- Prévoir clair, sombre et système ; le mode clair est la présentation principale des maquettes actuelles. Même organisation, mêmes fonctions et informations dans les deux thèmes.
- Clair : fond gris très clair `#F6F8FC`, surfaces et navigation blanches, texte principal `#172033`, secondaire `#526078`, séparateurs `#E2E8F0`, bleu principal `#315FEA`.
- Sombre : fond anthracite bleuté `#11151D`, navigation `#151A24`, surfaces `#1C2330`, texte principal `#F2F5FA`, secondaire `#B1BECE`, séparateurs `#303949`, bleu `#6494FF`.
- Ces couleurs sont des valeurs de départ à vérifier dans les composants réels. Mesurer les contrastes ; une couleur de statut accompagne toujours un texte. Ne pas réintroduire le vert/sauge comme identité principale.
- Typographie lisible, tableaux adaptés au travail sur ordinateur, espacements cohérents, boutons hiérarchisés et densité utile. Préserver les usages sur écran réduit. Éviter les grands bandeaux décoratifs et l'accumulation de cartes.
- Réutiliser Filament, Livewire, Alpine et les composants communs. Aucun changement de technologie ou de dépendance n'est déduit de cette direction.

## Textes, actions et aides

- Utiliser uniquement des textes utiles au travail : titres métier, actions précises, erreurs compréhensibles et prochaine étape explicite.
- Retirer de l'interface métier les mentions de développement, prototype, démonstration, conversion, jalons, tests, détails internes et numéros de version techniques.
- Conserver les informations nécessaires à une décision métier, notamment les versions de documents, la provenance utile, les pièces manquantes et les restrictions réelles. Reformuler simplement ; ne pas cacher une limite effective sous prétexte de supprimer le jargon.
- Distinguer Voir, Choisir, Ajouter, Modifier, Retirer le lien, Archiver et Supprimer. Le bouton d'enregistrement nomme exactement l'objet modifié.
- Une action principale identifiable ; les actions secondaires restent accessibles dans des menus contextualisés. Les fonctions rares ne sont pas supprimées pour simplifier l'écran.
- Une info-bulle apporte une précision ; elle ne remplace pas le libellé d'une action importante ni la seule explication d'une erreur ou d'un blocage. Elle doit être accessible au focus et son information essentielle au tactile.
- Les messages de chargement, succès, absence de résultat, erreur, conflit et indisponibilité doivent être prévus explicitement.

## Navigation et dossier

Regroupement cible du dossier, sans retrait de fonction :

| Rubrique | Fonctions à préserver |
| --- | --- |
| Synthèse | Informations générales, points à compléter, liens et accès directs |
| Conception | Budget, modes, tableaux, lignes, modèles, copies et documents associés |
| Organisation | Équipe, hébergement, transports, batteries du camion et feuille de route |
| Préparation | Ramassage, fabrication, étapes physiques, accessoires |
| Documents | Pièces privées, préparation préfectorale et PDF générés |
| Suivi | Rapport de tir, commentaires et historique |

Les parcours ne forment pas un assistant linéaire. Les rubriques peuvent avancer en parallèle. Les quatre états administratifs existants restent distincts des alertes d'avancement et du cycle physique.

L'accueil cible privilégie les tâches à traiter, les prestations prochaines, la reprise des dossiers et les actions adaptées au profil. Les règles d'agrégation doivent être explicites ; inconnu, absent, non nécessaire et zéro sont des situations différentes.

La recherche globale visible, les résultats contextualisés, les vues métier enregistrées et les favoris sont des objectifs de conception. Ne pas les annoncer comme disponibles sans preuve. Raccourcis cibles : `⌘ K` / `Ctrl K`, flèches, Entrée et Échap ; vérifier les conflits navigateur et la saisie. Les raccourcis doivent être découvrables et ne jamais être le seul accès à une action.

## Formulaires et imbrications : exigence prioritaire

Avant de changer un écran, relever le chemin complet, les champs rares et les branches secondaires dans l'ancien système et le prototype. Ne pas inférer une parité globale du seul registre ou de la présence d'un nom de module.

1. Distinguer fiche commune, relation au dossier et document/événement. Exemples : personne / affectation ; hôtel / nuitée ; matériel / quantité du camion ; produit / ligne du plan.
2. Conserver toute la pile de consultation et d'édition. Ne pas imposer une profondeur arbitraire de deux ou trois fenêtres. Rendre le chemin complet lisible, éventuellement en repliant les ancêtres.
3. Un seul panneau est actif au clavier. Adapter sa largeur à la tâche ; proposer l'agrandissement pour les contenus denses.
4. Enregistrer un enfant ne sauvegarde pas le parent. Chaque parent conserve sa saisie pendant les consultations, les modifications d'enfants et les retours de branche.
5. Revenir ferme un niveau et le bouton nomme ce niveau. Un saut vers un ancêtre contrôle les brouillons qu'il abandonnerait. Croix, Échap et clic extérieur suivent la même protection.
6. Actualiser un libellé modifié sans remplacer les valeurs en cours de saisie. Un lien archivé, devenu invalide ou inaccessible doit être expliqué et traité selon la règle métier, sans remplacement silencieux.
7. Conserver recherche, filtres, tri, pagination et défilement au retour à une liste ; restaurer le focus vers l'action d'origine.
8. Erreurs et conflits conservent la saisie. Les droits, versions concurrentes, validations et contrôles de stock restent appliqués côté serveur.

Chaînes de référence à préserver et tester selon le lot :

- Dossier → client → contacts → modifier contact → retours.
- Ligne → catalogue/produit → groupe ou dépôt → modifier référentiel → retour à la ligne.
- Affectation → profil → pièces/contrat ; affectation → hébergement → nuitée → hôtel/personne.
- Camion → dossiers → dossier/client ; camion → matériel → quantité ou modification de fiche.
- Camion → calcul batteries → préparation → stock/documents.
- Déclaration → responsable → profil → diplôme/agrément.
- Feuille de route → personne/camion/nuitée → retour au même jour.
- Document → versions/archive ; historique → objet concerné.

## Conservation des règles métier

Ne pas transformer un dessin en nouvelle règle. Notamment : les besoins d'équipe ne créent pas d'affectations ; une demande d'hôtel ne réserve rien ; la quantité camion ne décompte pas le stock global ; le ramassage utilise un total et la fabrication ne le décompte pas à nouveau ; validation d'accessoires, batteries, cycle physique et état administratif sont distincts. Les droits sur données privées et salaires restent respectés.

Les fonctions de contrats, frais, règlements, exports, référentiels et applications liées restent dans le périmètre métier applicable, même lorsqu'elles ne figurent pas sur la maquette du dossier. Une simplification visuelle ne justifie aucun retrait fonctionnel.

## Mise en application par lots

- Relire cette référence au démarrage et avant toute évolution d'interface. Dans une conversation déjà active, terminer ou sécuriser le lot en cours avant d'intégrer des changements transversaux.
- Pour chaque lot, identifier les étapes et branches concernées, les comportements existants, les écarts UX proposés et les limites connues. Préserver les modifications concurrentes dans le checkout.
- Faire évoluer d'abord les composants communs dans un lot explicitement prévu, puis les appliquer progressivement : navigation/textes/actions, thèmes et panneaux, accueil/recherche/vues, modules métier.
- Pour un ajout métier en cours, appliquer les conventions compatibles immédiatement ; isoler les refontes plus larges afin de garder un résultat vérifiable.
- Mettre à jour les registres et rapports exigés par les consignes existantes lorsque du code ou un comportement est modifié. Les évolutions UX ajoutées sont des extensions locales, pas une parité historique présumée.
- Une divergence de design doit être justifiée par une règle métier, l'accessibilité, une contrainte technique démontrée ou une nouvelle demande utilisateur. Documenter le compromis ; ne pas redessiner arbitrairement les écrans voisins.

## Critères de recette d'un lot d'interface

Pour chaque chemin touché : vérifier fonction métier, consultations liées, saisies parent/enfant, enregistrement et annulation, retours, erreurs, conflits et droits. Couvrir les niveaux et branches effectivement concernés ; la seule capture ne prouve pas leur fonctionnement.

Vérifier visuellement clair et sombre, textes, densité, actions, état vide et chargements ; contrôler clavier/focus et écran réduit. Mesurer les contrastes et tester lecteur d'écran/zoom dans le périmètre de recette approprié. Réutiliser les tests pertinents existants et ajouter seulement les contrôles nécessaires aux risques ou comportements nouveaux.

Conserver des captures courantes et un compte rendu indiquant précisément : ce qui est implémenté, ce qui a été testé, ce qui reste proposé, les limites et le statut de déploiement. Ne pas annoncer que « l'UX est validée » depuis les seules images ou d'anciens tests.

## Constats datés de la revue de conception

Le 22 octobre 2026 : chaîne ligne → produit → groupe → édition parcourue, quantité provisoire conservée au retour ; formulaire du lien camion/matériel ouvert ; ouverture Fiche client bloquée par un droit `client-documents.view` manquant ; référence retrouvée dans la liste mais absente des résultats globaux. Ces constats sont des observations datées à revérifier dans le code courant, pas des correctifs à appliquer aveuglément ni une raison de contourner les droits. Voir le guide et ses preuves.
