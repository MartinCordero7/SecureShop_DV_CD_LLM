
# UNIVERSIDAD DE LAS FUERZAS ARMADAS ESPE 
## DESARROLLO DE SOFTWARE SEGURO 

**NRC:** 36902

**INTEGRANTES:** 
* Tnte. Dávila Anabel
* Martín Cordero 
* Ariel Llumiquinga

### 1.- Identificar al menos quince activos de SecureShop.

1. Datos de usuarios
2. Credenciales de acceso 
3. Catálogo de productos
4. Datos de los pedidos (órdenes de compra)
5. API Gateway
6. User Service (Microservicio de usuarios)
7. Product Service (Microservicio de productos)
8. Order Service (Microservicio de pedidos)
9. Bases de datos de cada dominio
10. Repositorio de código fuente (GitHub)
11. Logs y registros de auditoría
12. Red y comunicaciones entre componentes (Tráfico interno)
13. Secretos y configuración (claves JWT, contraseñas, variables de entorno)
14. Clúster de contenedores (Infraestructura Kubernetes/Docker)
15. Pasarela de pagos (Integración externa de facturación)

### 2.- Clasificar cada activo según:

| Activo | Clasificación |
| :--- | :--- |
| Datos de usuarios | Datos / Información |
| Credenciales de acceso | Datos / Información |
| Catálogo de productos | Datos / Información |
| Datos de los pedidos (órdenes de compra) | Datos / Información |
| API Gateway | Servicio / Infraestructura |
| User Service (Microservicio de usuarios) | Software / Servicio |
| Product Service (Microservicio de productos) | Software / Servicio |
| Order Service (Microservicio de pedidos) | Software / Servicio |
| Bases de datos de cada dominio | Infraestructura / Datos |
| Repositorio de código fuente (GitHub) | Información / Software |
| Logs y registros de auditoría | Información / Datos |
| Red y comunicaciones entre componentes | Infraestructura |
| Secretos y configuración | Información / Datos |
| Clúster de contenedores (Kubernetes/Docker) | Infraestructura |
| Pasarela de pagos | Servicio |

### 3.- Responder:
**¿Qué consecuencias tendría para SecureShop que este activo fuera accedido, modificado o quedara indisponible?**

| Activo | Tipo | Consecuencias (Acceso, Modificación, Indisponibilidad) |
| :--- | :--- | :--- |
| **Datos de usuarios** | Información / Datos | El acceso expone información personal. Su modificación corrompe perfiles. Su indisponibilidad impide consultar a los clientes. |
| **Credenciales de acceso** | Información / Datos | El acceso permite suplantación de identidad. Su modificación bloquea a usuarios legítimos. Su indisponibilidad impide el inicio de sesión. |
| **Catálogo de productos** | Información / Datos | El acceso expone métricas de negocio. Su modificación altera precios. Su indisponibilidad impide ver qué comprar. |
| **Datos de los pedidos** | Información / Datos | El acceso expone historiales de compra. Su modificación permite fraude en envíos. Su indisponibilidad detiene el procesamiento de ventas. |
| **API Gateway** | Servicio / Infraestructura | El acceso/modificación permite manipular el enrutamiento. Su indisponibilidad desconecta a los clientes de todos los microservicios. |
| **User Service** | Software / Servicio | Modificarlo altera la lógica de gestión de cuentas. Su indisponibilidad impide registrar, consultar o administrar usuarios. |
| **Product Service** | Software / Servicio | Modificarlo corrompe la validación de stock. Su indisponibilidad impide gestionar el catálogo tecnológico de la empresa. |
| **Order Service** | Software / Servicio | Modificarlo altera la creación de compras. Su indisponibilidad paraliza las ventas, siendo el mayor impacto al negocio. |
| **Bases de datos** | Infraestructura / Datos | El acceso extrae datos masivos. La modificación corrompe la información central. Su indisponibilidad tumba la persistencia del sistema. |
| **Repositorio GitHub** | Información / Software | El acceso filtra la propiedad intelectual y vulnerabilidades. La modificación inyecta código malicioso. Su indisponibilidad detiene el desarrollo. |
| **Logs de auditoría** | Información / Datos | El acceso expone comportamientos del sistema. La modificación oculta rastros de atacantes. Su indisponibilidad impide investigar incidentes. |
| **Red y comunicaciones** | Infraestructura | El acceso permite espiar datos en tránsito (sniffing). La modificación permite ataques Man-in-the-Middle. La indisponibilidad aísla los microservicios. |
| **Secretos y config.** | Información / Datos | El acceso otorga llaves maestras al atacante (bases de datos, JWT). La modificación desconfigura el sistema. Su indisponibilidad impide que los servicios arranquen. |
| **Clúster Kubernetes** | Infraestructura | El acceso da control total del entorno. La modificación permite desplegar malware (mineros cripto). La indisponibilidad tumba toda la plataforma. |
| **Pasarela de pagos** | Servicio | El acceso no autorizado a los tokens de pago genera fraude. La modificación altera la confirmación de pagos. La indisponibilidad impide cobrar el dinero. |

