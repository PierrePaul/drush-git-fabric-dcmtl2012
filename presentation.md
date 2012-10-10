# Déploiement de niveau entreprise avec Git, Drush et Fabric

## Drush
## Drush?
![Broken Window](/images/presentation-drush/window-1.jpg)

## Drush!
![Clean Window](/images/presentation-drush/window-2.jpg)

## Fonctions de Drush
- Télécharger des modules
- Activer/Désactiver des modules
- Déinstaller des modules
- Rouler les tests\*

## Pourquoi Drush est-il important?
Permet d'automatiser le plus de fonctions manuelle posible.
## Pourquoi Drush est-il important?
L'erreur est humaine. Enlevons le facteur humain.
## Pourquoi Drush est-il important?
C'est peut-être un développeur junior qui va devoir pousser le code en ligne.
## Pourquoi Drush est-il important?
Tous les sysadmins sont malades (oktoberfest).
## Pourquoi Drush est-il important?
Entandu chez un client : "En toute franchise, la documentation de projet, c'est pas notre force."

## Comment installer Drush
Pear
    pear channel-discover pear.drush.org
    pear install drush/drush

_Pear est brisé_ sur MacOSX Mountain Lion
    sudo cp /private/etc/php.ini.default /private/etc/php.ini
    sudo php /usr/lib/php/install-pear-nozlib.phar
    pear config-set php\_ini /private/etc/php.ini
    pecl config-set php\_ini /private/etc/php.ini  
    sudo pear upgrade-all

## Comment installer Drush :: Pear
- Permet de mettre à jour facilement.
- Accessible de tous les utilisateurs sur la machine

## Où est-il installé?

## Drush aliases
    $aliases\['dev'\] = array(
        'root' => '/path/to/drupal',
        'uri' => 'dev.mydrupalsite.com',
    );
    $aliases\['live'\] = array(
        'root' => '/other/path/to/drupal',
        'uri' => 'mydrupalsite.com',
    );
## Fonctions importantes
- sql-dump (drush @dev sql-dump > backup.sql)
- sql-connect (drush @live sql-connect)

## Drush make
Compile en cascade un projet.

Télécharge tous les modules et les patchs spécifiées.

## Drush make example
https://github.com/Wiredcraft/example
    core = "7.x"
    api = "2"

    ; Includes ====================================================================

    includes[] = "https://raw.github.com/makara/buildkit_plus_v7/master/base.make"

    ; Modules =====================================================================

    projects[mollom][type] = "module"
    projects[mollom][subdir] = "contrib"
    projects[mollom][version] = "1.1"
## Git?
## Git
## Branch
## Pull
## Remotes
## Push
## Gitolite/Gitosis
Gitosis est mort, longue vie à Gitosis!

Dernier commit est en 2009.
Gitolite est complet et fonctionne bien.

## Fabric?
## Fabric
## Config SSH

## Autres outils à considérer
## Jenkins
## Ansible - Chef - Puppet - BCFG2
## Vagrant
