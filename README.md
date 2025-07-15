# Dashboard: “Onboarding y Cancelaciones de Cuentas de Usuario”

## 🎯 Tablero en Power BI

He desarrollado un tablero dinámico en Power BI que **muestra en tiempo real los procesos de onboarding y las cancelaciones de cuentas de usuarios** de una app para una empresa del **sector Fintech**.
Con el fin de **evaluar la efectividad del proceso de incorporación de nuevos usuarios** (onboarding) y **detectar patrones o causas de cancelación de cuentas**, facilitando decisiones basadas en datos en tiempo real.

## 💡 Ventajas para el negocio:

- **Optimización de estrategias de adquisición y retención:** permite identificar qué segmentos tienen mayor cancelación.


- **Monitoreo proactivo:** la empresa puede actuar de forma inmediata ante caídas en el onboarding o aumentos en las cancelaciones.


- **Toma de decisiones basada en datos:** facilita la evaluación del impacto de campañas, políticas o cambios en la app.


- **Segmentación precisa de usuarios:** ayuda a diseñar experiencias personalizadas según el tipo de cuenta o persona.


- **Detección de tendencias temporales:** con la evolución mensual del onboarding, es posible anticipar comportamientos estacionales o problemas recurrentes.
  

## 📊 Información Visualizada

El tablero presenta los siguientes indicadores clave:

- **Total de cuentas creadas**


- **Total de clientes activos:** usuarios que han utilizado algún producto de la app, evidenciado al menos un movimiento/transacción en su cuenta.


- **Total de clientes inactivos:** usuarios que no han realizado movimientos en su cuenta durante un período determinado.


- **Gráfico de líneas con la evolución** diaria, mensual o trimestral de altas y bajas de cuentas.


- **Dos gráficos de anillos que segmentan:**

    **Cuentas comerciales vs. personales**

    **Personas físicas vs. personas jurídicas**


**Toda esta información puede ser filtrada por:**

- Rango de fechas

- Tipo de producto

- Jurisdicción

- Estado de la cuenta

- Tipo de cuenta (comercial o personal)

- Tipo de usuario (PF o PJ)

## ⚙️ Procedimiento de Desarrollo

### Conexión a Fuentes de Datos

- Conexión a una base de datos web para obtener los datos de usuarios, onboarding y cancelaciones.

- Conexión a una base de datos PostgreSQL para acceder a:

    - Tabla de movimientos/transacciones de usuarios

    - Tabla de cargas impositivas o comisiones por operaciones

Se utilizó el modo **Direct Query** para optimizar el rendimiento, reduciendo el uso de almacenamiento y acelerando la actualización de datos.

### Transformación y Limpieza de Datos

Se realizaron los siguientes pasos:

- Eliminación de columnas innecesarias

- Corrección de tipos de datos

- Manejo de valores nulos, duplicados y errores

- Unificación de formatos (fechas, monedas, etc.)

- Creación de columnas condicionales para identificar si un movimiento fue "completado" o "fallido", según códigos definidos en la base de datos

  <img width="941" height="159" alt="image" src="https://github.com/user-attachments/assets/7bca26e5-7a2f-415f-bcf7-0cf34648c25b" />


- Adición de una columna personalizada para mostrar los montos con decimales y su signo (+/-), según si se trata de ingresos o egresos

<img width="947" height="604" alt="image" src="https://github.com/user-attachments/assets/9a75b0ae-d9bd-4663-96af-e2a4bbf1cb6c" />


### Modelado de Datos

- Relación entre la tabla de “Usuarios” y la de “Movimientos de Usuarios” mediante un ID común.

- Relación adicional entre “Movimientos de Usuarios” y la tabla de “Cargas Impositivas/Comisiones”.

- Creación de una tabla de referencia de Jurisdicciones, relacionada con “Movimientos de Usuarios”.

<img width="925" height="693" alt="image" src="https://github.com/user-attachments/assets/dea263b2-cdc7-414f-8eb0-d89b4c62126b" />


### Diseño de Visualizaciones

Se priorizó una presentación clara, funcional y atractiva, con las siguientes decisiones de diseño:

- **Tarjetas** para mostrar cantidad total de usuarios, activos e inactivos

- **Gráfico de líneas** para representar la evolución de altas y bajas

- **Gráficos de anillos** para segmentar tipos de cuenta y tipo de usuario

- **Segmentaciones de datos** (Slicers) para aplicar filtros de forma intuitiva

- Aplicación de buenas prácticas de visualización: paleta de colores, alineación, espaciado y jerarquía visual

- Configuración de interacciones entre objetos visuales para permitir el cruce de filtros, entre los objetos visuales de la página, de tal manera que haciendo click en cualquier objeto visual, automáticamente se filtren el resto de los objetos de la página, permitiendo un Tablero completamente dinámico y funcional.

    Ejemplo de Tablero estableciendo un filtro de fecha:
      <img width="935" height="522" alt="image" src="https://github.com/user-attachments/assets/ac6f4e0f-9904-4d53-b625-731a78cc788d" />

    Ejemplo de Tablero filtrando por fecha y teniendo en cuenta sólo las cuentas comerciales, al realizar un click sobre el gráfico de anillos ”Account Types”:
    <img width="936" height="523" alt="image" src="https://github.com/user-attachments/assets/a2c38f31-13fd-426a-b9fb-2923228b1bf3" />


### Publicación y Distribución

**1)** Publicación del reporte en el servicio Power BI (Power BI Service)

**2)** Configuración de actualizaciones automáticas

**3)** Asignación de permisos de acceso a los stakeholders

