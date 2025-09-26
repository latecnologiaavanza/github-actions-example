# 🟦 ¿Qué es el ciclo de desarrollo del software?

👉 Es el **proceso estructurado** que se sigue para **crear, mantener y evolucionar un software** desde que nace la idea hasta que se retira del uso.

📌 Incluye todas las etapas necesarias:

* **Planificación**
* **Diseño**
* **Implementación**
* **Pruebas**
* **Despliegue**
* **Mantenimiento**

---

# 🟦 Etapas principales del ciclo de desarrollo del software

### 1. **Planificación / Análisis de requisitos**

* Definir qué problema resolverá el software.
* Recoger necesidades de los usuarios (requisitos funcionales y no funcionales).
* Ejemplo: un banco necesita una app móvil para transferencias seguras.

---

### 2. **Diseño**

* Se define cómo se construirá el software.
* Incluye:

  * Arquitectura (monolito, microservicios, etc.).
  * Diseño de base de datos.
  * Diagramas UML.
* Ejemplo: decidir que la app bancaria usará **microservicios con Spring Boot** y **base de datos PostgreSQL**.

---

### 3. **Implementación (Codificación)**

* Los programadores escriben el código fuente siguiendo el diseño.
* Ejemplo: desarrollar los módulos de login, transferencias, historial de transacciones.

---

### 4. **Pruebas**

* Se verifica que el software funcione como se espera.
* Tipos de pruebas:

  * Unitarias (cada módulo).
  * Integración (módulos juntos).
  * Aceptación (validar con el cliente).
* Ejemplo: probar que no se pueda transferir dinero sin saldo suficiente.

---

### 5. **Despliegue**

* Se pone el software en producción para que los usuarios lo usen.
* Ejemplo: la app bancaria ya está disponible en Google Play y App Store.

---

### 6. **Mantenimiento**

* Corrección de errores.
* Actualizaciones de seguridad.
* Nuevas funcionalidades.
* Ejemplo: añadir **pago de servicios** en la app bancaria.

---

# 🟦 Modelos de ciclo de desarrollo

Existen varias **metodologías** que organizan estas etapas:

1. **Cascada (Waterfall)** → lineal, cada fase termina antes de empezar la otra.
2. **Iterativo / Incremental** → se construye por partes.
3. **Ágil (Scrum, Kanban)** → desarrollo en ciclos cortos (*sprints*), con entregas continuas.
4. **DevOps** → combina desarrollo + operaciones, con CI/CD para despliegues automáticos.

---

# 🟦 Ejemplo sencillo

Imagina que quieres crear un **sistema de reservas para un cine**:

1. Planificación → el cliente quiere que se reserven entradas online.
2. Diseño → se usará Java + Spring Boot + MySQL.
3. Implementación → programar login, compra de entradas, selección de asientos.
4. Pruebas → verificar que no se pueda reservar la misma butaca dos veces.
5. Despliegue → subir la app al servidor.
6. Mantenimiento → añadir promociones y descuentos.

---

# 🟦 Conclusión

✔️ El **ciclo de desarrollo del software** es el camino completo desde la **idea** hasta la **ejecución y mantenimiento** del software.
✔️ Garantiza que el software sea **útil, de calidad y mantenible**.
✔️ Se puede aplicar con distintos modelos: **cascada, ágil, DevOps**.
