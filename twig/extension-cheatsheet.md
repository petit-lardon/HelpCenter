# Twig Extensions

[&#8672; *Table of contents*](/helpCenter/)

[Documentation](https://twig-extensions.readthedocs.io/en/latest/index.html)

**Instalation:**

```bash
composer install twig/extensions
```

## Text Extension

```yml
# app/config/services.yml
services:
    twig.extension.text:
      class: Twig_Extensions_Extension_Text
      tags:
        - { name: twig.extension }
```

### truncate

Use the `truncate` filter to cut off a string after limit is reached.

```twig
{% raw %}
{{ 'Hello World!'|truncate(5) }} => Hello...
{{ 'Hello World!'|truncate(7, true) }} => Hello World!
{{ 'Hello World!'|truncate(7, false, '??') }} => Hello W??
{% endraw %}
```

### wordwrap

Use the `wordwrap` filter to split your text in lines with equal length.

```twig
{% raw %}
{{ "Lorem ipsum dolor sit amet, consectetur adipiscing"|wordwrap(10) }}

Lorem ipsu
m dolor si
t amet, co
nsectetur
adipiscing


{{ "Lorem ipsum dolor sit amet, consectetur adipiscing"|wordwrap(10, "zz\n") }}

Lorem ipsuzz
m dolor sizz
t amet, cozz
nsectetur zz
adipiscing
{% endraw %}
```

## Array Extension

```yml
# app/config/services.yml

services:
    twig.extension.array:
      class: Twig_Extensions_Extension_Array
      tags:
        - { name: twig.extension }
```

### shuffle

Use the `shuffle` filter to randomly reorder an array.

```twig
{% raw %}
{% set myArray = [1, 2, 3, 4, 5] %}
{% set myArrayShuffled = myArray|shuffle %} => [5, 1, 3, 4, 2]
{% endraw %}
```

## Date Extension

```yml
# app/config/services.yml

services:
    twig.extension.date:
      class: Twig_Extensions_Extension_Date
      tags:
        - { name: twig.extension }
```

### time_diff

Use the `time_diff` filter to render the difference between a date and now.

```twig
{% raw %}
{{ post.published_at|time_diff }}
{% endraw %}
```

## Intl Extension

```yml
# app/config/services.yml

services:
    twig.extension.intl:
      class: Twig_Extensions_Extension_Intl
      tags:
        - { name: twig.extension }
```

### localizeddate

Use the `localizeddate` filter to format dates into a localized string representating the date.

> localizeddate(date_format, time_format, locale, timezone, format, calendar)

```twig
{% raw %}
{{ post.published_at|localizeddate('medium', 'none', locale) }}
{% endraw %}
```

### localizednumber

Use the `localizednumber` filter to format numbers into a localized string representating the number.

> localizednumber(style, type, locale)

```twig
{% raw %}
{{ product.quantity|localizednumber }}
{% endraw %}
```

### localizedcurrency

Use the `localizedcurrency` filter to format a currency value into a localized string.

> localizedcurrency(currency, locale)

```twig
{% raw %}
{{ product.price|localizedcurrency('USD') }}
{% endraw %}
```
