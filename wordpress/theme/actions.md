##admin_init => si page pas créée, la fonction suivante ne sera pas appelée
`add_action('admin_init', callback);`

##admin_enqueue_scripts => la fonction dans ne sera appelé que si on est connecté à l'administration
`add_action('admin_enqueue_scripts', callback);`

