##Inclusion

L'inclusion permet de créer un bout de code qui pourra être réutilisé si besoin dans d'autres templates

```twig
{% include '@components/title/default/template.html.twig' with {
    'class': 'main__title',
    'content': title
} only %}
```


L'inclusion est utile pour la répétition d'une partie de code dans plusieurs templates
Si l'on veut dupliquer un bout de code dans un template unique, on utilise une [macro](/macro.md)

NB: l'utilisation du paramètre `only` permet de ne passer que les variables nécessaires au template inclus, pour un gain en temps de chargement de la page (pour les templates complexes)
