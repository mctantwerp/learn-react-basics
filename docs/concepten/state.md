# State

De state van een component kan je vergelijken met een geheugen van een component. Bij het initialiseren geven we een bepaalde waarde mee, en afhankelijk van acties kan deze waarde aanpassen. Een state is gebonden aan een component en kan niet rechtstreeks updated worden door parent of child componenten.

Telkens deze waarde aanpast zal de component updaten en de nieuwe state laten zien.

Een state initialiseren kan je op 2 manieren doen. De meest voor de hand liggende methode is door het gebruik van een statefull component. Dat doe je zo:

```javascript
class StateExample extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Bram',
      roles: ['docent','developer'],
      age: 34
    };
  }
  ...
  render() {}
}
```

We geven een object mee aan de state van de component, waarvan je de waarden kan gebruiken in de render functie:

```javascript
render() {
  return (
    <div class="person">
      <p class="person__name">{ this.state.name }</p>
      <p class="person__age">{ this.state.age }</p>
    </div>
  );
}
```

Als je de state van een component wil updaten, kan dat niet zomaar. We willen immers dat een component weet dat zijn state aangepast is, en daarom ook opnieuw rendert. Een state updaten moeten we dus doen door gebruik te maken van een functie. Dat doe je zo:

```javascript
this.setState({ name: 'Bram Verdyck' });
```

Je hoeft hier niet het hele object mee te geven, enkel de waarden die aanpassen. Achter de schermen gaat React deze nieuwe waarden aanpassen in het state object en de render functie van de component opnieuw aanroepen.

Het kan zijn dat er op verschillende plekken tegelijk een state aanpassing gebeurd. Om er zeker van te zijn dat je altijd de laatste state hebt, kan je met de setState functie, in plaats van een object, ook een callback functie meegeven. Dat ziet er dan zo uit:

```javascript
this.setState((state, props) => ({
    age: state.age + 1,
}));
```

[:octicons-link-external-16: React JS: State and lifecycle](https://reactjs.org/docs/state-and-lifecycle.html){.md-button target="_blank"}
