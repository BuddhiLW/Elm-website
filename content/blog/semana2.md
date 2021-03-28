---
{
	"type" : "blog",
	"author" : "Branquinho",
	"title" : "Second Bootcamp Week",
	"description" : "Advances and Org-mode to writting front-end.",
	"image": "images/article-covers/recursive-draw.jpg",
	"published": "2021-03-27",
}
---

## Minha semana, {#minha-semana}

Essa semana, de  19 de  março de 2021  à 26 de março de 2021, fiz uma cópia do Instagram, como exercício no bootcamp do Responde Aí.

Agora, dia 27, eu tirei o tempo livre para aprender mais sobre diversos assuntos. Senti-me cansado durante toda a tarde. Ando bem estressado, mordendo meus lábios. 

Mas, avancei mais uma aula de Mandarim, com a magnífica professora Xiǎo (张小难老市); aprendi um pouco mais sobre CSS webkit. Aprendi que dá para produzir algumas animações e feitos simples, com CSS puro; exportei meu site (que você está lendo), para [meu repositório](https://github.com/BuddhiLW/elm-pages-starter), o qual utiliza o Netilify para integrar continuamente (CI) meu site sob commits ao repositório - meu site foi escrito em Elm.

Os próximos passos são:

-   Avançar mais duas aulas de Mandarim.
-   Linkar meu site aos trabalhos do bootcamp (disponíveis na navigation bar).

<!-- Algumas coisas maneira que podem ser feitas com CSS, no presente. -->

<!-- Com Bulma: -->

<!-- <\!-- <button class="button is-loading"> -\-> -->
<!-- <\!--   Loading button -\-> -->
<!-- <\!-- </button> -\-> -->

<!-- {{< figure src="./button.gif" >}} -->

Com elocubrações (não tente isso em casa):

<!-- <script src="https://cpwebassets.codepen.io/assets/editor/iframe/iframeRefreshCSS-4793b73c6332f7f14a9b6bba5d5e62748e9d1bd0b5c52d7af6376f3d1c625d7e.js"></script> -->

Agora, um pouco do que fiz no emacs para gerar html e css, bem como a habilidade de preview, usando [ob-browser](https://github.com/krisajenkins/ob-browser).


## Using emacs-lisp code to automatically tangle the written source-blocks to actual files .css and .html. {#using-emacs-lisp-code-to-automatically-tangle-the-written-source-blocks-to-actual-files-dot-css-and-dot-html-dot}

**Preparar o arquivo .org para automaticamente linkar os blocos de código à arquivos css e html, respectivamente.**

```emacs-lisp
;; Automatically tangle our Emacs.org config file when we save it
(defun efs/org-babel-tangle-config-local ()
  (when (string-equal (buffer-file-name)
		      (expand-file-name "html-css.org"))
    ;; Dynamic scoping to the rescue
    (let ((org-confirm-babel-evaluate nil))
      (org-babel-tangle))))

(add-hook 'org-mode-hook (lambda () (add-hook 'after-save-hook #'efs/org-babel-tangle-config-local)))

```


## Creating html and css in orgmode-file and previewing it. {#creating-html-and-css-in-orgmode-file-and-previewing-it-dot}

Criando o html e css, dentro desse arquivo org, para preview.


### CSS {#css}

```css
div{
    color:blue;
    font-family: Optima;
}

div p{
    font-family: URW Gothic L;
    color: red;
}
```


### HTML {#html}

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@0.9.2/css/bulma.min.css">
    <title>Ob-browser</title>
  </head>
  <body>
    <h1 class="title"><strong>Nem tudo são divs</strong></h1>
    <div><p class="subtitle">Let's go!</p></div>
    Sim, realmente.
  </body>
</html>
```

<!-- {{< figure src="/ox-hugo/demo.png" >}} -->


### Here is my preview: {#here-is-my-preview}

**Aqui está meu preview**

{{< figure src="/home/buddhilw/PP/Org/Html-org/demo.png" >}}
