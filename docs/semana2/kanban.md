# Guía de Configuración y Enlace de Tablero Kanban — GitHub Projects

> [!NOTE]  
> **Aclaración de buenas prácticas:** Este documento no pretende sustituir el tablero interactivo real del equipo por una tabla estática en Markdown. Su propósito es servir como guía operativa para la creación, configuración y vinculación del **GitHub Project público** oficial del proyecto, tal como lo exige el syllabus del programa *Blockchain Builders 101*.

---

## 1. Pasos para crear el GitHub Project

1. Dirigirse a la pestaña **Projects** del repositorio [`santiagofrancodev/ProyectoBase`](https://github.com/santiagofrancodev/ProyectoBase) (o a nivel de la organización/perfil).
2. Hacer clic en **New project** y seleccionar la plantilla **Board** (Tablero).
3. Nombrar el proyecto: **`Ayuda con Destino — MVP Kanban`**.
4. En la configuración de visibilidad del proyecto (*Project Settings*), asegurarse de que esté marcado como **Public** (Público) para permitir la evaluación por parte de los mentores de BB101.
5. Vincular el proyecto al repositorio `ProyectoBase`.

---

## 2. Configuración de Columnas del Flujo de Trabajo

El tablero debe estructurarse con cinco columnas alineadas con el ciclo ágil de desarrollo del bootcamp:

| Columna | Propósito | Criterio de entrada |
| :--- | :--- | :--- |
| **`Backlog`** | Depósito general de ideas, historias de usuario formuladas y tareas futuras. | Historias de usuario redactadas en Markdown pendientes de priorización formal. |
| **`Por hacer (To Do)`** | Tareas priorizadas para el sprint o la semana actual con criterios de aceptación claros. | Tarea con alcance definido, asignada a un integrante y lista para ser abordada. |
| **`En curso (In Progress)`** | Tareas activas en desarrollo en este momento. Límite de trabajo en progreso recomendado: máximo 2 tareas por persona. | La persona ha comenzado la redacción documental o el modelado técnico. |
| **`Revisión (Review)`** | Entregables o documentos finalizados que requieren la lectura crítica y aprobación del otro integrante. | Pull Request abierto o documento en borrador listo para contrastación y feedback. |
| **`Hecho (Done)`** | Tareas completadas que cumplen al 100% los criterios de aceptación y cuentan con el commit respectivo. | Archivo fusionado en la rama principal o entregable validado y publicado. |

---

## 3. Automatización y Vinculación de Issues

- Cada Historia de Usuario (`US-01`, `US-02`, etc.) definida en [`ProductBlueprint.md`](ProductBlueprint.md) debe convertirse en un **Issue** dentro del repositorio.
- Las tareas deben etiquetarse usando labels estandarizados:
  - `documentation` / `discovery`
  - `must-have` / `should-have` / `could-have`
  - `semana-1` / `semana-2` / `semana-3`
- Al abrir un Pull Request que resuelva una tarea, incluir la palabra clave correspondiente (ej. `Closes #12`) para que GitHub mueva automáticamente la tarjeta a la columna `Hecho`.

---

## 4. Enlace al Tablero Oficial

- **URL del GitHub Project:** `[Pendiente de creación por Santiago Franco y enlace aquí]`
- **Responsable de mantenimiento del tablero:** Santiago Franco y Gustavo Arcila.
