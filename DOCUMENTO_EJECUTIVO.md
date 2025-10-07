# Documento Ejecutivo – Gestión de Reservas Hoteleras

*Docente:*  
Ing. Hely Suárez Marín  

*Integrantes:*  
- Jairo Andrés Rincón Blanco  
- Andrés Camilo Cuvides Ortega  

*Asignatura:*  
Ingeniería de Software – Modelos de Software y Documentación  

*Fecha:*  
7 de octubre de 2025  

---

## 1. Planteamiento del Problema
La gestión de reservas hoteleras enfrenta actualmente múltiples desafíos: errores en el registro manual de huéspedes, cancelaciones de última hora, sobreventa y falta de integración entre plataformas online y sistemas internos.  
Estas deficiencias generan pérdidas financieras, baja satisfacción del cliente y dificultades en la planificación operativa.  

---

## 2. Definición del Problema
- *Procesos manuales y dispersos:* Captura de datos en hojas de cálculo o formularios no integrados, duplicación de información y errores de transcripción.  
- *Falta de sincronización multicanal:* La publicación de inventario y tarifas en múltiples OTA (Online Travel Agencies) sin un sistema centralizado genera sobreventas y precios desalineados.  
- *Cancelaciones frecuentes:* Afectan la previsión de ocupación, la planificación de limpieza y el flujo de caja.  
- *Riesgos de cumplimiento y seguridad:* Procesamiento de pagos sin controles adecuados (PCI DSS) y exposición de datos sensibles de clientes.  

---

## 3. Solución Propuesta
Se plantea el desarrollo de una **Plataforma de Gestión de Reservas Hoteleras
** que integre automatización de procesos, analítica de datos y herramientas de autoservicio para los clientes.  


---

## 4. Impacto
1. *Eficiencia interna:* Reducción de sobreventas, mayor precisión en disponibilidad, optimización de precios y ocupación.  
2. *Satisfacción del cliente:* Transparencia en reservas, confirmaciones inmediatas y menor tasa de errores.  
3. *Escalabilidad y modernización:* Arquitectura modular adaptable al crecimiento.  
4. *Seguridad y cumplimiento:* Protección de datos sensibles y cumplimiento normativo.  

---

## 5. Revisión / Investigación
- Los sistemas de reservas web aumentan la eficiencia y reducen los errores de disponibilidad (Hu y Gu, 2013).  
- Algoritmos de predicción de cancelaciones alcanzan más del 80 % de precisión (Liu, 2025).  
- Estrategias de precios dinámicos incrementan los ingresos por habitación (Zhu et al., 2022).  
- Arquitecturas basadas en microservicios mejoran la disponibilidad y escalabilidad (Barua y Kaiser, 2024).  

---

# 6. Diagramas UML Realizados

## 6.1 Diagrama de Casos de Uso

El diagrama de casos de uso representa las principales interacciones entre los actores y el sistema de gestión de reservas hoteleras.

Se identifican cuatro actores principales: **Huésped**, **Recepcionista**, **Administrador** y **Sistema OTA (Online Travel Agency)**.

- El **Huésped** realiza reservas, consulta disponibilidad, modifica o cancela sus reservas.
- El **Recepcionista** gestiona registros manuales, valida pagos y asigna habitaciones.
- El **Administrador** supervisa operaciones, controla usuarios, tarifas y genera reportes.
- El **Sistema OTA** sincroniza inventarios, tarifas y disponibilidad con plataformas externas.

Este diagrama permite visualizar cómo cada actor interviene dentro del flujo del sistema, mostrando las relaciones y dependencias entre sus acciones.
 
  ![Casos de Uso](images/DIAGRAMA DE CASOS DE USO.jpeg)
---

## 6.2 Diagrama de Actividades

El diagrama de actividades muestra el flujo operativo de una reserva hotelera desde su creación hasta su cierre.

El proceso inicia con la **búsqueda de disponibilidad por parte del huésped**, seguida de la **selección de habitación y fechas**. Luego se procede a la **confirmación de reserva** y al **pago**, ya sea en línea o presencial.

Posteriormente, el **Recepcionista** valida la información, confirma la reserva en el sistema y actualiza la disponibilidad.  
Si el huésped decide cancelar, el flujo se desvía hacia la **cancelación y liberación de habitación**.

El proceso finaliza con el **check-in**, **estadía** y **check-out**, registrando automáticamente los cambios en el sistema.  
Este diagrama detalla el flujo secuencial, decisiones y actividades críticas para garantizar una operación fluida.

---

## 6.3 Diagrama de Secuencia

El diagrama de secuencia describe la interacción temporal entre los actores y el sistema durante el proceso de reserva.

1. El **Huésped** solicita disponibilidad.
2. El **Sistema** responde con opciones de habitaciones.
3. El huésped selecciona una opción y confirma la reserva.
4. El **Sistema** envía la información al **Recepcionista**, quien valida el pago.
5. En caso de confirmación, la reserva se almacena en la base de datos y se actualiza el inventario.
6. Si ocurre una cancelación, el **Sistema OTA** y el **Sistema interno** se sincronizan para reflejar los cambios.

El diagrama muestra el orden cronológico de los mensajes y la colaboración entre componentes del sistema.

---

## 6.4 Diagrama de Comunicación

### 6.4.1 Comunicación Aprobada

El diagrama de comunicación aprobada muestra cómo interactúan los componentes del sistema cuando la reserva es confirmada.

