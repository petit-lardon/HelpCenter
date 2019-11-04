Chaque page est customisable. Pour plus de flexibilité et une meilleur maintenabilité, on déclare un nouveau fichier dans les fonctions.php pour les fichiers de style

require get_template_directory().'/inc/enqueue.php';

##'/inc/enqueue.php';
````php
function myfolio_load_admin_scripts($hook) {
    if('toplevel_page_myfolio' != $hook) {
        return;
    }

    wp_register_style('myfolio_admin', get_template_directory_uri().'/css/myfolio.admin.css', array(), '1.0.0', 'all');
    wp_enqueue_style('myfolio_admin');
}

add_action('admin_enqueue_scripts', 'myfolio_load_admin_scripts');
```

wp_register_style
déclaration du fichier css

wp_enqueue_style
ajout et lancement du css

add_action
lancement de la fonction de callback si l'action est lancée