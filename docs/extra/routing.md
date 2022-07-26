# Routing

Routing ligt aan de basis van elke web applicatie. Historisch liep routing via de back-end, via de server. Een browser surft naar een bepaald pad, dat pad wordt opgezocht op de server, de server beslist welke data er terug moet worden gestuurd (of welke HTML) en de browser rendered het antwoord van de server.

Bij moderne web applicaties die in front-end frameworks worden gebouwd, wordt er meer en meer gebruik gemaakt van _client side routing_. Dat betekent dat de routing wordt verzorgt door het front-end framework, waardoor de server niet meer belast wordt voor deze taak. Dit betekent dat een server minder requests moet afhandelen, en dat deze taak in de browser wordt afgehandeld, wat wil zeggen dat elke gebruiker (client) deze logica op zijn eigen computer uitvoert.

| Pro                              | Con                                 |
| -------------------------------- | ----------------------------------- |
| Snel                             | minder SEO friendly                 |
| Enkel de nodige data             | Soms meer data initiëel laden       |
| Transities & animaties mogelijk  | Veel ajax requests                  |
| Minder load voor de server       | Libraries nodig om dit goed te doen |
| Offline mogelijk                 | Heel wat logica verhuist naar FE    |
| Geen pageloads tijdens navigatie |                                     |

Om routing toe te voegen aan React moeten we een extra module installeren. Er zijn meerdere modules online te vinden om routing toe te voegen aan React applicaties. Een veelgebruikte module is de 'React Router' module.

### Installatie

Die kan je installeren via volgend commando:

```javascript
yarn add react-router-dom
```

We zien hier een specifieke versie van de React Router module, speciaal voor gebruik in de browser (DOM). Naast de DOM versie bestaan er nog 2 versies:&#x20;

* DOM: de versie voor web
* Native: de versie voor native applicaties (met React Native)
* Core: de basisfunctionaliteit die gedeeld wordt door DOM en Native

### Implementatie

Na het installeren van de Router module moeten we deze toevoegen in onze applicatie. In de meeste gevallen gebruiken we 1 routing voor de volledige app. We moeten de \<App /> component dus laten weten dat er genavigeerd kan worden. Dat doen we zo:

=== "index.js"

    ```javascript
    ...
    import { BrowserRouter as Router } from 'react-router-dom';
    ...
    ReactDom.render(<Router><App /></Router>, document.getElementById('root'));
    ...
    ```

Door de \<App /> component in de \<Router /> component te zetten, kunnen we binnen de \<App /> component onze routes gaan definiëren.

Een route definiëren doe je zo, in de \<App /> component:

=== "App.js"

    ```javascript
    ...
    import { Route } from 'react-router-dom';
    ...
    // in de render functie van <App />
    <Route path="/" component={Home} />
    ```

Bovenstaande regel registreert een nieuwe route, de basisroute ( / ) waarop de \<Home /> component moet gerenderd worden.

Stel dat je in je \<App /> component variabelen hebt (bijvoorbeeld een state) die je via props wil doorgeven aan je component, dan kan je dat op volgende manier doen:

=== "App.js"

    ```javascript
    // in de render functie van <App />
    <Route path="/comments" render={
        (props) => (
            <CommentsList {...props} comments={this.state.comments} />
        )
    } />
    ```

Dit is een ietwat complexere notatie, waarbij we een render functie gebruiken. In deze render functie kan je conditioneel componenten renderen, of bijvoorbeeld props meegeven aan componenten. De (props) die in de functie worden meegegeven, zijn standaard props van de router. De props die worden meegegeven aan elke component die via een Route wordt gerenderd zijn de volgende:

* [match](https://reactrouter.com/web/api/match){:target="_blank"}
* [location](https://reactrouter.com/web/api/location){:target="_blank"}
* [history](https://reactrouter.com/web/api/history){:target="_blank"}

Je kan ook dynamische routes aanmaken, waarbij een deel van de routenaam bestaat uit een variabel deel. Dit doe je als volgt:

```javascript
<Route path="/comments/:id" component={Comment} />
```

We zien hier het gebruik van een route parameter, aangeduid door een : met een variabele naam erachter. Die parameter kan je terug ophalen uit de route props (zie lijstje hierboven, de match prop, match.params.id) in de component zelf, in dit geval de \<Comment /> component.

### Route links

Als je nu een navigatie wil opbouwen, waarbij je wil linken naar deze routes, doe je dat best niet via de normale \<a> tag. Dan gaat de browser namelijk toch een request naar de server sturen en gaat de pagina herladen naar de nieuwe URL. Als we in de browser zelf willen navigeren, dan moet er gebruik gemaakt worden van de \<Link /> component. Ook dit is een onderdeel van de Router module.

```javascript
...
import { Link } from 'react-router-dom';
...
<Link to="/comments">Comments</Link>
```

De \<Link /> component is gemaakt voor basis links, eigenlijk voor gebruik doorheen de applicatie maar als je links wil gebruiken in een navigatie kan je beter gebruik maken van de \<NavLink /> component. Bij deze component kan je bijvoorbeeld handig gebruik maken van de activeClassName prop, om een class toe te voegen als de route actief is. Dat doe je zo:

=== "Nav.js"

    ```javascript
    ...
    import { NavLink } from 'react-router-dom';
    ...

    // in de render functie van <Nav />
    <NavLink to="/comments" activeClassName="active">Comments</Link>
    ```

### Switch

Eenmaal je routes begint aan te maken, zal je snel merken dat bijvoorbeeld de algemene route ( / ) altijd actief gaat zijn, en dus altijd in dit geval de \<Home /> component gaat renderen. Dat kan natuurlijk niet de bedoeling zijn. Je kan dit vermijden door je routes te _wrappen_ in een \<Switch /> component. Deze component gaat er voor zorgen dat de router de eerste route die matched, dus die gelijk is aan de path prop van een \<Route /> component, rendered en daarna stopt met verder te kijken. Als je er dan op let dat je de meest specifieke routes bovenaan zet en de meer algemene routes onderaan, dan zou je in theorie altijd correct moeten renderen.

Dit ziet er dan ongeveer zo uit:

=== "App.js"

    ```javascript
    ...
    import { Route, Switch } from 'react-router-dom';
    ...
    // in de render functie van <App />
    <Switch>
        <Route path="/comments/:id" component={Comment} />
        <Route path="/comments" render={
            (props) => (
                <CommentsList {...props} comments={this.state.comments} />
            )
        } />
        <Route path="/" component={Home} />
    </Switch>
    ```

Moest je toch mismatches krijgen, kan je nog altijd gebruik maken van de exact prop. Deze zorgt ervoor dat de Route exact moet matchen met de path prop van een component om te activeren:

=== "App.js"

    ```javascript
    <Route path="/" exact component={Home} />
    ```

### Meer info

Meer informatie over het gebruik van de Router vind je op de volgende link:

[:octicons-link-external-16: Reactrouter: Quick start](https://reactrouter.com/web/guides/quick-start){.md-button target="_blank"}
