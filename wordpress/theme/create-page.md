Toutes les fonctions pour le thème doivent être déclarées dans le fichier *functions.php*

Pour plus de clareté il est préférable de séparer le code et d'inclure les fichiers dans *functions.php*

####functions.php
```php
require get_template_directory().'/inc/function-admin.php';
```

####/inc/function-admin.php
```php
function folio_add_admin_page() {
    add_menu_page($page_title, $menu_title, $rights_required, $url_slug, $callback, $icon_url, $position);
}

add_action('admin_menu', 'folio_add_admin_page');

function myfolio_theme_create_page() {
    echo '<h1>MyFolio admin page</h1>';
}
```
Pour executer des choses, on doit lancer une action à wordpress en fonction d'un évènement
add_action( string $tag, callable $function_to_add, int $priority = 10, int $accepted_args = 1 )
[Documentation](https://developer.wordpress.org/reference/functions/add_action/)

On crée une nouvelle page dans le BO
add_menu_page( string $page_title, string $menu_title, string $capability, string $menu_slug, callable $function = '', string $icon_url = '', int $position = null )
[Documentation](https://developer.wordpress.org/reference/functions/add_menu_page/)

le rendu de la page est ajouté dans la fonction de callback 
function myfolio_theme_create_page()

###Note importante
Chaque fonction déclarée doit être unique.
Il est préférable d'être explicite dans son nom 
