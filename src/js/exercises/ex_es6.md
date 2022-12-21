![](../../assets/Logo_Yellow.png)

# Ejercicios JS - Array methods

```javascript
const countries = ['Finland', 'Sweden', 'Denmark', 'Norway', 'Iceland'];
const names = ['Carlos', 'María', 'Isidro', 'Cristina'];
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const products = [
  { product: 'banana', price: 3 },
  { product: 'mango', price: 6 },
  { product: 'potato', price: ' ' },
  { product: 'avocado', price: 8 },
  { product: 'coffee', price: 10 },
  { product: 'tea', price: '' },
];
```

1. Usa **_forEach_** para mostrar por consola cada país del array `countries`.
2. Usa **_forEach_** para mostrar por consola cada nombre del array `names`.
3. Usa **_forEach_** para mostrar por consola cada número del array `numbers`.
4. Usa **_map_** para crear un nuevo array con cada país del array `countries` en **mayúsculas**.
5. Usa **_map_** para crear un array con la **longitud** de cada país del array `countries`.
6. Usa **_map_** para crear un array con el cuadrado de cada número de array `numbers`.
7.  Usa **_map_** para crear un nuevo array con cada nombre del array `names` en mayúsculas.
8. Usa **_forEach_** para mostrar por consola el **precio** de cada producto en el array `products`.
9. Usa **_filter_** para filtrar los países que incluyan el string **_land_** en el array `countries`.
10. Usa **_filter_** para filtrar los países que tengan más de `6` letras en el array `countries`.
12. Usa **_filter_** para filtrar los páises que empiecen por `E` en el array `countries`.
13. Usa **_filter_** para filtrar los **productos** que tengan un **precio** mayor que `6`.
14. Declara un función llamada `getStringLists` que acepte un array de cualquier tipo de elementos, pero devuelva un array nuevo contentiendo sólo los strings.
15. Usa **_reduce_** para sumar todos los números del array `numbers`.
16. Usa **_reduce_** para restar todos los números del array `numbers`.