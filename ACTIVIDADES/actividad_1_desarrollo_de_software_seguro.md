# UNIVERSIDAD DE LAS FUERZAS ARMADAS ESPE 
## DESARROLLO DE SOFTWARE SEGURO 

**NRC:** 36902

**INTEGRANTES:** 
* Tnte. Dávila Anabel
* Martín Cordero 
* Ariel Llumiquinga

### 1.- Identificar al menos diez activos de SecureShop.

* Datos de usuarios
* Credenciales de acceso 
* Catálogo de productos
* Datos de los pedidos (órdenes de compra)
* Logs y registros de auditoría 
* API Gateway
* User Service (Microservicio de usuarios)
* Product Service (Microservicio de productos)
* Order Service (Microservicio de pedidos)
* Bases de datos de cada dominio
* Red y comunicaciones entre componentes
* Repositorio de código fuente (GitHub)
* Secretos y configuración (claves JWT, contraseñas de BD, variables de entorno)

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

### 3.- Responder:
**¿Qué consecuencias tendría para SecureShop que este activo fuera accedido, modificado o quedará indisponible?**

| Activo | Tipo | ¿Qué consecuencias tendría para SecureShop que este activo fuera accedido, modificado o quedara indisponible? |
| :--- | :--- | :--- |
| Datos de usuarios | Información / Datos | El acceso no autorizado podría exponer información personal de los clientes. Una modificación podría generar datos incorrectos o afectar las cuentas de los usuarios. Su indisponibilidad impediría consultar o gestionar correctamente la información de los clientes. |
| Credenciales de acceso | Información / Datos | Su acceso no autorizado podría permitir el ingreso a cuentas de usuarios o administradores. Una modificación podría impedir el acceso legítimo a las cuentas. Su indisponibilidad podría impedir la autenticación y el acceso a la plataforma. |
| Catálogo de productos | Información / Datos | El acceso no autorizado permitiría consultar información interna del catálogo. Una modificación podría mostrar productos, precios o existencias incorrectas. Su indisponibilidad impediría consultar o administrar los productos disponibles. |
| Datos de los pedidos (órdenes de compra) | Información / Datos | El acceso no autorizado podría exponer información de las compras realizadas. Una modificación podría alterar productos, cantidades, estados o información de los pedidos. Su indisponibilidad impediría consultar y procesar correctamente las órdenes de compra. |
| API Gateway | Servicio / Infraestructura | Un acceso o modificación no autorizada podría permitir manipular el acceso a los microservicios. Si quedara indisponible, los clientes no podrían acceder normalmente a los servicios de SecureShop, afectando las operaciones de usuarios, productos y pedidos. |
| User Service (Microservicio de usuarios) | Software / Servicio | Una modificación podría alterar la lógica de gestión de usuarios y afectar su información o autenticación. Su indisponibilidad impediría registrar, consultar o administrar usuarios, afectando las funciones que dependen de este servicio. |
| Product Service (Microservicio de productos) | Software / Servicio | Una modificación podría provocar errores en la gestión del catálogo, precios o existencias. Su indisponibilidad impediría consultar o administrar los productos, afectando la operación de la plataforma. |
| Order Service (Microservicio de pedidos) | Software / Servicio | Una modificación podría alterar la lógica de creación o gestión de pedidos. Su indisponibilidad impediría registrar, consultar o actualizar órdenes de compra, afectando directamente el proceso de venta. |
| Bases de datos de cada dominio | Infraestructura / Datos | Un acceso no autorizado podría exponer información almacenada en los diferentes dominios. Una modificación podría provocar pérdida o corrupción de datos. Su indisponibilidad impediría que los microservicios consulten o almacenen información necesaria para funcionar. |
| Repositorio de código fuente (GitHub) | Información / Software | Un acceso no autorizado podría exponer el código y configuraciones del sistema. Una modificación podría introducir errores o código malicioso en la aplicación. Su indisponibilidad dificultaría el desarrollo, mantenimiento y despliegue de nuevas versiones de SecureShop. |

### Referencias:

* National Institute of Standards and Technology. (2024). The NIST Cybersecurity Framework (CSF) 2.0. NIST
* International Organization for Standardization. (2022). ISO/IEC 27001:2022: Information security, cybersecurity and privacy protection — Information security management systems — Requirements. ISO
* OWASP Foundation. (2023). OWASP API Security Top 10. OWASP