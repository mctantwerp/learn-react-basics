# Loops

Daar we regelmatig data in arrays of objecten gebruiken, is het vrij voor de hand liggend dat we loops gaan gebruiken om die data te gaan renderen. Nu, we maken gebruik van JSX, dus dat maakt het eenvoudig om door arrays of objecten te gaan loopen. Toch zijn er enkele belangrijke dingen die je moet weten als je gebruik wil maken van loops.

### Map

Stel, we hebben volgende data structuur waarin commentaren worden bijgehouden over de les 'React basics'. Die data zou er zo kunnen uitzien:

```javascript
const comments = [
    {
        author: 'An Oniem',
        timestamp: '08/10/2021',
        message: 'Waauw, inspired much, dat ga ik vanaf nu veel gebruiken!'
    },
    {
        author: 'John Doe',
        timestamp: '08/10/2021',
        message: 'WAAAT is dit? Ik snap er niks van!'
    },
    {
        author: 'Tom Bola',
        timestamp: '08/10/2021',
        message: 'Java SCRIPT?? Is dit niet de les Barista Basics?? Help!'
    }
];
```

Als we deze data nu willen gebruiken in React, kunnen we dat op verschillende manieren doen. We kunnen gebruik maken van een `for loop` , waarmee we een nieuwe array van elementen gaan genereren. We kunnen ook gebruik maken van een `Array.forEach` , maar de handigste functie om dit in zo weinig mogelijk code te kunnen verwezenlijken, is de `Array.map` functie. Die functie loopt door een bestaande array, en net zoals de forEach, gaat bij elke record in die Array een functie aanroepen. De data die je returned in die functie, wordt de nieuwe record in de nieuwe Array.

JSX kan Arrays van componenten meteen renderen. We kunnen dus gebruik maken van die Array.map functie om rechtstreeks een Array van React componenten op te bouwen. Dat zou er zo uit kunnen zien:

```javascript
const commentsComponents = comments.map(comment =>
    <Comment
        author={comment.author}
        time={comment.timestamp}
    >{comment.message}</Comment>
);
```

Hierboven zien we meteen de kracht van een Array.map functie. We loopen door de comments en returnen een React component Comment die meteen de properties van het comment object als props op de Comment component zet.

### Key

Stel, je hebt een applicatie gebouwd waarbij studenten comments kunnen geven. Die comments komen live binnen, en je moet dus je React componenten regelmatig updaten. Je Array van  comments zal dan in een state zitten, in een overkoepelende component. Telkens die state wordt aangepast (nieuwe comment gepusht in de Array van comments), zullen de comments opnieuw gerenderd worden. React doet dit best efficiënt, maar kan wel wat extra hulp gebruiken om te detecteren of een component opnieuw gerenderd moet worden of niet.&#x20;

De manier waarop we hierboven de Array.map gebruiken om comments te renderen, gaat ervoor zorgen dat alle comments telkens volledig opnieuw moeten worden gerenderd. Dat is niet zo efficiënt. Om React te helpen beslissen of een element opnieuw moet worden gerenderd, kunnen we gebruik maken van _keys_. Keys zijn eenvoudigweg unieke identifiers (id) die we per element toekennen, die React achterliggend kan gebruiken in de beslissing om een element opnieuw te renderen. Het toevoegen van zo'n keys is best eenvoudig, maar je moet wel rekening houden dat een key, net zoals een ID in HTML, maar 1 keer per pagina mag voorkomen. Als je bijvoorbeeld meerdere oplijstingen van dezelfde comments per pagina wil gebruiken, zal je dus voor elke lijst een unieke key moeten meegeven.

Een key toevoegen aan een element doe je bijvoorbeeld zo:

```javascript
const commentsComponents = comments.map((comment, i) =>
    <Comment
        key={`section-1-comment-${i}`} // een unieke key voor elke comment in section-1
        author={comment.author}
        time={comment.timestamp}
    >{comment.message}</Comment>
);
```

### Voorbeeld

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="OJgKQWN" data-user="TroTi13" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/TroTi13/pen/OJgKQWN">
  React comments</a> by Bram Verdyck (<a href="https://codepen.io/TroTi13">@TroTi13</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

[:octicons-link-external-16: React JS: Lists and keys](https://reactjs.org/docs/lists-and-keys.html){.md-button target="_blank"}
