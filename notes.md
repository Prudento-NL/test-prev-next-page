# Notities voor de testsite voor het toevoegen van een vorige en voorgaande pagina onderaan een post.

## Voorbereiding:
- Nieuwe repo gemaakt op GitHub: [test-prev-next-page](https://github.com/Prudento-NL/test-prev-next-page.git).
- Files gekopieerd van de vakantie van Friesland.
- Getest en werkt. Push naar GitHub.
- Framework writings heeft de mogelijkheid in zich om de vorige/volgende pagina te kiezen. Dit wordt de bron voor de wijzigingen.

## Info
[W3Schools: Icons Tutorial](https://www.w3schools.com/icons/default.asp)  
[W3Schools: How TO - Next and Previous Buttons](https://www.w3schools.com/howto/howto_css_next_prev.asp)  
[W3Schools: How TO - Icon Buttons](https://www.w3schools.com/howto/howto_css_icon_buttons.asp)  

## Snippet toevoegen aan de layout post
De layout die gebruik wordt voor de posts is _layout/post.html.
De layout is onderdeel van de gem (in dit geval minima). Om de layout aan te passen moet de layout gekopieerd worden vanuit de gem. Zie de snippet hieronder.
N.B. Framework writings maakt ***geen*** gebruik van een gem.

Na het toevoegen van de code in post.html zijn de linken zichtbaar en werken.
Opmaak is niet netjes en het pijltje dat zichtbaar is bij Framework writings is niet aanwezig omdat de icon buttons nog niet werken.
## *TODO: Werkend maken pijltjes (of andere oplossing)*
- *Aan de linken naar de vorige/volgende pagina is een > teken toegevoegd in de originele blog.*
- *Dit wordt gedaan m.b.v. _Font Based Icons_ in dit geval &#xE001.*

### Toegevoegd aan post.html (voor `</article>`):  
```
  <!-- Previous/next page START -->
  <a class="u-url" href="{{ page.url | relative_url }}" hidden></a>
  <div class="pagination">
    {% if page.previous.url %}
    <span class="prev">
      <a href="{{ site.url }}{{ site.baseurl }}{{ page.previous.url }}">
        &#xE000; {{ page.previous.title }}
      </a>
    </span>
    {% endif %}
    {% if page.next.url %}
    <span class="next">
      <a href="{{ site.url }}{{ site.baseurl }}{{ page.next.url }}">
        {{ page.next.title }} &#xE001;
      </a>
    </span>
    {% endif %}
  </div>
  <!-- Previous/next page END -->
```

## CSS toevoegen  
Voor de opmaak moet CSS toegevoegd worden.
Kopieer de CSS uit Framework writings style.scss (deel van .pagination).  
 - code toegevoegd aan _sass/minima.scss (snippet hieronder)
  - Errors oplossen:
    - Error over mobile: uitgevinkt
    - Error over kleuren pagination: bestaande kleuren uit minima.scss gebruikt

## *TODO: Waar kunnen we dit deel van de css het beste plaatsen?*
## *TODO: Error Mobile*

### Code toegevoegd aan _sass/minima.scss  
```
/// Previous/next page START

.pagination {
  font-weight: 300;
  padding: 2em 0;
  width: 100%;
  display: inline-block;

  // UITGEVINKT: GAF EEN ERROR
  // @include mobile {
  //   font-size: $small-font-size;
  // }

  > .prev {
    float: left;
    width: 50%;
    a {
      color: $grey-color;
      &:hover, &:focus {
        color: $grey-color-dark;
      }
    }
  }

  > .next {
    float: right;
    text-align: right;
    width: 50%;
    a {
      color: $grey-color;
      &:hover, &:focus {
        color: $grey-color-dark;
      }
    }
  }
}

// Previous/next page END

```











