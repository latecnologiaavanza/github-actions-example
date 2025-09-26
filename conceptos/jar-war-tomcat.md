# 🟦 1. ¿Qué es un JAR?

👉 **JAR (Java ARchive)** es un archivo comprimido que empaqueta **clases compiladas (.class), recursos (imágenes, propiedades, XML, etc.) y metadatos** en un solo archivo con extensión `.jar`.

📌 Es como un **.zip especial para Java**, que facilita la distribución y reutilización de aplicaciones o librerías.

### 🔹 Características

* Se usa principalmente para **aplicaciones de escritorio o librerías Java**.
* Se ejecuta con el comando:

  ```bash
  java -jar aplicacion.jar
  ```
* Puede contener un **archivo `MANIFEST.MF`**, donde se define la clase principal (`Main-Class`) a ejecutar.

### 🔹 Ejemplo

Supongamos que tienes una aplicación simple de consola en Java:

```java
public class Hola {
    public static void main(String[] args) {
        System.out.println("Hola desde un JAR!");
    }
}
```

Compilas y generas un `Hola.jar`. Ahora puedes distribuirlo y ejecutarlo en cualquier máquina con **JRE/JVM** instalado:

```bash
java -jar Hola.jar
```

✅ **Uso típico**: Librerías (como `mysql-connector.jar`, `spring-core.jar`) o aplicaciones de consola.

---

# 🟦 2. ¿Qué es un WAR?

👉 **WAR (Web Application ARchive)** es un archivo comprimido similar al JAR, pero pensado para **aplicaciones web en Java**.

📌 Contiene:

* Archivos **.class** (código compilado).
* Archivos **JSP/HTML/CSS/JS** (interfaz web).
* Librerías necesarias (`.jar` en `/WEB-INF/lib`).
* Configuración (`web.xml` en `/WEB-INF/`).

### 🔹 Características

* Se despliega en un **servidor de aplicaciones** (como **Apache Tomcat**, WildFly, GlassFish, JBoss, etc.).
* Es el formato estándar para aplicaciones Java EE (Jakarta EE).
* Estructura típica:

  ```
  MiApp.war
   ├── index.jsp
   ├── css/
   ├── js/
   ├── WEB-INF/
   │    ├── classes/   (clases compiladas)
   │    ├── lib/       (dependencias .jar)
   │    └── web.xml    (configuración de la app)
  ```

### 🔹 Ejemplo

Un proyecto con Servlets + JSP se empaqueta en `MiApp.war`.
Luego lo copias al directorio `webapps/` de Tomcat.
Cuando arrancas Tomcat, tu aplicación estará disponible en:

```
http://localhost:8080/MiApp
```

✅ **Uso típico**: Aplicaciones web empresariales en Java.

---

# 🟦 3. ¿Qué es Tomcat?

👉 **Apache Tomcat** es un **servidor web y contenedor de servlets** desarrollado por la Apache Software Foundation.

### 🔹 ¿Qué significa esto?

* **Servidor web**: Permite manejar **peticiones HTTP** (como lo hace Apache HTTPD o Nginx).
* **Contenedor de Servlets/JSP**: Ejecuta código Java web (Servlets, JSP, JSF).

📌 En pocas palabras: Tomcat es el "motor" que interpreta el código Java web (WAR) y lo sirve a los navegadores.

### 🔹 Funcionamiento

1. El cliente (navegador) hace una petición:

   ```
   GET /MiApp/hola
   ```
2. Tomcat recibe la petición.
3. Busca el **Servlet** correspondiente dentro del WAR desplegado.
4. Ejecuta el código Java y genera una respuesta (HTML/JSON/etc.).
5. Envía la respuesta al navegador.

### 🔹 Ejemplo básico con Servlet

```java
@WebServlet("/hola")
public class HolaServlet extends HttpServlet {
    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws IOException {
        res.getWriter().println("Hola desde Tomcat!");
    }
}
```

Empaquetas esto en un `MiApp.war`, lo despliegas en Tomcat, y accedes desde:

```
http://localhost:8080/MiApp/hola
```

✅ **Usos de Tomcat**:

* Desplegar aplicaciones web Java (WAR).
* Manejar APIs REST con frameworks como Spring MVC o Jakarta EE.
* Ideal para entornos medianos (para proyectos grandes se usan servidores más robustos como WildFly o Payara).

---

# 🟦 Diferencias entre JAR, WAR y Tomcat

| Característica  | JAR 🟦                     | WAR 🟧                                   | Tomcat 🟥                                   |
| --------------- | -------------------------- | ---------------------------------------- | ------------------------------------------- |
| Tipo de archivo | Librería / aplicación Java | Aplicación web Java                      | Servidor web / contenedor                   |
| Extensión       | `.jar`                     | `.war`                                   | No aplica                                   |
| Contiene        | Clases + recursos          | Clases + recursos + páginas web          | Motor para ejecutar WAR                     |
| Cómo se ejecuta | `java -jar archivo.jar`    | Se despliega en Tomcat (u otro servidor) | Se ejecuta con `startup.sh` o `startup.bat` |
| Ejemplo de uso  | `mysql-connector.jar`      | `MiAppWeb.war`                           | `Tomcat 10` sirviendo aplicaciones web      |

---

# 🟦 Conclusión

* **JAR** → archivo empaquetado para programas Java o librerías.
* **WAR** → archivo empaquetado para aplicaciones web Java.
* **Tomcat** → servidor web que **ejecuta y gestiona WAR**.

👉 Piensa en esto:

* Si tienes un **programa de escritorio o librería** → JAR.
* Si tienes una **aplicación web en Java** → WAR.
* Si quieres **ejecutar esa aplicación web** → necesitas Tomcat u otro servidor.
