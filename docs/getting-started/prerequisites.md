# Prerequisites

In deze cursus gaan we gebuik maken van een handige 'starter pack' om snel React applicaties te kunnen bouwen. Om die starter pack te kunnen gebruiken heb je NodeJS nodig.

NodeJS is een tool die je in staat stelt Javascript op systeemniveau uit te voeren, via je CLI (Command Line Interface), Terminal. Je kan NodeJS hier downloaden en installeren:

{% embed url="https://nodejs.org/en/" %}

{% hint style="warning" %}
Bij het schrijven van deze cursus maken we gebruik van de **LTS versie** (op dit moment 14.x). Hoewel de nieuwste versie van NodeJS (op dit moment 16.x) nieuwere functionaliteiten biedt, is er geen garantie dat de code uit deze cursus altijd gaat werken op die nieuwe versies.

Indien er stukken code niet werken op nieuwere versies van NodeJS, kan je dat altijd laten weten via mail, discord of een Github pull request!
{% endhint %}

Zowel op MacOS als op Windows zit bij de NodeJS installatie ook NPM (Node Package Manager) bij. Naast NPM kan je ook een andere Package Manager gebruiken, die net zoals React door Facebook is ontwikkeld. Deze Package Manager noemt Yarn, en is volledig compatibel met NPM packages. Yarn kan gek genoeg gewoon geinstalleerd worden door gebruik te maken van NPM (inception).

{% embed url="https://classic.yarnpkg.com/en/docs/install#windows-stable" %}

Hoewel de verschillen tegenwoordig klein zijn, zijn er wel degelijk verschillen tussen NPM en Yarn. Het grote voordeel van NPM is dat het standaard wordt meegeleverd met NodeJS, en dus niet nog eens extra moet worden geïnstalleerd. Het voordeel van Yarn is dat het sneller is dan NPM, vooral bij grotere packages, omdat Yarn simultaan verschillende packages tegelijk kan installeren. Daarnaast was Yarn lange tijd veiliger dan NPM omdat Yarn nieuwe technieken introduceerde, zoals het gebruik van lock files. Ondertussen is NPM ook in sneltempo sneller en veiliger geworden, waardoor de verschillen tegenwoordig klein zijn.
