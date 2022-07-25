# Conditional rendering

We kunnen een component verschillende dingen laten renderen a.d.h.v. variabelen (state of props). Dit ziet er ongeveer zo uit:

```javascript
if (condition) {
    return <Element />
}

return <OtherElement />
```

We kunnen hier ook een if / else statement gebruiken:

```javascript
if (condition) {
    return <Element />
} else {
    return <OtherElement />
}
```

Als we specifiek delen van een element conditioneel willen renderen, kunnen we ook gebruik maken van inline if statements

```javascript
return condition ? <Element /> : <OtherElement />
```

### Voorbeeld

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="rNwXJoo" data-user="TroTi13" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/TroTi13/pen/rNwXJoo">
  React fake login button</a> by Bram Verdyck (<a href="https://codepen.io/TroTi13">@TroTi13</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

[:octicons-link-external-16: React JS: Conditional rendering](https://reactjs.org/docs/conditional-rendering.html){.md-button target="_blank"}
