# Wat is React?

React is een javascript library (verzameling van handige functionele tools) om web applicaties (User Interfaces / UI) te bouwen.

Hou er rekening mee dat React, in tegenstelling tot sommige andere frameworks, geen one stop shop is. React is enkel een gereeschap (tool) om front-end componenten binnen een applicatie te bouwen. Gelukkig leeft er rond React een groot ecosysteem van uitbreidingen en extra tools om naar wens extra functionaliteiten toe te voegen. React zelf is dus enkel echt de basis.

React is gebouwd door Facebook, maar is wel open source. [Je kan de broncode bekijken op Github](https://github.com/facebook/react){:target="_blank"}.

### React ❤️ Atomic Design

Het bouwen van een React applicatie gaat eigenlijk hand in hand met de principes van Atomic Design. Je bouwt eenvoudige componenten (atoms) die je combineert in complexere componenten (molecules en organismes), die je dan op pagina's (pages / buckets) kan weergeven. Omdat de componenten opgebouwd worden in Javascript, is het relatief makkelijk om data tussen componenten te delen en uit te wisselen, om zo complexe, interactieve web applicaties te bouwen.

Omdat React component based werkt, kan je je veel beter structuur en herbruikbaarheid gaan inbouwen in je applicatie.

### Browser / Server / App

React is een verzameling van tools, die op zichzelf geen extra benodigdheden heeft om te werken in een browser. Je kan React implementeren in een gewone HTML pagina, in een PHP framework, in een .net web applicatie.

Daarnaast kan je React ook _serverside_ (javascript op een NodeJS server) gebruiken, om al bepaalde logica uit te voeren (bijvoorbeeld authenticatie, pre-rendering etc) voordat een gebruiker de pagina te zien krijgt.

Als er ook nood is aan een native applicatie (Android of iOS app), kunnen hiervoor ook React componenten gebruikt worden, via [React Native](https://reactnative.dev/){:target="_blank"}.

Zo kan je dus met 1 codebase, je componenten op verschillende platformen gaan gebruiken. Dat is één van de vele sterke punten van React.

### Compileren

Hoewel je de React library gewoon kan inladen via een script tag in je HTML pagina, en daarna eenvoudige componenten kan maken door gebruik te maken van javascript, zal je snel merken dat deze methode best veel code vereist. Daarom biedt React ook standaard een manier aan om met heel wat minder code, en templates die sterk lijken op normale HTML, componenten te bouwen. Daarover snel meer verder in deze cursus.

Daarnaast bouw je React applicaties op uit verschillende componenten. Die componenten zitten in verschillende bestanden en kunnen ingeladen en gebruikt worden in verschillende andere componenten, zelfs tegelijkertijd, met verschillende data.

Om deze verschillende bestanden en templates om te zetten naar efficiënte Javascript code die elke browser kan lezen en begrijpen, moeten we onze React code compileren. [Daarvoor maakt React gebruik van Webpack](https://webpack.js.org/){:target="_blank"}.

Geen nood, er zijn verschillende 'starter packs' waaruit je kan vertrekken, die de hele webpack configuratie al bevatten. Later in deze cursus gaan we zo'n starter pack bekijken (create-react-app), en laat ik jullie zien hoe je de configuratie en setup van deze tool kan bekijken, om er uit te leren, of om aan te passen naar wens.

### ES6

Hoewel je de React library met 'old school' javascript kan gebruiken, is het sterk aangeraden om toch gebruik te maken van de vele nieuwe functionaliteiten die Ecmascript 6 (en 7,8,9,...) bieden. Dingen zoals 'Object destructuring' of 'Array destructuring', Classes, ' modules en 'arrow functions'.

Als dit onbekend klinkt, kan je op het Grow platform enkele video's bekijken waarbij deze functionaliteiten in detail worden besproken:

<div class="grid cards" markdown>

- :octicons-video-16: [Ecmascript 6 @ Grow](https://grow.nxtmedia.technology/videos/filter?filter%5Bcraft%5D=frontend&filter%5Btag%5D=es6){:target="_blank"}
- :fontawesome-brands-js: [Mozilla: Javascript herhaling](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript){:target="_blank"}

</div>
