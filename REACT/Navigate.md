Uso per fare rerouting dove non posso usare Javascript, ma invece devo richiamare un componente

```JSX
<Route path="/404" element={<NotFound/>}/>
<Route path="/*" element={<Navigate to="/404"}
```

In pratica Navigate fa rimbalzare ad un altro route quando l'utente ci arriva.