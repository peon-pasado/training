## Upsolving

- **problema 1 (resumen)**: Se pide leer un archivo indeterminadamente hasta recibir el número 42.

Como el problema no es claro, podemos usar un while $\infty$ y agregando un condicional adentro:

```c++
while (true) {
    int n;
    cin >> n;
    if (n == 42) break;
    cout << n << endl;
}
```

Lo de malo de este código es que asume que se recibirá el número 42, nosotros podemos parar cuando ya no hay más datos:

```c++
int n;
while (cin >> n) {
    if (n == 42) break;
    cout << n << endl;
}
```

En el anteriro código usamos la función **cin** como una condicional. La función **cin** puede ser usada como un condicional si se ha podido leer algo de la entrada o no.

**nota**: A pesar de que la función **cin >>** y **cout <<** no parezcan funciones, **c++** hace una conversión interna y lo transforma a **cin.operator>>(n)** lo cual hace la mágia.

Por último podemos poner el código de una forma más compacta:

```c++
int n;
while ((cin >> n) && n != 42) {
    cout << n << endl;
}
```

- **problema 2 (resumen)**: contar la cantidad de dígitos de un número que dividen al mismo.

Podemos revisar un dígito a la vez con el siguiente algoritmo: Revisar la unidad (**n%10**), quitar la unidad (**n/10**) y así hace que el número se haga **0**. 

**Ejemplo:** n = 123, veo el 3 con n%10, lo transfomo a n = 12 usando la división entera n/10, luego verifico el 2, luego se vuelve 1 dividiendo entre 10 y por último se vuelve 0.

```c++
int n;
cin >> n;
while (n > 0) {
    int digito = n % 10;
    //código
    n /= 10;
}
```

En la parte de **código** podemos contar lo que deseamos:

```c++
if (digito > 0 && n % digito == 0) {
    respuesta += 1;
}
```

- **problema 3 (resumen)**: Debemos responder la máxima cantidad de manzanas luego de dividir la suma total de manzanas de forma equitativa.

Para este problema la respuesta sería el mínimo entero de la suma de manzanas: **ceil(suma / n)**. Para valores no negativos la división entera es igual a la función máximo entero, nostros podemos notar que para valores enteros: **ceil(a / b) = floor((a + b - 1) / b)**. Lo que nos deja el siguiente código:

```c++
int n;
cin >> n;
int suma = 0;
for (int i = 0; i < n; ++i) {
    int ai;
    cin >> ai;
    suma += ai; 
}
cout << (suma + n - 1) / n << endl;
```

- **problema 4 (resumen)**: Se pide imprimir la cantidad de número que no son representables por na + mb con n y m no negativos y a y b dado en la entrada donde a o b es 2.

- **a y b pares**: los impares no son representables así que la respuesta es -1.

- **min(a, b) == 1**: todos los números son representables. respuesta es 0.

- **max(a, b) impar**: podemos representar todos los números mayores o iguales a max(a, b) - 1, si estos son impares se pueden representar como max(a, b) + 2m y luego todos los pares como 2m. notemos que no podemos expresar los números impares menores a max(a, b). Respuesta: **floor(max(a, b) / 2)**. 

```c++
int a, b;
cin >> a >> b;
if (a % 2 == b % 2) cout << -1 << endl;
else if (min(a, b) == 1) cout << 0 << endl;
else cout << max(a, b) / 2 << endl;
```

también:

```c++
int a, b;
cin >> a >> b;
if (a % 2 == b % 2) cout << -1 << endl;
else cout << (a + b - 2) / 2 << endl;
```