# 🟦 ¿Qué es tipado en programación?

El **tipado** es la forma en que un lenguaje de programación **define, gestiona y aplica las reglas de los tipos de datos** (números, cadenas, booleanos, objetos, etc.).
👉 Dicho de otra forma: el tipado controla **qué valores puede almacenar una variable y qué operaciones se pueden hacer con ellos**.

Ejemplo:
En **Java** (tipado fuerte y estático):

```java
int numero = 10;    
numero = "hola"; // ❌ Error: no puedes asignar un String a un int
```

En **Python** (tipado dinámico):

```python
numero = 10     
numero = "hola"  # ✅ permitido, ahora numero es un string
```

---

# 🟦 Tiempo de compilación vs tiempo de ejecución

## 🔹 Tiempo de compilación

* Es la etapa en que el **compilador analiza tu código fuente** (archivo `.java`, `.cpp`, etc.) y lo convierte en un lenguaje intermedio o máquina (ejemplo: **bytecode en Java**).
* Aquí se detectan **errores de sintaxis y de tipos**.

Ejemplo en Java:

```java
int x = "hola"; 
```

❌ Esto da error **en compilación** porque el compilador (`javac`) ve que `"hola"` no es un `int`.

👉 Ventaja: el error se detecta **antes de ejecutar** el programa.

---

## 🔹 Tiempo de ejecución

* Es el momento en que el programa ya compilado **se está ejecutando en la máquina o JVM**.
* Aquí ocurren errores que dependen del flujo del programa y los datos reales.

Ejemplo en Java:

```java
int[] numeros = new int[3];
numeros[5] = 10; // ❌ Error en ejecución: ArrayIndexOutOfBoundsException
```

El compilador no lo detecta, pero al ejecutar sí falla.

---

# 🟦 Tipos de tipado

## 1️⃣ Estático vs Dinámico

* **Estático** → Los tipos se verifican en **tiempo de compilación**.
  Ejemplo: **Java, C, C++**

  ```java
  int x = 5;  
  x = "texto"; // ❌ Error en compilación
  ```

* **Dinámico** → Los tipos se verifican en **tiempo de ejecución**.
  Ejemplo: **Python, JavaScript**

  ```python
  x = 5
  x = "texto"  # ✅ permitido, ahora x es un string
  ```

---

## 2️⃣ Fuerte vs Débil

* **Fuerte** → No permite mezclas inseguras de tipos.
  Ejemplo: **Java, Python, Haskell**

  ```java
  int x = 10;
  String s = x; // ❌ Error, no puedes asignar int a String directamente
  ```

* **Débil** → Permite conversiones automáticas (a veces inseguras).
  Ejemplo: **JavaScript, PHP**

  ```javascript
  let x = 10 + "5";  // "105" → convierte el número a string
  ```

---

## 3️⃣ Explícito vs Implícito

* **Explícito** → El programador debe declarar el tipo.
  Ejemplo: **Java, C++**

  ```java
  int edad = 18;
  ```

* **Implícito** → El compilador/intérprete infiere el tipo automáticamente.
  Ejemplo: **Python, Kotlin, TypeScript**

  ```python
  edad = 18   # Python deduce que es un int
  ```

---

## 4️⃣ Tipado fuerte con inferencia

Algunos lenguajes combinan **tipado fuerte** con **inferencia automática**.
Ejemplo: **Kotlin, TypeScript, Rust, Java (desde la versión 10 con `var`)**

```java
var edad = 18;   // inferido como int
edad = "hola";  // ❌ Error, sigue siendo int
```

---

# 🟦 Resumen en tabla

| Clasificación | Característica                    | Ejemplos           |
| ------------- | --------------------------------- | ------------------ |
| **Estático**  | Tipos verificados en compilación  | Java, C, C++       |
| **Dinámico**  | Tipos verificados en ejecución    | Python, JavaScript |
| **Fuerte**    | No mezcla tipos implícitamente    | Java, Python       |
| **Débil**     | Conversión automática entre tipos | JavaScript, PHP    |
| **Explícito** | Programador declara el tipo       | Java, C++          |
| **Implícito** | El lenguaje infiere el tipo       | Python, Kotlin     |

---

# 🟦 ¿Qué es Java en cuanto a tipado?

* **Estáticamente tipado** → los tipos se verifican en compilación.
* **Fuertemente tipado** → no mezcla tipos sin conversión.
* **Principalmente explícito**, aunque desde Java 10 soporta **inferencia con `var`**.

Ejemplo:

```java
var nombre = "Juan";  // inferido como String
nombre = 10;          // ❌ Error, sigue siendo String
```

---

# 🟦 Conclusión

* El **tipado** define cómo un lenguaje maneja los tipos de datos.
* Los tipos más comunes son: **estático/dinámico**, **fuerte/débil**, **explícito/implícito**.
* La diferencia clave es **cuándo** se detectan los errores → en **compilación** (estático) o en **ejecución** (dinámico).
* **Java** → estático, fuerte, principalmente explícito.
