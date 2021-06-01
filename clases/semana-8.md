## Standard Template Library

La librería estándar de plantillas (STL) es una librería con varios accesorios que sirven para una cantidad significativa de problemas típicos, está dividida en **contenedores**, **utilidades** y **algoritmos**.

### **Contenedores**:

1. **vector**: Es una plantilla para mantener array dinámicos, que crecen o se reduce como queramos.

   ```c++
   #include <vector> //libreria que contiene al contenedor.
   using namespace std;
   
   vector<int> v; //declarar un vector de ints vacío {}.
   v.push_back(2); //agregar el 2 {2}.
   v.push_back(5); //agregar el 5 {2, 5}.
   v.push_back(-1); //agregar el -1 {2, 5, -1}.
   cout << v[1] << '\n'; //imprimir el segundo elemento.
   vector<long long> u(10); //declarar un vector con 10 elementos 
   						 //long long (0 por defecto).
   cin >> u[2]; //leer el tercer elemento.
   
   for (int i = 0; i < v.size(); ++i) { //imprimir los elementos del vector v.
       cout << v[i] << " ";
   } 
   cout << '\n';
   
   for (int vi : v) { //otra forma más fácil de imprimir.
       cout << vi << " ";
   }
   cout << '\n';
   ```

2. **set**:  Es una plantilla para mantener conjuntos ordenados, sin repetición.

   ```c++
   #include <set> //librería que contiene al contenedor.
   using namespace std;
   
   set<string> s; //declarar un set de strings vacío.
   s.insert("hola"); //insertando el string "hola". {"hola"}
   s.insert("adios"); //insertando el string "adios". {"adios", "hola"}
   s.insert("buenas"); //insertando el string "buenas". {"adios", "buenas", "hola"}
   
   for (string si : s) { //imprimiendo los strings, separados por espacios.
       cout << si << " ";
   } 
   cout << '\n';
   
   bool is_hola = s.count("hola"); //verificando que este 
   								//(count 1: esta, count 0: no esta)
   
   s.erase("adios"); //eliminando string adios.
   
   cout << s.size() << '\n'; //imprimiendo la cantidad de elementos distintos
   ```

   

3. **map**: Es una plantilla para mantener un mapeo, como una función con valores discretos.

   ```c++
   #include <map> //librería que contiene al contendor
   using namespace std;
   
   map<int, int> id; //declaramos un mapping entre un entero y otro entero.
   id[-1] = 1; //mapeo el valod de -1 a 1.
   cout << id[-1] << '\n'; //imprimo el valor de mapeo de -1 (1).
   id[123] = -2323; //mapeo de 123 a -2323.
   id[-1] += 1; //aumento en 1 el mapeo de -1 (2 = 1+1).
   id[5]; //creo un mapeo de 5, pero que valor? 0 por defecto.
   cout << id[5] << '\n'; //imprime 0.
   
   id.erase(-1); //elimino el mapeo de -1.
   
   for (pair<int, int> e : id) { //imprime todos los pares de valor/mapeo
       cout << e.first << " " << e.second << '\n'; //imprime el valor y el mapeo.
   }
   ```

4. **priority_queue**: Es una plantilla que mantiene el mayor elemento (podemos usar set, pero priority_queue es más óptimo).

   ```c++
   #include <queue> //librería del contenedor
   using namespace std;
   
   priority_queue<int> q; //crea un priority queue vacío
   q.push(5); //agrega el 5
   q.push(-1); //agrega el -1
   q.push(6); //agrega el 6
   q.push(2); //agrega el 2
   cout << q.top() << '\n'; //imprime el mayor (6).
   q.pop(); //elimina el mayor
   cout << q.top() << '\n'; //imrpime 5.
   q.pop();
   cout << q.top() << '\n'; //imrpime 2.
   ```

