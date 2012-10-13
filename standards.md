# Les standards de programmation Drupal
## Les fameux standards
<http://drupal.org/coding-standards>

- Indentation et espace
- Operateurs et Casting
- Structres de controles (if, foreach, switch, etc.)
- Longeur des lignes (nombre de caractère sur une ligne)
- Appels de fonction et déclaration
- Appel à un constructeur
- Les arrays!
- Les classes!
- Convention pour les noms de variables, fonctions et classes
- Demo Eclipse!
- Documentation de fichier
- Documentation de fonction
- Documentation `inline`
- Demo rapide Sublime Text!
- Documentation de formulaire (FAPI)
- Documentation de fonction de thème
- Documentation de fichier de thème
- Misc
- Base de données
- Javascript 
- CSS
- Markup

## Indentation et espaces
Celui que je déteste le plus, 2 espaces et pas de tabulation!

## Operateurs et Casting
Une facile, un espace entre les opérateurs et un espace entre chaque opérateur.

    (int) $salaire_developpeur_drupal;

    $impot = $salaire_developpeur_drupal / 50;

## Longueur de ligne
C'est historique, les écrans pouvaient afficher dans le bon vieux temps 80 charactères par ligne. 
Convention peu suivie et assez lousse dans le merveilleux monde Drupal.
En général on doit se limiter à 80 chars sauf dans les cas (vagues) suivants :

- Déclaration de variables
- Déclaration de fonctions
- Déclaration de classes
- Trop compliqué à lire si on essait de faire rentrer ça sur 80chars.
- les conditions ne doivent pas être sur plusieurs lignes

## Longueur de ligne

Une note importante, les standards sont vagues sur ce point pour éviter que des développeurs brillants essait de remporter le prix "Ligne la moins lisible, mais qui rentre sur 80 charactères.".

![Darwin Award](images/standards/darwin-award.jpg)

##  Appels de fonction et déclaration
Un espace avant et après le égal, comme tous les opérateurs:

    $salaire_developpeur_drupal = calcul_impot(99999999);

Dans le cas où on aurait un bloc d'appel, il faut aligner les signes égal...

    $impot_developpeur_drupal = calcul_impot(99999999);
    $ipot_python              = calcul_impot(10);

Pour la déclaration d'une fonction, un espace avant et après les paramètres :

    function calcul_impot_python ($salaire, $taux_imposition = 0.1) {
    }

## Appel à un constructeur
Toujours inclure les parentheses, même s'il n'y a aucun argument:

    $drupal = new Site();
    $drupal = new Site('Vraiment cool');

## Les arrays!
Un espace après la virgule et un espace après =>

    $programme = array("Enregistrement", "10:00" => "Pierre Paul");

Il faut se rappeler la règle des 80 charactères:

    $programme = array(
        '8:00'  => 'Enregistrement',
        '9:00'  => 'session 1',
        '10:00' => 'session 2',
        '11:00' => 'session 3',
        '12:00' => 'Diner!',
    );

C'est fortement recommander de garder une virgule après le dernier item.

## Les classes!
- Le nom des classes doivent être `UpperCamel` (première lettre de chaque mot en majuscule).
- Les méthodes de ces classes doivent suivrent le `lowerCamel` (première lettre en minuscule, les lettres des autres mots en majuscule)
- Acronyme dans le nom? En majuscule! 
    
    class JSONParser () {
    }

- Ne devrait pas avoir Drupal dans son nom
- Ni "Class"...
- C'est le contraire pour les interfaces : ParserInterface (){}
- Même chose pour les classes de tests
- Les classes de type factory sont encouragées
- Le chaining est encouragé aussi
- Programmer le plus possible avec des interfaces, plutôt que son implémentation (Program to an interface, not an implementation).

## Exemple

    class AnimalInterface {
        public function deranger();
    }

    class Chat implements AnimalInterface {
       public function deranger() {
           return t('Break everything');
       }
    }

    function deranger_encore(AnimalInterface $animal) {
        $animal->deranger();
    }

