# 🟦 ¿Qué es un lenguaje de programación?

Un **lenguaje de programación** es un **conjunto de reglas, símbolos y palabras clave** que permiten a los programadores **dar instrucciones a una computadora** para que realice tareas específicas.

👉 Es el puente entre **el pensamiento humano** y **el lenguaje máquina (binario: 0 y 1)**.

Ejemplo en **Java**:

```java
System.out.println("Hola Mundo");
```

Este código es entendible por un humano → pero la computadora lo ejecuta finalmente como **instrucciones en binario** gracias al compilador/intérprete.

---

# 🟦 Características principales de un lenguaje de programación

1. **Sintaxis** → Reglas sobre cómo escribir el código (como la gramática en un idioma humano).
   Ejemplo: en Java siempre terminamos con `;`.

2. **Semántica** → El significado de las instrucciones escritas.
   Ejemplo: `if (x > 10)` significa tomar una decisión condicional.

3. **Abstracción** → Permite expresar ideas complejas con instrucciones más simples.
   Ejemplo: en lugar de manipular memoria directamente, puedes usar un `ArrayList`.

---

# 🟦 Tipos de lenguajes de programación

## 🔹 Según el **nivel**

* **Lenguajes de bajo nivel** → cercanos a la máquina.

  * Ejemplo: **Ensamblador**.
  * Muy rápidos, pero difíciles de leer.

* **Lenguajes de alto nivel** → cercanos al humano.

  * Ejemplo: **Java, Python, C#**.
  * Más fáciles de aprender, portables y legibles.

---

## 🔹 Según la **ejecución**

* **Compilados** → El código fuente se convierte en lenguaje máquina antes de ejecutarse.

  * Ejemplo: **C, C++**.
  * Ventaja: velocidad.
  * Desventaja: menos flexibilidad.

* **Interpretados** → El código se ejecuta línea por línea en un intérprete.

  * Ejemplo: **Python, JavaScript**.
  * Ventaja: facilidad para probar rápidamente.
  * Desventaja: más lentos.

* **Mixtos** (Compilados + Interpretados) → Se compila a un código intermedio (*bytecode*), y luego la **máquina virtual** lo interpreta.

  * Ejemplo: **Java (JVM), C# (CLR)**.

---

## 🔹 Según el **paradigma**

* **Imperativos** → Secuencia de instrucciones paso a paso. (C, Pascal)
* **Orientados a objetos (OOP)** → Organizan el código en objetos y clases. (Java, C#, Python)
* **Funcionales** → Basados en funciones matemáticas y sin estados mutables. (Haskell, Scala, Elixir)
* **Lógicos** → Basados en reglas y hechos. (Prolog)

👉 Hoy en día, muchos lenguajes son **multiparadigma** (ej: Python, JavaScript, Kotlin).

---

# 🟦 Ejemplo práctico

### Mismo programa en distintos lenguajes:

**Python** (interpretado, dinámico, alto nivel):

```python
print("Hola Mundo")
```

**Java** (compilado a bytecode, estático, OOP):

```java
public class Hola {
    public static void main(String[] args) {
        System.out.println("Hola Mundo");
    }
}
```

**C** (compilado, bajo nivel comparado con Java/Python):

```c
#include <stdio.h>

int main() {
    printf("Hola Mundo\n");
    return 0;
}
```

👉 Todos hacen lo mismo: mostrar "Hola Mundo", pero con sintaxis y complejidad diferentes.

---

# 🟦 ¿Por qué existen tantos lenguajes?

* **Rendimiento** → C y C++ se usan en sistemas operativos o videojuegos.
* **Facilidad de uso** → Python se usa en ciencia de datos e IA.
* **Portabilidad** → Java corre en cualquier sistema con JVM.
* **Web** → JavaScript reina en el desarrollo frontend.

Cada lenguaje está optimizado para **resolver problemas específicos**.

---

# 🟦 Conclusión

Un **lenguaje de programación** es:

* Un medio de comunicación entre humanos y computadoras.
* Tiene **sintaxis** (cómo se escribe) y **semántica** (qué significa).
* Puede ser **alto/bajo nivel**, **compilado/interpretado**, y seguir distintos **paradigmas**.
* El lenguaje que eliges depende del **contexto del problema** que quieras resolver.
