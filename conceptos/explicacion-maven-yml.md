```yaml
name: proyecto cicd flow
```

* **`name`** → Nombre descriptivo del workflow.
* Aparece en la pestaña **Actions** de tu repo en GitHub.
* Aquí se llama **"proyecto cicd flow"**.

---

```yaml
on:
  push:
    branches: [ "master" ]
  pull_request:
    branches: [ "master" ]
```

* **`on`** → Define los **eventos que activan el workflow**.
* `push` → el workflow se ejecuta cada vez que haces un **push** a la rama `master`.
* `pull_request` → el workflow también se ejecuta cada vez que se abre un **pull request** hacia `master`.

👉 Esto asegura que **cada cambio en `master` se construya y pruebe automáticamente**.

---

```yaml
jobs:
  build:
```

* **`jobs`** → Conjunto de **trabajos** que ejecuta el workflow.
* Aquí solo hay un job, llamado **`build`**.
* Cada job corre de manera independiente (incluso en paralelo, si defines varios).

---

```yaml
    runs-on: ubuntu-latest
```

* Especifica el **sistema operativo** donde se ejecutará el job.
* `ubuntu-latest` → GitHub provee una máquina virtual con Ubuntu preconfigurada.
* También podrías usar `windows-latest` o `macos-latest`.

---

```yaml
    steps:
```

* **`steps`** → Lista de pasos que forman parte del job `build`.
* Cada paso puede ejecutar comandos o usar una acción ya existente de GitHub Marketplace.

---

```yaml
    - uses: actions/checkout@v4
```

* **`uses`** → Indica que se usará una **acción predefinida**.
* `actions/checkout@v4` → acción oficial de GitHub que **descarga el código fuente de tu repo** dentro de la máquina virtual.
* Sin esto, el workflow no tendría acceso a tu proyecto.

---

```yaml
    - name: Set up JDK 21
      uses: actions/setup-java@v4
      with:
        java-version: '21'
        distribution: 'temurin'
        cache: maven
```

* **`- name`** → Nombre del paso, aparece en los logs de ejecución.
* `uses: actions/setup-java@v4` → acción oficial que **instala y configura Java** en la máquina.
* `with:` → parámetros para configurar la acción:

  * `java-version: '21'` → instala **Java 21**.
  * `distribution: 'temurin'` → define la distribución (Temurin = OpenJDK mantenido por Adoptium).
  * `cache: maven` → habilita cache para dependencias de Maven (ahorra tiempo en builds futuros).

---

```yaml
    - name: Build with Maven
      run: mvn clean install
```

* **`run`** → ejecuta un comando en la terminal del runner (la VM de Ubuntu).
* Aquí corre:

  * `mvn clean install` → limpia compilaciones previas (`clean`), compila el proyecto, corre las pruebas y empaqueta el artefacto (`install`).

👉 Básicamente aquí se valida que tu aplicación **compila bien, pasa los tests y genera el .jar/.war**.

---

## ✅ En resumen

Este workflow hace lo siguiente:

1. Se activa al hacer push o PR en `master`.
2. Ejecuta un job `build` en una VM con Ubuntu.
3. Descarga el código del repo.
4. Instala Java 21 (Temurin).
5. Ejecuta `mvn clean install` para compilar, probar y empaquetar la app.