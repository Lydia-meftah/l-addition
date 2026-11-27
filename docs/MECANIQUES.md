# L'Addition — Mecaniques de jeu

Version simplifiee tiree du doc de game design. References mecaniques ET narration : Dead Plate + Papers Please. Plateforme : site web statique (HTML/CSS/JS). Delai environ 1 mois et demi, perimetre volontairement reduit.

## Cadrage
Principe directeur : coder d'abord une boucle de service simple et satisfaisante. L'ambiance et l'horreur viennent par-dessus, en effets visuels et sonores, sans mecanique supplementaire. Tout le reste est optionnel et se coupe si le temps manque.

## Les deux references
Papers Please : la boucle de travail repetitive jour apres jour, et la narration qui passe par le travail plutot que par de longs dialogues ; en option une courte phase apres le service. Dead Plate : le service sous pression du temps, la montee d'ambiance et d'horreur au fil des jours, et plusieurs fins selon la performance.

## Boucle de jeu
Un client arrive avec une commande. Le joueur prepare la boisson (suite d'etapes). Il sert avant que la patience du client tombe a zero. Reussite ou echec, puis client suivant. Le tout sur une journee limitee par un chrono.

## Le service
Commandes : chaque client demande une recette tiree dans une petite liste, simple au debut puis un peu plus complexe. Preparation : une recette est une suite d'etapes (ajouter un ingredient, faire une action), avec une validation souple : si l'ensemble final des ingredients est bon, c'est reussi, sans tenir compte de l'ordre. Patience : une seule jauge par client qui descend avec le temps ; a zero le client part (echec). Resultat : bonne boisson servie a temps = reussite et un peu de score ; mauvaise ou trop tard = echec. Pas de combos ni d'economie compliquee pour le MVP.

## Recettes de depart
Espresso (tasse, cafe). Americano (tasse, cafe, eau chaude). Latte (tasse, cafe, lait, mousse). Cappuccino (tasse, cafe, mousse, cacao). Ingredients minimum : cafe, eau chaude, lait, mousse de lait, un sirop, glace pour les boissons froides.

## Structure et narration
Jours successifs : la performance d'une journee influence l'ambiance du lendemain (normale ou degradee). Narration par le travail : l'horreur transparait dans les commandes, le texte et l'ambiance, pas dans de longs dialogues. Option apres le service : courte scene chez soi, a couper en premier si le delai est serre. Fins selon la performance : une simple evaluation de fin choisit une fin.

## Ambiance et horreur (gros effet, peu de code)
Le texte des commandes vire au vert ou a des couleurs anormales quand l'ambiance se degrade. La degradation suit les erreurs cumulees de la journee : 0 a 2 erreurs reste normal, 3 et plus donne un leger malaise (teinte verdatre), 6 et plus passe en degrade (vert anormal et sons). En multi-journees, le niveau d'un jour peut se reporter sur l'ambiance de depart du lendemain.

## Battle creativite (bonus / joker)
Mode ou le joueur compose librement une recette pour satisfaire le patron et faire baisser la jauge. Peut servir de mecanique joker pour eviter le remplissage de la jauge. Hors perimetre si le delai est serre.

## Parametres de depart (a regler)
Duree d'une journee : 120 s. Patience max : 100. Vitesse de baisse de patience : 6 par seconde. Seuils de couleur de patience : vert au-dessus de 60, orange entre 25 et 60, rouge en dessous de 25. Capacite de la file : 3 clients. Intervalle d'apparition : 5 s. Prix d'une boisson : 3. Ce sont des valeurs de depart a ajuster.

## Systemes techniques
Horloge temps reel (patience et chrono). Machine a etats du client : arrivee, en attente, en preparation, servi (content) ou parti (fache) ; un client sert une seule fois puis est retire. Validation de commande souple (comparaison d'ensembles d'ingredients). Compteur de score et evaluation de fin de journee. Donnees des recettes dans un fichier, pas en dur. Effets d'ambiance (couleur du texte, sons). localStorage pour la progression et le meilleur score.

## Perimetre realiste (environ 1 mois et demi)
MVP prioritaire : boucle de service, patience, 3 a 4 recettes, une journee jouable, effet d'ambiance minimal (le texte qui change de couleur). Seulement si le temps le permet : plusieurs journees avec degradation progressive, phase apres le service, fins multiples, battle creativite.