### 4.- Análisis de Amenazas, Controles y Etapas de Implementación

| Activo | Amenaza (x3) | Mecanismo de Control | Etapa de Implementación |
| :--- | :--- | :--- | :--- |
| **1. Datos de usuarios** | 1. Robo masivo por inyección SQL. | Uso de consultas parametrizadas (ORM). | Implementación / Verificar |
| | 2. Interceptación de datos en tránsito. | Cifrado de canal con TLS/HTTPS. | Diseño / Despliegue |
| | 3. Fuga de datos por personal interno. | Enmascaramiento de datos sensibles. | Diseño |
| **2. Credenciales** | 1. Ataques de fuerza bruta. | Límite de espera (Rate limiting / Lockout). | Requisitos (NF) / Diseño |
| | 2. Robo de contraseñas por phishing. | Autenticación de doble factor (2FA). | Requisitos (F) |
| | 3. Brecha de la base de datos de claves. | Almacenamiento con Hashing fuerte (Bcrypt) + Salt. | Implementación |
| **3. Catálogo de productos** | 1. Modificación maliciosa de precios. | Control de acceso basado en roles (RBAC). | Requisitos (F) / Diseño |
| | 2. Extracción de datos masiva (Scraping). | Implementación de WAF y CAPTCHA. | Despliegue / Operación |
| | 3. Subida de imágenes con malware. | Validación de entradas y sanitización. | Implementación |
| **4. Datos de pedidos** | 1. Manipulación del estado de pago (IDOR). | Validación de autorización en el backend. | Diseño / Implementación |
| | 2. Pérdida de registros de facturación. | Backups automatizados y redundancia. | Operación (Monitorizar) |
| | 3. Repudio de compra por el usuario. | Firmas digitales y trazabilidad de sesión. | Diseño |
| **5. API Gateway** | 1. Denegación de servicio (DDoS). | Throttling y balanceo de carga. | Diseño / Despliegue |
| | 2. Evasión de la autenticación. | Validación estricta de tokens JWT en el Gateway. | Implementación |
| | 3. Exposición de puertos inseguros. | Hardening: eliminar puertos innecesarios. | Despliegue |
| **6. User Service** | 1. Escalada de privilegios. | Principio de mínimo privilegio. | Diseño / Implementación |
| | 2. Dependencias con vulnerabilidades. | Gestión de dependencias (SCA automatizado). | Despliegue |
| | 3. Caída por alta concurrencia. | Pruebas de carga y autoescalado. | Operación |
| **7. Product Service** | 1. Inyección de código (XSS) en descripción. | Sanitización y codificación de salidas. | Implementación |
| | 2. Alteración de datos en capas. | Uso de DTO (Data Transfer Object) estructurados. | Implementación |
| | 3. Errores de lógica en stock. | Pruebas de código estáticas (SAST) y dinámicas (DAST). | Implementación (Verificar) |

### Referencias:

* National Institute of Standards and Technology. (2024). The NIST Cybersecurity Framework (CSF) 2.0. NIST
* International Organization for Standardization. (2022). ISO/IEC 27001:2022: Information security, cybersecurity and privacy protection — Information security management systems — Requirements. ISO
* OWASP Foundation. (2023). OWASP API Security Top 10. OWASP