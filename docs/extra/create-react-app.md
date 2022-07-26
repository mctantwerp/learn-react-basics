# Create react app

Vooral uit nood om een ’standaard’ React setup te hebben om snel Proof Of Concepts (POC) te maken, of om componenten te ontwikkelen in een standaard React omgeving, is de ’create-react-app’ (CRA) Command Line Interface (CLI) ontwikkeld.

## Installatie

Het enige dat je nodig hebt om CRA te gebruiken, is NodeJS. Daarna kan je in enkele seconden een basis React applicatie opzetten. Dat doe je door het volgende commando uit te voeren:

```sh
npx create-react-app <mapnaam>
cd <mapnaam>
npm run start
```

Dit commando gaat de create-react-app uitvoeren (zonder dat een echte installatie nodig is) en een map aanmaken (met de naam die je invult in plaats van \<mapnaam>. Daarin wordt een volledige setup uitgevoerd van een React applicatie.

![Install react](/_resources/images/install_react.svg)

Wanneer de setup afgerond is, zal je merken dat er de folder \<mapnaam> opgevuld is met een basis react app. Als we, zoals de setup op het einde aangeeft, naar de map navigeren via onze terminal, en daarin het commando `yarn start` of `npm run start` uitvoeren, zal je merken dat je browser wordt geopend en surft naar http://localhost:3000. Dit is de standaard url waarop NodeJS applicaties lokaal draaien.

Als we naar de files in de folder kijken, zien we daar enkele belangrijke files en folders.

### Public folder

De public folder bevat alle files die niet gecompileerd moeten worden. Daarin kan je dus files zetten zoals een favicon of andere meta iconen. Let er op dat je deze files niet kan importeren in je React componenten. Als je dat wel wil doen, zal je die ergens in de src folder moeten steken.

#### index.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    ...
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    ...
    <link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png" />
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
    <title>React App</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
  </body>
</html>

```

Hierboven een ietwat verkorte versie van de /public/index.html file. We zien hier enkele opmerkelijke dingen:

```html
<link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
```

Als we naar files uit de public folder willen refereren, dienen we de %PUBLIC\_URL% variabele gebruiken. Achterliggend wordt dit opgevangen en door de correcte url vervangen.

```html
<link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
```

Er wordt gerefereerd naar een manifest.json file. Die file bevat alle meta data voor browsers om deze applicatie (mits enkele requirements, zoals HTTPS), te herkennen als een web app (PWA) en die ook installeerbaar te maken vanuit de browser en hopelijk binnenkort ook vanuit enkele mobiele App stores.

```html
<noscript>You need to enable JavaScript to run this app.</noscript>
<div id="root"></div>
```

Een `<noscript>` tag die bezoekers laat weten dat er javascript wordt gebruikt om deze app te renderen. De `<noscript>` tag is enkel zichtbaar als javascript is uitgeschakeld in een browser.

De #root div herkennen we uit de voorgaande voorbeelden. Hierin gaat onze React applicatie gerenderd worden.

In de index.html kan je bijvoorbeeld nog een statische elementen toevoegen die je niet via React wil renderen, of bijvoorbeeld script tags voor tracking etc.

### Src folder

De src folder bevat eigenlijk alle React logica. Hierin gaan we al onze componenten bouwen. Er staan al enkele files in, die we hier kort bespreken.

#### index.js

Het startpunt van de applicatie. Hierin gebruiken we de ReactDOM.render functie om onze applicatie (standaard gewoon een `<App />` component) te renderen.

```js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```

We zien hier meteen ook de moderne manier om React te gebruiken, als NPM package welke we importeren in onze javascript componenten. Op deze manier kan Webpack achterliggend heel efficiënt onze javascript code gaan bundelen, en worden enkel de scripts die we vanuit de index.js importeren, uiteindelijk gebundeld in de applicatie.

!!! info ""
    Merk ook op dat we per component hier ook .css files kunnen inladen. Deze css files worden door Webpack mee gebundeld en bij een 'build' als aparte, geoptimaliseerde, gebundelde css file mee opgenomen.

#### App.js

```js
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}

export default App;
```

De App component rendered een logo en wat tekst, samen met een link naar de React website. Hierin ga je dus zelf componenten importeren en gebruiken.

## Build

Als we klaar zijn om onze applicatie online te zetten, moeten we onze applicatie 'builden'. Dit wil zeggen dat we alle files gaan optimaliseren en een pakket opmaken met statische files (html, css, js, images) die we online kunnen zetten.

Als we de applicatie willen builden moeten we gebruik maken van het build command dat je ook in de package.json terugvind: `yarn build`

Er wordt een build folder aangemaakt met daarin alle geoptimaliseerde files.

## Eject

Ben je nieuwsgierig naar hoe zo'n create-react-app achter de schermen werkt, kan je éénmalig een commando uitvoeren om alle configuratie files en setup uit te node\_modules folder te halen en in de root van je project te zetten. Dat commando is het volgende: `yarn eject`

!!! warning "Opgelet"
    Dit commando is onomkeerbaar! Hoewel je applicatie gewoon zal blijven werken als voorheen, zit je meteen met heel wat meer files en kans op misconfiguraties. Doe dit in het begin dus enkel bij een simpele setup die je enkel gebruikt om te oefenen, en maak desnoods een back-up (zonder de node\_modules folder!!) zodat je altijd terug kan.

[:octicons-link-external-16: Github: create-react-app](https://github.com/facebook/create-react-app){.md-button target="_blank"}
