# Celis&Ud

**Celis&Ud** es una plataforma web *full-stack* diseñada con el propósito social y técnico de centralizar, gestionar y descubrir establecimientos de restauración con opciones 100% seguras sin gluten. La aplicación resuelve un problema crítico para el colectivo celíaco mediante un ecosistema robusto que combina un portal de búsqueda y feedback para el usuario final con un backoffice avanzado de administración.

---

## Características Principales

### Portal de Usuario
* **Búsqueda Avanzada y Filtrado:** Localización ágil de restaurantes basada en categorías, localización geográfica y etiquetas específicas de seguridad alimentaria.
* **Comunidad y Feedback:** Sistema dinámico para que los usuarios registrados dejen reseñas detalladas, evalúen su experiencia y aporten valor a la comunidad.
* **Gestión de Perfil:** Panel personalizado donde el usuario puede administrar sus datos de cuenta y personalizar su perfil mediante un sistema de avatares dinámicos.

### Panel de Administración (Backoffice)
* **Control del Catálogo:** Altas, bajas y modificaciones en tiempo real de los establecimientos y sus cartas/menús sin gluten.
* **Moderación del Sistema:** Supervisión activa de las reseñas y valoraciones de los usuarios para mitigar falsos testimonios y mantener la fiabilidad de la plataforma.
* **Gestión de Usuarios:** Panel de control de credenciales, roles y permisos dentro de la aplicación.

---

## Stack Tecnológico

* **Backend:** Java 17, Spring Boot 3.x, Spring Data JPA, Spring Security.
* **Persistencia y Datos:** Hibernate, Base de datos relacional SQL (MySQL / PostgreSQL), Pool de conexiones HikariCP.
* **Frontend:** HTML5, CSS3, JavaScript, integración de vistas mediante motor de plantillas dinámico ([Thymeleaf / Framework del proyecto]).
* **Gestión de Dependencias:** Apache Maven.
* **Control de Versiones:** Git & GitHub.

---

## Arquitectura y Desafíos Técnicos Destacados

### 1. Modelo de Datos y Relaciones Complejas (JPA/Hibernate)
Se diseñó un mapeo de entidades relacionales meticuloso para soportar la lógica de negocio sin comprometer el rendimiento:
* Relaciones `@OneToMany` y `@ManyToOne` para la correcta vinculación entre los Usuarios, los Restaurantes y las Reseñas (`Reviews`), aplicando estrategias de carga perezosa (`FetchType.LAZY`) para optimizar el tráfico de red y las consultas SQL.
* Ciclos de vida de entidades controlados para garantizar la integridad referencial en cascada ante bajas del sistema.

### 2. Algoritmo de Ranking Seguro (*Secure Restaurants*)
Uno de los pilares del backend es el algoritmo automatizado de puntuación. Este componente evalúa de forma ponderada:
* El volumen total de reseñas del establecimiento.
* La consistencia de las calificaciones de seguridad alimentaria frente a la puntuación de calidad general.
* Priorización automática en las búsquedas de aquellos locales con mayores garantías verificadas por la comunidad, reduciendo el riesgo de exposición al gluten.

### 3. Sistema de Almacenamiento de Avatares
Implementación de un flujo dedicado en el backend para la subida y renderizado de imágenes de perfil de usuario. El sistema gestiona la validación del formato de archivo, la persistencia en servidor/directorio de recursos y el enlace dinámico con la entidad de usuario en la base de datos.

### 4. Seguridad y Control de Accesos
La aplicación integra **Spring Security** para segmentar el acceso a los recursos web mediante una arquitectura basada en roles (`ROLE_USER`, `ROLE_ADMIN`):
* Protección de rutas críticas y endpoints REST mediante configuraciones explícitas de filtros de seguridad.
* Cifrado robusto de contraseñas de usuario antes de su almacenamiento en base de datos.

---

## Desarrollo y Colaboración

Este proyecto ha sido desarrollado con fines académicos en la **Universidad Rey Juan Carlos (URJC)**

---

## Instalación y Despliegue Local

### Prerrequisitos
Antes de comenzar, asegúrate de tener instalado en tu equipo:
* **Java JDK 17**
* **Apache Maven 3.x**
* Un servidor de bases de datos activo (MySQL / PostgreSQL)

### Pasos para la ejecución
1. **Clonar el repositorio:**
   ```bash
   git clone [https://github.com/AlexisMaestroLopez/Celis-Ud.git](https://github.com/AlexisMaestroLopez/Celis-Ud.git)
   cd Celis-Ud
