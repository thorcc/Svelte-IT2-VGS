# Overganger i Svelte

The svelte/transition module exports seven functions: fade, blur, fly, slide, scale, draw and crossfade. They are for use with Svelte .

Svelte/transition modulen kommer med syv funksjoner for overganger, som kan brukes i Svelte.
Overgangene er fade, blur. fly. slide, scale, draw og crossfade.

## Fade

Animerer synligheten (opacity) til et element fra 0 til 1 for `in`, og fra 1 til 0 `out`.

> 1 er helt synlig og 0 er helt usynlig

`fade` kan ta inn følgende parametere:

- `delay` (`number`, default 0) - millisekunder før overgangen starter
- `duration` (`number`, default 400) - millisekunder overgangen varer
- `easing` (`funksjon`, default `linear`) - en ['easing'-funksjon](https://svelte.dev/docs#svelte_easing)

<iframe width="900" height="600" title="html og css" src="https://svelte.dev/repl/d1999b78b5df443e95b32347ac42922d?version=3.31.2" scrolling="no"></iframe>