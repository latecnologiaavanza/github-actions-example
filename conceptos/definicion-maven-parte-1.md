# 🚀 Guía Completa de Maven: Qué es, para qué sirve, plugins y goals

---

## 🔹 1. ¿Qué es Maven?

**Maven** es una **herramienta de construcción y gestión de proyectos Java** desarrollada por Apache.
Es uno de los *build tools* más usados en el ecosistema Java (junto con Gradle).

La palabra "Maven" viene del yidis y significa *“el que acumula conocimiento”*.

---

## 🔹 2. ¿Para qué sirve Maven?

Maven resuelve cuatro problemas fundamentales en proyectos Java:

### 📦 1. Gestión de dependencias

Antes se descargaban manualmente librerías `.jar`. Con Maven, solo declaras lo que necesitas en `pom.xml`:

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
  <version>3.2.4</version>
</dependency>
```

👉 Maven se encarga de:

* Descargar esa librería desde un repositorio central o remoto.
* Descargar también sus **dependencias transitivas** (las que necesita esa librería).
* Guardarlas en el repositorio local `~/.m2/repository`.

---

### 🏗️ 2. Automatización del ciclo de construcción (build lifecycle)

Maven define un **ciclo de vida** estándar para construir software:

* Compilar
* Ejecutar pruebas
* Empaquetar (JAR/WAR)
* Instalar en el repo local
* Desplegar en un repo remoto

👉 Así no tienes que inventar un proceso, todo está estandarizado.

---

### 📂 3. Estandarización de proyectos

Maven establece una **estructura estándar** para proyectos Java:

```
mi-proyecto/
 ├── src/
 │   ├── main/
 │   │   └── java/       (código fuente)
 │   │   └── resources/  (configuración, properties)
 │   ├── test/           (pruebas unitarias)
 ├── target/             (artefactos generados)
 └── pom.xml             (configuración de Maven)
```

👉 Cualquier desarrollador que vea un proyecto Maven ya sabe dónde encontrar cada cosa.

---

### ⚙️ 4. Extensibilidad mediante **plugins**

Maven en realidad **no sabe hacer nada por sí solo**.
Todo lo que hace (compilar, testear, empaquetar, etc.) lo hace a través de **plugins**.

---

## 🔹 3. ¿Qué es un plugin en Maven?

Un **plugin** es un conjunto de funcionalidades que extiende a Maven.
Cada plugin implementa acciones que pueden ejecutarse durante el ciclo de vida de Maven.

Ejemplos de plugins comunes:

* **maven-compiler-plugin** → compila el código Java.
* **maven-surefire-plugin** → ejecuta pruebas unitarias.
* **maven-jar-plugin** → empaqueta en JAR.
* **spring-boot-maven-plugin** → permite ejecutar apps Spring Boot con `mvn spring-boot:run`.

👉 Piensa en un **plugin** como un “paquete de herramientas” que sabe hacer tareas específicas.

---

## 🔹 4. ¿Qué es un goal en Maven?

Dentro de cada plugin, hay **goals**.
Un **goal** es una acción individual que puede ejecutar Maven.

Ejemplo:

* El plugin `maven-compiler-plugin` tiene el goal `compile`.
* El plugin `maven-surefire-plugin` tiene el goal `test`.
* El plugin `spring-boot-maven-plugin` tiene el goal `spring-boot:run`.

👉 Piensa en un **goal** como una **tarea específica** dentro de un plugin.

---

## 🔹 5. Relación entre Lifecycle, Fase, Plugin y Goal

* **Lifecycle (ciclo de vida)** → el conjunto de fases predefinidas (ejemplo: `default`).
* **Phase (fase)** → un paso dentro del ciclo (ejemplo: `compile`, `test`, `package`).
* **Plugin** → un conjunto de herramientas que sabe ejecutar ciertas tareas.
* **Goal** → una tarea concreta que implementa un plugin.

👉 Maven asocia **fases** del ciclo de vida con **goals de plugins**.

Ejemplo:

* Fase **compile** → ejecuta el goal `compiler:compile`.
* Fase **test** → ejecuta el goal `surefire:test`.
* Fase **package** → ejecuta el goal `jar:jar` o `spring-boot:repackage`.

---

## 🔹 6. Ciclos de vida en Maven

Maven tiene 3 ciclos de vida principales:

1. **default** → construcción del proyecto.
2. **clean** → limpieza del directorio `target/`.
3. **site** → generación de documentación/reportes.

👉 Un “build completo” suele ser `clean + default`.

---

### Ciclo **default** en detalle

Fases más importantes en orden:

1. **validate** → verifica que el proyecto es válido.
2. **compile** → compila el código fuente.
3. **test-compile** → compila el código de prueba.
4. **test** → ejecuta pruebas unitarias.
5. **package** → empaqueta en JAR/WAR.
6. **verify** → verificaciones extra.
7. **install** → instala en repo local (`~/.m2`).
8. **deploy** → sube el artefacto a un repo remoto.

---

## 🔹 7. Ejemplo de `pom.xml` con plugins

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.ejemplo</groupId>
    <artifactId>mi-app</artifactId>
    <version>1.0.0</version>
    <packaging>jar</packaging>

    <dependencies>
        <!-- Dependencia: Spring Boot Web -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <version>3.2.4</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <!-- Plugin para compilar -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.11.0</version>
                <configuration>
                    <source>21</source>
                    <target>21</target>
                </configuration>
            </plugin>

            <!-- Plugin para ejecutar Spring Boot -->
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>
```

👉 Aquí:

* `maven-compiler-plugin` ejecuta el goal `compile` en la fase `compile`.
* `spring-boot-maven-plugin` añade el goal `spring-boot:run` que puedes ejecutar manualmente.

---

## 🔹 8. Ejemplos de comandos útiles

* `mvn clean` → limpia el proyecto.
* `mvn compile` → compila.
* `mvn test` → ejecuta tests.
* `mvn package` → empaqueta en JAR/WAR.
* `mvn install` → instala en repo local.
* `mvn deploy` → despliega en repo remoto.
* `mvn spring-boot:run` → ejecuta la app (gracias al plugin de Spring Boot).

---

# 🔹 9. Resumen gráfico

```
Build (concepto general)
 ├── Ciclo clean → limpiar
 ├── Ciclo default → construir
 │     ├─ validate
 │     ├─ compile → plugin-compiler:compile
 │     ├─ test → plugin-surefire:test
 │     ├─ package → plugin-jar:jar
 │     ├─ install → instala en ~/.m2
 │     └─ deploy → sube a repositorio remoto
 └── Ciclo site → documentación

Plugin = conjunto de funcionalidades
Goal = acción específica dentro de un plugin
```

---

✅ **En conclusión**:

* **Maven** = herramienta de gestión de proyectos Java.
* **Plugin** = paquete de funcionalidades que extiende a Maven.
* **Goal** = acción concreta de un plugin.
* **Lifecycle (default, clean, site)** = conjunto de fases que definen el flujo de construcción.
* **Fase** = paso dentro de un ciclo (ej: `compile`, `test`, `package`).
* **Build** = proceso completo que combina lifecycle + plugins + goals.
