# 🟦 Guía completa: JVM, JRE, JDK y conceptos relacionados en Java

---

## 1️⃣ Java: ¿Qué es?

Java es un **lenguaje de programación de alto nivel, orientado a objetos, multiplataforma**.
Se diseñó bajo el principio de **“Write Once, Run Anywhere” (WORA)** → escribe tu código una vez y ejecútalo en cualquier dispositivo que tenga una JVM.

👉 Ejemplo: Un programa en Java puede correr en Windows, Linux o Mac **sin modificar el código fuente**, gracias a la JVM.

---

## 2️⃣ ¿Qué es la JVM?

**JVM = Java Virtual Machine (Máquina Virtual de Java)**

* Es el **entorno de ejecución** que interpreta y ejecuta el **bytecode** generado al compilar un programa Java.
* Traduce ese bytecode a **instrucciones nativas** que entiende el sistema operativo y el procesador.
* Asegura la **portabilidad** del código.

### Funciones principales de la JVM:

1. **Carga** clases y bibliotecas necesarias.
2. **Verifica** el bytecode para evitar errores de seguridad.
3. **Ejecuta** el código (usando intérprete o JIT - *Just-In-Time Compiler*).
4. **Gestión de memoria** (incluye *Garbage Collector* para liberar memoria automáticamente).

👉 Ejemplo práctico:
Cuando ejecutas:

```bash
java HolaMundo
```

La JVM carga el archivo `HolaMundo.class` (bytecode) y lo convierte a instrucciones nativas que tu computadora entiende.

---

## 3️⃣ ¿Qué es el JRE?

**JRE = Java Runtime Environment (Entorno de Ejecución de Java)**

* Es el **conjunto de herramientas necesarias para ejecutar aplicaciones Java**.
* Incluye:

  * **JVM** (máquina virtual que interpreta el bytecode).
  * **Bibliotecas estándar de Java** (colecciones, IO, networking, utilidades, etc.).

👉 El JRE **NO incluye herramientas de desarrollo** (como compilador `javac`), solo lo necesario para ejecutar programas.

Ejemplo: Si solo quieres **usar aplicaciones Java** (pero no programar), con instalar el JRE es suficiente.

---

## 4️⃣ ¿Qué es el JDK?

**JDK = Java Development Kit (Kit de Desarrollo de Java)**

* Es el **paquete completo para desarrollar en Java**.
* Incluye:

  * El **JRE** (y por lo tanto, la JVM).
  * Herramientas de desarrollo:

    * `javac` → compilador de Java (convierte código fuente `.java` en bytecode `.class`).
    * `javadoc` → genera documentación en HTML.
    * `jdb` → depurador.
    * Herramientas de empaquetado (`jar`, `javap`, etc.).

👉 Si quieres **programar en Java**, necesitas el **JDK**.

---

## 5️⃣ Relación entre JDK, JRE y JVM

Podemos verlo como capas:

```
JDK  =  JRE  +  Herramientas de desarrollo
JRE  =  JVM  +  Bibliotecas estándar
JVM  =  Motor de ejecución del bytecode
```

📌 **Resumiendo:**

* **JVM** → ejecuta el bytecode.
* **JRE** → entorno para ejecutar aplicaciones (JVM + librerías).
* **JDK** → entorno para desarrollar aplicaciones (JRE + compilador y herramientas).

---

## 6️⃣ Java como lenguaje de **alto nivel**

Un lenguaje de **alto nivel** es aquel que está más cerca del **lenguaje humano** que del lenguaje máquina.

* Java se considera **alto nivel** porque:

  * Usa **palabras clave legibles** (`class`, `public`, `if`, `while`) en lugar de instrucciones de hardware.
  * Es **independiente de la arquitectura** gracias a la JVM.
  * Ofrece **abstracciones** (clases, objetos, colecciones, excepciones) que ocultan los detalles complejos del hardware.

👉 Ejemplo:
En Java:

```java
System.out.println("Hola mundo");
```

En **lenguaje ensamblador** (bajo nivel), escribir "Hola mundo" requiere decenas de instrucciones específicas de CPU.

---

## 7️⃣ Bajo nivel vs Alto nivel

* **Lenguaje de bajo nivel**: cercano a la máquina, depende de la arquitectura. Ej: ensamblador, C en algunos casos.
* **Lenguaje de alto nivel**: cercano al humano, abstrae el hardware. Ej: Java, Python, C#.

👉 **Java es alto nivel** porque no trabajas directamente con registros de memoria o instrucciones de CPU.

---

## 8️⃣ Tipado en Java

Java es un lenguaje **estáticamente tipado y fuertemente tipado**:

1. **Estáticamente tipado** → El tipo de cada variable se conoce en **tiempo de compilación**.

   * Ejemplo:

     ```java
     int numero = "hola"; // ❌ Error de compilación
     ```

     El compilador (`javac`) detecta el error antes de ejecutar.

2. **Fuertemente tipado** → No permite mezclar tipos de manera implícita insegura.

   * Ejemplo:

     ```java
     int x = 10;
     double y = x; // ✅ permitido porque hay conversión segura
     String s = x; // ❌ error, no se puede convertir int a String automáticamente
     ```

👉 Esto hace que Java sea más **seguro y robusto**, aunque menos flexible que lenguajes dinámicos como Python o JavaScript.

---

## 9️⃣ Ejemplo completo del flujo (JDK → JVM)

1. Escribes un programa en `HolaMundo.java`.

   ```java
   public class HolaMundo {
       public static void main(String[] args) {
           System.out.println("Hola Mundo");
       }
   }
   ```

2. Usas el **JDK** para compilarlo:

   ```bash
   javac HolaMundo.java
   ```

   Esto genera `HolaMundo.class` (bytecode).

3. El **JRE/JVM** ejecuta el programa:

   ```bash
   java HolaMundo
   ```

   👉 Y aparece: `Hola Mundo`.

---

## 🔟 Resumen visual

```
[JDK] = [JRE + Compilador (javac), herramientas]
[JRE] = [JVM + Librerías estándar]
[JVM] = [Ejecutor de bytecode → instrucciones máquina]

Java = Lenguaje de alto nivel
Tipado = Estático + Fuerte
```

---

📌 **Conclusión:**

* El **JDK** lo usas para programar.
* El **JRE** lo usas para ejecutar.
* La **JVM** es el motor que hace que tu programa corra en cualquier sistema operativo.
* Java es **alto nivel**, **estáticamente tipado** y **fuertemente tipado**, lo que lo hace portable, seguro y robusto.
