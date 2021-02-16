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

## Eksempel 4 - Animasjon med flere CSS-egenskaper

<iframe width="900" height="600" title="Animasjonshastighet" src="https://svelte.dev/repl/9d0636ff75f2412599ea6aa6a03b4f2a?version=3.32.3" scrolling="no"></iframe>

## Eksempel 5 - Step-animasjon

```HTML
<h1>Step-animasjon</h1>

<script>
	const deltakere = [
		{
			navn: "Aksel Lund Svindal",
			bilde: "aksel.jpg",
			beskrivelse: "En av tidenes største alpinister med 36 rennseire i verdenscupen og 13 medaljer i VM og OL, hvorav 7 gull. Han har vunnet verdenscupen sammenlagt 2 ganger og super-G-cupen 5 ganger, utforcupen 2 ganger ganger samt storslalåmcupen og kombinasjonscupen en gang. Har også 20 NM-gull. La opp i februar 2019."
		},
		{
			navn: "Cecilie Leganger",
			bilde: "cecilie.jpg",
			beskrivelse: "Oppnådde status som verdens beste håndballkeeper allerede som 18-åring og regnes som en av tidenes beste håndballspillere. Spilte 162 landskamper og har vært med på å vinne gull, sølv og bronse i VM, gull og bronse i EM og OL-bronse. Med Slagelse og Larvik har hun vunnet Mesterligaen tre ganger, vært dansk seriemester 2 ganger, en gang dansk cupmester og vunnet Europacupen for cupvinnere 2 ganger. La opp i 2014."
		},
		{
			navn: "Johann Olav Koss",
			bilde: "johann.jpg",
			beskrivelse: "Skøytelegenden har til sammen satt 10 verdensrekorder og 18 norske rekorder. Ble olympisk mester på 1500, 5000 og 10 000 meter i 1994, alle med ny verdensrekord. Han tok også OL-gull på 1500 m og sølv på 10.000 m i 1992. Han har 3 allround VM-gull, VM-sølv og VM-bronse samt et gull og 3 sølv i EM. La opp i 1994."
		},
		{
			navn: "Øystein Pettersen",
			bilde: "oystein.jpg",
			beskrivelse: "Skiløperen med tilnavnet «Pølsa» tok OL-gull i lagsprint i Vancouver 2010 sammen med Petter Northug. Har vært på pallen 8 ganger i verdenscupen, alle i sprint, og har 5 NM-medaljer. I tillegg er han kjent som den skiløperen med flest seire i Toppidrettsveka og Blinkfestivalen på rulleski. Fra 2014 satset han på langløp og oppnådde to seire og flere pallplasser i Ski Classics. La opp i 2019."
		},
		{
			navn: "Linda Medalen",
			bilde: "linda.jpg",
			beskrivelse: "En av Norges mest meritterte fotballspillere, med 152 landskamper og 64 landslagsmål. Hun spilte på laget som vant VM-gull i 1995, VM-sølv i 1991 og vant et uoffisielt VM i 1998. Var på bronselaget under OL i 1996 og har et gull og to sølv i EM. Ble japansk seriemester og to ganger cupmester med laget Nikko, der hun var toppscorer i 1996. Med Asker er hun 4 ganger seriemester og 2 ganger cupmester. La opp i 2006."
		},
		{
			navn: "Håvard Tvedten",
			bilde: "havard.jpg",
			beskrivelse: "Debuterte for Norge mot Portugal i 2000 og har til sammen skåret 809 mål på 208 landskamper. I VM 2011 ble han kåret til verdens beste venstrekant og han ble tatt ut på verdenslaget i 2020. Vinner av Europacupen med BM Valladolid 2009, dansk mester i 2012, dansk supercupvinner 2012 og dansk sølvvinner 2013. Tok bronse i VM for klubblag med Al-skadd Lebanon 2011 og var topp 3 toppscorer i den spanske ligaen 2006-2011. La opp i 2016."
		},
		{
			navn: "Anne Margrethe Hausken Nordberg",
			bilde: "anne-m.jpg",
			beskrivelse: "Orientering er en ny sport i Mesternes mester-sammenheng. Hausken er en av våre største profiler innen idretten og har vunnet til sammen 11 VM-medaljer, hvorav 3 gull, samt 2 EM-gull. I verdenscupen har hun en totalseier og 10 enkeltseire. To ganger har hun vunnet O-ringen, det største orienteringsarrangementet i verden. Hun har vunnet NM-gull 31 ganger, hvorav 13 i stafett, og har 8 seire i orienteringsløpet Blodslitet. La opp i inneværende sesong."
		},
		{
			navn: "Magnus Midtbø",
			bilde: "magnus.jpg",
			beskrivelse: "For første gang er klatring representert i Mesternes mester. Midtbø er senior Norgesmester i sportsklatring 18 ganger, har vunnet 13 kongepokaler og er nordisk mester 7 ganger. Han har en 3. plass World Games, flere pallplasseringer i World Cup og 4. plass VM. Som junior ble han verdensmester og vant Europacupen sammenlagt 3 ganger. Han er én av seks i verden som har klatret en rute med vanskelighetsgrad 9b, og blant fem som har gått 8c+ onsight (på første forsøk uten forkunnskaper). La opp i 2017 og driver i dag sin egen YouTube-kanal om klatring med millioner av visninger."
		},
		{
			navn: "Synnøve Solemdal",
			bilde: "synnove.jpg",
			beskrivelse: "Solemdal har bidratt sterkt til norske stafettsuksesser i internasjonale mesterskap. Under VM i 2012, 2013, 2016 og 2020 var hun med på lagene som tok til sammen fire gull og en bronse på stafett og to gull på mix-stafett . Hun har også to individuelle verdenscupseire i 2012 og 2013. La opp i 2020 for å bli student på heltid."
		},
		{
			navn: "Genette Våge",
			bilde: "genette.jpg",
			beskrivelse: "Tidenes yngste deltaker i Mesternes mester har vært blant verdens beste kvinnelige motocrossførere, med 5.plass i VM, 2 gull og 3 sølv i NM og 2 sølv i Svensk Mesterskap. Hun er den første jenta i Norgeshistorien som har kommet på NM-pallen med gutta, og den eneste i Skandinavia som har kvalifisert seg til AMA Amateur National -løpet i USA uansett kjønn - og det to ganger. Kåret til Årets kvinnelige motorsportutøver i 2014 og 2015 og Årets kvinnelige motorsportutøver i 2015. I 2015 ble hun som den første kvinne i historien kåret til Årets motorsportutøver. Måtte legge opp i 2018 på grunn av en bruddskade."
		}
	]
	import { onMount } from "svelte";

	let innerramme;

	onMount(() => {
		let innerKeyframes = [{
			transform: "translateY(0px)"
		},{
			transform: "translateY(-5000px)"
		}];

		let innerOptions = {
			duration: 30000,
			easing: "steps(10)"
		};

		innerramme.animate(innerKeyframes, innerOptions);
	})
</script>

<div id="ytterramme">
	<div bind:this={innerramme} id="innerramme">
		{#each deltakere as deltaker}
			<div class="deltaker">
				<h2>{deltaker.navn}</h2>
				<img src="{deltaker.bilde}" alt="">
				<p>{deltaker.beskrivelse}</p>
			</div>	
		{/each}
	</div>
</div>


<style>
	#ytterramme{
		height: 500px;
		overflow: hidden;
	}
	.deltaker{
		height: 500px;
	}
	img{
		width: 500px;
	}
</style>
```