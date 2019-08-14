# Responsive images

[&#8672; *Table of contents*](/helpCenter/)

## Definition

> `src` *default source if browser don't support* `srcset`


> `srcset` *list of alternative sources*
> - **`w`** *descriptor get the image depending on image and screen width*
> - **`x`** *descriptor get the image depending on pixel density*
> - **`image-640.jpg 640w** *image name + width of this image*


> `sizes` *media query rules to get finale image*
> - *first rule checked is applied*
> - **(min-width: 1200px) 100vw** *for screen > 1200px the image should take the entire width of the screen*
> - **(min-width: 768px) 50vw** *for screen > 768px find the image who takes 50% of the entire screen*

### We can't use x and w descriptor in the same declaration

## Width descriptor

```html
  <img class="image"
    src="image-1280.jpg"
    srcset="image-640.jpg 640w,
            image-1280.jpg 1280w,
            image-1800.jpg 1800w"
    sizes="(min-width: 1200px) 100vw, (min-width: 768px) 50vw, 25vw"
    alt="Responsive image">
```

## Density descriptor

```html
  <img class="image"
    src="image.jpg"
    srcset="image.jpg 1x,
            image@2x.jpg 2x"
    alt="Responsive image">
```

## Compatibility

| IE      | Edge    | Firefox | Chrome  | Safari  | Opera   |
| ------- |:-------:|:-------:|:-------:|:-------:|:-------:|
| [ ]     | [x]     | [x]     | [x]     | [x]     | [x]     |

