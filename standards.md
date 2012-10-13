# Les standards de programmation Drupal
## Les fameux standards
<http://drupal.org/coding-standards>

- Indentation et espace
- Operateurs et Casting
- Strucutres de controles (if, foreach, switch, etc.)
- Longeur des lignes (nombre de caractère sur une ligne)
- Appels de fonction et déclaration
- Appel de à des constructeurs de classe
- Les arrays!
- Convention pour les noms de variables, fonctions et classes
- Demo Eclipse!
- Documentation de fichier
- Documentation de fonction
- Documentation `inline`
- Demo Sublime Text!
- Documentation de formulaire (FAPI)
- Documentation de fonction de thème
- Documentation de fichier de thème
- Documentation de classe
- Misc
- Base de données
- Javascript 
- CSS

## Indentation et espaces


## Misc
- PHP tag d'ouverture
Toujours <?php ?>, jamais la version courte <? ?>.

La fermeture n'est pas obligatoire si nous sommes dans un fichier module.

Évitez de laisser le tag ouvert dans un fichier thème, pour des raisons de claretée.

- Deux points dans les thèmes
Encore une fois, on ajoute toujours les deux points, même si ca fonctionne sans.
Exemple : <?php print $drupalcamp_year; ?>

## Base de données
http://drupal.org/node/2497

## Javascript
http://drupal.org/node/172169

## CSS
http://drupal.org/node/302199

## http://drupal.org/project/coder
A besoin de Grammar parser (http://drupal.org/project/grammar_parser)

## http://drupal.org/project/coder_tough_love
## Handling text in secure fashion http://drupal.org/node/28984
Un peu vieux, mais permait de voir les points importants.
Utilisation de check-plain, filter-xss sur le output.

## Drupal sandbox with Coder http://upgrade.boombatower.com/tools/php/directories
Pas open source. Offre plus de fonctionnalités. La version gratuite du service offre les mêmes fonctionnalités que Coder et SQL Parser. Semble vouloir aller vers une solution payante pour fournir la possibilité de migrer les modules de Drupal6 à 7. Aucune manière de payer.

## Bonnes pratiques de developpement

    EntityFieldQuery
    entity_metadata_wrapper
    Never hack core
    hook_extra_fields

## Nice to have

## Migrate
Jamais nescessaire d'avoir un upgrade path pour le code. Question de bon sens et de confiance en ce qui concerne le data.

## Simpletest
## Functionnal tests
## Unit tests
## Upgrade tests
## Examples module http://drupal.org/project/examples
Contient des exemples de tests pour (presque) chacun des API fournit par le core de Drupal.
## Vimrc http://drupal.org/node/1389006
