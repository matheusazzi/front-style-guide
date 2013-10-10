Front-end Styleguide
=================

Esse é um styleguide para boas práticas de front-end.
Por favor, Contribua.

## Geral

### Protocolo

Omitir o protocolo (http:, https:) das URLs das imagens e midias, style sheets, scripts que estão disponíveis em ambos protocolos.

Omitindo o protocolo torna a "URL relativa", evita problemas de conteúdo misto e resulta em menores tamanhos de arquivo.

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

## Formatação geral

### Indentação

Indente o código com 4 espaços.

Use espaços para indentação, apenas 4 espaços.
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

Remove os espaços em branco.

Não recomendado:

	<p>Lorem ipsum.   </p>

Recomendado:

	<p>Lorem ipsum.</p>

## Codificação

Use UTF-8 (sem BOM).

Verifique se o seu editor usa UTF-8 (sem BOM) como codificação de caracteres.

Especificar a codificação em templates HTML e documentos via `<meta charset="utf-8">`. Não especificar a codificação de folhas de estilo.

## HTML Style Rules

### Documento

Use HTML5 sempre!

A sintax HTML5 deve ser definida em todos os documentos HTML: `<!DOCTYPE html>`.

Não feche elementos nulos, ou seja, use `<br>`, não `<br />`.

### Validação HTML

Use HTML validado quando possível.

Use ferramentas como o W3C HTML validator para teste.

Não recomendado:

	<span>
		<ul>
			<a href="#">Lorem ipsum</a>
			<br>
			<a href="#">Lorem ipsum</a>
		</ul>
	</span>

Recomendado:

	<div>
		<ul>
			<li>Lorem ipsum</li>
			<li>Lorem ipsum</li>
			<li>Lorem ipsum</li>
		</ul>

		<p>Lorem ipsum sit amet</p>
	</div>

### Semântica

Use HMTL de acordo com seu propósito.

Use os elementos ("tags") para o objetivo que eles foram criados. Por exemplo, use `h1`, `h2`, `h3`, `h4`, `h5`, `h6` para cabeçalhos ou itens importantes, `p` para parágrafos, `a` para âncoras, etc.

Usar HTML de acordo com seu propósito é importante para acessibilidade, reuso, e código eficiente.

Não recomendado:

	<div onclick="goToContact();">Contato</div>

Recomendado:

	<a href="contato" title="Contato">Contato</a>

### Multimídia Fallback

Forneça alternativas para conteúdos multimídia.

Para mídias, como imagens, videos, objetos animados via canvas, tenha certeza de oferecer alternativas de acesso. Para imagens use alt="" e para videos e audios use legendas ou texto, se disponíveis.

Não recomendado:

	<img src="logotipo.png">

Recomendado:

	<img src="logotipo.png" alt="Empresa FooBar">

### Separation of Concerns

Separate structure from presentation from behavior.

Strictly keep structure (markup), presentation (styling), and behavior (scripting) apart, and try to keep the interaction between the three to an absolute minimum.

That is, make sure documents and templates contain only HTML and HTML that is solely serving structural purposes. Move everything presentational into style sheets, and everything behavioral into scripts.

In addition, keep the contact area as small as possible by linking as few style sheets and scripts as possible from documents and templates.

Separating structure from presentation from behavior is important for maintenance reasons. It is always more expensive to change HTML documents and templates than it is to update style sheets and scripts.

Não recomendado:

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
			<h1 style="font-size: 20px;">HTML sucks</h1>
			<p style="font-size: 10px; color: #333; margin: 0 15px 10px;">I've read about this on a few sites but now I'm sure</p>
			<h2 padding-top: 40px; color: red;>HTML is stupid!!1</h2>
			<center>I can't believe there's no way to control the styling of my website without doing everything all over again!</center>
		</body>
	</html>

Recomendado:

	<!DOCTYPE html>
	<html>
		<head>
			<title>My first CSS-only redesign</title>
			<link rel="stylesheet" href="css/main.css">
		</head>

		<body>
			<h1>My first CSS-only redesign</h1>
			<p>I've read about this on a few sites but today I'm actually doing it: separating concerns and avoiding anything in the HTML of my website that is presentational.</p>
			<h2>It's awesome!</h2>
			<script src="js/main.js"></script>
		</body>
	</html>

