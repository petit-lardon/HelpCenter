##Traduction
Au niveau du template, on déclare des variables 
```twig
 set translationVars = {
    '%pagination.start%': pagination.current | default({}),
    '%pagination.end%': pagination.hitsEnd
}
```

Que l'on transmet à la clé de trad
```html
<title>{{ 'bridge.theme.pages.results.geolocation.meta.title' | trans(translationVars, 'seo') }}</title>
```
+ Le pipe trans permet de lancer la commande de traduction native twig
+ Le premier paramètre est une variable transmise à la traduction, pour avoir accès à des sonnées dynamiques dans les traductions
+ Le second paramètre définit le nom du du fichier de traduction

Ces deux paramètres sont facultatifs

La clé de trad est déclarée via la commande 
```
php bin/console translation:update --output-format xlf --force fr ComponentsBundle
```

Et initialisée ainsi
```html
<trans-unit id="" resname="front_bundle.views.pages.geo-divisions.country.title.with-pagination">
    <source>front_bundle.views.pages.geo-divisions.country.title.with-pagination</source>
    <target>Page %pagination.start% sur %pagination.end%</target>
</trans-unit>
```
