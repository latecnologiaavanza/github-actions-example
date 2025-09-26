# 🟦 ¿Qué es un entorno de ejecución?

👉 El **entorno de ejecución** (o *runtime environment*) es el **conjunto de recursos y condiciones que necesita un programa para ejecutarse correctamente**.

Es como el “ecosistema” donde vive y funciona un software.

Incluye:

* **Sistema operativo** (Windows, Linux, macOS).
* **Librerías necesarias** (por ejemplo, `.dll`, `.so`, `.jar`).
* **Intérprete o máquina virtual** (ej: JVM en Java, Node.js para JS).
* **Configuraciones** (variables de entorno, rutas, permisos).

📌 Sin un entorno de ejecución adecuado, el programa **no podría ejecutarse** aunque esté bien escrito.

---

# 🟦 Ejemplos

### 🔹 Java

* Un programa Java necesita la **JVM (Java Virtual Machine)** para ejecutarse.
* El entorno de ejecución aquí es el **JRE (Java Runtime Environment)** que incluye la JVM + librerías básicas de Java.

Ejemplo:

```bash
java -jar app.jar
```

Este comando ejecuta la app en el **entorno de ejecución de Java**.

---

### 🔹 Python

* Un script `.py` necesita el **intérprete de Python** (`python3`).
* Si no tienes Python instalado, el programa no corre.

Ejemplo:

```bash
python3 hola.py
```

---

### 🔹 Node.js

* Una aplicación con `app.js` (JavaScript del lado del servidor) necesita que esté instalado **Node.js** como entorno de ejecución.

Ejemplo:

```bash
node app.js
```

---

# 🟦 Diferencia entre "compilación" y "ejecución"

* **Compilación** → convierte tu código fuente a un formato ejecutable (ej: `.class`, `.exe`).
* **Ejecución** → es cuando ese código se corre dentro de un **entorno de ejecución** adecuado.

Ejemplo en Java:

1. Compilas → `javac Hola.java` → genera `Hola.class`.
2. Ejecutas → `java Hola` → JVM corre el `.class` en el **entorno de ejecución**.

---

# 🟦 Analogía

Piensa en una obra de teatro 🎭:

* El **guion** → es tu código fuente.
* Los **actores entrenando** → es la compilación.
* El **teatro con luces, escenario y público** → es el entorno de ejecución.

Sin teatro (entorno), la obra no se puede presentar aunque tengas guion y actores.

---

# 🟦 Conclusión

El **entorno de ejecución**:
✔️ Es el lugar y las herramientas necesarias para que un programa corra.
✔️ Varía según el lenguaje: JRE en Java, intérprete en Python, Node.js en JS, etc.
✔️ Asegura que tu software se ejecute igual en diferentes máquinas, siempre que ese entorno esté disponible.
