## W3C errors

#The first child option element of a select element

 The first child option element of a select element with a required attribute, and without a multiple attribute, and without a size attribute whose value is greater than 1, must have either an empty value attribute, or must have no text content. Consider either adding a placeholder option label, or adding a size attribute with a value equal to the number of option elements.

```html
<div class="lf-location__contact__form__sujet form-group">
     form_label(formView.children['sujet']) 
     form_widget(formView.children['sujet'], {
        'attr': {
            'required': formView.children['sujet'].vars.required,
            'multiple': false
        }, 
        'placeholder': 'Choose an option'}) 
</div>
```
