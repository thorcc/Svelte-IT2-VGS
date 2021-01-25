# Objekter

Objekter er indekserte variabler, som lagrer data ved nøkler og verdier.
Et objekt lages i javascript med krøllparenteser `{}`, etterfulgt av `nøkkel: verdi`.
For hvert nytt par av nøkler og verdier skrives ett komma `,`.
For eksempel:

````javascript
let president = {
    navn: "Emmanuel Macron",
    yrke: "President"
}
````

> Det er vanlig med linjeskift for hvert nytt par med nøkkel/verdi, men det fungerer også uten linjeskift.

Vi kan hente ut, og endre, verdier fra objekter ved å bruke punkt-notasjon, eks:

````javascript
president.navn // "Emmanuel Macron"
president.yrke // "President"

president.navn = "Joe Biden" // Endrer verdien som hører til nøkkelen navn
````

Alternativ kan vi bruke firkantparenteser for å hente ut verdier, eks:

````javascript
president["navn"] // "Emmanuel Macron"
president["yrke"] // "President"

president["navn"] = "Joe Biden"
````

> Med firkantparenteser er det også mulig å hente ut egenskaper ved sende å inn variabler som nøkler, se eksempel med fotballag.

## Metoder

| Metode           | Beskrivelse                                       | Eksempel                 | Resultat                                            |
|------------------|---------------------------------------------------|--------------------------|-----------------------------------------------------|
| Object.keys()    | Lager en array med alle nøklene                   | `Object.keys(president)`    | `["navn","yrke"]`                                   |
| Object.values()  | Lager en array med alle verdiene                  | `Object.values(president)`  | `["Emmanuel","President"]`                          |
| Object.entries() | Lager en array med alle par av nøkler og verdier  | `Object.entries(president)` | `[["navn","Emmanuel Macron"],["yrke","President"]]` |

## Eksempel 1: Fra objekt til HTML med Svelte

<iframe width="900" height="600" title="objekt til html" src="https://svelte.dev/repl/366059b4d49d4016bb32443ef1a4afba?version=3.31.2" scrolling="no"></iframe>

> Legg merke til hvordan verdiene hentes ut på linje 24 og 25.

## Eksempel 2: Trommemaskin

<iframe width="900" height="600" title="trommemaskin" src="https://svelte.dev/repl/ca54fc3711fd491eb87438bdab1f4eaf?version=3.31.2" scrolling="no"></iframe>
