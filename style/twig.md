# Twig

We use Twig for templating on WordPress. These rules can and should carry over to Drupal's and any custom PHP application (presumably using Symfony or Laravel) using Twig and JavaScript applications using [Nunchucks](https://github.com/mozilla/nunjucks) for templating. 

* General Style
* Conventions

## General Style
This can all be found on Twig's [official documentation](http://twig.sensiolabs.org/doc/coding_standards.html). Placing here incase it ever changes. 

We use __two spaces__ for indentation rather than tabs. 

Put one (and only one) space after the start of a delimiter ({{, {%, and {#) and before the end of a delimiter (}}, %}, and #}):

```html
{{ foo }}
{# comment #}
{% if foo %}{% endif %}
```

When using the whitespace control character, do not put any spaces between it and the delimiter:

```
{{- foo -}}
{#- comment -#}
{%- if foo -%}{%- endif -%}
```

Put one (and only one) space before and after the following operators: comparison operators (==, !=, <, >, >=, <=), math operators (+, -, /, *, %, //, **), logic operators (not, and, or), ~, is, in, and the ternary operator (?:):

```
{{ 1 + 2 }}
{{ foo ~ bar }}
{{ true ? true : false }}
```

Put one (and only one) space after the : sign in hashes and , in arrays and hashes:

```
{{ [1, 2, 3] }}
{{ {'foo': 'bar'} }}
```

Do not put any spaces after an opening parenthesis and before a closing parenthesis in expressions:

```
{{ 1 + (2 * 3) }}
```

Do not put any spaces before and after string delimiters:

```
{{ 'foo' }}
{{ "foo" }}
```

Do not put any spaces before and after the following operators: |, ., .., []:

```
{{ foo|upper|lower }}
{{ user.name }}
{{ user[name] }}
{% for i in 1..12 %}{% endfor %}
```

Do not put any spaces before and after the parenthesis used for filter and function calls:

```
{{ foo|default('foo') }}
{{ range(1..10) }}
```

Do not put any spaces before and after the opening and the closing of arrays and hashes:

```
{{ [1, 2, 3] }}
{{ {'foo': 'bar'} }}
```

Use lower cased and underscored variable names:

```
{% set foo = 'foo' %}
{% set foo_bar = 'foo' %}
```

Indent your code inside tags (use the same indentation as the one used for the target language of the rendered template):

```
{% block foo %}
   {% if true %}
       true
   {% endif %}
{% endblock %}
```


## Conventions

### Macros vs. Includes
There is a good [SO discussion](http://stackoverflow.com/questions/7630945/twig-macros-vs-includes) on the difference, but in general we prefer includes over macros. In most of our work includes seem much easier and just as flexible, and not having to place `import` statements at the top of each page keeps the template a little bit cleaner.  

Passing parameters to include files using `with` affords us most of the functionality we would need. A common use might be a shared include for displaying an article preview, but that preview may need to change display based on context. If we were making simple adjustments, adding modifier classes to certain elements, we can pass values to the import:

```
{# index.twig #}
{% for article in articles %}
	{% include "modules/article-preview.twig" with { 'article': article, 'mode': 'tall' } only %}
{% endfor %}
```

And our include would look like:

```html
{# mocules/article-preview.twig #}
{# article [object] the article content that we're passing in #}
{# mode [string] adds a modifier class to the container to control display #}

<article class="article article--{{ mode }}">
	<h2>{{ article.title }}</h2>
	<p>{{ article.title }}</p>
</article>
```

Be sure to note which parameters the include can accept and describe how they are used. 

The `only` keyword prevents any other values from being passed to the file, so any global values such as `{{ theme.link }}` are called in the fragment it will not render. In most cases, `only` can be avoided.

If you find common code being used in more than two places, it should be converted to an include.

### Templates and HTML

Keep templates as spartan as possible. While it is possible in Twig, avoid complex sets of conditional statements in favor of placing that logic in a PHP via Twig filters.

Because each template should yield one component/module/fragment, most files should be fewer than 100 lines tall. Avoid excessive line breaks and use a break only to separate the top of a comment from the HTML above it. If the page is too difficult to read, your markup is likely too convoluted. 

 