## Convention pour les noms de variables
*Variables*
- En minuscule, les mots séparés par traits soulignés
- Les variables avec des valeurs persistentes devraient toujours passer par variable_get() et variable_set()

    $taux_imposition = variable_get('monmodule_taux_imposition', 0.5);

- Les constantes toujours en majuscules, séparé encore par des traits soulignés(_)

## Demo Eclipse!

## Documentation de fichier
Tous les fichiers de code (donc pas les fichiers de thème .tpl.php et les fichiers .info) doivent commencer par :

    /**
    * @file
    * Description courte
    * 
    * Description longue
    */

C'est le format Doxygen. Ce format est nécessaire pour générer une documentation automatique des projets avec PHPDoc.

## FAPI
- Toutes les fonctions qui génèrent des formulaires doivent spécifier les paramètres (s'il y a des paramètres autres que $form et $formstate).
- Les fonctions connexes (\_validate, \_submit) devrait être documenté avec @see

   /**
   * Form constructor for the user login form.
   *
   * @param $message
   *   The message to display.
   *
   * @see user_login_form_validate()
   * @see user_login_form_submit()
   * @ingroup forms
   */
   function user_login_form($form, &$form_state, $message = '') 

## Les fonctions de thème
Les paramètres devraient être énumérés et expliquer.

    /**
    * Returns HTML for a foo.
    *
    * @param $variables
    *   An associative array containing:
    *   - foo: The foo object that is being formatted.
    *   - show_bar: TRUE to show the bar component, FALSE to omit it.
    *
    * @ingroup themeable
    */
    function theme_foo($variables) {
    }

## Les fichiers de thème
- Commence par @file comme un fichier de code
- Liste et explique toutes les variables définies par la fonction _theme()

Voir node.tpl.php

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
- Ne pas utiliser de mot réservé seulement à MySQL, SQLite, etc. pour des noms de colonnes. Exemple : all, always, attribute, call, etc.
- Les instructions SQL doivent être en majuscule. Sinon l'abstration des bases de données ne fonctionnera pas du tout. Exemple: SELECT nid FROM ...
- Passer toutes les valeurs dans des filtres (%d, %f, %s, etc.)

## Javascript
http://drupal.org/node/172169
- Première lettre des variables doit être en minuscule.
- Les points-virgules (;) sont obligatoires. Sinon on risque de briser l'aggrégation des fichiers javascript.
- Le nom des fonctions sont aussi lowerCamelCase.
- Le nom des fonctions devraient commencer par le nom du module pour éviter des problèmes de collision.
- Les constantes devraient passer par drupal_add_js
- Utiliser le plus possible === plutôt que ==
- eval is evil
- Utiliser Drupal.checkPlain() pour du contenu soumis par l'utilisateur.
- Utiliser Drupal.t() pour du contenu qui doit être traduis.

## CSS
http://drupal.org/node/302199
- Les selecteurs sur une ou plusieurs lignes, les instructions dans un bloc séparé.
- Chaque instruction doit être sur une ligne séparée
- Les instructions doivent être en ordre alphabétique.
- Doivent se terminer avec un point virgule.
- Dans le cas des propriétés réservés à certains vendeurs (moz-*), ils doivent être groupés ensemble, toujours en ordre alphabétique.
- Les instructions réservé à un vendeur doivent être spécifiés avant les instructions génériques (sauf pour filter).

## Markup
<http://groups.drupal.org/node/6355>
- Ne jamais utiliser l'attribut ID.
- Tous les divs devraient avoir au moins une classe css.
- Un identifiant unique, si approprié
- Vaut mieux avoir trop de classes que pas assez.
- Un span est inline, un block est un élément de bloc. À garder en tête avant de jouer avec le display dans un fichier css.
- Ne pas ajouter de markup autour d'élément de markup. Exemple: ne pas mettre un <h2> dans un <div> (sauf si nécessaire)


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
