# Syntax

### Eenvoudige component in Javascript

Het toevoegen van React logica in een bestaande website is best eenvoudig. Met enkele regels code kan je al een eenvoudige slimme component maken. In de codepen hieronder vind je een eenvoudig voorbeeld van een React button.

Let er op dat in dit voorbeeld 2 scripts worden ingeladen (via de settings van codepen). Die scripts zijn de volgende:

```html
<!-- Load React. -->
<!-- Note: when deploying, replace "development.js" with "production.min.js". -->
<script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>
```

#### Voorbeeld

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="WNOWJME" data-user="TroTi13" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/TroTi13/pen/WNOWJME">
  React button</a> by Bram Verdyck (<a href="https://codepen.io/TroTi13">@TroTi13</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

!!! info ""
    Maak gebruik van de HTML en Babel (JS) tab om te kijken hoe deze slimme like button werkt.

#### In detail

```html
<div id="button-container">...</div>
```

Onze HTML bestaat enkel uit een container, een div met een id. De meeste front-end frameworks werken op deze manier. Binnen die container zal je React component of applicatie werken.

```js
class LikeButton extends React.Component {}
```

Dit voorbeeld maakt gebruik van classes om een component te bouwen. Hoewel dit in nieuwere versies van React niet meer nodig is, zal je nog veel documentatie tegenkomen waarin componenten worden gebouwd met behulp van classes. Later in de cursus gaan we alternatieve functionele componenten zien, maar de principes blijven wel hetzelfde.

```js
constructor(props) {
    super(props);
    this.state = { liked: false };
  }
```

Een constructor is een functie die wordt aangeroepen elke keer er een _instance_ van die class wordt aangemaakt.

Bij React componenten is dit een belangrijke functie omdat we daarbij 'props' kunnen doorgeven. Meer over props later in de cursus, maar onthou alvast dat props een manier zijn om, van buiten de component, data door te geven naar de component zelf.

We zien in dit voorbeeld ook een state property, wat een object als value krijgt. Deze state property is een speciale React property, welke kortweg zal functioneren als een geheugen voor onze component. Hierin kunnen we waarden opslaan en aanpassen, en onze component zal altijd de laatste 'state' weergeven.

```js
render() {
    return ...;
}
```

Eigenlijk de belangrijkste functie van onze component, is de render functie. React zal de render functie aanroepen als een component moet worden weergegeven, maar ook telkens er dingen veranderen (bvb de state) binnen een component. Een component kan dus meerdere keren renderen om zo altijd updated te zijn met de rest van de applicatie.

```js
React.createElement(
  'button', // type element (div, span, button, ...)
  { onClick: () => this.setState({ liked: true }) }, // props
  'Like' // children, elementen die binnen dit element moeten leven
);
```

Met deze functie wordt een React element gemaakt, welke 3 argumenten verwacht: type, props en children (zie comments in de code hierboven). Op basis van deze argumenten maakt React een HTML component met javascript functionaliteiten gekoppeld.

Als we even 'inzoomen' op de props, zien we daar een onClick functie. Daarbinnen wordt setState aangeroepen. setState is een speciale React functie die binnen een component gebruikt wordt om de component state te updaten (weet je nog, die this.state in de constructor). Naast het updaten van de waarde van de state, zal deze functie ook aan de component laten weten dat de state een nieuwe waarde heeft, en dus de component opnieuw zijn render functie moet uitvoeren om de nieuwe state te laten zien.

!!! warning "Opgelet"
    Hier wordt gebruik gemaakt van een _arrow function_ (() => ()). We gebruiken hier een arrow function omdat we het _this_ keyword gebruiken. Een normale functie zou de context binnenin de functie aanpassen, waardoor het _this_ keyword niet meer refereert naar de component, maar naar het button element in dit geval (button.onClick). Een arrow functie verandert de context binnenin niet, waardoor _this_ dus refereert naar de Class.

```js
ReactDOM.render(
  React.createElement(LikeButton),
  document.querySelector('#button-container')
);
```

Om onze component effectief te renderen in een web app, moeten we aan React laten weten waar hij deze moet renderen natuurlijk. Dat doe je via de ReactDOM.render functie, waarbij je als eerste argument een React Element meegeeft (hier wordt een nieuw Element gemaakt waarin de Like Button component zit). Als tweede argument wordt een DOM element meegegeven, welke refereert naar onze container die we in HTML hebben opgezet.

### Gebruik JSX

In bovenstaand voorbeeld maken we een eenvoudige Like Button, door gebruik te maken van de React Javascript API. Hoewel dit laat zien hoe React in zijn werk gaat, is dit best omslachtig om bijvoorbeeld meerdere componenten te gaan renderen. React biedt hier een oplossing onder de naam JSX.

Hoewel JSX heel gelijkend is met templating tools zoals bijvoorbeeld handlebars, is JSX een syntax extentie van Javascript. Dat betekent dat, hoewel het lijkt dat je HTML schrijft met daarin variabelen, je daarbinnen de volledige kracht van javascript behoudt en dus functies, arrays etc kan blijven gebruiken. Dit concept zal later nog duidelijker worden in de verschillende voorbeelden in deze cursus.

Het enige dat je extra moet doen om JSX te kunnen gebruiken rechtstreeks in de browser, is Babel toevoegen:

```html
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="YzQMvrV" data-user="TroTi13" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/TroTi13/pen/YzQMvrV">
  React button met JSX</a> by Bram Verdyck (<a href="https://codepen.io/TroTi13">@TroTi13</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

#### In detail

Over het algemeen verandert er in dit voorbeeld slechts op 2 plaatsen iets. Dat wordt hieronder uitgelicht.

```js
return (
  <button onClick={() => this.setState({ liked: true })}>
    Like
  </button>
);
```

We zien hier het gebruik van JSX. Deze return statement is exact hetzelfde als die in het vorige voorbeeld. De button in dit voorbeeldje is eigenlijk een JSX tag, die achter de schermen wordt omgezet naar de React.createElement functie. Dezeflde argumenten worden hier gebruikt:

* type: button, de naam van de tag
* props: de attributen die worden gezet op de button tag
* children: de elementen die binnen de button tag leven

```js
ReactDOM.render(<LikeButton />, document.querySelector('#button-container'));
```

Ook in de render functie gebruiken we nu een JSX tag om de LikeButton effectief als element te kunnen gebruiken.

Door gebruik te maken van JSX wordt het ook veel makkelijker om componenten te herkennen en om props mee te geven. Je zal praktisch nooit React componenten zien die geen gebruik maken van JSX.

!!! info "Compileren"
    Bovenstaande implementatie van JSX (via de script tag) is best inefficiënt en vergt veel rekenkracht van de browser om live JSX om te zetten naar javascript. Daarom is het beter om je code op voorhand te compileren. Meer daarover hier: [https://reactjs.org/docs/add-react-to-a-website.html#add-jsx-to-a-project](https://reactjs.org/docs/add-react-to-a-website.html#add-jsx-to-a-project)

Een voorbeeld van het hergebruik van componenten kan je in volgend voorbeeld bekijken:

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="powBKOm" data-user="TroTi13" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/TroTi13/pen/powBKOm">
  React button met JSX en meerdere componenten</a> by Bram Verdyck (<a href="https://codepen.io/TroTi13">@TroTi13</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>

<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
