# FlowerOS Mobile - Sistema Operativo Móvil

**FlowerOS Mobile** es un simulador de sistema operativo móvil desarrollado con **Electron**. 

El proyecto simula los conceptos clave de un sistema operativo móvil actual, como la gestión de procesos en memoria RAM, administración de energía y batería, un sistema de archivos virtual persistente (VFS), manejo de sensores/GPS y un conjunto completo de aplicaciones integradas en una interfaz tipo smartphone.

---

## Características Principales

### Núcleo del Sistema Operativo (`os-core.js`)
* **Gestor de Procesos y Memoria (ProcessManager):**
  * Simula una memoria RAM total de 2048 MB (400 MB reservados para el SO).
  * Control del ciclo de vida de procesos: `Running`, `Paused`, `Terminated`.
  * Mecanismo de liberación automática de memoria (kill de procesos en segundo plano) cuando el uso de RAM supera el 85%.
* **Gestor de Energía y Batería (PowerManager):**
  * Tasa de consumo de batería dinámica en función de la cantidad de aplicaciones en ejecución.
  * Modo de ahorro de batería automático/manual.
  * Transición de estados de encendido, bloqueo por PIN, reinicio y apagado completo del dispositivo.
* **Sistema de Archivos Virtual (VFS - FileSystemManager):**
  * Persistencia de datos en formato JSON (`.os-vfs.json`).
  * Almacenamiento local para archivos de texto, contactos, conversaciones, eventos de calendario y alarmas.

---

## Aplicaciones Integradas

El sistema operativo cuenta con **15 aplicaciones funcionales**:

| Aplicación | Descripción |
| :--- | :--- |
| **Ajustes** | Configuración de PIN de seguridad, temas, fondos de pantalla SVG, hora y GPS. |
| **Opciones de Desarrollador** | Monitor en tiempo real de RAM, lista de PCB de procesos, consumo de batería y logs. |
| **Explorador de Archivos** | Creación, lectura, edición y eliminación de archivos en el VFS. |
| **Cámara** | Simulación de captura fotográfica mediante diálogo nativo de Electron (IPC). |
| **Galería** | Visualización de imágenes almacenadas en el sistema. |
| **Navegador** | Simulador de navegador web con historial persistente. |
| **Teléfono** | Marcador telefónico, simulación de llamadas y registro de llamadas. |
| **Mensajes** | Envío y recepción de mensajes SMS simulados. |
| **Contactos** | Agenda de contactos. |
| **Música** | Simulador de reproductor de audio interactivo. |
| **Reloj** | Hora actual, cronómetro, temporizador y alarmas. |
| **Calculadora** | Calculadora. |
| **Calendario** | Calendario con agenda de eventos. |
| **Telegram** | Integración de Telegram Web. |
| **GPS Vzla** | Geolocalización simulada (coordenadas, altitud y ciudad en Venezuela). |

---

## Requisitos Previos

Antes de ejecutar el proyecto, asegúrate de tener instalado:

* [Node.js](https://nodejs.org/) (versión 16.0 o superior)

---

## Instalación y Ejecución

Sigue estos pasos para clonar y ejecutar el proyecto en tu máquina local:

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/AleC2111/Sistema-operativo-movil.git
   cd Sistema-operativo-movil
   ```

2. **Instalar las dependencias:**
   ```bash
   npm install
   ```

3. **Iniciar la aplicación:**
   ```bash
   npm start
   ```

---

## Estructura del Proyecto

```text
Sistema-operativo-movil/
├── index.html           # Estructura HTML de la pantalla, frame del móvil y UI de apps
├── index.js             # Proceso principal de Electron (Main process, IPC, permisos)
├── styles.css           # Estilos CSS3 (animaciones, temas, layout del smartphone)
├── js/
│   ├── os-core.js       # Núcleo del SO: VFS, ProcessManager, PowerManager y sensores
│   ├── apps.js          # Lógica e implementación de las 15 aplicaciones integradas
│   └── renderer.js      # Controlador de UI del proceso de renderizado y barra de estado
├── package.json         # Configuración del proyecto y dependencia de Electron
└── README.md            # Documentación del proyecto
```
