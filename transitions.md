# Overganger i Svelte

[Svelte/transition](https://svelte.dev/docs#svelte_transition)  

Svelte/transition modulen kommer med syv funksjoner for overganger, som kan brukes i Svelte.
Overgangene er fade, blur. fly. slide, scale, draw og crossfade.

For å bruke overgangene må vi importere de overgangene vi skal bruke fra svelte-biblioteket.

````HTML
<script>
    import { overgang } from "svelte/transition";
</script>
````

Når overgangene er importert kan de på HTML-elementer ved attributten `transition:overgang`.

````HTML
<div transition:overgang={{parametere}}>Dette er et HTML-element</div>
````

## Fade

Animerer synligheten (opacity) til et element fra 0 til 1 for `in`, og fra 1 til 0 `out`.

> 1 er helt synlig og 0 er helt usynlig

`fade` kan ta inn følgende parametere:

- `delay` (`number`, default 0) - millisekunder før overgangen starter
- `duration` (`number`, default 400) - millisekunder overgangen varer
- `easing` (`funksjon`, default `linear`) - en ['easing'-funksjon](https://svelte.dev/docs#svelte_easing)

<iframe width="900" height="600" title="html og css" src="https://svelte.dev/repl/d1999b78b5df443e95b32347ac42922d?version=3.31.2" scrolling="no"></iframe>

## Blur

Animerer et blur filter sammen med synlighet

blur kan ta inn følgende parametere:

    - delay (`number`, default 0) — milliseconds før overgangen starter
    - duration (`number`, default 400) — milliseconds overgangen varer
    - easing (`function`, default `cubicInOut`) — en ['easing'-funksjon](https://svelte.dev/docs#svelte_easing)
    - opacity (`number`, default 0) - opacityverdien som overgagen skal gå fra og til
    - amount (`number`, default 5) - størrelsen på 'blur'-en i piksler


<iframe width="900" height="600" title="html og css" src="https://svelte.dev/repl/e8f3616c2c88482c8b67de4b4af14fa1?version=3.31.2" scrolling="no"></iframe>

## Fly

Animerer x og y posisjonene, og synligheten til et element.

fly kan ta inn følgende parametere:

    - delay (`number`, default 0) — milliseconds før overgangen starter
    - duration (`number`, default 400) — milliseconds overgangen varer
    - easing (`function`, default `cubicInOut`) — en ['easing'-funksjon](https://svelte.dev/docs#svelte_easing)
    - opacity (`number`, default 0) - opacityverdien som overgagen skal gå fra og til
    - x (`number`, default 0) - x-forskyvning som skal animeres fra og til
    - y `number`, default 0) - x-forskyvning som skal animeres fra og til

<iframe width="900" height="600" title="html og css" src="https://svelte.dev/repl/dd26bed10c6e43c9b6ee1f96793853d3?version=3.31.2" scrolling="no"></iframe>

## Slide

Sklir et element inn eller ut

slide kan ta inn følgende parametere:

    - delay (`number`, default 0) — milliseconds før overgangen starter
    - duration (`number`, default 400) — milliseconds overgangen varer
    - easing (`function`, default `cubicInOut`) — en ['easing'-funksjon](https://svelte.dev/docs#svelte_easing)

<iframe width="900" height="600" title="html og css" src="https://svelte.dev/repl/e2372fe9260a4fea948b01baa5a4aceb?version=3.31.2" scrolling="no"></iframe>

# Scale

Skalerer et element

scale kan ta inn følgende parametere:

    - delay (`number`, default 0) — milliseconds før overgangen starter
    - duration (`number`, default 400) — milliseconds overgangen varer
    - easing (`function`, default `cubicInOut`) — en ['easing'-funksjon](https://svelte.dev/docs#svelte_easing)
    - start (`number`, default 0) - skaleringsverdien som overgangen skal gå fra og til
    - opacity (`number`, default 0) - opacityverdien som overgagen skal gå fra og til


<iframe width="900" height="600" title="html og css" src="https://svelte.dev/repl/1117497bd7954af7982c41011b35bea6?version=3.31.2" scrolling="no"></iframe>

# Draw

Tegner en SVG-sti.
[Les mer om Draw på svelte.dev/docs](https://svelte.dev/docs#draw)


<iframe width="900" height="600" title="html og css" src="https://svelte.dev/repl/9e0c2644f3f94166a9e0f5ceca7ca57e?version=3.31.2" scrolling="no"></iframe>

