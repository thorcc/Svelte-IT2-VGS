# Kom i gang med Svelte

Svelte er et rammeverk for å bygge nettsider.
For å lage nettsider i Svelte skriver man for det meste vanlig HTML, CSS og Javascript.
La oss se på noen eksempler:

## Hallo Verden

### HTML og CSS

Vi kan skrive HTML og CSS akkurat likt som i et vanlig HTML-dokument.

<iframe width="900" height="600" title="html og css" src="https://svelte.dev/repl/a70165bb18be44e480756b6217b9e766?version=3.29.4" scrolling="no"></iframe>

### Javascript

Javascript skrives i en egen script-tagg, også dette er helt likt som i vanlig HTML.
Men legg merke til hvordan variabelen skrives ut på nettsiden, vi bruker krøllparenteser `{}` rett i HTML-koden.
Vi har altså ingen querySelector, innerHTML eller andre DOM-metoder.

<iframe width="900" height="600" title="variabler" src="https://svelte.dev/repl/197dff4ba08f4d0794c91f6374bee8cb?version=3.29.4" scrolling="no"></iframe>

I vanlig HTML måtte vi skrevet følgende:

````html
<html>
  <body>
    <h1>Hallo <span id="navn"></span>!</h1>

    <script>
        const spNavn = document.querySelector("#navn");
        let navn = "verden"
        spNavn.innerHTML = navn;
      </script>
  </body>
</html>
````

### Knytte variabler til input-felt (*bind*)

Vi kan bruke nøkkelordet `bind` for å knytte variabler til input felt.

<iframe width="900" height="600" title="bind" src="https://svelte.dev/repl/44a8b0c529a14943b172dede12143fd9?version=3" scrolling="no"></iframe>
