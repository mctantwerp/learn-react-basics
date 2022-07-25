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

{% embed url="https://codepen.io/TroTi13/pen/rNwXJoo?editors=1111" %}

{% embed url="https://reactjs.org/docs/conditional-rendering.html" %}

