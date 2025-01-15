# Comparar 2 valores

Vamos a ver las formas de comparar números e incluso números con strings.

```jsx
const numero1 = 20;
const numero2 = "20";
const numero3 = 30;
```

Si escribimos `console.log(numero1 == numero3)` para empezar no estamos asignando un valor como con las variables al asignar un símbolo de igual, estamos comparando valores, en este caso el resultado seria false.

```jsx
console.log(numero1 == numero2); // true
```

En este ejemplo si comparamos un numero con un string con el mismo valor no hay problema aunque sea un string digamos que este comparador no es muy estricto. Existe otro **comparador** que es mas **estricto** que seria con 3 símbolos de igual y es estricto porque además de fijarse en el valor revisa algo llamado tipo de dato, es decir, que sean ambos strings o ambos números.

```jsx
console.log(numero1 === numero2); // false
```

Existe también un comparador para diferenciar valores, por ejemplo al comparar password cuando se esta creando una cuenta. Que el resultado diga true se refiere a que si son diferentes los valores.

```jsx
const password1 = "admin";
const password2 = "Admin";

console.log(password1 != password2); // true
```

Tambien podemos utilizarlo con los strings y números. Y de nueva cuenta tenemos diferenciadores estrictos que seria lo mismo revisa el valor y además el tipo de dato.

```jsx
console.log(numero1 != numero2); // false

console.log(numero1 !== numero2); // true
```