### Entity References

Do not use entity references.

There is no need to use entity references like &mdash;, &rdquo;, or &#x263a;, assuming the same encoding (UTF-8) is used for files and editors as well as among teams.

The only exceptions apply to characters with special meaning in HTML (like < and &) as well as control or "invisible" characters (like no-break spaces).

Não recomendado:

The currency symbol for the Euro is &ldquo;&eur;&rdquo;.

Recomendado:

The currency symbol for the Euro is "".

### Type Attributes

Omit type attributes for style sheets and scripts.

Do not use type attributes for style sheets (unless not using CSS) and scripts (unless not using JavaScript).

Specifying type attributes in these contexts is not necessary as HTML5 implies text/css and text/javascript as defaults. This can be safely done even for older browsers.

Não recomendado:

	<link type="text/css" rel="stylesheet" href="//www.google.com/css/maia.css">

	<script type="text/javascript" src="//www.google.com/js/gweb/analytics/autotrack.js"></script>

Recomendado:

	<link rel="stylesheet" href="//www.google.com/css/maia.css">

	<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>

## HTML Formatting Rules

### General Formatting

Use a new line for every block, list, or table element, and indent every such child element.

Independent of the styling of an element (as CSS allows elements to assume a different role per display property), put every block, list, or table element on a new line.

Also, indent them if they are child elements of a block, list, or table element.

(If you run into issues around whitespace between list items it's acceptable to put all li elements in one line. A linter is encouraged to throw a warning instead of an error.)

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

### HTML Quotation Marks

When quoting attributes values, use double quotation marks.

Use double ("") rather than single quotation marks ('') around attribute values.

Use ('') for javascript.

Não recomendado:

	<a class='bt bt-primary'>Sign in</a>

Recomendado:

	<a class="bt bt-primary">Sign in</a>

## CSS Style Rules

### CSS Validity

Use valid CSS where possible.

Unless dealing with CSS validator bugs or requiring proprietary syntax, use valid CSS code.

Use tools such as the W3C CSS validator to test.

Using valid CSS is a measurable baseline quality attribute that allows to spot CSS code that may not have any effect and can be removed, and that ensures proper CSS usage.

### ID and Class Naming

Use meaningful or generic ID and class names.

Instead of presentational or cryptic names, always use ID and class names that reflect the purpose of the element in question, or that are otherwise generic.

Names that are specific and reflect the purpose of the element should be preferred as these are most understandable and the least likely to change.

Generic names are simply a fallback for elements that have no particular or no meaning different from their siblings. They are typically needed as "helpers."

Using functional or generic names reduces the probability of unnecessary document or template changes.

Não recomendado:

	#navigation {} // Nomeclatura extensa.
	.bt-verde-maior {} // Classe usada apenas para um botão verde grande.
	.bt-green {} // Fixada a cor verde, se necessitasse mudar a cor do layout precisaria trocar a classe, alterando o html.
	#login-area {} // Nome composto sem necessidade.
	#left-bar {} // Fixado que é uma barra no lado esquerdo se fosse preciso mudar para o lado direito precisaria alterar o html.
	.images-lists {} // Somente imagens.

Recomendado:

	#nav {} // Nomeclatura simples, sem perder o sentido.
	.bt-secondary {} // Um botão diferente do botão padrão.
	.bt-big {} // Contém propriedades para aumentar o tamanho padrao de .bt
	#login {} // Area de login.
	#sidebar {} // Barra lateral.
	.galleries {} // Pode ser galeria de imagens, videos, audio.





## Referências:

- [Google HTML/CSS Style Guide](http://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml)
- [idiomatic.css](https://github.com/necolas/idiomatic-css)
- [Google JavaScript Style Guide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
- [Github Style Guide](https://github.com/styleguide)
- [Douglas Crockford's Code Conventions for JavaScript](http://javascript.crockford.com/code.html)
- [idiomatic.js](https://github.com/rwldrn/idiomatic.js/)
- [Zeno Rocha Coding Style](https://github.com/zenorocha/my-coding-style)
- [jQuery JavaScript Style Guide](http://contribute.jquery.org/style-guide/js/)
- [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
