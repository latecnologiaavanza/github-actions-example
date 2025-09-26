# 🟦 ¿Qué es Maven?
Maven es una **herramienta de gestión y automatización de proyectos Java**.  
Sirve principalmente para:
- **Compilar** el código fuente.
- **Ejecutar pruebas** automáticamente.
- **Empaquetar** el proyecto (JAR, WAR, etc.).
- **Gestionar dependencias** (descargar librerías externas desde repositorios).
- **Generar documentación y reportes**.
- **Instalar y desplegar** el proyecto en repositorios locales o remotos.

👉 La clave es que Maven define un **ciclo de vida del proyecto** y automatiza las tareas típicas de desarrollo.  
En lugar de que el programador escriba scripts manuales, solo dice:  
```bash
mvn clean install
```
y Maven hace todo el flujo (limpiar, compilar, probar, empaquetar, instalar).

---

# 🟦 Ciclos de vida en Maven
Maven tiene **3 ciclos de vida principales**:

1. **default** → el ciclo central, encargado de *construir* el proyecto (compilar, testear, empaquetar, instalar, desplegar).  
2. **clean** → encargado de *limpiar* los archivos generados (por ejemplo `target/`).  
3. **site** → genera documentación y reportes del proyecto.

Cada ciclo está compuesto de **fases**.

---

# 🟦 Fases (Phases)
Una **fase** es un paso dentro de un ciclo de vida.  
Ejemplo del ciclo **default**:

- `validate` → validar que el proyecto es correcto.
- `compile` → compilar el código fuente.
- `test` → ejecutar pruebas unitarias.
- `package` → empaquetar en JAR/WAR.
- `verify` → ejecutar verificaciones adicionales.
- `install` → instalar el paquete en el repositorio local.
- `deploy` → desplegar en un repositorio remoto.

👉 Cuando ejecutas una fase, Maven ejecuta **todas las fases anteriores** automáticamente.  
Ejemplo:
```bash
mvn install
```
Ejecuta: `validate → compile → test → package → verify → install`.

---

# 🟦 Plugins en Maven
Maven en sí **no sabe compilar, ni probar, ni empaquetar**.  
Todo lo hace mediante **plugins**.

Un **plugin** en Maven es un conjunto de **goals** que implementan funciones concretas.  
Ejemplos:
- `maven-compiler-plugin` → compilar código Java.
- `maven-surefire-plugin` → ejecutar pruebas unitarias.
- `maven-jar-plugin` → crear un archivo JAR.
- `maven-deploy-plugin` → subir artefactos a repositorios remotos.

---

# 🟦 Goals (Metas)
Un **goal** es una tarea concreta proporcionada por un plugin.  
Ejemplo:
- `compiler:compile` → compila el código fuente.
- `compiler:testCompile` → compila el código de pruebas.
- `surefire:test` → ejecuta los tests.

👉 Cada fase del ciclo de vida tiene goals atados por defecto.  
Por ejemplo:
- La fase `compile` invoca el goal `compiler:compile`.  
- La fase `test` invoca el goal `surefire:test`.

Tú puedes añadir o configurar plugins/goals en tu `pom.xml`.

---

# 🟦 Diferencia entre build y default
- **default** → es el ciclo de vida de Maven que define fases desde `validate` hasta `deploy`.  
- **build** → es el proceso general de construcción de un proyecto (compilar, probar, empaquetar, etc.), que Maven implementa usando el ciclo `default` + plugins.  
👉 En pocas palabras: el *build* usa el ciclo `default`, pero no son lo mismo.

---

# 🟦 Automatización
✅ Sí, **todo esto se ejecuta automáticamente**.  
Tú solo llamas a Maven con un comando, por ejemplo:

```bash
mvn clean install
```

y Maven hace automáticamente:
1. `clean` → borra la carpeta `target/`.
2. `compile` → compila el código fuente.
3. `test` → corre las pruebas unitarias.
4. `package` → empaqueta en un JAR/WAR.
5. `install` → guarda el artefacto en el repositorio local.

👉 No necesitas compilar ni ejecutar pruebas manualmente. Maven automatiza todo el flujo de construcción.

---

📌 En resumen:
- Maven = automatizador de proyectos Java.  
- Ciclo de vida = conjunto de fases.  
- Fase = un paso del ciclo.  
- Plugin = añade capacidades (compilar, probar, empaquetar).  
- Goal = tarea concreta de un plugin.  
- Build = proceso general de construir un proyecto (que en Maven se hace con el ciclo `default`).  
