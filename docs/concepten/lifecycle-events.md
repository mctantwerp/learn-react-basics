# Lifecycle events

Naast props en een lokale state kunnen stateful componenten ook gebruik maken van de lifecycle events van een React component.

## Mount / Unmount

Een React component bevat een functie die wordt uitgevoerd wanneer een component wordt toegevoegd aan de DOM (mount, zichtbaar in je browser), en ook wanneer hij wordt weggehaald (unmount).

Die speciale functies zijn enkel toegankelijk in een stateful (Class) component, en implementeer je als volgt:

```javascript
constructor() {...}

componentDidMount {
    // logica hier om uit te voeren net na het renderen van component
}

componentWillUnmount {
    // logica hier om uit te voeren net voor een component wordt weggehaald
}
```

[:octicons-link-external-16: React JS: State and lifecycle](https://reactjs.org/docs/state-and-lifecycle.html#adding-lifecycle-methods-to-a-class){.md-button target="_blank"}
