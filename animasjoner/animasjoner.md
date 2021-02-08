# Web animations API i Svelte

<iframe width="560" height="315" src="https://www.youtube.com/embed/Xz9lYXTyT2o" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

https://developer.mozilla.org/en-US/docs/Web/API/Element/animate

Vi kan animere HTML-elementer med javascript ved å bruke metoden `.animate` på elementene.

## Syntaks

`element.animate(keyframes, options);`

## Parametere

- `keyframes`: en **Array** med keyframe-objekter. Eks: `[{ transform: "translateX(0)" }, { transform: "translateX(100px)" }]`

- `options`: enten et **Number** med tiden på animasjonen eller et **Object** med egenskaper. Options-objektet kan ha disse egenskapene:
  - `duration`: Antall millisekunder for hver iterasjon av animasjonen. (Number)
  - `iterations`: Antall ganger animasjonen skal kjøre, `Infinity` er for alltid. (Number)
  - `delay`: Antall millisekunder før animasjonen starter. (Number)
  - `direction`: Retningen på animasjonen, kan være: `normal`, `reverse`, `alternate`, `alternate-reverse`. (String)
  - `easing`: Hvordan animasjonen endrer seg over en iterasjon, kan være: `linear`,`ease`, `ease-in`, `ease-in-out`, eller `cubic-bezier()`, [mer om easing](https://developer.mozilla.org/en-US/docs/Web/CSS/easing-function). (String)
  - `fill`: Hva som skjer med elementet når animasjonen er ferdig. `forwards` lar elementet bli slik det er ved slutten av animasjonen, `backwards` endrer det tilbake til utangspunktet. (String)

> OBS! For å bruke .animate i svelte, må vi vente til siden har lastet. Dette gjøres ved å importere funksjonen `onMount` fra svelte-biblioteket, og putte animasjonene inn i den funksjonen. Se eksempel under.

## Eksempel 1 - enkel animasjon

```HTML
<script>
    import { onMount } from "svelte";

    let kongen;
    onMount(()=> {
        kongen.animate([
            { transform: 'translateY(0px)' },
            { transform: 'translateY(-300px)' }
        ],{
            duration: 1000,
            iterations: Infinity
        });
    })
</script>

<img bind:this={kongen} src="kongen.jpg">
```

## Eksempel 2 - styre en animasjon med knapper

```HTML
<script>
	import { onMount } from "svelte";
	let kongen;
	let kongeanimasjon;

	onMount(()=> {
			// Lagrer animasjonen i en variabel
			kongeanimasjon = kongen.animate([
					{ transform: "translateY(0px)" },
					{ transform: "translateY(300px)"},
					{ transform: "translateY(100px)" }
			],{
					duration: 1000,
					direction: "alternate",
					iterations: Infinity
			});

			kongeanimasjon.pause(); // Setter animasjonen på pause når siden lastes
	});

</script>

<button on:click={() => kongeanimasjon.pause()}>Pause</button>
<button on:click={() => kongeanimasjon.play()}>Play</button>

<img bind:this={kongen} src="https://www.kongehuset.no/aim/kongehuset2/files/0/1/d/f584679f4255178f2c34bd1320d0456a0bb6253767/01df584679f4255178f2c34bd1320d0456a0bb6253767.jpg/Scale?geometry=966%3Ex" alt="Kongen">

<style>
    img{
    width: 200px;
    }
</style>
```

<iframe width="900" height="600" title="html og css" src="https://svelte.dev/repl/6d321579610942398fdbfcb10a0cc680?version=3.31.2" scrolling="no"></iframe>

## Eksempel 3 - Animasjonshastighet

Med egenskapen `.playbackRate` kan vi endre hastigheten til en animasjon, se eksempel under.

<iframe width="900" height="600" title="Animasjonshastighet" src="https://svelte.dev/repl/465bef3f336e43508309ef726bbb1e3f?version=3.32.1" scrolling="no"></iframe>
