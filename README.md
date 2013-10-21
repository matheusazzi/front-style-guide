Front-end Styleguide
=================

Esse é um styleguide para boas práticas de front-end.

O objetivo disso é ter documentado todas as boas práticas para um desenvolvimento consistente, legível e funcional. Para servir de consulta a desenvolvedores antigos e ajuda aos novos. <b>Aqui não encontra-se a verdade absoluta</b>, apenas um apurado de todo o conteúdo disponível e que foram considerados um bom modelo.

<b>O conteúdo foi retirado da web e pertence exclusivamente a seus criadores citados nos créditos.</b>

Por favor, [Contribua](https://github.com/matheusazzi/front-style-guide/).

## Tabela de conteúdo

1. Geral
    1. Protocolo
    2. Indentação
    3. Font case
    4. Sem whitespace
    5. Codificação
    6. Comentários
    7. Páginas de erro
2. HTML Regras
    1. Documento
    2. Elementos nulos
    3. Validação HTML
    4. Semântica
    5. Multimídia fallback
    6. Separação de conceitos
    7. Entity references
    8. Tipo de atributo
    9. Formatação dos elementos
    10. HTML Quotation marks
3. CSS Regras
    1. CSS Validado
    2. Nomeação de ID e Class
    3. Separação de nomeclatura
    4. Tipo de seletores
    5. Propriedades shorthand
    6. Zero e unidades
    7. Zero à esquerda
    8. Hexadecimais
    9. CSS Hacks
    10. Organização

## Geral

### Protocolo

Omitir o protocolo (http:, https:) das URLs das imagens, midias, style sheets, scripts que estão disponíveis em ambos protocolos.

Omitir o protocolo torna a "URL relativa", evitando problemas de conteúdo misto.

Não Recomendado:
```html
<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>
```
```css
.example {
	background: url('http://www.google.com/images/example');
}
```

Recomendado:
```html
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```
```css
.example {
	background: url('//www.google.com/images/example');
}
```

### Indentação

Apenas um estilo deve existir em todo o projeto. Seja sempre consistente na utilização de espaços em branco. Use espaços em branco para melhorar a legibilidade.

Nunca misture espaços e tabs para indentação.

Escolha entre indentação suave (espaços) ou tabulação. Atenha-se à sua escolha sem falhar. (Preferência: espaços)
Se usar espaços, escolha o número de caracteres usados por nível de indentação. (Preferência: 4 espaços)

<b>Dica:</b> configure seu editor para "mostrar invisíveis". Isso irá permitir que você elimine espaços em branco da quebra de linha, elimine espaços em branco de linhas vazias sem indentação e evite commits poluídos.

<b>Dica:</b> use um [EditorConfig](http://editorconfig.org/) arquivo (ou equivalente) para ajudar a manter a convenção básica de espaços em branco que você aceitou para sua base de código.

```html
<ul>
	<li>Fantastic</li>
	<li>Great</li>
</ul>
```
```css
.example {
	color: blue;
}
```

### Font case

Sempre use minúsculo.

Todo o código deve estar em letras minúsculas: Isso se aplica a nomes de elementos HTML, atributos, valores de atributos (exceto text/CDATA), seletores CSS, propriedades e valores de propriedade (com exceção de strings).

Não recomendado:
```html
<A HREF="/">Home</A>
```
```css
.example {
	color: #E5E5E5;
}
```

Recomendado:
```html
<img src="google.png" alt="Google">
```
```css
.example {
	color: #e5e5e5;
}
```

### Sem whitespace

Remova os espaços em branco, eles são desnecessários e podem complicar o uso de ferramentas de diff.

Não recomendado:
```html
<p>Lorem ipsum.   </p>
```
Recomendado:
```html
<p>Lorem ipsum.</p>
```
### Codificação

Use UTF-8 (sem BOM).

Verifique se o seu editor usa UTF-8 (sem BOM) como codificação de caracteres.

Especifique a codificação em arquivos HTML via `<meta charset="utf-8">`.

Não especifique a codificação de folhas de estilo.

### Comentários

Comente o código quando achar necessário, seja cauteloso, o excesso também pode prejudicar.

Isso dependerá da complexidade do projeto.

### Páginas de erro

Sempre tenha páginas de erro para seu projeto ou forneça algum fallback para o usuário.

É recomendado ao menos fornecer a página de erro 404 (Página não encontrada).

## HTML Regras

### Documento

Use HTML5 sempre!

A sintax HTML5 deve ser definida em todos os documentos HTML usando:
```html
<!DOCTYPE html>
```

Para uma melhor organização e suporte da sua aplicação, utilize a notação abaixo, com ela você fornecerá fallback a navegadores antigos mais facilmente.

```html
<!DOCTYPE html>
<!--[if lt IE 7]>      <html lang="pt-BR" class="no-js lt-ie9 lt-ie8 lt-ie7"> <![endif]-->
<!--[if IE 7]>         <html lang="pt-BR" class="no-js lt-ie9 lt-ie8"> <![endif]-->
<!--[if IE 8]>         <html lang="pt-BR" class="no-js lt-ie9"> <![endif]-->
<!--[if gt IE 8]><!--> <html lang="pt-BR" class="no-js"> <!--<![endif]-->
```

### Elementos nulos

Não feche elementos nulos, ou seja, use `<br>`, não `<br />`.

### Validação HTML

Use HTML validado sempre que possível.

Use ferramentas como o W3C HTML validator para teste.

Não recomendado:
```html
<span>
	<ul>
		<a href="#">Lorem ipsum</a>
		<br>
		<a href="#">Lorem ipsum</a>
	</ul>
</span>
```
Recomendado:
```html
<div>
	<ul>
		<li>Lorem ipsum</li>
		<li>Lorem ipsum</li>
		<li>Lorem ipsum</li>
	</ul>

	<p>Lorem ipsum sit amet</p>
</div>
```
### Semântica

Use HMTL de acordo com seu propósito.

- Use os elementos ("tags") para o objetivo que eles foram criados. Por exemplo, use `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>` para cabeçalhos ou itens importantes, `<p>` para parágrafos, `<a>` para âncoras, etc.
- Cada parágrafo deve estar dentro de uma tag `<p>`. Nunca use `<br/>` para criar multiplos parágrafos.
- Itens em forma de lista sempre devem estar dentro de `<ul>`, `<ol>`, ou `<dl>`, Nunca use `<div>` ou `<p>`.
- Cada texto atrelado a um input de formulário deve utilizar a tag `<label>`. Especialmente elementos radio ou checkbox.
- Mesmo que usar aspas duplas (" ") em atributos seja opcional, <b>sempre</b> as declare para tornar o código mais legível.
- Sempre declare um `<title></title>` para cada página.

Usar HTML de acordo com seu propósito é importante para semântica, acessibilidade, reúso, e código eficiente.

Não recomendado:
```html
<div onclick="goToContact();">Contato</div>
```
Recomendado:
```html
<a href="contato" title="Contato">Contato</a>
```
### Multimídia fallback

Forneça alternativas para conteúdos multimídia.

Para mídias, como imagens, videos, objetos animados via canvas, tenha certeza de oferecer alternativas de acesso. Para imagens use `alt=""` e para videos e audios use legendas ou texto, se disponíveis.

Não recomendado:
```html
<img src="logotipo.png">
```
Recomendado:
```html
<img src="logotipo.png" alt="Empresa FooBar">
```
### Separação de conceitos

Separe a estrutura da apresentação e do comportamento.

Separe estritamente a estrutura (markup), apresentação/estilo (style sheet), e comportamento (scripts), mantendo eles cada um no seu arquivo mas com as suas interações.

Separar a estrutura da apresentação e comportamento é muito importante por motivos de manutenção. 

É sempre mais custoso para alterar documentos que não estão bem estruturados.

Não recomendado:
```html
<!DOCTYPE html>
<html>
	<head>
		<title>HTML sucks</title>
		<style>
			body {
				background-color: #888;
				color: #fff;
			}
		</style>
		<script>
			alert('HTML sucks!!!!!');
		</script>
	</head>

	<body>
		<h1 style="font-size: 20px;">HTML Sucks</h1>
		<p style="font-size: 10px; color: #333; margin: 0 15px 10px;">Lorem ipsum dolor</p>
		<h2 padding-top: 40px; color: red;>HTML is stupid!!1</h2>
		<center>Lorem ipsum dolor sit amet, consectetur adipisicing elit</center>
	</body>
</html>
```
Recomendado:
```html
<!DOCTYPE html>
<html>
	<head>
		<title>My first CSS-only redesign</title>
		<link rel="stylesheet" href="css/main.css">
	</head>

	<body>
		<h1>My first CSS-only redesign</h1>
		<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit.</p>
		<h2>It's awesome!</h2>
		<script src="js/main.js"></script>
	</body>
</html>
```

### Entity references

Não use entity references.

Não é necessário utilizar entity references como `&mdash;`, `&rdquo;`, ou `&#x263a;`, assumindo que você está utilizando codificação UTF-8.

As únicas exceções se aplicam a caracteres com significado especial em HTML (como `<` e `&`), bem como caracteres "invisíveis" (como `&nbsp;`).

Não recomendado:

O simbolo atual para o Euro é `&ldquo;&eur;&rdquo;`.

Recomendado:

O simbolo atual para o Euro é `£`.

### Tipo de atributo

Omita o tipo `type=""` para as folhas de estilo e scripts.

Não use o atributo type para folhas de estilo (a não ser que não usar CSS) e scripts (a não ser que não usar JavaScript).

Não é necessário especificá-los, o HTML5 tem como padrão `text/css` para folhas de estilos e `text/javascript` para scripts.

Isso pode ser feito com segurança, mesmo para navegadores mais antigos.

Não recomendado:
```html
<link type="text/css" rel="stylesheet" href="//www.google.com/css/maia.css">
<script type="text/javascript" src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```
Recomendado:
```html
<link rel="stylesheet" href="//www.google.com/css/maia.css">
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

### Formatação dos elementos

Use uma nova linha para cada elemento block, list ou table, e indente todos seus elementos filhos.

Independente do estilo de um elemento (o CSS permite que aos elementos assumir um papel diferente através da propriedade display), coloque cada elemento block, list ou table em uma nova linha.

Também indente mesmo que sejam filhos de outro elemento block, list ou table.
```html
<blockquote>
  	<p><em>Space</em>, the final frontier.</p>
</blockquote>

<ul>
	<li>Moe</li>
	<li>Larry</li>
	<li>Curly</li>
</ul>

<h1>HTML Rocks!</h1>

<table>
  	<thead>
    	<tr>
			<th scope="col">Income</th>
			<th scope="col">Taxes</th>
  		</tr>
  	</thead>
  	<tbody>
    	<tr>
      		<td>$ 5.00</td>
      		<td>$ 4.50</td>
		</tr>
  	</tbody>
</table>
```

### HTML Quotation marks

Sempre use aspas duplas no arquivo html.

Use aspas duplas (" ") ao invés de simples (' ').

Use (' ') para JavaScript e CSS.

Não recomendado:
```html
<a class='bt bt-primary'>Login</a>
```
Recomendado:
```html
<a class="bt bt-primary">Login</a>
```
## CSS Regras

### CSS Validado

Use CSS válidado sempre que possível. Pois isso também pode ajudar a garantir a qualidade do seu código.

### Nomeação de ID e Class

Use nomes significantes e genéricos para classes e IDs.

Em vez de nomes descritivos ou enigmáticos, sempre use nomes que refletem o propósito do elemento em questão, ou que são de maneira genérica.

O uso de nomes funcionais e genéricos reduz a probabilidade de documentação desnecessária e mudanças na estrutura.

Além disso, a prática de nomes genéricos é melhor, pois sendo muito específico toda vez que o layout precisar ser alterado você precisará mudar o nome do(a) ID/classe se for muito específico e não condizer com o novo layout.

Não recomendado:
```css
#navigation {} /* Nomeclatura extensa desnecessária. */
.bt-verde-maior {} /* Classe usada somente para um botão verde grande. */
.bt-green {} /* Fixada a cor verde, caso precisar mudar a cor, precisará trocar a classe, alterando o html. */
#login-area {} /* Nome composto sem necessidade. */
#left-bar {} /* Fixado que é uma barra no lado esquerdo, se for preciso mudar para o lado direito precisará alterar o html. */
.images-lists {} /* Somente imagens. */
```
Recomendado:
```css
#nav {} /* Nomeclatura simples, sem perder o sentido. */
.bt-secondary {} /* Um botão diferente do botão padrão. */
.bt-big {} /* Contém propriedades para aumentar o tamanho padrao de .bt */
#login {} /* Area de login. */
#sidebar {} /* Barra lateral. */
.gallery {} /* Pode ser galeria de imagens, videos, audio. */
```

### Separação de nomeclatura

Separe as palavras em IDs e Classes com um "-".

Não concatene palavras em um seletor.

Ter um padrão definido ajuda para não haver nomes conflitando e em manutenções.

Não recomendado:
```css
#videoid
.bt_big
.titlePage
```
Recomendado:
```css
#video-id
.bt-big
.title-page
```

### Tipo de seletores

Evite utilizar tipos de seletores em IDs e Classes.

A menos que seja necessário, sempre deve evitar essa prática.

Evitando seletores ancestrais desnecessários também ajudará na performance do seu site.

Não recomendado:
```css
ul#products {}
h2.title-page {}
div.error {}
```
Recomendado:
```css
#products {}
.title-page {}
.error {}
```

### Propriedades shorthand

Não recomendado:
```css
border-top-style: none;
font-family: Arial, tahoma, sans-serif;
font-size: 16px;
line-height: 1.4;
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;
```
Recomendado:
```css
border-top: 0;
font: 16px/1.4 Arial, tahoma, sans-serif;
padding: 0 1em 2em;
```

### Zero e unidades

Omita a especificação da unidade quando o valor for "0".

Pois zero é zero em qualquer unidade, então é desnecessária essa informação.

Não recomendado:
```css
margin: 0px;
```
Recomendado:
```css
padding: 0;
border: 0;
```

### Zero à esquerda

Omita o "0" na frente de valores entre -1 e 1, não é necessário.
```css
font-size: .8em;
opacity: .5;
```

### Hexadecimais

se 3 characteres hexadecimais quando possível.

Para cores isso é permitido, 3 characteres hexadecimais é melhor para digitar e mais sucinto.

Não recomendado:
```css
color: #eebbcc;
background-color: #666666;
```
Recomendado:
```css
color: #ebc;
background-color: #666;
```

### CSS Hacks

Não utilize CSS Hacks!

Essa é uma prática muito ruim e pode gerar algumas complicações.

Utilize uma abordagem diferente com fallbacks, seja utilizando o [Modernizr](http://modernizr.com/) ou com a declaração de navegadores antigos no comentário do início da página.

```css
.no-csstransitions seletor { ... }
.lt-ie9 seletor { ... }
```

## CSS Style Rules

### Comentários

Código bem comentado é extremamente importante. Tire tempo para descrever componentes, como eles funcionam, suas limitações, e o modo como são construídos. Não deixe outros no time adivinharem o propósito de códigos incomuns ou não óbvios.

Estilo de comentário deve ser simples e consistente dentro de uma única base de código.

- Coloque comentários em uma nova linha acima do seu assunto.
- Evite comentários no fim da linha.
- Mantenha o comprimento da linha a um máximo sensível, por exemplo, 80 colunas.
- Faça o uso liberal de comentários para quebrar o código CSS em seções distintas.
- Use comentários com iniciais maiúsculas e indentação de texto consistente.
- Dica: configure seu editor para lhe prover com atalhos a geração do padrão de comentários acordado.

```css
/* ==========================================================================
   Bloco de comentário de seção
   ========================================================================== */

/* Bloco de comentário de sub-seção
   ========================================================================== */

/*
 * Bloco de comentário de grupo
 * Ideal para explicações em múltiplas linhas e documentação.
 */

/**
 * Breve descrição usando o estilo de formato de comentário Doxygen
 *
 * A primeira frase da descrição longa começa aqui e continua
 * nesta linha por um tempo finalmente concluindo aqui no final deste parágrafo.
 *
 * A descrição longa é ideal para explicações mais detalhadas e documentação.
 * Ele pode incluir HTML exemplo, URLs, ou qualquer outra informação
 * que seja considerada necessária ou útil.
 *
 * @tag Esta é uma tag chamada 'tag'
 *
 * @todo Esta é uma declaração de tarefas que descreve uma tarefa atômica para ser 
 * concluída numa data posterior. Ela envolve depois de 80 caracteres e as linhas a
 * seguir são Recuado por dois espaços.
 */

/* Comentário básico */
```

### Formatação

Para um CSS consistente é necessário ter sempre um espaçamento e indentação padronizada. Ajudando a tornar o código mais legível.

O formato de código escolhido deve garantir que o código seja: fácil de ler; fácil de comentar claramente; minimize a chance de introduzir erros acidentalmente; e resulte em úteis visualizações de diferença.

- Um seletor discreto por linha em um conjunto de regras com multi-seletores.
- Um único espaço antes da abertura das chaves em um conjunto de regras.
- Uma única declaração por linha em um bloco de declarativo.
- Um nível de indentação para cada declaração.
- Um único espaço depois dos dois pontos de uma declaração.
- Use valores minúsculos e abreviações hexadecimais, por exemplo, #aaa.
- Use aspas simples ou duplas de forma consistente. Preferência é por aspas duplas,    por exemplo, conteúdo:" ".
- Citação valores de atributos em seletores, por exemplo, input [type="checkbox"].
- Onde for permitido, evitar especificar unidades para zero valores, por exemplo, margin: 0.
- Inclua um espaço após cada vírgula em propriedades separadas por vírgula ou valores de funções.
- Sempre inclua um ponto-e-vírgula no fim da última declaração em um bloco declarativo.
- Coloque o fechamento das chaves na mesma coluna que o primeiro caracter do conjunto de regras.
- Separe cada conjunto de regras por uma linha em branco.

Não recomendado:
```css
.selector-1,.selector-2{
    border:1px solid;
    color:#333;
    position:absolute;
}
.selector-3{
    margin:0;
    background-color:red;
}
```
Recomendado:
```css
.selector-1,
.selector-2 {
    border: 1px solid;
    color: #333;
    position: absolute;
}

.selector-3 {
    margin: 0;
    background-color: red;
}
```

#### Exceções e ligeiros desvios

Quando é necessário a declaração de apenas uma propriedade, podemos declarar de forma mais simples.
```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

### Organização

Organização de código é uma importante parte de qualquer base de código CSS, e crucial para grandes bases de código.

Separe logicamente partes distintas do código.

Use arquivos separados (concatenados por um processo de build) para ajudar a dividir o código para componentes distintos.


### Desenvolvimento em progresso.

## Créditos e Referências:

- [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
- [idiomatic.css](https://github.com/necolas/idiomatic-css)
- [Google JavaScript Style Guide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
- [Github Style Guide](https://github.com/styleguide)
- [Douglas Crockford's Code Conventions for JavaScript](http://javascript.crockford.com/code.html)
- [idiomatic.js](https://github.com/rwldrn/idiomatic.js/)
- [Zeno Rocha Coding Style](https://github.com/zenorocha/my-coding-style)
- [jQuery JavaScript Style Guide](http://contribute.jquery.org/style-guide/js/)
- [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
- [Mozilla JavaScript](https://developer.mozilla.org/en-US/docs/Developer_Guide/Coding_Style#JavaScript_practices)
