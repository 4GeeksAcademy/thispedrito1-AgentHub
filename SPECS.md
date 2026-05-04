# AgentHub Admin Dashboard - Especificaciones Técnicas

## 1. Descripción del Producto
AgentHub es una plataforma SaaS B2B que permite alquilar agentes de IA preconfigurados. Este panel de administración es la herramienta interna para que los operadores de AgentHub gestionen usuarios, supervisen la salud de los agentes, controlen el catálogo de "skills" y auditen las contrataciones y errores del sistema.

## 2. Stack Tecnológico y Restricciones
- **Lenguajes:** HTML5 semántico y JavaScript Vanilla (ES6+).
- **Estilos:** Tailwind CSS v3.x mediante CDN.
- **Iconografía:** SVGs integrados (Heroicons style).
- **Interactividad:** JS puro sin frameworks ni librerías externas.
- **Persistencia:** Modo oscuro persistente vía `localStorage`.
- **Datos:** 100% Hardcoded (Mock data).

## 3. Especificaciones por Sección

### 3.1 Dashboard
1. **Tarjetas de Métricas:** Cuatro contenedores en grid (1x1 móvil, 2x2 tablet/desktop). Cada una con: Icono de fondo suave, etiqueta (ej. "Ingresos"), valor principal destacado y un indicador de tendencia neutro.
2. **Alertas Visuales:** La tarjeta de "Agentes Fallando" debe usar colores de advertencia (Rojo/Amber) para diferenciarla de las métricas de negocio.
3. **Weekly Activity:** Placeholder de gráfico mediante un contenedor con bordes discontinuos (`border-dashed`), fondo grisáceo muy tenue y un texto centrado "Activity Chart Placeholder".

### 3.2 Gestión de Usuarios
1. **Tabla de Datos:** Columnas para Nombre, Email, Plan (Badge: Free, Pro, Enterprise) y Estado (Badge: Activo, Inactivo).
2. **Acciones:** Botón de tres puntos verticales (`⋮`) que despliega un menú flotante absoluto.
3. **Modal de Detalle:** Al activar "Ver detalle", se muestra un modal centrado con el perfil completo (avatar ficticio, fecha de registro y última conexión).

### 3.3 Gestión de Agentes
1. **Lista de Agentes:** Cada fila muestra el agente y su propietario. El estado (Activo/Inactivo/Failing) debe usar indicadores tipo "dot" (punto de color).
2. **Skills Colapsables:** Un botón "View Skills" que expande un área con `transition-all` y `duration-300`, mostrando las habilidades como etiquetas (badges) pequeñas.
3. **Configuración:** El modal "Configurar" debe contener un elemento `<textarea>` con el "System Prompt" del agente, simulando un entorno de edición de instrucciones de IA.

### 3.4 Catálogo de Skills
1. **Definición Contextual:** Un bloque informativo (Card con fondo de color suave) que explica que las "Skills" son módulos de código (herramientas) que los agentes invocan vía herramientas (function calling).
2. **Métricas de Uso:** Cada skill indica el número de agentes que la tienen instalada (ej: "Used by 12 agents").
3. **Grid de Habilidades:** Presentación en tarjetas con icono, nombre y descripción corta de la funcionalidad.

### 3.5 Contrataciones (Hiring)
1. **Registro Financiero:** Tabla que detalla Cliente, Agente, Skills incluidas, Rango de fechas y el Monto Total.
2. **Desglose de Precios:** El modal "Ver detalle" debe mostrar una lista tipo factura donde se vea el precio base del agente + el coste adicional por cada skill contratada.

### 3.6 Log de Errores
1. **Severidad Visual:** Los errores se categorizan en "Critical" (Rojo), "Warning" (Amarillo) e "Info" (Azul) mediante badges de alta visibilidad.
2. **Trazabilidad:** Timestamp en formato `YYYY-MM-DD HH:mm:ss`.
3. **Acción de Resolución:** El botón "Marcar como resuelto" debe simular un cambio de estado visual (ej: reducir opacidad de la fila).

## 4. Inventario de Componentes UI
- **Sidebar:** Navegación lateral fija con estados `active:bg-indigo-600`.
- **Metric Card:** Cuadrado con sombra, padding 6 y bordes redondeados.
- **Action Dropdown:** Menú `z-50` con sombras profundas y cierre automático.
- **Modal Overlay:** Fondo oscuro semi-transparente (`bg-opacity-50`) con efecto de desenfoque (`backdrop-blur`).
- **Badge:** Pequeños contenedores con texto en mayúsculas y bordes redondeados (`rounded-full`).

## 5. Criterios de Aceptación
1. El toggle de **Modo Oscuro** debe añadir/quitar la clase `.dark` al elemento `<html>`.
2. Los **Dropdowns** deben cerrarse si el usuario hace clic en cualquier lugar fuera del menú.
3. Los **Modales** deben bloquear el scroll del cuerpo y cerrarse al hacer clic en el fondo oscuro.
4. La **Transición de Skills** en la sección de Agentes debe ser fluida (no un salto brusco).
5. Los datos de agentes (ej. "Nova-7") deben ser consistentes si aparecen en múltiples vistas.