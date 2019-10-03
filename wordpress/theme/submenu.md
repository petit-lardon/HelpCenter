Dans l'action qui crée la page dans le BO, il y un un simple appel à faire sur une fonction native de wordpress
```php
add_submenu_page( string $parent_slug, string $page_title, string $menu_title, string $capability, string $menu_slug, callable $function = 'my_function' )
```

Cette fonction appelle une fonction de callback qui se chargera d'afficher du contenu
```php
function my_function() {
    echo '<h1>Settings page</h1>';
}
```

Dans cette fonction, on peut appeler un fichier externe pour y déclarer notre template et éviter de surcharger inutilement la page
```php
function my_function() {
    require_once(get_template_directory().'/inc/templates/mon_template_perso.php');
}
```

On crée ensuite le fichier correspondant dans le dossier 
inc/templates/mon_template_perso.php

####inc/templates/mon_template_perso.php
```php
<h1>MyFolio settings page</h1>
<h3>Manage options</h3>

<?php bloginfo(); ?>
```