El **Huésped** solicita la reserva al **Sistema**, el cual consulta la **Base de Datos** y notifica al **Recepcionista**.  
Una vez validado el pago, se envía confirmación al huésped y se actualiza la disponibilidad tanto en el sistema interno como en las **OTAs conectadas**.

### 6.4.2 Comunicación Rechazada

En el caso de comunicación rechazada, el **Huésped** realiza una solicitud, pero el **Sistema** detecta falta de disponibilidad o error en el pago.  
Se notifica al **Recepcionista** y al huésped, permitiendo reintentar la operación o ajustar fechas.  
El proceso garantiza transparencia y evita sobreventas.

---

## 6.5 Diagrama de Paquetes

El diagrama de paquetes organiza el sistema en módulos funcionales:

- **Capa de Presentación**: interfaces web para huéspedes, recepcionistas y administradores.
- **Capa de Lógica de Negocio**: manejo de reservas, cancelaciones, facturación y sincronización OTA.
- **Capa de Datos**: almacenamiento de usuarios, habitaciones, tarifas y transacciones.

Esta estructura modular permite un mantenimiento más ágil y facilita la escalabilidad del sistema hotelero.

---

## 6.6 Diagrama de Clases

El diagrama de clases muestra las entidades principales y sus relaciones:

- **Huésped** realiza uno o varios **Pedidos de Reserva**.
- Cada **Reserva** está asociada a una **Habitación**, una **Factura** y puede tener un **Pago**.
- El **Recepcionista** gestiona las reservas y su estado.
- El **Administrador** controla usuarios, tarifas y reportes.
- El **Sistema OTA** sincroniza los datos de disponibilidad.

Cada clase contiene atributos como `id`, `nombre`, `fecha_reserva`, `estado`, y métodos para registrar, actualizar o cancelar reservas.  
Refleja la estructura base de datos del sistema hotelero.

---

## 6.7 Diagrama de Objetos

El diagrama de objetos ejemplifica instancias reales del sistema:

- **Huésped: Juan Pérez** → realiza la reserva **R001** para la **Habitación 204**.
- **Recepcionista: Laura Gómez** → confirma la reserva y registra el pago.
- **Reserva R001** → estado: *Confirmada*, fecha: *2025-10-07*.
- **Factura F001** → total: *$350.000 COP*, método: *Tarjeta*.

Muestra cómo las clases se materializan en datos reales dentro del flujo operativo, reflejando un momento concreto del sistema.

---

## 6.8 Diagrama de Estados

El diagrama de estados representa el ciclo de vida de una reserva:

1. **Creada**
2. **Pendiente de Confirmación**
3. **Confirmada**
4. **En Estadía**
5. **Finalizada**
6. **Cancelada**

Cada transición refleja acciones del huésped o del recepcionista, mostrando cómo la reserva avanza o se interrumpe dentro del ciclo del servicio hotelero.

---

## 6.9 Diagrama de Tiempo

El diagrama de tiempo muestra la evolución temporal de los eventos:

- El **Huésped** realiza la reserva.
- El **Sistema** registra los datos.
- El **Recepcionista** valida y confirma.
- Durante la estadía, el sistema actualiza el estado en tiempo real.
- Finalmente, se realiza el **check-out** y cierre de la transacción.

Permite analizar la duración y secuencia de los procesos para optimizar la gestión de recursos.

---

## 6.10 Diagrama de Componentes

El diagrama de componentes organiza la solución en niveles:

- **Front-End (Web/App)**: interfaz usada por huéspedes y personal del hotel.
- **API REST**: maneja la lógica de negocio, autenticación y control de roles.
- **Servicios de Negocio**: Reservas, Habitaciones, Pagos, Facturación, Reportes.
- **Base de Datos MySQL**: almacena información estructurada de reservas y usuarios.

Este diseño modular facilita la integración con OTAs y sistemas contables.

---

## 6.11 Diagrama de Instalación

El diagrama de instalación muestra la estructura física del sistema:

- Los usuarios (huéspedes, recepcionistas, administradores) acceden desde navegadores o aplicaciones móviles.
- El **Servidor de Aplicación (Laravel/PHP)** aloja la lógica del sistema y API REST.
- El **Servidor de Base de Datos (MySQL)** almacena toda la información de reservas y usuarios.

Refleja cómo los componentes se distribuyen e interconectan en el entorno operativo.

---

## 6.12 Diagrama de Despliegue

El diagrama de despliegue ilustra cómo se implementa el sistema en infraestructura real:

- El **Cliente Web/Móvil** se conecta al **Servidor de Aplicaciones Laravel**.
- Este se comunica con la **Base de Datos MySQL** alojada en el servidor interno o en la nube.
- Los **Módulos de Reserva**, **Gestión de Usuarios** y **Sincronización OTA** se ejecutan de forma coordinada.

Este modelo garantiza alta disponibilidad, seguridad y escalabilidad para la gestión hotelera.

---


## 7. Actores y Funciones
| *Actor*        | *Funciones principales* |
|------------------|----------------------------|
| *Huésped*      | Realiza reservas, consulta disponibilidad, gestiona cancelaciones. |
| *Recepcionista* | Registra reservas manuales, valida pagos, asigna habitaciones. |
| *Administrador* | Supervisa operaciones, gestiona usuarios, tarifas y reportes. |
| *Sistema OTA*  | Intercambia información de disponibilidad y precios. |


---

## 7. Conclusiones
El proyecto de *Gestión de Reservas de Hotel* permitirá digitalizar el proceso, reducir errores humanos, mejorar la eficiencia operativa y garantizar la seguridad de la información.  
