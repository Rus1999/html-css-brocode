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
<meta>
```
```js
// attribute
- charset="character_set"
- name="application-name | author | description | generattor | keywords | viewport"
- http-equiv="content-security-policy | content-type | default-style | refresh"
- content="text" // value associated with http-equiv or name attribute
```
```html
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
<a>hyperlink text</a>
```
```js
// attribute
- href="link | path | mailto:email@example.com"
- target="_blank | _parent | _self | _top"
- title="tooltips text"
```

### Images
```html
<img>
```
```js
// attribute
- src="path, link"
- alt="alternative text"
- height="size" 
- width="size"
- border="size"
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
```
```js
// common attributes
-	controls // show media player control 
-	autoplay // play when loaded 
-	muted // muted when play 
-	loop // loop when end 
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

### Section
```html
<header>
	<!-- block container -->
	<!-- can have more than one in one file -->
	<!-- but not inside <footer> <address> and <header> -->
	title, subtitle, logo, navbar, icon, autorship information
</header>

<nav>
	<!-- set of navigation links -->
	navigation link
</nav>

<article>
	<!-- independent, self-contained content -->
	forum post, blog post, news story
</article>

<aside>
	<!-- some content aside from the content -->
	side content, side bar
</aside>

<main>
	<!-- unique content not repeated across document such as sidebars, navigation links, copyright information, site logos, and search forms. -->
	<!-- only one in one file -->
	<!-- not inside <article>, <aside>, <footer>, <header>, or <nav> -->
	main content
</main>

<footer>
	<!-- more than one in one file -->
	authorship information, copyright information, contact information, sitemap, back to top links, related documents
	
	<address> 
		<!-- all italic -->
		<!-- block container --> 
		email address, URL, physical address, phone number, social media handle and etc.
	</address>
</footer>
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

### Button
```html
<button>button text</button>
<a><button>link button</button></a>
```
```js
// attribute 
- type="button | reset | submit"
- disabled
```

### Form
```html
<!-- structure -->
<form> 
	<!-- supported tag -->
	<input>
	<textarea> </textarea>
	<button> </button>
	<select> 
	<option> </option>
	<optgroup> </optgroup>
	<fieldset>
	<label> </label>
	<output> </output>
</form>
```
```js
// attribute
- action="path" // des that data will send to
- method="GET | POST"
- enctype="multipart/form-data" // for large file sending
```

### Input
```html
<input>
```
```js
// attribute
type="button | checkbox | color | date | datetime-local | email | file | hidden | image | month | number | password | radio | range | reset | search | submit | tel | text (default) | time | url | week "
autocomplete="on | off"
min="min val" // min value
max="max val" // max value
minlength="min char" // min characters required
maxlength="max char" // max characters allowed
placeholder="hint text" // hint user what to input
pattern="regular expression"
readonly
required // fill out required
disabled
checked
```
```html
<!-- radio button -->
<input type="radio" id="option1" value="option1" name="title">
<input type="radio" id="option2" value="option2" name="title">
<input type="radio" id="option3" value="option3" name="title">

<!-- dropdown list -->
<select>
	<optgroup label="group name">
		<option value="option1">option1</option>
		<option value="option2">option2</option>
		<option value="option3">option3</option>
	</optgroup>
</select>

<!-- checkbox -->
<input type="checkbox" id="checkbox1">
<input type="checkbox" id="checkbox2">

<!-- textarea -->
<textarea rows="size" cols="size">
	lorem500
</textarea>

<!-- file -->
<input type="file" id="file1" accept="audio/* | video/* | image/*">
```

### Label
```html
<label> </label>

<!-- defines a label for -->
<input type="checkbox">
<input type="color">
<input type="date">
<input type="datetime-local">
<input type="email">
<input type="file">
<input type="month">
<input type="number">
<input type="password">
<input type="radio">
<input type="range">
<input type="search">
<input type="tel">
<input type="text">
<input type="time">
<input type="url">
<input type="week">
<meter>
<progress>
<select>
<textarea>
```
```js
// attribute
for="element_id" // specifies element that label will bound to that element
form="from_id"
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

<!-- attribute values -->
<element align="left | right | center | justify"
```

### Width & Height
```html
<!-- supported tags -->
<input>
<img>
<video>
<iframe>
<canvas>

<!-- attribute values -->
<element width="size"> <!-- height auto -->
<element height="size"> <!-- width auto -->
<element width="size" height="size">
```

### Self Closing tag
```html
<!-- line break -->
<br>

<!-- horizontal rule -->
<hr>


```