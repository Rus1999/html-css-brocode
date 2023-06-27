### Structure
```html
<!DOCTYPE html>
<html>
	<head>
		<title>Website Title</title>
	</head>
	<body>
		...
			content
		...
	</body>
</html>
```

### meta
```html
<!-- infomation about data -->
<meta
	charset="character_set"
	name="application-name | author | description | generattor | keywords | viewport"
	http-equiv="content-security-policy | content-type | default-style | refresh"
	content="text" <!-- value associated with http-equiv or name attribute -->
>

<!-- example -->
<!-- Define keywords for search engines: -->
<meta name="keywords" content="HTML, CSS, JavaScript">

<!-- Define a description of your web page: -->
<meta name="description" content="Free Web tutorials for HTML and CSS">

<!-- Define the author of a page: -->
<meta name="author" content="John Doe">

<!-- Refresh document every 30 seconds: -->
<meta http-equiv="refresh" content="30">

<!-- Setting the viewport to make your website look good on all devices: -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### Link
```html
<!-- link defines relationship between the current document and an external resource -->
<link>

<!-- favicon -->
<!-- supported file type: .ico, .png, .gif, .jpg, .svg -->
<!-- minimum file type 96*96 pixels -->
<link rel="icon" type="image/jpg" href="path">
```

### Header
```html
<h1> text </h1>
<h2> text </h2>
<h3> text </h3>
<h4> text </h4>
<h5> text </h5>
<h6> text </h6>
```

### Paragraph
```html
<!-- ignore space and new line -->
<p> text </p>

<!-- preformated include all space and new line -->
<pre> text </pre>
```

### Hyperlink
```html
<a 
	 href="link | path | mailto:email@example.com"
	 target="_blank | _parent | _self | _top"
	 title="tooltips text"
>
	 link text
</a>
```

### Images
```html
<img 
	src="path, link"
	alt="alternative text"
	height="size" 
	width="size"
	border="size"
>
```

### Media
```html
<!-- audio -->
<audio controls autoplay muted loop>
	<source src="path/file.mp3" type="audio/mpeg">
	<source src="path/file.wav" type="audio/wav"> <!-- backup when mp3 failed -->
</audio>

<!-- video -->
<video 
	 src="path"
	 height="size"
	 width="size"
>
	<source src="path/file.mp4" type="video/mp4">
	<source src="path/file.webm" type="video/webm"> <!-- backup when mp4 failed -->
</video>

<!-- common attributes -->
<tag 
	controls <!-- show media player control -->
	autoplay <!-- play when loaded -->
	muted <!-- muted when play -->
	loop <!-- loop when end -->
>
</tag>

```

### Text Formatting
```html
<b> bold text </b>
<i> italic </i>
<u> underlined </u>
<del> strikethrough </del>
<big> big </big>
<small> small </small>
<sub> subscript </sub>
<sup> superscript </sup>
<tt> monospaced (character width have all the same size) </tt>
<mark> highlighted </mark>
```

### Container Group
```html
<!-- inline container grouping -->
<span> ... </span> <span> ... </span> <span> ... </span>

<!-- block container grouping -->
<!-- take up whole line -->
<div> ... </div>
<div> ... </div>
<div> ... </div> 
```

### List
```html
<!-- Unordered List -->
<ul> <!-- bullet -->
	<li>list1</li>
	<li>list2</li>
	<li>list3</li>
	<ul> <!-- nested -->
		<li>list3.1</li>
		<li>list3.2</li>
	</ul>
</ul>

<!-- Ordered List -->
<ol> <!-- number -->
	<li>list1</li>
	<li>list2</li>
	<li>list3</li>

	<ol> <!-- nested -->
		<li>list3.1</li>
		<li>list3.2</li>
	</ol>
</ol>

<!-- Description List -->
<dl>
	<dt>list1</dt>
		<dd>description</dd>
	<dt>list2</dt>
		<dd>description</dd>
</dl>

```

### Table
```html
<table border="size">
	<tr>
		<th>header1</th>
		<th>header2</th>
		<th>header3</th>
	</tr>
	<tr>
		<td>h1 row1</td>
		<td>h2 row1</td>
		<td>h3 row1</td>
	</tr>
</table>
```

### Align
```html
<!-- supported tags -->
<caption>
<hr>
<iframe>
<img>
<legend>
<table>
<tbody>
<tfoot>
<th>
<thead>

<!-- attribuet values -->
<tag align="left | right | center | justify"
```



### Self Closing tag
```html
<!-- line break -->
<br>

<!-- horizontal rule -->
<hr>


```