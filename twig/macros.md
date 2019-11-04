##Macros

La macro permet de créer un bout de code dans un template qui pourra être réutilisé si besoin

```{{ _self.pageTitle(locations, translationVars) }}```
_self fait référence au template en cours
pageTitle fait référence à la fonction donnée à la macro

```{% macro pageTitle(locations, translationVars) %}
    {% if locations.isGeolocationSearch() %}
        {% set title = 'bridge.theme.pages.results.geolocation.h1' | transchoice(locations.total, translationVars, 'seo') %}
    {% else %}
        {% set title = 'bridge.theme.pages.results.query.h1' | transchoice(locations.total, translationVars, 'seo') %}
    {% endif %}

    {% include '@components/title/default/template.html.twig' with {
        'class': 'lf-results__main__title',
        'hLevel': 1,
        'content': title
    } only %}
{% endmacro %}```

La macro est utile pour la répétition d'une partie de code dans un template unique
Si l'on veut dupliquer un bout de code sur des templates différents, on utilise une [inclusion](/inclusion.md)
