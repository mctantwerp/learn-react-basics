# Props

In HTML zijn we al gewend om attributen op elementen te kunnen zetten. Die attributen hebben invloed op het element zelf. Ze kunnen de weergave van een element veranderen (class, style, id, ...), of interactiviteit toevoegen/wegnemen (onclick, disabled), complexere logica activeren in een element(input type, form action en method, ...) of data weergeven in een element (value).

Het gedrag van deze standaard componenten is eigenlijk heel vergelijkbaar met de werking van React componenten. Met deze attributen kan je data doorgeven aan je componenten.

```javascript
function Greeting(props) {
  return (
    <h1>Gegroet, { props.name }</h1>
  );
}

function App() {
  return (
    <React.Fragment>
      <Greeting name=“studenten” />
      <Greeting name=“mama” />
      <Greeting name=“X Æ A-12” />
    </React.Fragment>
  );
}
```

!!! info ""
    Props zijn read-only, de data kan dus ingelezen worden, maar niet worden aangepast.

[:octicons-link-external-16: React JS: Components and props](https://reactjs.org/docs/components-and-props.html){.md-button target="_blank"}
