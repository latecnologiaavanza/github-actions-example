### 🔹 1. **Primero compilar**

* Toma tu código fuente `.java`
* Lo convierte en `.class` (bytecode de la JVM).
* Resultado:

  ```
  target/classes/...
  ```

---

### 🔹 2. **Después empaquetar**

* Toma esos `.class` ya compilados + recursos (`application.properties`, `static/`, etc.)
* Los mete en un **JAR** o **WAR**.
* En Spring Boot, el `spring-boot-maven-plugin` además incluye todas las dependencias → "fat JAR".
* Resultado:

  ```
  target/miapp-1.0.0.jar
  ```

---

✅ **En resumen:**

1. **Compilar** → preparar las clases.
2. **Empaquetar** → armar el archivo ejecutable.

---

👉 Si ejecutas:

```bash
mvn clean package
```

Maven hace **ambos pasos**: primero compila, luego empaqueta.
