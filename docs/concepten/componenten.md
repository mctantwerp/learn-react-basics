# Componenten

Componenten in React kan je op twee manieren schrijven: een _Class_ component of een _Function_ component. De naamgeving van deze componenten geeft al een grote hint hoe deze componenten moeten worden opgebouwd.

Als je begint met het opbouwen van componenten in React, is er een belangrijke vuistregel: een component moet zo dom mogelijk gemaakt worden. Hoe dommer een component, hoe makkelijker het is om deze component te testen, en hoe kleiner de kans dat er iets breekt als je aanpassingen maakt.

Uitgaande van dit principe kan je dus in React een component op twee verschillende manieren opbouwen.

## Functional component

Een functional component is gemaakt om zo simpel mogelijk te functioneren. In zijn basis is dit soort componenten niet meer dan een Javascript functie. Deze Javascript functie krijgt via argumenten zijn [props](props.md) (data van buiten de component zelf) binnen en kan aan de hand van die props beslissingen maken over hoe de component moet worden weergegeven. Een functional component heeft geen _render_ functie, maar returned zijn output meteen.

Een _functional_ component wordt ook een _stateless_ component genoemd, omdat dit soort component geen complexe logica rond states van React componenten bevat.

```javascript
function HelloWorld() {
  return <h1>Hello, world</h1>
}
```

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="VwWOZBb" data-user="TroTi13" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/TroTi13/pen/VwWOZBb">
  React functional components</a> by Bram Verdyck (<a href="https://codepen.io/TroTi13">@TroTi13</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>


## Class components

Class components dienen voor complexere componenten. Een component die bijvoorbeeld een waarde moet kunnen onthouden ([state](state.md)) en daarmee logica uitvoeren. Een component die net voor of net na de render functie iets moet uitvoeren ([lifecycle events](lifecycle-events.md)). Een class component wordt ook een _stateful_ component genoemd, omdat deze component een state heeft (ook al is die leeg).

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="WNOBRgb" data-user="TroTi13" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/TroTi13/pen/WNOBRgb">
  React class components</a> by Bram Verdyck (<a href="https://codepen.io/TroTi13">@TroTi13</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
