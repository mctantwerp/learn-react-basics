# JSX

In de 'Getting Started' hebben we al een teaser gekregen van JSX en hoe JSX eigenlijk best hard lijkt op gewone HTML. Laat ons even iets dieper duiken in wat JSX juist is, en wat het NIET is.

{% hint style="info" %}
JSX is, net als React en Yarn, ontwikkeld door Facebook
{% endhint %}

## JSX: Javascript XML

JSX is een syntax extensie die gebouwd is op Ecmascript (Javascript), om op een relatief makkelijke en slimme manier om te gaan met HTML in Javascript. Het is niet de bedoeling om op termijn JSX een onderdeel te maken van de Ecmascript standaarden, maar echt als een syntax extensie die, met behulp van compilers zoals Webpack, kan helpen om op een leesbare manier HTML via Javascript te kunnen injecteren in je pagina.

Een voorbeeld van hoe een functie zonder JSX en met JSX er kan uitzien:

{% tabs %}
{% tab title="Zonder JSX" %}
```javascript
function HelloWorld() {
    const wrapper = document.createElement('div');
    const heading= document.createElement('h1');
    const content = document.createTextNode('Hello, world');
    
    wrapper.classList.add('wrapper');
    heading.classList.add('heading--1');
    
    heading.appendChild(content);
    wrapper.appendChild(heading);
    
    return wrapper;
}

// een extra om even de implementatie dan te tonen
document.querySelector('#root').appendChild(HelloWorld());
```
{% endtab %}

{% tab title="Met JSX" %}
```javascript
function HelloWorld() {
    return <div className="wrapper">
        <h1 className="heading--1">Hello, world</h1>
    </div>;
}

ReactDOM.render(
  <HelloWorld/>,
  document.querySelector('#root')
);
```
{% endtab %}
{% endtabs %}

In bovenstaand voorbeeld zien we een hele eenvoudige component die niet veel meer doet dan een boodschap tonen in een titel.

#### /sidenote

In het voorbeeld zonder JSX zouden we gebruik kunnen maken van _innerHTML_ in plaats van de appendChild methode. Dat zou er dan zo uit zien:

```javascript
function HelloWorld() {
    return '<div class="wrapper"><h1 class="heading--1">Hello, world</h1></div>';
}

// een extra om even de implementatie dan te tonen
document.querySelector('#root').innerHTML = HelloWorld();
```

Nu denk je waarschijnlijk, dit is gewoon nog korter dan de JSX versie. Klopt! En in dit geval kan je gebruik maken van de innerHTML methode omdat deze component zo eenvoudig is. Maar opgelet, als je innerHTML gebruikt, hou er dan rekening mee dat alle HTML die je zo toevoegt, ook uitgevoerd kan worden. Als daar dus een script tag in komt te staan, dan wordt die script uitgevoerd op de moment dat je die toevoegt aan je HTML.

## JSX != HTML

Hoewel JSX sterk lijkt op HTML, is het dat natuurlijk niet. Achter de schermen worden JSX tags omgezet naar Javascript functionaliteiten. Je kan JSX herkennen aan een aantal duidelijke verschillen:

### \<Self-closing tags />

We kennen in HTML al self-closing tags, tags die geen inhoud hebben mogen afgesloten worden in éénzelfde tag. Enkele voorbeelden:

```markup
<img src="/images/placeholder.png" />
<br />
```

In JSX MOET een tag die geen inhoud heeft, altijd zichzelf meteen ook afsluiten. Achter de schermen gaat een JSX tag altijd kijken of er inhoud (children) moet gerenderd worden. Als een tag zichzelf niet meteen afsluit, gaat JSX er vanuit dat er inhoud moet zijn. Indien die er dan toch niet is, gaat JSX een fout geven.

Zo kan je, in tegenstelling tot in HTML, elke tag self-closing schrijven in JSX:

```markup
<div />
<span />
<br />
```

### Root element

Zoals de afkorting JSX zelf vermeld, is JSX gebaseerd op de XML syntax, net zoals HTML. De XML syntax gaat steeds uit van een Root element met daarin een verzameling van componenten (children). Als je dus meerdere JSX componenten tegelijk wil renderen, zal je die altijd in een overkoepelend element moeten steken. Dit kan een simpele DIV component zijn, of als je geen HTML tag wil renderen kan je gebruik maken van [Fragments](https://reactjs.org/docs/fragments.html).

```markup
<div>
    <div />
    <span />
    <br />
</div>
```

### Variabelen

JSX biedt ook de mogelijkheid om variabelen te gebruiken. Die herken je steeds aan de accolades (brackets, { }). Variabelen kunnen als content van een element worden gebruikt, maar ook als waarde van een attribuut / prop.

```markup
<div>{ content }</div>
```

### Attributen / props

In HTML zijn we gewend om attributen op elementen te zetten in de vorm van een string. Denk bijvoorbeeld aan een afbeelding en het _src_ attribuut:

```markup
<img src="/images/placeholder.png" />
```

In JSX kunnen we ook variabele data meegeven aan elementen. Daarvoor gebruiken we dan ook de bracket notatie zoals hierboven beschreven.

```javascript
const imageSource = '/images/placeholder.png';
<img src={ imageSource } />
```

### className / htmlFor

Een duidelijk verschil merk je op bij het toevoegen van een class. In HTML doe je dit door het attribuut ‘class’ toe te voegen. Daar dit een _reserved word_ is in Javascript, wordt in JSX de ’className’ property gebruikt.

```markup
<div className="wrapper">lorem ipsum</div>
```

Hetzelfde geldt voor het keyword ’for’, welke je op een label kan gebruiken. For in Javascript wordt gebruikt in loops. Om dit te vermijden wordt gebruik gemaakt van ’htmlFor’.

```markup
<label htmlFor=“input”>Label</label>
```

### Events

Een event listener en event handler toevoegen met JSX doet denken aan de ’oldschool’ inline javascript events. Achter de schermen worden deze props natuurlijk uitgevoerd door correcte event listeners.

```javascript
<div onClick={ () => alert('hello') }>Click me, I'm a button?</div>
```

{% hint style="info" %}
Let op de camel case notatie. In HTML zijn deze inline argumenten lowercase. In JSX zijn deze geschreven in de (lower) camel case notatie.
{% endhint %}
