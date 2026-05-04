# AgentHub Admin Dashboard - Especificaciones Técnicas (v1.1.0)

## 1. Descripción del Producto
AgentHub es una plataforma SaaS para el alquiler de agentes de IA. Este panel permite gestionar la operativa interna: usuarios, agentes, habilidades (skills), contratos y errores de ejecución.

## 2. Stack Tecnológico
- HTML5 / Vanilla JavaScript (ES6+).
- CSS: Tailwind CSS v3.x vía CDN.
- Persistencia: LocalStorage para el estado del Modo Oscuro.

## 3. Reglas de Interfaz y UX
- **Modo Oscuro:** Implementado mediante la clase `.dark` en el elemento raíz.
- **Navegación:** Sidebar persistente con 6 secciones. Los cambios de vista se gestionan mediante manipulación del DOM (clases `hidden`).
- **Modales:** Deben incluir un backdrop semi-transparente con desenfoque, cierre mediante botón dedicado y cierre al hacer clic fuera del contenedor (backdrop).
- **Dropdowns:** Menús de acción (`⋮`) que se cierran automáticamente al perder el foco o hacer clic fuera.
- **Transiciones:** Los elementos colapsables (Skills) deben usar `max-height` para una expansión fluida.

## 4. Requisitos de Datos (Hardcoded)
- **Dashboard:** 4 tarjetas de métricas (Ingresos, Pérdidas, Activos, Fallando) y un área de gráfico.
- **Usuarios:** Mínimo 5 registros con nombre, email, plan y estado.
- **Agentes:** Mínimo 4 registros con propietario, estado y lista de habilidades expandible.
- **Skills:** Catálogo de 4 habilidades con descripción y contador de uso.
- **Contrataciones:** Mínimo 4 registros con desglose de precios en modal.
- **Log de Errores:** Mínimo 6 registros categorizados por severidad (Critical, Warning, Info).

## 5. Criterios de Aceptación
1. El toggle de modo oscuro cambia la estética de todo el panel y persiste tras recargar.
2. Cada sección es accesible desde el sidebar con feedback visual de "estado activo".
3. Al menos 4 secciones distintas activan modales funcionales.
4. Las skills de los agentes están ocultas inicialmente y se revelan con animación.