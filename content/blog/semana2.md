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

# Table of Contents

1.  [Minha semana,](#orgabad9f7)
2.  [Using emacs-lisp code to automatically tangle the written source-blocks to actual files .css and .html.](#org532b2be)
3.  [Creating html and css in orgmode-file and previewing it.](#orgb749298)
    1.  [CSS](#org127fc17)
    2.  [HTML](#org893a535)
    3.  [Here is my preview:](#orgc73e27d)



<a id="orgabad9f7"></a>

# Minha semana,

Essa semana, de  19 de  março de 2021  à 26 de março de 2021, fiz uma cópia do Instagram, como exercício no bootcamp do Responde Aí.

Agora, dia 27, eu tirei o tempo livre para aprender mais sobre diversos assuntos. Senti-me cansado durante toda a tarde. Ando bem estressado, mordendo meus lábios. Mas, avancei mais uma aula de Mandarim, com a magnífica professora Xiǎo (张小难老市); aprendi um pouco mais sobre CSS webkit. Aprendi que dá para produzir algumas animações e feitos simples, com CSS puro; exportei meu site (que você está lendo), para [meu repositório](https://github.com/BuddhiLW/elm-pages-starter), o qual utiliza o Netilify para integrar continuamente (CI) meu site sob commits ao repositório - meu site foi escrito em Elm.

Os próximos passos são:

-   Avançar mais duas aulas de Mandarim.
-   Linkar meu site aos trabalhos do bootcamp (disponíveis na navigation bar).

Agora, um pouco do que fiz no emacs para gerar html e css, bem como a habilidade de preview, usando [ob-browser](https://github.com/krisajenkins/ob-browser).


<a id="org532b2be"></a>

# Using emacs-lisp code to automatically tangle the written source-blocks to actual files .css and .html.

**Preparar o arquivo .org para automaticamente linkar os blocos de código à arquivos css e html, respectivamente.**

    ;; Automatically tangle our Emacs.org config file when we save it
    (defun efs/org-babel-tangle-config-local ()
      (when (string-equal (buffer-file-name)
    		      (expand-file-name "html-css.org"))
        ;; Dynamic scoping to the rescue
        (let ((org-confirm-babel-evaluate nil))
          (org-babel-tangle))))
    
    (add-hook 'org-mode-hook (lambda () (add-hook 'after-save-hook #'efs/org-babel-tangle-config-local)))


<a id="orgb749298"></a>

# Creating html and css in orgmode-file and previewing it.

Criando o html e css, dentro desse arquivo org, para preview.


<a id="org127fc17"></a>

## CSS

    div{
        color:blue;
        font-family: Optima;
    }
    
    div p{
        font-family: URW Gothic L;
        color: red;
    }


<a id="org893a535"></a>

## HTML

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

![img](demo.png)


<a id="orgc73e27d"></a>

## Here is my preview:

**Aqui está meu preview**

![img]([[file:~/PP/Front-end/Org-mode/demo.png][file:~/PP/Front-end/Org-mode/demo.png]])
