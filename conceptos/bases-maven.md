# 🚀 Guía Completa: Compilar, Ejecutar, Build y Ciclo de Vida en Maven

---

## 🔹 1. Conceptos básicos

### ✅ **Compilar**

* Acción de transformar código fuente (`.java`) → bytecode (`.class`) que entiende la JVM.
* En Maven:

  ```bash
  mvn compile
  ```
* Resultado: en `target/classes` aparecen los `.class`.
  👉 **No ejecuta la app, solo la prepara.**

---

### ✅ **Ejecutar**

* Acción de **correr el programa ya compilado** en la JVM.
* Ejemplo con un JAR generado:

  ```bash
  java -jar target/app.jar
  ```

👉 Aquí la aplicación se “pone en marcha” (ejemplo: levanta un servidor Spring Boot).

---

### ✅ **Build**

* Es un **término genérico** en el desarrollo de software: significa **“construir la aplicación”**.
* Incluye varias tareas: **compilar, ejecutar pruebas, empaquetar, instalar y/o desplegar**.
* En Maven, cuando hacemos un build, casi siempre estamos usando el ciclo de vida **default** (y a veces `clean` y/o `site`).

Ejemplo:

```bash
mvn clean install
```

👉 Hace un **build completo**: limpia, compila, ejecuta pruebas, empaqueta y deja el artefacto en el repositorio local (`~/.m2`).

⚠️ **Importante:**

* **Build ≠ default**

  * *Build* → concepto general.
  * *Default* → un ciclo de vida específico en Maven que define fases como `compile`, `test`, `package`, etc.
  * Cuando decimos "hacer un build en Maven", casi siempre nos referimos a ejecutar fases del ciclo **default**.

---

## 🔹 2. Ciclos de vida en Maven

Maven define **3 ciclos de vida principales (lifecycles):**

1. **default** → se encarga de la construcción real del proyecto (compilar, probar, empaquetar, instalar, desplegar).
2. **clean** → limpia lo generado en `target/`.
3. **site** → genera documentación del proyecto (informes, reportes).

👉 Un **build completo** normalmente incluye al menos `clean` + `default`.

---

## 🔹 3. Ciclo de vida `default` en detalle

El ciclo `default` se compone de varias **fases (phases)** que Maven ejecuta en orden.
Estas son las más importantes:

1. **validate** → valida que el proyecto está correcto y listo (ejemplo: `pom.xml` bien formado).
2. **compile** → compila el código fuente (`.java` → `.class`).
3. **test-compile** → compila las clases de prueba.
4. **test** → ejecuta las pruebas unitarias (JUnit/TestNG).
5. **package** → empaqueta el código compilado en un artefacto (`.jar`, `.war`, `.ear`).
6. **verify** → ejecuta verificaciones adicionales (ejemplo: chequeos de calidad, integración).
7. **install** → instala el artefacto en el **repositorio local** (`~/.m2/repository`) para que otros proyectos lo puedan usar como dependencia.
8. **deploy** → publica el artefacto en un **repositorio remoto** (ejemplo: Nexus, Artifactory, GitHub Packages).

---

## 🔹 4. Relación entre Fases y Goals

* **Fase (phase):** paso dentro de un ciclo de vida.
* **Goal:** acción específica que realiza un *plugin*.

Ejemplo:

* La fase `compile` ejecuta el goal `compiler:compile` (del plugin `maven-compiler-plugin`).
* La fase `test` ejecuta el goal `surefire:test` (del plugin `maven-surefire-plugin`).

👉 Cada fase está asociada a uno o más goals de plugins.

---

## 🔹 5. Ejemplos prácticos de comandos Maven

* **Compilar únicamente código fuente:**

  ```bash
  mvn compile
  ```

  👉 Solo genera `.class`, no empaqueta ni corre pruebas.

* **Ejecutar solo las pruebas unitarias:**

  ```bash
  mvn test
  ```

  👉 Compila + compila pruebas + corre tests.

* **Empaquetar en JAR/WAR sin instalar:**

  ```bash
  mvn package
  ```

  👉 Deja el artefacto en `target/`.

* **Build completo e instalación en repo local:**

  ```bash
  mvn install
  ```

  👉 Compila + testea + empaqueta + instala en `.m2/repository`.

* **Build completo y despliegue en repo remoto:**

  ```bash
  mvn deploy
  ```

  👉 Lo mismo que `install`, pero lo sube a un repo remoto.

* **Build completo pero saltando tests:**

  ```bash
  mvn clean install -DskipTests
  ```

---

## 🔹 6. Diferencias resumidas

| Concepto     | Qué significa                                                          | Ejemplo en Maven                                 |
| ------------ | ---------------------------------------------------------------------- | ------------------------------------------------ |
| **Compilar** | Traducir `.java` → `.class`                                            | `mvn compile`                                    |
| **Ejecutar** | Correr el programa ya compilado                                        | `java -jar target/app.jar`                       |
| **Build**    | Proceso completo: compilar + testear + empaquetar + instalar/desplegar | `mvn clean install`                              |
| **default**  | Ciclo de vida que define fases de construcción                         | Se ejecuta en `mvn package`, `mvn install`, etc. |
| **clean**    | Ciclo que limpia la carpeta `target/`                                  | `mvn clean`                                      |
| **site**     | Ciclo que genera reportes/documentación                                | `mvn site`                                       |

---

## 🔹 7. Mapa mental simplificado

```
Build (concepto general)
 ├── Ciclo clean → limpiar
 ├── Ciclo default → construir
 │     ├─ validate
 │     ├─ compile
 │     ├─ test-compile
 │     ├─ test
 │     ├─ package
 │     ├─ verify
 │     ├─ install
 │     └─ deploy
 └── Ciclo site → documentación
```

---

✅ **En conclusión:**

* **Build** = proceso general de construir el software (usando Maven o cualquier otra herramienta).
* **Default** = ciclo de vida específico en Maven para construir.
* Un *build* en Maven **normalmente significa ejecutar el ciclo `default` (y a veces `clean` y/o `site`) hasta cierta fase como `install` o `deploy`**.
