
```css
.spinner{
  width: 50px;
  height: 50px;
  border: 1px solid black;
  border-radius: 50%;
  border-top: 1px solid red;
  animation-name: spinna;
  animation-duration: 1s;
  animation-iteration-count: infinite;
  animation-timing-function: linear;
}

  
@keyframes spinna{
  from {transform: rotate(0deg); }
  to {transform: rotate(360deg); }
}
```

```html
<div id="spinner" class="spinner d-none"></div>
```