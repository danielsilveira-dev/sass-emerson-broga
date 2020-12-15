# SASS

<a href="#variaveis">Variáveis</a> |
<a href="#maps">Maps</a> |
<a href="#funcoes">Funções</a> |
<a href="#dark">Darken</a> |
<a href="#media">Media Queries</a> |

- <a href="https://sass-lang.com/">Site</a>
- <a href="https://sass-lang.com/documentation">Documentação</a>

## Plugins Necessários

- Sass Live Compiler
- Live Server

1. Para começar, crie um arquivo `index.html` e depois crie um arquivo `main.scss`.
2. Após criado os arquivos, na barra de status, clique em Watch Sass para o VS Code ficar "monitorando" o arquivo SCSS. (Caso fechar o VS Code, você deverá clicar em Watch Sass novamente).
3. Assim que você clicar no Watch Sass, irá gerar mais dois arquivos:

- `main.css` e `main.css.map`

No scss você pode definir as regras de forma aninhada, conforme abaixo:

```scss
body {
  background: blueviolet;
  color: #fff;
  h1 {
    color: yellow;
  }
}
```

<h2 id="variaveis">Variáveis</h2>
As variáveis, podem ser definidas da seguinte forma:

```scss
$primary-color: yellow;
```

Como você pode perceber, usamos um cifrão na frente do nome separado por hífen.

<h2 id="maps">Maps</h2>

```scss
$primary-color: yellow; // Variável

$font-weight: (
  "regular": 400,
  "medium": 500,
  "bold",
  700,
);
```

Como você pode ver, podemos criar um map da propriedade `font-weight` no Sass, com seus atributos.

## Arquivos parciais

Podemos criar arquivos parciais dentro de uma aplicação Sass da seguinte forma:

Ao criar o arquivo, começamos com o caractere `_` e com a extensão `*.scss`.  
No arquivo principal do nosso Sass `main.scss`, importamos nosso novo arquivo Sass `_variables.scss` como no exemplo:

```scss
@import "./variables";
```

<h2 id="funcoes">Funções</h2>

```scss
@function weight($key) {
  // Na função posso passar o que quero fazer com ela, no caso weight($atributodopeso)
  @return map-get($font-weight, $key);
}

h1 {
  color: $primary-color;
  font-weight: weight(
    bold
  ); // Depois só colocar o valor do weight que você quer escolher pra usar a função
}
```

<h2>Mixins</h2>
Trecho de código onde você vai querer repetir dentro da estilização

```scss
@function weight($key) {
  @return map-get($font-weight, $key);
}

@mixin flexCenter {
  display: flex;
  justify-content: center;
  align-items: center;
}
body {
  background: darken(#fff, 30%);
  color: #fff;
  .container {
    @include flexCenter(

    ); // Quando incluímos um mixin, precisamos incluir o mesmo conforme exemplo
    h1 {
      color: $primary-color;
      font-weight: weight(bold);
    }
    p {
      color: $primary-color;
    }
    a {
      color: $primary-color;
    }
  }
}
```

<h2 id="dark">background: darken(#fff, 30%);</h2>

Podemos inserir algumas propriedades no background dos elementos:

```scss
background: darken(#fff, 30%); // Irá escurecer a cor branco.
background: lighen(#000, 20%); // A mesma coisa para a cor preto.
```

<h2 id="media">Media Queries</h2>

```scss
@media (max-width: 768px) {
  height: auto;
}
```
