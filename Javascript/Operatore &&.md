In Js, se metto in AND due oggetti, se entrambi sono truthy (https://developer.mozilla.org/en-US/docs/Glossary/Falsy), restituisce l'ultimo elemento.

Con REACT, se mi interessa un ternario senza l'else, posso dire 

paramDaValutare && risposta che mi interessa.

In questa maniera, se il parametro è presente (non è falsy) allora viene automaticamente generata la risposta che mi interessa. Se no, la valutazione si ferma al primo false che trova.