# 🚀 Guía completa: Docker + GitHub Actions en tu proyecto Spring Boot

---

## 📌 1. ¿Qué es Docker?

Docker es una tecnología que te permite empaquetar tu aplicación junto con todo lo que necesita (Java, librerías, dependencias, configuración) en una **imagen**.

De esa imagen puedes crear **contenedores**, que son instancias ejecutándose, totalmente aisladas y portables.

👉 Piénsalo así:

* **Dockerfile** = la receta.
* **Imagen Docker** = la torta ya lista.
* **Contenedor** = la torta servida en un plato (corriendo).

---

## 📌 2. Tu Dockerfile explicado

```dockerfile
FROM eclipse-temurin:21-jdk-alpine
EXPOSE 8080
ADD target/springboot-images-new.jar springboot-images-new.jar
ENTRYPOINT ["java","-jar","/springboot-images-new.jar"]
```

### 🔹 Línea por línea

1. **`FROM eclipse-temurin:21-jdk-alpine`**

   * Imagen base: trae Linux Alpine (muy liviano) + JDK 21 (Eclipse Temurin).
   * Esto asegura que tu app tenga el Java necesario.

2. **`EXPOSE 8080`**

   * Indica que tu aplicación correrá en el puerto 8080.
   * No abre el puerto por sí mismo, solo documenta qué puerto usará el contenedor.

3. **`ADD target/springboot-images-new.jar springboot-images-new.jar`**

   * Copia el JAR generado por Maven (`target/springboot-images-new.jar`) dentro de la imagen.
   * Dentro del contenedor se llamará igual: `springboot-images-new.jar`.

4. **`ENTRYPOINT ["java","-jar","/springboot-images-new.jar"]`**

   * Define el comando que se ejecuta al arrancar el contenedor.
   * En este caso, arranca tu aplicación Spring Boot con:

     ```bash
     java -jar springboot-images-new.jar
     ```

---

## 📌 3. ¿Qué es GitHub Actions?

GitHub Actions es un sistema de **CI/CD** (Integración Continua y Entrega Continua).
Permite definir **workflows** (flujos de trabajo) en archivos `.yml` que se ejecutan automáticamente cuando ocurre un evento en tu repositorio (ej: un `push` o `pull request`).

👉 En tu caso:

* Al hacer **push a master**,
* Se compila tu proyecto,
* Se construye la imagen Docker,
* Y se publica en Docker Hub.

---

## 📌 4. Tu workflow `.yml` explicado

```yaml
name: proyecto cicd flow

on:
  push:
    branches: [ "master" ]
  pull_request:
    branches: [ "master" ]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v4
    - name: Set up JDK 21
      uses: actions/setup-java@v4
      with:
        java-version: '21'
        distribution: 'temurin'
        cache: maven
    - name: Build with Maven
      run: mvn clean install

    - name: Build & push Docker image
      uses: mr-smithers-excellent/docker-build-push@v6
      with:
        image: christianraul/springboot-images-new
        tags: latest
        registry: docker.io
        dockerfile: Dockerfile
        username: ${{ secrets.DOCKER_USERNAME }}
        password: ${{ secrets.DOCKER_PASSWORD }}
```

---

### 🔹 Bloque por bloque

1. **`name: proyecto cicd flow`**

   * Nombre descriptivo de tu pipeline.

2. **`on:`**

   * Define los eventos que disparan el workflow.
   * Aquí: cuando haces `push` o un `pull_request` a la rama `master`.

3. **`jobs:`**

   * Un workflow puede tener varios **jobs** (tareas).
   * Aquí solo tienes uno: `build`.

4. **`runs-on: ubuntu-latest`**

   * Indica el **sistema operativo** donde se ejecutará el job (un runner de GitHub con Ubuntu).

5. **`steps:`**

   * Son los pasos que ejecuta el job.

---

### 🔹 Pasos dentro del job

1. **Checkout del código**

   ```yaml
   - uses: actions/checkout@v4
   ```

   * Descarga tu repositorio en el runner para que se pueda compilar.

2. **Configurar JDK 21**

   ```yaml
   - name: Set up JDK 21
     uses: actions/setup-java@v4
     with:
       java-version: '21'
       distribution: 'temurin'
       cache: maven
   ```

   * Instala JDK 21 en el runner.
   * Usa la distribución **Temurin**.
   * Activa caché para Maven → acelera las builds.

3. **Compilar con Maven**

   ```yaml
   - name: Build with Maven
     run: mvn clean install
   ```

   * Ejecuta `mvn clean install`:

     * **clean** → limpia compilaciones previas.
     * **install** → compila, testea, empaqueta y coloca el artefacto en el repositorio local Maven.
   * Aquí se genera el JAR en `target/springboot-images-new.jar`.

4. **Construir y subir imagen Docker**

   ```yaml
   - name: Build & push Docker image
     uses: mr-smithers-excellent/docker-build-push@v6
     with:
       image: christianraul/springboot-images-new
       tags: latest
       registry: docker.io
       dockerfile: Dockerfile
       username: ${{ secrets.DOCKER_USERNAME }}
       password: ${{ secrets.DOCKER_PASSWORD }}
   ```

   * Usa una acción externa (`docker-build-push`) que:

     1. Construye la imagen usando tu **Dockerfile**.
     2. Le pone el nombre `christianraul/springboot-images-new:latest`.
     3. La sube a **Docker Hub** (`docker.io`).
   * Se autentica con tus credenciales (`username` y `password`) que guardaste en **GitHub Secrets** para no exponerlas públicamente.

---

## 📌 5. Flujo completo de CI/CD

1. Subes código a GitHub (`push` a master).
2. GitHub Actions detecta el cambio y corre el workflow.
3. El runner Ubuntu:

   * Descarga tu código.
   * Instala Java 21.
   * Compila con Maven → genera el `.jar`.
   * Construye la imagen Docker con ese `.jar`.
   * La sube a Docker Hub.
4. Desde cualquier máquina puedes hacer:

   ```bash
   docker pull christianraul/springboot-images-new:latest
   docker run -p 8080:8080 christianraul/springboot-images-new
   ```

   Y tu app se levanta en un contenedor 🚀.

---

## 📌 6. Beneficios

* **Automatización total** → no compilas ni creas la imagen manualmente.
* **Consistencia** → siempre se construye igual en GitHub.
* **Entrega continua** → cada push a master produce una nueva imagen lista para desplegar.
* **Portabilidad** → cualquiera puede bajar la imagen desde Docker Hub y correrla.
