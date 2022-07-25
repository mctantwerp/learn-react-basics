# Usage

* Zorg ervoor dat je zeker python3 hebt
* Installeer mkdocs (`pip install mkdocs`)
* Installeer mkdocs-material (`pip install mkdocs-material`)
* Installeer de vereiste packages (Zie `Gebruikte packages` onderaan)
* Use `mkdocs serve` om de site lokaal te kunnen bekijken

## Belangrijk!

Wij gebruiken het **material insiders** thema wat ons extra features en opties geeft. Als je lokaal test kan het zijn dat niet alles er grafisch doorkomt zoals je zou willen op basis van de kitchensink. Don't worry! Eens dit online gebuild wordt komt dit helemaal goed.

Bij grotere aanpassingen of het schrijven van mini courses zal er altijd een online testomgeving voorzien worden waarop je kan testen en al je aanpassingen wel kan bekijken. Contacteer sam.serrien@kdg.be indien je hier gebruik van wil maken.

# Gebruikte packages

pip install mkdocs-git-committers-plugin-2
pip install mkdocs-git-revision-date-localized-plugin
pip install mkdocs-git-authors-plugin

# Interesting features / settings

## Geen toggles maar sections voor 1ste level van navigatie

```md
features
    - navigation.sections
```
