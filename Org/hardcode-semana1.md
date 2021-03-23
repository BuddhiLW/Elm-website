
# Table of Contents

1.  [Hard coding](#org3bc74a5)
    1.  [Pedrão](#orga082b5a)
        1.  [HTML e CSS, primeiro exercício](#orgedb5535)
    2.  [Pedrão Aula 2](#orgabab554)
        1.  [CSS](#org6972b51)
        2.  [HTML](#org625e808)
        3.  [Primeiro Exercício](#orgd82ddbb)
        4.  [Segundo exercício](#org0bd35aa)
        5.  [Terceiro exercício](#org72c5f6e)
        6.  [Quarto exercício](#orgd20b598)
    3.  [Pedrão Aula 3](#org5bb1402)
        1.  [keywords (kw)](#org39236a7)
    4.  [Pedrão Aula4](#orgd7c086e)



<a id="org3bc74a5"></a>

# Hard coding


<a id="orga082b5a"></a>

## Pedrão

Usaremos:

-   <https://codesandbox.io/>
-   <https://www.notion.so/bootcampra/Materiais-e9e449a49af2432c8fed55dcd0957ffa>


<a id="orgedb5535"></a>

### HTML e CSS, primeiro exercício

-   <https://codesandbox.io/>

    <!DOCTYPE html>
    <html lang="pt-br">
      <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link href="css/style.css" rel="stylesheet" type="text/css">
        <link rel="icon" href="https://clojurescript.org/images/cljs-logo-icon-32.png">
      </head>
      <body>
        <div id="app">
          <h2>Recomendados</h2>
          <p><strong>Vídeos</strong> que <em>selecionamos</em> para você</p>
        </div>
        <script src="js/compiled/globo.js" type="text/javascript"></script>
      </body>
    </html>

[Orgmode site](https://orgmode.org)

![img](/home/buddhilw/PP/Org/Bootcamp/Resources/PrimeiraSemana/Orgmode.jpg)


<a id="orgabab554"></a>

## Pedrão Aula 2


<a id="org6972b51"></a>

### CSS

    .titulo {
        font-weight: bold;
        color: gray;
    }
    
    .subtitulo{
        color: darkblue;
    }
    h1 {
        color: #A3A100;
    }

-   Usar "reset CSS" -> [Meyer Reset CSS](https://meyerweb.com/eric/tools/css/reset/)


<a id="org625e808"></a>

### HTML

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>YouTube</title>
      </head>
      <body>
        <div id="app">
          <h1 class="titulo">Pedrão sabe muito sobre front-end</h1>
        </div>
      </body>
    </html>


<a id="orgd82ddbb"></a>

### Primeiro Exercício

1.  CSS

        p {
            color: orange;
        }
        .p1 {
            text-decoration: underline;
        }
        .p2 {
            font-style: italic;
        }
        .p3 {
            font-style: italic; /* Itálico */
            text-decoration: underline;
        }

2.  HTML

        <!DOCTYPE html>
        <html lang="pt-br">
          <head>
            <meta charset="UTF-8" />
            <title>Exercício</title>
          </head>
        
          <body>
            <p class="p1">
              Find empty spot in cupboard and sleep all day and sometimes switches in
              french and say "miaou" just because well why not. Rub face on owner meow
              and walk away. Need to check on human, have not seen in an hour might be
              dead oh look, human is alive, hiss at human, feed me instantly break out
              into full speed gallop across the house for no reason.
            </p>
            <p class="p2">
              I like big cats and i can not lie i'm bored inside, let me out i'm lonely
              outside, let me in i can't make up my mind whether to go in or out, guess
              i'll just stand partway in and partway out, contemplating the universe for
              half an hour how dare you nudge me with your foot?!?! leap into the air in
              greatest offense! stuff and things sit in a box for hours bite off human's
              toes i like fish.
            </p>
            <p class="p3">
              Meow in empty rooms rub my belly hiss. Cat ass trophy side-eyes your
              "jerk" other hand while being petted yet you are a captive audience while
              sitting on the toilet, pet me kick up litter cats are the world ptracy.
              Meow loudly just to annoy owners look at dog hiiiiiisssss catty ipsum yet
              cat sit like bread. Swat at dog whenever a door is opened, rush in before
              the human that box? i can fit in that box your pillow is now my pet bed
            </p>
          </body>
        </html>
    
    -   alt/title -> contexto de imagem para mecanismos de procura


<a id="org0bd35aa"></a>

### Segundo exercício

1.  CSS

        body {
            background: #fafafa;
        }
        h1 {
            color: #333333;
        }

2.  HTML

        <!DOCTYPE html>
        <html lang="pt-br">
          <link
            rel="stylesheet"
            href="https://cdn.rawgit.com/filipelinhares/ress/master/dist/ress.min.css
        	  "
            />
          <link rel="stylesheet" href="st.css" />
          <head>
            <meta charset="UTF-8" />
            <title>Home</title>
          </head>
          <body>
            <h1>Bem-vindo à Home</h1>
          </body>
        </html>


<a id="org72c5f6e"></a>

### Terceiro exercício

-   Dimensionamento
-   Disposição

1.  CSS

    -   Usar div (division) -> ambientes locais
    -   margin-bottom
    
        body {
            background-color: #f9f9f9;
            font-family: Arial;
        }
        
        h1, h2, .titulo-video, .subtitulo-video	{
            margin-left: 20px
        }
        
        h1{
            font-size: 20px;
            font0weight: bold;
        }
        h2{
            font-size: 15px;
            color: #333
        }
        
        .titulo-video{
            font-weight: bold;
        }
        
        .subtitulo-video {
            color: gray;
        }

2.  HTML


<a id="orgd20b598"></a>

### Quarto exercício

1.  CSS

        button {
            height: 200px;
            width: 100px;
            margin-top: 200px;
        }

2.  HTML

        <!DOCTYPE html>
        <html>
          <head>
            <title>Senhora, senhora!</title>
            <meta charset="utf-8" />
          </head>
          <body>
            <h1>Senhora, senhora!</h1>
            <button>Não sou funcionária da assembleia!</button>
          </body>
        </html>


<a id="org5bb1402"></a>

## Pedrão Aula 3


<a id="org39236a7"></a>

### keywords (kw)

-   default agent stylesheet.
-   


<a id="orgd7c086e"></a>

## Pedrão Aula4

