# htmlski
A HTML based templating language

```handlebars
<!-- Variables -->
{{ value }}
{{ foo.value }}
{{ foo['value'] }}

{{{ rawHtml }}} - Triple brackets won't be escaped

<!-- Global Variables -->
{{ _self }} - The current template
{{ _context }} - The current context

<!-- Settings Variables -->
{{> set myVar = 'Hello world' }}

<!-- If -->
<div if="myVar === true">
	Hello
</div>

<div elseif="myVar === false">
	World
</div>

<div else>
	!!!
</div>

<!-- Loops -->
<ul>
	<!-- Iterating over an array -->
	<li for="value in rows">
		{{ value.name }}
	</li>
</ul>

<ul>
	<!-- Iterating over key/value pairs (key is optional) -->
	<li for="key, value in rows">
		{{ key }}: {{ value }}
	</li>
</ul>

<ul>
	<!-- Loops are injected with the `loop` variable -->
	<li for="a in b">
		{{ loop.index }} - Current iteration index (0 indexed)
		{{ loop.first }} - Bool, true if first iteration
		{{ loop.last }} - Bool, true if last iteration
	</li>
</ul>

<ul>
	<!-- Loops can be combined with if -->
	<li for="row in rows" if="row.enabled === true">
		{{ row.title }}
	</li>
	<li else>
		Row disabled
	</li>
</ul>

<!-- Import -->
<!-- You can import templates for easy re-use -->
<!-- input.html -->
<link rel="export" as="Input" />
<meta is="prop" name="label" typeof="string" content="Default Label" />
<meta is="prop" name="type" typeof="string" /><!-- No content means prop is required? -->

<label>
	<span>{{ label }}</span>
	<input 
		type="{{ type }}"
	/>
	{{{ children }}}
</label>

<!-- form.html -->
<link rel="import" href="input.html" />
<link rel="import" href="button.html" as="MyButton" />

<Input label="Name" type="text">
	<span>Some children</span>
</Input>

<MyButton>Hello</MyButton>
```