5. **multiset**: Al igual que set pero, permiten elementos repetidos.

   ```c++
   #include <set>
   using namespace std;
   
   multiset<int> ms;
   ms.insert(2);
   ms.insert(5);
   ms.insert(6);
   cout << *ms.lower_bound(4) << '\n'; //imprime el primer elemento no menor a 4 (5).
   cout << *ms.upper_bound(4) << '\n'; //imprime el primer elemento mayor a 4 (5).
   
   cout << *ms.lower_bound(5) << '\n'; //5
   cout << *ms.upper_bound(5) << '\n'; //6
   
   
   ```

### **Utilidades**:

 1. **pair**: permite agrupar dos elementos.

    ```c++
    #include <utility> //libreria de utilidades
    using namespace std;
    
    pair<int, int> p; //incializar un pair de dos 0s. 
    pair<int, int> q(2, 4); //inicializar un pair con valores 2 y 4.
    pair<int, int> r{3, 6}; //inicializar un pair con valores 3 y 6.
    
    cout << q.first << '\n'; //imprimir primer elemento (2).
    cout << q.second << '\n'; //imprimir segundo elemento (4).
    
    map<int, int> f;
    f[5] = 3;
    pair<int, int> s = *f.find(5); // s = (5, 3)
    
    pair<int, int> t = {1, 2}; // t{1, 2}.
    pair<int, int> u = make_pair(1, 2); // u = pair<int, int>(1, 2);
    ```

2. **auto**: una variable multiusos.

   ```c++
   auto x = "hola"; //x es un array de caracteres.
   auto y = string("hola"); //y es un string
   auto w = {1, -1.}; //w es un pair<int, float>
   auto u = {1, 2, 3}; //u es un vector<int>{1, 2, 3}
   priority_queue<int> v;
   auto t = v; //t es un priority_queue
   ```

3. **lambda functions**: funciones sin nombre.

   ```c++
   auto f = [](int a, int b) { //declaramos una funcion que suma dos numeros
   	return a+b;
   };
   
   vector<int> v{1, 4, 3};
   auto g = [&](int i, int j) { //declaramos una funcion que suma dos numeros 
       return v[i] + v[j]; 	 //en v, a traves de los indices. 
   };
   
   ```

### **Algoritmos**:

 1. **sort**: Permite ordenar un vector.

    ```c++
    #include <algorithm> //donde estan incluidos los algoritmos
    using namespace std;
    
    vector<int> v{3, 1, 8, 5};
    sort(v.begin(), v.end());
    for (auto e : v) { //1, 3, 5, 8
        cout << e << ' ';
    }
    cout << '\n';
    
    int n = 4;
    int arr[n+1] = {3, 1, 5, 8};
    sort(arr, arr+n);
    for (int i = 0; i < n; ++i) {
        cout << arr[i] << ' ';
    }
    cout << '\n';
    
    //ordenar con un comparador, tomando el valor absoluto de los elementos:
    vector<int> u{5, 1, -2, 3, -10, 8, -4};
    sort(u.begin(), u.end(), [](int a, int b) {
        return abs(a) < abs(b);
    }); //1, -2, 3, -4, 5, 8, -10.
    ```

2. **accumulate**: Suma de elementos.

   ```c++
   #include <algorithm>
   using namespace std;
   
   vector<int> v{1, 3, 5, 10, -1};
   cout << accumulate(v.begin(), v.end(), 0) << '\n';//imprime 18=1 + 3 + 5 + 10 + (-1)
   ```

3. **min_element/max_element**: Halla el menor elemento más a la izquierda.

   ```c++
   #include <algorithm>
   using namespace std;
   
   vector<int> v{1, 3, 5, 10, 3};
   cout << *min_element(v.begin(), v.end()) << '\n'; //3
   cout << min_element(v.begin(), v.end()) - v.begin() << '\n'; //1 (segundo elemento)
   ```

4. otras: **unique**, **count_if**, **next_permutation**, **reverse**, **lower_bound**, **upper_bound**, etc.

