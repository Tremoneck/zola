+++
title="Footnotes"
weight=100
+++

Zola has the ability to template footnotes and footnote references.
For this functionality you need to create a new component called
```footnote``` and ```footnote_reference```.

Both take 4 parameters.
- name: The name given by you to the footnote in the angle brackets.
- perma-link: The permanent link to the current page.
- n: The count of the footnote. Starts at one.
- nr: The count of the references to this particular footnote.

By default Zola uses the equivalent of the following templates.
```jinja
{% raw -%}
{% component footnote(perma-link, name, n, nr) %}
    <div class="footnote-definition" id="{{name}}" >
        <sup class="footnote-definition-label">{{n}}</sup>
        {{ body }}
    </div>
{% endcomponent %}
{% endraw -%}
```
```jinja
{% raw -%}
{% component footnote_reference(perma-link, name, n, nr) %}
    
    <sup class="footnote-reference" id="fr-{{name}}-{{nr}}">
      <a href="{{perma-link}}#fn-{{name}}">
        {{name}}
      </a>
    </sup>
{% endcomponent %}
{% endraw -%}
```
