Dans l'action qui crée la page dans le BO, il y un un simple appel à faire sur une fonction native de wordpress
####/inc/function-admin.php
```php
add_action('admin_init', callback = 'field_function');

function field_function() {
    register_setting('myfolio_settings_group', 'first_name');
    register_setting('myfolio_settings_group', 'last_name');
    register_setting('myfolio_settings_group', 'user_description');

    add_settings_section('sidebar-options', 'Sidebar options', 'callback_sidebar_options', $page_title);

    add_settings_field('sidebar-name', 'Full name', 'callback_sidebar_name', $page_title, 'sidebar-options');
    add_settings_field('sidebar-user-description', 'User description', 'callback_sidebar_user_description', $page_title, 'sidebar-options');
}

function callback_sidebar_options() {
    echo 'Customize your sidebar informations';
}

function callback_sidebar_name() {
    $firstName = esc_attr(get_option('first_name'));
    $lastName = esc_attr(get_option('last_name'));

    echo '<input type="text" name="first_name" value="'.$firstName.'" placeholder="first name" />';
    echo '<input type="text" name="last_name" value="'.$lastName.'" placeholder="last name" />';
}

function myfolio_sidebar_user_description() {
    $userDescription = esc_attr(get_option('user_description'));

    echo '<input type="text" name="user_description" value="'.$userDescription.'" placeholder="little description" />';
}
```

[register_setting](https://developer.wordpress.org/reference/functions/register_setting/)


[add_settings_section](https://developer.wordpress.org/reference/functions/add_settings_section/)


[add_settings_field](https://developer.wordpress.org/reference/functions/add_settings_field/)

