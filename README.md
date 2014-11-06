# Reveal.js with i18n translation files

This sample project shows how to build slides with reveal.js in different languages. 

## Test it
To replace the slides content with a specific language you need add the query parameter *lang* to the url:

```
http://127.0.0.1:8000/?lang=de
```

reveal.js need to be started in server mode in order to find the external language files:

```
npm install
grunt serve
```

## How does it work
The *index.html* page contains the slides for the default language. The directory *i18n* followed by a language code contains the corresponding slides for this language, e.g.

```
i18n/de
```

The *js/i18n.js* is included in the *index.html*. If the *lang* query parameter is set, the javascript finds all slides by the class *.content* and replaces the default content with the content of the given language. The *id* attribute of the specific slide represents the language file name. The format of the file is automatically detected by the javascript code. So don&#39;t specify the format in the *id* attribute itself. *HTML* and *Markdown* are supported as formats.

```
<section class="content" id="second" data-markdown><script type="text/template">
##Default language
</script></section>
```

The slide above tries to find the file *i18n/de/second.md* in case the language code *de* has been specified in the url. *data-markdown* indicates that the external file needs to be a markdown file

```
<section class="content" id="third">
<h2>Default language</h2>
</section>
```

This slide tries to find the file *i18n/de/third.html* in case the language code *de* has been specified in the url. No *data-markdown* attribute is set so the external file format *.html* is used.